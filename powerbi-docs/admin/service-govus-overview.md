---
title: Power BI til US Government-kunder – oversigt
description: US Government-kunder kan føje et Power BI-abonnement til deres Microsoft 365 Government-abonnement. Få mere at vide om, hvordan du tilmelder dig, opretter forbindelse og gennemser tilgængelige funktioner i denne tjenestebeskrivelse.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/19/2021
ms.custom: gcc
LocalizationGroup: Get started
ms.openlocfilehash: e7100be7890673cecc77a8a1147a25a942fc4666
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597603"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI til US Government-kunder

Denne artikel er for kunder inden for de amerikanske offentlige myndigheder, der udruller Power BI som en del af en Microsoft 365-plan til offentlige myndigheder. Planer til offentlige myndigheder er designet til at opfylde de særlige behov hos organisationer, der overholder amerikanske standarder og sikkerhedsstandarder. Power BI-tjenesten, der er udviklet til US Government-kunder, adskiller sig fra den kommercielle version af Power BI-tjenesten. Disse funktionsforskelle og egenskaber er beskrevet i følgende afsnit.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Føj Power BI til din Microsoft 365-plan til offentlige myndigheder

Før du kan få et Power BI US Government-abonnement og tildele licenser til brugere, skal du tilmelde dig et Microsoft 365-abonnement til offentlige myndigheder. Hvis din organisation allerede har en Microsoft 365-plan for offentlige myndigheder, skal du gå videre til [Køb et Power BI Pro-abonnement til offentlige myndigheder](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Tilmeld dig en Microsoft 365-plan til offentlige myndigheder

Hvis du er ny kunde, skal du validere din organisations berettigelse, før du kan tilmelde dig en Microsoft 365-plan til offentlige myndigheder.  Kom i gang ved at udfylde [formularen til bekræftelse af berettigelsen til Microsoft 365 til offentlige myndigheder](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Du kan sikre dig, at du vælger den rette plan til din organisation ved at gennemse [tjenestebeskrivelserne for Microsoft 365 til de amerikanske offentlige myndigheder](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Hvis du allerede har udrullet Power BI i et kommercielt miljø og gerne vil migrere til US Government-cloudmiljøet, skal du føje et nyt Power BI Pro-abonnement til dit Microsoft 365-abonnement til offentlige myndigheder. Derefter skal du replikere de kommercielle data til Power BI-tjenesten til US Government, fjerne kommercielle licenstildelinger fra brugerkonti og derefter tildele en Power BI Pro Government-licens til brugerkontiene.
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Køb et Power BI Pro-abonnement til offentlige kunder

Når du har udrullet Microsoft 365, kan du tilføje et Power BI Pro-abonnement. Følg den trinvise vejledning i, hvordan du [tilmelder din US Government-organisation](service-govus-signup.md), for at købe Power BI Pro Government-tjenesten. Køb tilstrækkeligt mange licenser til alle de brugere, der skal bruge Power BI, og tildel derefter disse licenser til individuelle brugerkonti.

> [!IMPORTANT]
> Power BI US Government er ikke tilgængelig som en *gratis* licens. Hver enkelt bruger skal tildeles en *Pro-licens* for at få adgang til Government Community Cloud. Hvis en brugerkonto har fået tildelt en gratis licens, er brugeren kun autoriseret til at få adgang til den kommercielle cloud og vil opleve problemer med godkendelse og adgang. Hvis du har købt Power BI Premium, behøver du ikke at tildele Pro-licenser for at aktivere brugeradgang.  Alle brugere i organisationen har adgang til rapporter, der er delt med dem, så længe rapporterne er udgivet til en Premium-kapacitet. Hvis du vil gennemgå forskellene mellem licenstyper, skal du se [Funktioner i Power BI-tjenesten efter licenstype](../fundamentals/service-features-license-type.md).
>

## <a name="government-cloud-instances"></a>Instanser i det offentlige cloud

Microsoft 365 indeholder forskellige miljøer, så de offentlige myndigheder kan opfylde de forskellige overensstemmelseskrav. Du kan finde flere oplysninger om hvert miljø under:

* [Microsoft 365 GCC (Government Community Cloud)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) er udviklet til forbundsmyndigheder samt statslige og lokale myndigheder.

* [Microsoft 365 GCC High (Government Community Cloud High)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) er udviklet til forbundsmyndigheder, forsvarsindustrien, rumfartsindustrien og andre organisationer, der opbevarer kontrollerede ikke-klassificerede oplysninger. Dette miljø egner sig til nationale sikkerhedsorganisationer og virksomheder med ITAR-data (International Traffic in Arms Regulations) eller DFARS-krav (Defense Federal Acquisition Regulations Supplement).

* [Microsoft 365 DoD-miljøet](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) er udviklet udelukkende til det amerikanske forsvarsministerium.


## <a name="sign-in-to-power-bi-for-us-government"></a>Log på Power BI for US Government

URL-adressen til oprettelse af forbindelse til Power BI er forskellig for offentlige brugere og kommercielle brugere. Hvis du vil logge på Power BI, skal du bruge følgende URL-adresser:

| Kommerciel version  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Din konto kan være konfigureret i mere end ét cloudmiljø. Hvis din konto er konfigureret på denne måde, kan du vælge, hvilken cloud der skal oprettes forbindelse til, når du logger på Power BI Desktop.

## <a name="allow-connections-to-power-bi"></a>Tillad, at der oprettes forbindelse til Power BI

Hvis du vil bruge Power BI-tjenesten, skal du tillade forbindelser til påkrævede slutpunkter på internettet. Disse destinationer skal være tilgængelige for at muliggøre kommunikation mellem dit eget netværk, Power BI og andre afhængige tjenester.

I nedenstående tabel viser vi de påkrævede slutpunkter, som du kan føje til din liste over tilladte for at aktivere forbindelsen til Power BI-tjenesten med henblik på generel brug af webstedet. Disse slutpunkter er entydige for US Government-cloudmiljøet. Power BI-tjenesten kræver kun, at TCP-port 443 er åben for de viste slutpunkter. Slutpunkterne for hentning af data, dashboard- og rapportintegration, Power BI-visualiseringer og andre valgfri tjenester er ikke unikke for US Government-cloudmiljøet. Hvis du også vil føje disse URL-adresser til listen over tilladte, skal du se [Føj Power BI URL-adresser til listen over tilladte](power-bi-whitelist-urls.md).

Godkendelse, identitet og administration for Power BI afhænger af forbindelsen til Microsoft 365-tjenester. Du skal også oprette forbindelse til Microsoft 365 for at få vist overvågningslogge. Hvis du vil identificere slutpunkterne for disse tjenester, skal du se Microsoft 365-integration i nedenstående tabel.

### <a name="power-bi-urls-for-general-site-usage"></a>Power BI-URL-adresser til generel brug af webstedet

|  Formål | Destination |
| ---- | ----- |
| Back-end-API'er | **GCC**: api.powerbigov.us |
| | **GCC-High**: api.high.powerbigov.us |
| | **DoD**: api.mil.powerbi.gov.us |
| Back-end-API'er | **GCC**: *analysis.usgovcloudapi.net |
| | **GCC High**: *.high.analysis.usgovcloudapi.net |
| | **DoD**: *.mil.analysis.usgovcloudapi.net |
| Back-end-API'er | **Alle**: *.pbidedicated.usgovcloudapi.net |
| CDN (Content Delivery Network) | **GCC**: gov.content.powerapps.us |
| | **GCC High**: high.content.powerapps.us |
| | **DoD**: mil.content.powerapps.us |
| Microsoft 365-integration | **GCC**: [Globale slutpunkter](/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| | **GCC High**: [US Government GCC High-slutpunkter](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints) |
| | **DoD**: [US Government DOD-slutpunkter](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints) |
| Portal |**GCC**: *.powerbigov.us |
| | **GCC-High**: *.high.powerbigov.us |
| | **DoD**: *.mil.powerbigov.us |
| Tjenestetelemetri | **Alle**: dc.services.visualstudio.us |
| Meddelelser til orientering (valgfrit) | **Alle**: dynmsg.modpim.com |
| NPS-undersøgelser (valgfrit) | **Alle**: nps.onyx.azure.net |

## <a name="connect-government-and-global-azure-cloud-services"></a>Opret forbindelse mellem Government-tjenester og globale Azure Cloud-tjenester

Azure er fordelt på flere cloudmiljøer. Du kan som standard aktivere firewallregler for at åbne en forbindelse til en cloudspecifik forekomst, men netværket på tværs af skyen er anderledes.  Hvis du vil kommunikere mellem tjenester i den offentlige cloud og tjenesterne i Government Community Cloud, skal du konfigurere særlige firewallregler. Hvis du f.eks. vil have adgang til offentlige cloudforekomster af en SQL-database fra din offentlige cloududrulning af Power BI, skal du have en firewallregel i SQL-databasen. Konfigurer særlige firewallregler for SQL-databaser, så der tillades forbindelser til Azure Government Cloud for følgende datacentre:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona
* Det østlige US DoD
* Det centrale US DoD

Hvis du vil have adgang til cloud-IP-intervallerne for US Government, skal du downloade filen [Azure IP Ranges and Service Tags – US Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063). der vises intervaller for både Power BI og Power Query.

Du kan finde flere oplysninger om Microsoft Azure Government-cloudtjenester under [Azure Government-dokumentation](/azure/azure-government/).

Hvis du vil konfigurere firewalls for SQL-databaser, skal du følge fremgangsmåden for at [oprette og administrere IP-firewallregler](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Tilgængelighed af funktioner i Power BI

Der er visse forskelle mellem offentlige planer og kommercielle planer for at imødekomme kravene til offentlige cloudkunder. Vores mål er at gøre alle funktioner tilgængelige i cloudmiljøer for de offentlige myndigheder inden for 30 dage fra, de bliver generelt tilgængelige. I nogle tilfælde forhindrer underliggende afhængigheder os i at gøre en funktion tilgængelig. På listen nedenfor vises de funktioner, der endnu ikke er tilgængelige i et bestemt offentligt miljø, eller som er tilgængelige med begrænset funktionalitet. Listen bruger følgende nøgle:

|Nøgle |Beskrivelse|
|-----|------|
|![tilgængelig](../media/yes.png)|Funktionen er tilgængelig i miljøet med eventuelle undtagelser, der er defineret i fodnoter.|
|![ikke tilgængelig](../media/no.png)| Funktionen er ikke tilgængelig i miljøet, og vi har ikke en forventet tidsramme for levering.|

Vi medtager kvartalet for anslået tilgængelighed, hvis udgivelsen planlægges for et miljø.

|Funktion |GCC |GCC High |DoD|
|------|------|------|------|
|[Azure B2B-samarbejde mellem cloudmiljøet for de offentlige myndigheder og det kommercielle cloudmiljø](service-admin-azure-ad-b2b.md)<sup>1</sup>|![tilgængelig](../media/yes.png)|![tilgængelig](../media/yes.png)|![tilgængelig](../media/yes.png)
|[Skabelonapps](../connect-data/service-template-apps-overview.md)<sup>2</sup>|![tilgængelig](../media/yes.png) |![tilgængelig](../media/yes.png)| ![tilgængelig](../media/yes.png)|
|[Integrer i SharePoint Online ved hjælp af Power BI-webdelen](/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![tilgængelig](../media/yes.png)|![tilgængelig](../media/yes.png)|![ikke tilgængelig](../media/no.png)|
|[Data beskyttelse (MIP-mærkater)](service-security-sensitivity-label-overview.md)|![tilgængelig](../media/yes.png)|![tilgængelig](../media/yes.png) |1\. kvt. 2021|
|[Dataflow – -direkte forespørgsel](../transform-model/dataflows/dataflows-configure-consume.md) | ![tilgængelig](../media/yes.png) |![tilgængelig](../media/yes.png)|Ikke planlagt |
|[Power BI-fanen i Teams](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>3</sup>|![tilgængelig](../media/yes.png)|![ikke tilgængelig](../media/no.png)|![ikke tilgængelig](../media/no.png)|
|[Store modeller](service-premium-large-models.md) | 1\. kvt. 2021 |1\. kvt. 2021| Ikke planlagt |
|[Dataflow – SQL Compute-programoptimering](../transform-model/dataflows/dataflows-premium-features.md) | ![ikke tilgængelig](../media/no.png) |![ikke tilgængelig](../media/no.png)| ![ikke tilgængelig](../media/no.png) |
|[Foretag et kald til kvalitetsdata-connector](/microsoftteams/cqd-power-bi-connector)|![ikke tilgængelig](../media/no.png)|![ikke tilgængelig](../media/no.png)|![ikke tilgængelig](../media/no.png)|
|[Bring Your Own Storage (Azure Data Lake Gen 2)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md)|![ikke tilgængelig](../media/no.png)|![ikke tilgængelig](../media/no.png)|![ikke tilgængelig](../media/no.png)|

<sup>1</sup> Selvom B2B Collaboration er tilgængelig til GCC, skal der udstedes en licens til eksterne brugere i dette miljø. Kommercielle cloudlicenser er ikke gyldige i GCC. Du kan finde flere oplysninger om kendte begrænsninger med B2B Collaboration til US Government ved at [sammenligne Azure Government og global Azure](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2).

<sup>2</sup> Marketplace-apps er ikke tilgængelige til cloudforekomster af US Government, så skabelonapps er begrænset til private apps og organisationsapps.

<sup>3</sup> Power BI-oplevelsen i Teams til GCC er begrænset, fungerer kun for klassiske arbejdsområder og indeholder ikke den forbedrede funktionalitet, der er beskrevet i [Integrerer Power BI-indhold i Microsoft Teams](../collaborate-share/service-embed-report-microsoft-teams.md).

## <a name="next-steps"></a>Næste trin

* [Tilmeld dig Power BI til US Government](service-govus-signup.md)
* [Microsoft Power Apps US Government](/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](/power-automate/us-govt)
* [Demo om Power BI US Government](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)
