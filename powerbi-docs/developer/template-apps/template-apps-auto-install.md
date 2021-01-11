---
title: Automatiser konfigurationen af installationen af skabelonprogrammer for dine kunder
description: Få mere at vide om automatisering af konfigurationen af installationen af skabelonprogrammer.
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: 33de464a1bb1389fadfbc7a85ded9365321e0a62
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926296"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>Automatiseret konfiguration af installationen af et skabelonprogram

Skabelonprogrammer er en fantastisk måde for kunder at begynde at få indsigt i deres data på. Få skabelonapps op at køre hurtigt ved at knytte dem til deres data. Skabelonappsene giver kunderne forudopbyggede rapporter, som de kan tilpasse efter deres egne behov.

Kunderne ved ikke altid, hvordan de opretter forbindelse til deres data. Det kan være et problem for kunderne at angive disse oplysninger, når de installerer en skabelonapp.

Hvis du er datatjenesteudbyder og har oprettet en skabelonapp for at hjælpe dine kunder med at komme i gang med at arbejde med deres data på din tjeneste, kan du gøre det nemmere for dem at installere din skabelonapp. Du kan automatisere konfigurationen af din skabelonapps parametre. Når kunden logger på din portal, vælger de et særligt link, som du har forberedt. Dette link:

- Starter automationen, som indsamler de nødvendige oplysninger.
- Forudkonfigurerer skabelonappens parametre.
- Omdirigerer kunden til deres Power BI-konto, hvor de kan installere appen.

Kunden skal blot vælge **Installér** og godkendes i forhold til datakilden, hvorefter han eller hun er klar.

Denne kundeoplevelse er illustreret nedenfor.

![Illustration af brugeroplevelsen med automatisk appinstallation.](media/template-apps-auto-install/high-level-flow.png)

Denne artikel indeholder en beskrivelse af det grundlæggende flow, forudsætningerne samt de primære trin og API'er, der skal bruges til at automatisere konfigurationen af installationen af en skabelonapp. Hvis du vil i gang med det samme, kan du dog springe til dette [selvstudium](template-apps-auto-install-tutorial.md), hvor du automatiserer konfigurationen af installationen af skabelonappen ved hjælp af et prøveprogram, vi har klargjort, og som bruger en Azure-funktion.

## <a name="basic-flow"></a>Grundlæggende flow

Det grundlæggende flow til automatisering af konfigurationen af installationen af et skabelonprogram er som følger:

1. Brugeren logger på ISV'ens portal og klikker på det angivne link. Denne handling igangsætter det automatiserede flow. I denne fase forberedes den brugerspecifikke konfiguration på ISV'ens portal.

1. ISV'en henter et token *kun til apps*, der er baseret på en [tjenesteprincipal (token kun til apps)](../embedded/embed-service-principal.md), der er registreret i ISV'ens lejer.

