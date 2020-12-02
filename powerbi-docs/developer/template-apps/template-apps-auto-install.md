---
title: Automatiser konfigurationen af installationen af skabelonprogrammer for dine kunder
description: Få mere at vide om automatisering af konfigurationen af installationen af skabelonprogrammer.
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: ca5db6ed7a07d5a6fb10133285378e8318527464
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386086"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>Automatiseret konfiguration af installationen af et skabelonprogram

Skabelonprogrammer er en fantastisk måde for kunder at begynde at få indsigt i deres data på. Med skabelonprogrammer kommer de hurtigt i gang, da de får indsigt i deres data og rapporter, der er oprettet på forhånd, som de kan tilpasse, hvis de vil.

Kunderne ved ikke altid, hvordan de skal få indsigt i deres data, og det kan være svært for dem at skulle levere disse oplysninger, når de installerer et skabelonprogram.

Hvis du er datatjenesteudbyder og har oprettet et skabelonprogram for at hjælpe dine kunder med at komme i gang med at arbejde med deres data på din tjeneste, kan du gøre det nemmere for dem at installere dit skabelonprogram ved at automatisere konfigurationen af parametrene for dit skabelonprogram. Når kunden logger på din portal, klikker de på et særligt link, du har forberedt. Dette starter automatiseringen, hvor de nødvendige oplysninger indsamles, parametrene for skabelonprogrammet forudkonfigureres, og kunden omdirigeres til vedkommendes Power BI-konto, hvor vedkommende kan installere programmet. Alt, hvad kunderne skal gøre, er at klikke på Installér, godkende i forhold til deres datakilde, og så er de klar! 

Denne kundeoplevelse er illustreret nedenfor.

![Illustration af brugeroplevelsen med automatisk programinstallation.](media/template-apps-auto-install/high-level-flow.png)

Denne artikel indeholder en beskrivelse af det grundlæggende flow, forudsætningerne samt de primære trin og API'er, der skal bruges til at automatisere konfigurationen af installationen af et skabelonprogram. Hvis du foretrækker at komme i gang med det samme, kan du dog springe til dette [selvstudium](template-apps-auto-install-tutorial.md), hvor du automatiserer konfigurationen af installationen af skabelonprogrammet ved hjælp af et prøveprogram, vi har klargjort, og som bruger Azure Functions.

## <a name="basic-flow"></a>Grundlæggende flow

Det grundlæggende flow til automatisering af konfigurationen af installationen af et skabelonprogram er som følger:

1. Brugeren logger på ISV'ens portal og klikker på det leverede link. Så startes det automatiserede flow. I denne fase forberedes den brugerspecifikke konfiguration på ISV'ens portal.

2. ISV'en henter et token **kun til programmer** baseret på en [tjenesteprincipal (token kun til programmer)](../embedded/embed-service-principal.md), der er registreret i ISV'ens lejer.

