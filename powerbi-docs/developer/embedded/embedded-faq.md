---
title: Ofte stillede spørgsmål om integrerede Power BI-analyser, der hjælper dig med at få bedre integreret BI-indsigt
description: Gennemse en liste over ofte stillede spørgsmål og svar om integrerede Power BI-analyser, der forbedrer kundernes integrerede BI-indsigt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 4d8096793c4663cbed71c3149bde11305ebee71e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886689"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Ofte stillede spørgsmål om Power BI Embedded

* Hvis du har andre spørgsmål, kan du [prøve at spørge Power BI-community'et](https://community.powerbi.com/).
* Har du stadig problemer? Gå til [supportsiden for Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Generelt

### <a name="what-is-power-bi-embedded"></a>Hvad er Power BI Embedded?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) gør det muligt for programudviklere at integrere flotte, fuldt interaktive rapporter i programmer, uden at de skal oprette deres egne datavisualiseringer og -kontrolelementer fra bunden.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Hvem er målgruppen for Power BI Embedded?

Udviklere og softwarefirmaer, også kaldet uafhængige softwareleverandører (eller ISV'er), kodningsprogrammer.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Hvordan er Power BI Embedded anderledes end Power BI-tjenesten?

Power BI er en software-as-a-service-analyseløsning, der giver virksomheder et enkelt overblik over deres vigtigste virksomhedsdata.

Microsoft udviklede Power BI Embedded til ISV'er, der vil integrere visuals i deres programmer for at hjælpe deres kunder med at tage analytisk beslutninger. Dette betyder, at ISV'er ikke selv behøver at oprette deres egne analyseløsning. [Integreret analyse](embedding.md) gør det muligt for virksomhedsbrugere at få adgang til virksomhedsdata og udføre forespørgsler mod dem for at generere indsigter i programmet.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Hvad er forskellen mellem Power BI Premium og Power BI Embedded?

Power BI Premium er kapacitetsmæssigt gearet mod virksomheder, som vil have en komplet BI-løsning, der giver adgang til en enkelt visning af virksomheden, kunderne og leverandørerne. Power BI Premium hjælper din virksomhed med at træffe beslutninger. Power BI Premium er et SaaS-produkt, der giver mulighed for brugere at forbruge indhold gennem mobilapps, internt udviklede apps eller i Power BI-portalen.

Power BI Embedded er til ISV'er, der vil integrere visuals i deres programmer. Power BI Embedded hjælper dine kunder med at træffe beslutninger, og fordi Power BI Embedded er beregnet til programudviklere, så kan kunderne af det pågældende program forbruge indhold lagret på Power BI Embedded-kapaciteter, herunder alle indenfor og udenfor virksomheden. Du kan ikke dele kapacitetsindhold i Power BI Embedded gennem publicering med et enkelt klik, publicering til web eller publicering med et enkelt klik til SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Hvad anbefaler Microsoft, når en kunde står over for valget mellem Power BI Premium og Power BI Embedded?

Microsoft anbefaler, at virksomheder køber Power BI Premium, som er en selvbetjent cloudbaseret BI-løsning i virksomhedsklassen. Vi anbefaler, at ISV'er køber Power BI Embedded til deres cloudbaserede komponenter til integreret analyse. En kunde kan dog købe et hvilket som helst produkt.

Der kan være situationer, hvor en ISV (typisk en større) ud over integration af apps ønsker at bruge en P SKU for at få adgang til yderligere fordele i den færdigpakkede Power BI-tjenesten i virksomheden. Nogle virksomheder beslutter måske at bruge A SKU'er i Azure, hvis de kun er interesserede i at producere line-of-business-programmer og integrere analyser i dem uden at have interesse i at bruge den færdigpakkede Power BI-tjeneste.

### <a name="how-many-embed-tokens-can-i-create"></a>Hvor mange integrerede tokens kan jeg oprette?

Integrationstokens med en PRO-licens er beregnet til udviklingstest, så en Power BI-masterkonto eller [tjenesteprincipal](embed-service-principal.md) kan kun generere et begrænset antal tokens. [Køb en kapacitet](#technical) for at integrere i et produktionsmiljø. Der er ingen grænse for hvor mange integrerede tokens, du kan generere, når du køber en kapacitet. Gå til [Tilgængelige funktioner](/rest/api/power-bi/availablefeatures) for at undersøge den brugsværdi, der angiver brugen af integrerede tokens i procent.

## <a name="technical"></a>Tekniske spørgsmål

### <a name="where-can-i-learn-more-about-capacity-and-skus-in-power-bi-embedded-analytics"></a>Hvor kan jeg få mere at vide om kapacitet og SKU'er i integreret analyse i Power BI?

Se artiklen [Kapacitet og SKU'er i integreret analyse i Power BI](embedded-capacity.md).

### <a name="what-are-the-prerequisites-for-creating-a-pbie-capacity-in-azure"></a>Hvad er forudsætningerne for at oprette en PBIE-kapacitet på Azure?

* Log på din organisationsmappe (Microsoft-konti understøttes ikke).
* Du skal have en Power BI-lejer, dvs. at mindst én bruger i din mappe har tilmeldt sig Power BI. 
* Du skal have et Azure-abonnement i din organisationsmappe.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Hvordan kan jeg overvåge Power BI Embedded-kapacitetsforbrug?

* Brug [Power BI-administrationsportalen](../../admin/service-admin-portal.md#power-bi-embedded).

* Download den [metriske app](../../admin/service-admin-premium-monitor-capacity.md) i Power BI.

* Brug [logføring af Azure-diagnosticering](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Kan min kapacitet skaleres automatisk, så den passer til mit appforbrug?

Automatisk skalering er ikke muligt i øjeblikket, men alle API'er kan skaleres når som helst.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Hvorfor afbrydes kapaciteten midlertidigt, når man opretter/skalerer/genoptager en kapacitet?

Klargøring af en kapacitet (skalering/genoptagelse/oprettelse) kan mislykkes. Du kan bruge API'en Hent oplysninger til at kontrollere en kapacitets ProvisioningState: [Kapaciteter – Hent oplysninger](/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Kan jeg kun oprette Power BI Embedded-kapaciteter i et bestemt område?

Med [Multi-Geo-funktionen (prøveversion)](embedded-multi-geo.md) kan du købe en [Power BI Embedded-kapacitet](azure-pbie-create-capacity.md) i et andet område end din private lejerplacering i Power BI

### <a name="why-cant-i-see-a-workspace-although-i-have-permissions"></a>Hvorfor kan jeg ikke se et arbejdsområde, selvom jeg har tilladelser?

Når en bruger har fået tildelt tilladelser til et arbejdsområde, en app eller artefakt, er arbejdsområdet muligvis ikke tilgængeligt med det samme via API-kald.
Resultatet kan enten være et manglende artefakt i et 'GET' API-svar eller en fejl, når du forsøger at bruge artefaktet.
Brugeren kan løse problemet ved at kalde [refreshUserPermissions API](/rest/api/power-bi/users/refreshuserpermissions), der opdaterer brugertilladelserne.


### <a name="how-can-i-find-my-pbi-tenant-region"></a>Hvordan kan jeg finde mit PBI-lejerområde?

Du kan bruge PBI-portalen til at finde dit PBI-lejerområde.

`https://app.powerbi.com/` > ? > Om Power BI

![Om Power BI](media/embedded-faq/about-01.png)
![Lejerområde](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>Hvad understøtter kanalen Cloud Solution Provider (CSP)?

* Du kan oprette PBIE for din lejer med abonnementstype CSP
* Partnerkonto kan logge på kundelejer og købe PBIE for kundelejeren, angive kundelejerbruger som administrator af Power BI-kapacitet

### <a name="why-do-i-get-an-unsupported-account-message"></a>Hvorfor får jeg en meddelelse om en ikke-understøttet konto?

Power BI kræver, at du tilmelder dig med en organisationskonto. Forsøg på at tilmelde sig til Power BI med en Microsoft-konto understøttes ikke.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Kan jeg bruge API'er til at oprette og administrere Azure-kapaciteter?

Ja. Der er PowerShell-cmdlet'er og REST API'er til Azure Resource Manager, som du kan bruge til at oprette og administrere PBIE-ressourcer.

* [REST-API'er](/rest/api/power-bi-embedded/) 
* [PowerShell-cmdlet'er](/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-capacity-role-in-a-pbi-embedded-solution"></a>Hvilken rolle har PBI's integrerede kapacitet i en PBI-integreret løsning?

Hvis du vil [gøre din løsning produktionsklar](move-to-production.md), skal du tildele det Power BI-indhold (arbejdsområde), dit program bruger, til en Power BI Embedded-kapacitet (A SKU).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>I hvilke Azure-områder er PBI Embedded tilgængelig?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) – se produkttilgængelighedsstyringen

Tilgængelige områder (16 – samme områder som Power BI)

* USA (6) – Det østlige USA, Det østlige USA 2, Det nordcentrale USA, Det sydcentrale USA, Det vestlige USA, Det vestlige USA 2
* Europa (2) – Det nordlige Europa, Det vestlige Europa
* Asien og Stillehavsområdet (2) – Det sydøstlige Asien, Det østlige Asien
* Brasilien (1) – Det sydlige Brasilien
* Japan (1) – Det østlige Japan
* Australien (1) – Det sydøstlige Australien
* Indien (1) – Det vestlige Indien
* Canada (1) – Det centrale Canada
* Storbritannien (1) – Det sydlige Storbritannien

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Hvad er godkendelsesmodellen for Power BI Embedded?

Power BI Embedded bruger fortsat Microsoft Azure Active Directory til at godkende masterbrugeren (en udpeget Power BI Pro-licenseret bruger) eller [tjenesteprincipalen](embed-service-principal.md) til at godkende programmet i Power BI.  

 En ISV kan implementere sin egen godkendelse og autorisation af sine programmer.

Du kan bruge din eksisterende mappe, hvis du allerede har en Microsoft Azure Active Directory-lejer. Du kan også oprette en ny Microsoft Azure Active Directory-lejer for dit integrerede programindholds sikkerhed.

Du kan bruge et [Azure Active Directory Authentication Library](/azure/active-directory/develop/active-directory-authentication-libraries) for at få et AAD-token. Der er klientbiblioteker til flere platforme.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Mit program allerede bruger AAD til brugergodkendelse. Hvordan kan vi bruge dette id til godkendelse til Power BI i et scenarie, hvor "Bruger ejer Data"?

Det er standard-OAuth på vegne af flow (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Du skal konfigurere programmet til at kræve tilladelser til Power BI-tjenesten (med de påkrævede områder). Når du har et brugertoken til din app, skal du bare kalde ADAL API AcquireTokenAsync ved hjælp af brugeradgangtokenet og angive URL-adressen til Power BI-ressourcen som ressource-id:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>Hvilket objekt-id er objekt-id'et for tjenesteprincipalen?

*Objekt-id'et* fra hovedskærmbilledet i en registreret app er objekt-id'et for appen.

Det objekt-id, der findes i afsnittet *Administreret program i en lokal mappe > Egenskaber* er det objekt-id for tjenesteprincipalen, du skal bruge. Dette objekt-id skal bruges som reference til en tjenesteprincipal i forbindelse med handlinger, eller hvis der skal foretages ændringer af objekt-id'et for tjenesteprincipalen. Det kan f.eks. være anvendelse af en tjenesteprincipal som administrator af et arbejdsområde.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Hvordan er Power BI Embedded anderledes end andre Azure-tjenester?

Du skal have en Power BI-konto, før du køber Power BI Embedded i Azure. Din Power BI-konto bestemmes af det område, hvor din Power BI Embedded er udrullet. Administrer din Power BI Embedded-ressource i Azure for at:

* Skalere op/ned
* Tilføje kapacitetsadministratorer
* Pausestille/genoptage tjenesten

Brug PowerBI.com til at tildele/fjerne tildelte arbejdsområder fra Power BI Embedded-kapaciteten.

### <a name="what-content-pack-data-types-can-you-embed"></a>Hvilke indholdspakke-datatyper kan du integrere?

Du *kan ikke* integrere **Dashboards** og **felter**, der er bygget ud fra indholdspakke-datasæt. Du *kan* imidlertid godt integrere **rapporter**, der er bygget ud fra et indholdspakke-datasæt.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Hvad er forskellen mellem at bruge RLS-filtre (Row-level Security – sikkerhed på rækkeniveau) og JavaScript-filtre?

Der er ofte forvirring omkring, hvornår der skal bruges RLS- kontra JavaScript-filtre, da én metode vedrører styring af, hvad en bestemt bruger kan se, og den anden vedrører optimering af brugerens visning.

I forbindelse med RLS kontrollerer ISV-udvikleren datafiltreringen som en del af modeloprettelsen og genereringen af integrerede tokens. Slutbrugeren ser kun det, ISV'en tillader brugeren at se. I dette tilfælde kan brugeren vælge at se mindre end det, der filtreres, men vedkommende kan ikke tilsidesætte RLS-konfigurationen og se mere end det, der er tilladt.

ISV'en kan muligvis beslutte, hvad brugeren ser på i første visning på vha. filtreringen på klientsiden (JavaScript), men kan ikke styre de ændringer, slutbrugeren eventuelt selv foretager af selve visningen. Da brug af JavaScript-klientkode kan udløse datofiltrering i backend, kan den ikke betragtes som sikker.

Se under [RLS- i forhold til JavaScript-filtre](embedded-row-level-security.md#using-rls-vs-javascript-filters) for at få flere oplysninger.

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Hvordan administrerer jeg tilladelser for tjenesteprincipaler med Power BI?

Når du aktiverer en [tjenesteprincipal](embed-service-principal.md), der skal bruges sammen med Power BI, er AD-tilladelserne for programmet ikke længere gældende. Tilladelserne for programmet administreres derefter via Power BI-administrationsportalen.

Tjenesteprincipaler nedarver tilladelserne til alle Power BI-lejerindstillinger fra deres sikkerhedsgruppe. Hvis du vil begrænse tilladelserne, skal du oprette en dedikeret sikkerhedsgruppe for tjenesteprincipaler og føje den til listen **Undtagen specifikke sikkerhedsgrupper** for de relevante aktiverede Power BI-indstillinger.

Dette er vigtigt, når du tilføjer tjenesteprincipalen som **administrator** til det nye arbejdsområde. Du kan administrere denne opgave via [API'erne](/rest/api/power-bi/groups/addgroupuser) eller Power BI-tjenesten.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Hvornår skal jeg bruge et program-id i forhold til et objekt-id for en tjenesteprincipal?

**[Program-id'et](embed-sample-for-customers.md#client-id)** , der også er kendt som *klient-id*, bruges til at oprette adgangstokenet, når program-id'et vedtages som godkendelse.

Hvis du vil henvise til en tjenesteprincipal for at udføre handlinger eller foretage ændringer, skal du bruge **[objekt-id'et for tjenesteprincipalen](embed-service-principal.md)** , f.eks. ved anvendelse af en tjenesteprincipal som administrator i et arbejdsområde.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Kan man administrere en datagateway i det lokale miljø med en tjenesteprincipal?

Du kan ikke administrere en datagateway i det lokale miljø (datagateway) ved hjælp af en [tjenesteprincipal](embed-service-principal.md), som du kan med en masterkonto.

Med en masterkonto kan du installere en datagateway, føje brugere til gatewayen, oprette forbindelse til datakilder og udføre andre administrative opgaver.

Med en tjenesteprincipal kan du konfigurere [sikkerhed på rækkeniveau](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal) ved hjælp af en datakilde i det lokale miljø med direkte forbindelse via SQL Server Analysis Services (SSAS). På denne måde kan du administrere brugere og deres adgang til data i SSAS, når du integrerer med **Power BI Embedded** ved hjælp af en tjenesteprincipal.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Kan man logge på Power BI-tjenesten med en tjenesteprincipal?

Nej. Du kan ikke logge på Power BI ved hjælp af en tjenesteprincipal.

Du kan desuden ikke bruge indhold som en bruger i eksterne programmer (SaaS-integrering). Det kan du kun, når du genererer et integrationstoken.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Hvad er de bedste fremgangsmåder til at forbedre ydeevnen?

[Ydeevnen i Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licensering

### <a name="how-do-i-purchase-power-bi-embedded"></a>Hvordan køber jeg Power BI Embedded?

Power BI Embedded fås gennem Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Hvad sker der, hvis jeg allerede har købt Power BI Premium, og jeg nu vil have noget af Power BI Embedded i Azure-fordelene?

Kunder betaler fortsat for alle eksisterende Power BI Premium-køb, indtil udløbet af deres aktuelle aftaleperiode og kan derefter skifte deres Power BI Premium-køb ud efter behov på det pågældende tidspunkt.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Er jeg stadig nødt til at købe Power BI Premium for at få adgang til Power BI Embedded?

Nej, Power BI Embedded omfatter Azure-baseret kapacitet, som du skal bruge for at installere og distribuere løsningen til kunder.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Hvilke købsbindinger er knyttet til Power BI Embedded?

Kunder kan ændre deres brug på timebasis. Der er ingen månedlig eller årlig binding knyttet til Power BI Embedded-tjenesten.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Hvordan vises forbruget af Power BI Embedded på min regning?

Power BI Embedded fakturerer på en forudsigelig timebaseret rate baseret på typen af node(r), der er installeret. Du faktureres, så længe ressourcen er aktiv, selvom der ikke er noget forbrug. Du skal afbryde din ressource midlertidigt for at stoppe faktureringen.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Hvem har brug for et Power BI Pro-licens til Power BI Embedded og hvorfor?

Du har brug for en Power BI Pro-licens eller [tjenesteprincipal](embed-service-principal.md) for at bruge REST-API'er. En analytiker, der skal føje rapporter til et Power BI-arbejdsområde, skal enten bruge en Power BI Pro-licens eller en tjenesteprincipal. En administrator, der skal administrere Power BI-lejeren og -kapaciteten, skal have en Power BI Pro-licens.

Da Power BI Embedded tillader brug af Power BI-portalen til administration og validering af integreret indhold, er Power BI Pro-licensen påkrævet for at godkende appen internt i PowerBI.com, så der kan oprettes adgang til rapporterne i de korrekte lagre.

Men hvis man vil [oprette/redigere integrerede rapporter](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) i sit eget program, behøver slutbrugeren ikke en Pro-licens, da det ikke er et krav, at slutbrugeren er Power BI-bruger.

### <a name="can-i-get-started-for-free"></a>Kan jeg komme i gang gratis?

Ja, du kan bruge din [Azure-kredit](https://azure.microsoft.com/free/) til Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Kan jeg få adgang til en prøveversion af Power BI Embedded i Azure?

Da Power BI Embedded er en del af Azure, er det muligt at bruge tjenesten med [kreditten på 200 USD, der modtages ved tilmeldingen til Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Er Power BI Embedded tilgængelig til nationale cloudmiljøer (US Government, Tyskland, Kina)?

Power BI Embedded er også tilgængelig til [nationale cloudmiljøer](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Er Power BI Embedded tilgængelig for almennyttige organisationer og uddannelsesinstitutioner?

Der er ingen særlige Azure-prissætning for almennyttige organisationer og uddannelsesinstitutioner.

## <a name="power-bi-workspace-collection"></a>Power BI Workspace Collection

### <a name="what-is-power-bi-workspace-collection"></a>Hvad er Power BI Workspace Collection?

**Power BI-arbejdsområdesamling** (**Power BI Embedded** Version 1) er en løsning, som er baseret på Azure-ressourcen **Power BI Workspace Collection**. Denne løsning gør det muligt at oprette **Power BI Embedded**-programmer til dine kunder ved hjælp af Power BI-indhold under **Power BI Workspace Collection**-løsningen, dedikerede-API'er og nøgler til arbejdsområdesamlinger til godkendelse af programmet til Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Kan jeg overføre indhold fra Power BI Workspace Collection til Power BI Embedded?

1. Du kan bruge overførselsværktøjet til at klone indhold fra **Power BI Workspace Collection** til Power BI – https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Start med den **Power BI Embedded**-program-POC, der bruger Power BI-indhold.

3. Når du er klar til produktion, skal du købe en **Power BI Embedded**-kapacitet og tildele dit Power BI-indhold (arbejdsområde) til denne kapacitet.

    > [!Note]
    > Du kan fortsætte med at bruge **Power BI Workspace Collection**, når du opretter parallelt med en **Power BI Embedded**-løsning. Når du er klar, kan du flytte kunden til den nye **Power BI Embedded**-løsning og lade **Power BI Workspace Collection**-løsningen udgå.

Du kan finde flere oplysninger under [Sådan overfører du indhold fra Power BI Workspace Collection til Power BI Embedded](./migrate-from-powerbi-embedded.md)

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>Frarådes det senere at bruge Power BI-arbejdsområdesamling?

Ja, men kunder, der allerede bruger løsningen med **Power BI-arbejdsområdesamling**, kan fortsætte med at bruge den, indtil det frarådes. Kunder kan også oprette nye arbejdsområdesamlinger og alle **Power BI Embedded**-programmer, der stadig bruger **Power BI Workspace Collection**-løsningen.

Men det betyder også, at der ikke føjes nye funktioner til løsninger med **Power BI-arbejdsområdesamling**. Vi opfordrer kunder til at planlægge deres migrering til den nye **Power BI Embedded**-løsning.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Hvornår ophører support til Power BI Workspace Collection?

Kunder, der allerede bruger **Power BI Workspace Collections**-løsningen, kan fortsætte med at bruge den indtil udgangen af juni 2018 eller indtil udgangen af deres supportaftale.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>I hvilke områder kan jeg oprette en Power BI-arbejdsområdesamling?

De tilgængelige områder er det sydøstlige Australien, det sydlige Brasilien, det centrale Canada, det østlige USA 2, det østlige Japan, det nordcentrale USA, det nordlige Europa, det sydcentrale USA, det sydøstlige Asien, det sydlige Storbritannien, det vestlige Europa, det vestlige Indien og det vestlige USA.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Hvorfor skal jeg overføre indhold fra PBI Workspace Collection til Power BI Embedded?

Der er nogle nye funktioner og egenskaber i **Power BI Embedded**-løsningen, som du ikke kan bruges sammen med **Power BI-arbejdsområdesamling**.

Nogle af funktionerne er:
* Alle PBI-datakilderne understøttes. Kun to **Power BI-arbejdsområdesamling**-datakilder understøttes. 
* Nye funktioner, f.eks. Spørgsmål og svar, opdatering, bogmærker, integrering af dashboards og felter, brugerdefinerede menuer, understøttes kun i **Power BI Embedded**-løsningen.
* Model for fakturering af kapacitet.

## <a name="embedding-setup-tool"></a>Embedding-konfigurationsværktøj

### <a name="what-is-the-embedding-setup-tool"></a>Hvad er konfigurationsværktøjet?

Med [Embedding-konfigurationsværktøjet](https://app.powerbi.com/embedsetup) kan du hurtigt komme i gang og downloade en eksempelapp for at komme i gang med at integrere med Power BI.

### <a name="which-solution-should-i-choose"></a>Hvilken løsning skal jeg vælge?

* [Embedding for your customers](embedding.md#embedding-for-your-customers) giver mulighed for at integrere dashboards og rapporter for de brugere, der ikke har en Power BI-konto. Kør løsningen i [Integrer indhold for dine kunder](https://app.powerbi.com/embedsetup) i *Embedding-konfigurationsværktøj*.
* Med [Embedding for your organization](embedding.md#embedding-for-your-organization) kan du udvide Power BI-tjenesten. Kør løsningen i [Integrer indhold for din organisation](https://app.powerbi.com/embedsetup) i *Embedding-konfigurationsværktøj*.

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>Jeg har downloadet eksempelappen. Hvilken løsning skal jeg vælge?

Hvis du arbejder med oplevelsen **Embed for your customers**, skal du gemme og udpakke filen *PowerBI-Developer-Samples.zip*. Derefter skal du åbne mappen *PowerBI-Developer-Samples-master\App Owns Data* og køre filen *PowerBIEmbedded_AppOwnsData.sln*.

Hvis du arbejder med **Embed for your organization**, skal du gemme og udpakke filen *PowerBI-Developer-Samples.zip*. Derefter skal du åbne mappen *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* og køre filen *pbi-saas-embed-report.sln*.

### <a name="how-can-i-edit-my-registered-application"></a>Hvordan kan jeg redigere min registrerede app?

Du kan få mere at vide om, hvordan du redigerer Azure AD-registrerede apps under [Hurtig start: Opdater et program i Azure Active Directory](/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Hvordan kan jeg redigere Power BI-brugerprofilen eller -dataene?

Du kan se, hvordan du redigerer dine Power BI-data, [her](../../fundamentals/service-basic-concepts.md).

Du kan finde flere oplysninger under [Fejlfinding af det integrerede program](embedded-troubleshoot.md).

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)