1. Ved hjælp af [REST API'er til Power BI](https://docs.microsoft.com/rest/api/power-bi/) opretter ISV'en en *installationsbillet*, der indeholder den brugerspecifikke parameterkonfiguration, som ISV'en har forberedt.

1. ISV'en omdirigerer brugeren til Power BI ved hjælp af en ```POST```-omdirigeringsmetode, der indeholder installationsbilletten.

1. Brugeren omdirigeres til sin Power BI-konto med installationsbilletten og bliver bedt om at installere skabelonprogrammet. Når brugeren vælger **Installér**, installeres skabelonappen.

>[!Note]
>Selvom parameterværdierne er konfigureret af ISV'en, når installationsbilletten oprettes, leveres legitimationsoplysninger relateret til datakilden kun af brugeren i de sidste faser af installationen. Dette forhindrer, at de eksponeres til en tredjepart, og sikrer en sikker forbindelse mellem brugeren og datakilderne for skabelonappen.

## <a name="prerequisites"></a>Forudsætninger

Følgende forudsætninger er påkrævet for at levere en forudkonfigureret installationsoplevelse for dit skabelonprogram:

* En Power BI Pro-licens. Hvis du ikke er tilmeldt Power BI Pro, kan du [tilmelde dig en gratis prøveversion](https://powerbi.microsoft.com/pricing/), før du begynder.
* Konfigurer din egen Microsoft Azure Active Directory-lejer. Se [Opret en Azure Active Directory-lejer](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant) for at få oplysninger om, hvordan du konfigurerer en.
* En **tjenesteprincipal (token kun til apps)** , der er registreret i ovennævnte lejer. Se [Integrer Power BI-indhold med en tjenesteprincipal og en programhemmelighed](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal) for at få flere oplysninger. Sørg for at registrere programmet som et **serverbaseret webprogram**. Du registrerer et serverbaseret webprogram for at oprette en programhemmelighed. Fra denne proces skal du gemme *app-id'et* (ClientID) og *programhemmeligheden* (ClientSecret) til senere trin.
* En **parameteriseret skabelonapp**, der er klar til installation. Skabelonappen skal være oprettet i den samme lejer, som du registrerer programmet i Azure Active Directory i. Se [Tip til skabelonapp](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips) eller [Opret en skabelonapp i Power BI](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create) for at få flere oplysninger. Fra skabelonappen skal du notere følgende oplysninger til de næste trin:
     * *App-id*, *pakkenøgle* og *ejer-id*, som de vises i URL-adressen til installation i slutningen af processen med at [definere egenskaber for skabelonappen](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app), da appen blev oprettet. Du kan også få det samme link ved at vælge **Hent link** i [Udgivelsesadministration](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) for skabelonappen.
    * *Parameternavne*, som defineret i datasættet for skabelonappen. Der skelnes mellem store og små bogstaver i parameternavne, og de kan også hentes via fanen **Parameterindstillinger**, når du [definerer egenskaberne for skabelonappen](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app), eller fra indstillingerne for datasæt i Power BI.

    >[!NOTE]
    >Du kan teste det forudkonfigurerede installationsprogram for din skabelonapp, hvis skabelonappen er klar til installation, selvom den endnu ikke er offentligt tilgængelig på AppSource. Men før brugere uden for din lejer kan bruge det automatiserede installationsprogram til at installere din skabelonapp, skal skabelonappen være offentligt tilgængelig på [markedspladsen til Power BI-programmer](https://app.powerbi.com/getdata/services). Før du distribuerer skabelonappen ved hjælp af det automatiserede installationsprogram, du opretter, skal du sørge for at publicere det i [Partnercenter](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer).

## <a name="main-steps-and-apis"></a>Primære trin og API'er

Nedenstående afsnit indeholder en beskrivelse af de primære trin til at automatisere konfigurationen af installationen af en skabelonapp og de API'er, du har brug for. Selvom de fleste af trinnene udføres ved hjælp af [REST API'er til Power BI](https://docs.microsoft.com/rest/api/power-bi/), udføres de nedenfor beskrevne kodeeksempler ved hjælp af .NET SDK.

## <a name="step-1-create-a-power-bi-client-object"></a>Trin 1: Opret et Power BI-klientobjekt

Brug af REST API'er til Power BI kræver, at du henter et *adgangstoken* til din [tjenesteprincipal](../embedded/embed-service-principal.md) fra Azure AD. Du skal have et [Azure AD-adgangstoken](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) til dit Power BI-program, før du kan foretage kald til [REST API'erne til Power BI](https://docs.microsoft.com/rest/api/power-bi/).
Hvis du skal oprette en Power BI-klient med dit adgangstoken, skal du oprette et Power BI-klientobjekt, som giver dig mulighed for at interagere med [REST API'erne til Power BI](https://docs.microsoft.com/rest/api/power-bi/). Du kan oprette dit Power BI-klientobjekt ved at omgive **AccessToken** med objektet **Microsoft.Rest.TokenCredentials**.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI client object. It's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>Trin 2: Opret en installationsbillet

Opret en installationsbillet, som bruges til at omdirigere brugerne til Power BI. Den API, der bruges til denne handling, er API'en **CreateInstallTicket**.
* [CreateInstallTicket til skabelonprogrammer](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

Der findes et eksempel på oprettelse af en installationsbillet til konfiguration og installation af skabelonapps i filen [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) i [prøveprogrammet](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample).


Følgende kodeeksempel viser, hvordan du bruger REST API'en **CreateInstallTicket** til skabelonappen.
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

// Issue the request to the REST API using .NET SDK.
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>Trin 3: Omdiriger brugere til Power BI med billetten

Når du har oprettet en installationsbillet, kan du bruge den til at omdirigere dine brugere til Power BI for at fortsætte med at installere og konfigurere skabelonappen. Dette gøres ved hjælp af en ```POST```-omdirigeringsmetode til skabelonappens URL-adresse til installation med installationsbilletten i anmodningsteksten.

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

Det følgende er et eksempel på [prøveprogrammets](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample) svar, som har installationsbilletten og automatisk omdirigerer brugerne til Power BI. Svaret på denne Azure-funktion er faktisk den samme formular til automatisk indsendelse af sig selv, som vi så i det foregående HTML-eksempel.

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
>Der er forskellige måder at bruge ```POST```-browseromdirigeringer på. Du bør altid bruge den mest sikre metode, hvilket afhænger af dine behov og begrænsninger for tjenesten. Vær opmærksom på, at nogle former for usikker omdirigering kan medføre, at dine brugere eller din tjeneste eksponeres for sikkerhedsproblemer.

## <a name="step-4-move-your-automation-to-production"></a>Trin 4: Flyt automatiseringen til produktion

Når den automatisering, du har designet, er klar, skal du sørge for at flytte den til produktion.

## <a name="next-steps"></a>Næste trin

* Se vores [selvstudium](template-apps-auto-install-tutorial.md), hvor der bruges en simpel Azure-funktion til at automatisere konfigurationen af installationen af en skabelonapp.
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/).