3. Ved hjælp af [REST API'er til Power BI](https://docs.microsoft.com/rest/api/power-bi/) opretter ISV'en en **installationsbillet**, der indeholder den brugerspecifikke parameterkonfiguration, som ISV'en har forberedt.

4. ISV'en omdirigerer brugeren til Power BI ved hjælp af en ```POST```-omdirigeringsmetode, der indeholder installationsbilletten.

5. Brugeren omdirigeres til sin Power BI-konto med installationsbilletten og bliver bedt om at installere skabelonprogrammet. Når brugeren klikker på Installér, installeres skabelonprogrammet.

>[!Note]
>Selvom parameterværdierne er konfigureret af ISV'en, når installationsbilletten oprettes, leveres legitimationsoplysninger relateret til datakilden kun af brugeren i de sidste faser af installationen. Dette forhindrer, at de eksponeres til en tredjepart, hvorved en sikker forbindelse mellem brugeren og datakilderne for skabelonprogrammet sikres.

## <a name="prerequisites"></a>Forudsætninger

Følgende forudsætninger er påkrævet for at levere en forudkonfigureret installationsoplevelse for dit skabelonprogram:

* En **Power BI Pro-licens**. Hvis du ikke er tilmeldt Power BI Pro, kan du [tilmelde dig en gratis prøveversion](https://powerbi.microsoft.com/pricing/), før du begynder.

* **Konfiguration af din egen Azure Active Directory-lejer**. Se [Opret en Azure Active Directory-lejer](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant) for at få oplysninger om, hvordan du konfigurerer en.

* En **tjenesteprincipal (token kun til programmer)** registreret i ovennævnte lejer. Se [Integrer Power BI-indhold med en tjenesteprincipal og en programhemmelighed](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal) for at få flere oplysninger. Sørg for at registrere programmet som et **serverbaseret webprogram**. Du registrerer et serverbaseret webprogram for at oprette en programhemmelighed. Fra denne proces skal du gemme *program-id'et* (klient-id) og *programhemmeligheden* (klienthemmelighed) til senere trin.

* Et **parameteriseret skabelonprogram**, der er klar til installation. Skabelonprogrammet skal være oprettet i den samme lejer, som du registrerer programmet i Azure Active Directory (Azure AD) i. Se [tip til skabelonprogram](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips.md) eller [Opret et skabelonprogram i Power BI](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create) for at få flere oplysninger. Fra skabelonprogrammet skal du notere følgende oplysninger til de næste trin:
     * *App-id*, *pakkenøgle* og *ejer-id*, som de vises i URL-adressen til installation i slutningen af processen [Definer egenskaber for skabelonprogrammet](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app), da programmet blev oprettet. Du kan også få det samme link ved at klikke på **Hent link** i [Udgivelsesadministration](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) for skabelonprogrammet.

    * *Parameternavne*, som defineret i datasættet for skabelonprogrammet. Der skelnes mellem store og små bogstaver i parameternavne, og de kan også hentes via fanen **Parameterindstillinger**, når du [definerer egenskaberne for skabelonprogrammet](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) eller fra indstillingerne for datasæt i Power BI.

    >[!NOTE]
    >Du kan teste det forudkonfigurerede installationsprogram på dit skabelonprogram, hvis skabelonprogrammet er klar til installation, selvom det endnu ikke er offentligt tilgængeligt på AppSource. Men før brugere uden for din lejer kan bruge det automatiserede installationsprogram til at installere dit skabelonprogram, skal skabelonprogrammet være offentligt tilgængeligt på [markedspladsen til Power BI-programmer](https://app.powerbi.com/getdata/services). Så før du distribuerer skabelonprogrammet ved hjælp af det automatiserede installationsprogram, du opretter, skal du sørge for at publicere det i [Partnercenter](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer).

## <a name="main-steps-and-apis"></a>Primære trin og API'er

Nedenstående afsnit indeholder en beskrivelse af de primære trin til at automatisere konfigurationen af installationen et skabelonprogram og de API'er, du har brug for. Selvom de fleste af trinnene udføres ved hjælp af [REST API'er til Power BI](https://docs.microsoft.com/rest/api/power-bi/), udføres de nedenfor beskrevne kodeeksempler ved hjælp af **.NET SDK**.

## <a name="step-1-create-a-power-bi-client-object"></a>Trin 1: Opret et Power BI-klientobjekt 

Brug af REST API'er til Power BI kræver, at du henter et **adgangstoken** til din [tjenesteprincipal](../embedded/embed-service-principal.md) fra **Azure AD**. Du skal have et [Azure AD-adgangstoken](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) til dit Power BI-program, før du kan foretage kald til [REST API'erne til Power BI](https://docs.microsoft.com/rest/api/power-bi/).
Hvis du skal oprette en Power BI-klient med dit **adgangstoken**, skal du oprette et Power BI-klientobjekt, som giver dig mulighed for at interagere med [REST API'erne til Power BI](https://docs.microsoft.com/rest/api/power-bi/). Du kan oprette dit Power BI-klientobjekt ved at wrappe **AccessToken** med et **_Microsoft.Rest.TokenCredentials_* _-objekt.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>Trin 2: Opret en installationsbillet

Opret en installationsbillet, som bruges til at omdirigere brugerne til Power BI. Den API, der bruges til denne handling, er _ *CreateInstallTicket** API.
* [CreateInstallTicket til skabelonprogrammer](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

Der findes en prøve på oprettelse af en installationsbillet til konfiguration og installation af skabelonprogrammer i filen [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) i [prøveprogrammet](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample).


Nedenfor er et kodeeksempel på brug af REST API'en *CreateInstallTicket* til skabelonprogrammet.
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>Trin 3: Omdiriger brugere til Power BI med billetten

Når du har oprettet en installationsbillet, kan du bruge den til at omdirigere dine brugere til Power BI for at fortsætte med at installere og konfigurere skabelonprogrammet. Dette gøres ved hjælp af en ```POST```-omdirigeringsmetode til skabelonprogrammets URL-adresse til installation med installationsbilletten i anmodningsteksten.

Der er forskellige dokumenterede metoder til, hvordan omdirigering udstedes ved hjælp af ```POST```-anmodninger. Det afhænger af scenariet, og hvordan dine brugere interagerer med portalen eller tjenesten, om du skal vælge den ene eller den anden metode.

I et simpelt eksempel, der primært bruges til testformål, anvendes en formular med et skjult felt, som automatisk sender sig selv ved indlæsning.

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

Nedenfor er et eksempel på [prøveprogrammets](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample) svar, som har installationsbilletten og automatisk omdirigerer brugerne til Power BI. Svaret på denne Azure-funktion er faktisk den samme formular til automatisk indsendelse af sig selv, som vi så i HTML-eksemplet ovenfor.

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>Selvom der er forskellige måder at bruge ```POST```-browseromdirigeringer på, bør du altid bruge den mest sikre metode, hvilket afhænger af dine behov og begrænsninger for tjenesten. Vær opmærksom på, at nogle former for usikker omdirigering kan medføre, at dine brugere eller din tjeneste eksponeres for sikkerhedsproblemer.

## <a name="step-4-move-your-automation-to-production"></a>Trin 4: Flyt automatiseringen til produktion

Når den automatisering, du har designet, er klar, skal du sørge for at flytte den til produktion.

## <a name="next-steps"></a>Næste trin

* Se vores [selvstudium](template-apps-auto-install-tutorial.md), hvor der bruges en simpel Azure-funktion til at automatisere konfigurationen af installationen af et skabelonprogram.

* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
