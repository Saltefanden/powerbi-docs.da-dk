---
title: Foretag fejlfinding af XMLA-slutpunktsforbindelse i Power BI Premium (prøveversion)
description: Beskriver, hvordan du foretager fejlfinding af forbindelsen via XMLA-slutpunktet i Power BI Premium.
author: minewiskan
ms.author: owend
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 10/14/2020
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: c8f0683e0789ec29577322424a4187a42ff5679f
ms.sourcegitcommit: 59d07be9c3e4a2067f6d42c3002a194371bc4341
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/16/2020
ms.locfileid: "92116563"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>Foretag fejlfinding af XMLA-slutpunktsforbindelse

XMLA-slutpunkter i Power BI Premium er baseret på den oprindelige Analysis Services-kommunikationsprotokol for at få adgang til Power BI-datasæt. Derfor er fejlfinding af XMLA-slutpunkter stort set det samme som fejlfinding af en normal Analysis Services-forbindelse. Der er dog nogle forskelle, hvad angår Power BI-specifikke afhængigheder.

## <a name="before-you-begin"></a>Inden du starter

Før du foretager fejlfinding af et scenarie med XMLA-slutpunkter, skal du gennemgå de grundlæggende principper, der er beskrevet under [Netværksmulighed for datasæt med XMLA-slutpunktet](service-premium-connect-tools.md). De mest almindelige brugseksempler med XMLA-slutpunkter beskrives der. Andre Power BI-fejlfindingsvejledninger, f. eks. [Foretag fejlfinding af gateways – Power BI](../connect-data/service-gateway-onprem-tshoot.md) og [Fejlfinding af Analysér i Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md), kan også være nyttige.

## <a name="enabling-the-xmla-endpoint"></a>Aktivering af XMLA-slutpunktet

XMLA-slutpunktet kan aktiveres både i Power BI Premium- og Power BI Embedded-kapaciteter. I mindre kapaciteter, f. eks. en A1-kapacitet med kun 2,5 GB hukommelse, kan der opstå en fejl i kapacitetsindstillingerne, når du forsøger at angive XMLA-slutpunktet til at **Læs/skriv** og derefter vælge **Anvend**. I fejlmeddelelsen angives følgende: "Der opstod et problem med arbejdsbelastningsindstillingerne. Prøv igen om et øjeblik.".

Her er et par ting, du kan prøve:

- Begræns hukommelsesforbruget for andre tjenester i kapaciteten, f. eks. dataflows, til 40 % eller mindre, eller deaktiver en unødvendig tjeneste helt.  
- Opgrader kapaciteten til en større SKU. Hvis du f. eks. opgraderer fra en A1- til en A3-kapacitet, løser dette konfigurationsproblemet, uden at du skal deaktivere dataflow.

Vær opmærksom på, at du også skal aktivere [indstillingen Eksportér data](service-premium-connect-tools.md#security) på lejerniveau i Power BI-administrationsportalen. Denne indstilling er også påkrævet til funktionen Analysér i Excel.

## <a name="establishing-a-client-connection"></a>Oprettelse af en klientforbindelse

Når du har aktiveret XMLA-slutpunktet, er det en god idé at teste forbindelsen til et arbejdsområde i kapaciteten. Du kan finde flere oplysninger under [Opret forbindelse til et Premium-arbejdsområde](service-premium-connect-tools.md#connecting-to-a-premium-workspace). Du kan også læse afsnittet [Forbindelses krav](service-premium-connect-tools.md#connection-requirements) for at få nyttige tip og oplysninger om aktuelle begrænsninger for XMLA-forbindelser.

### <a name="connecting-with-a-service-principal"></a>Oprettelse af forbindelse til en tjenesteprincipal

Hvis du har aktiveret lejerindstillinger for at tillade, at tjenesteprincipaler bruger Power BI-API'er som beskrevet i [Aktivér tjenesteprincipaler](service-premium-service-principal.md#enable-service-principals), kan du oprette forbindelse til et XMLA-slutpunkt ved hjælp af en tjenesteprincipal. Vær opmærksom på, at tjenesteprincipalen kræver det samme niveau af adgangsrettigheder på arbejdsområde- eller datasætniveau som almindelige brugere.

Hvis du vil bruge en tjenesteprincipal, skal du sørge for at angive oplysningerne om applikationsidentitet i forbindelsesstrengen som:

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

Eksempel:

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

Hvis du får vist følgende fejl:

"Vi kan ikke oprette forbindelse til datasættet på grund af ufuldstændige kontooplysninger. For tjenesteprincipaler skal du angive lejer-id'et sammen med app-id'et ved hjælp af formatappen: \<appId>@\<tenantId> og derefter prøve igen. "

Sørg for, at du angiver lejer-id'et sammen med app-id'et i det korrekte format.

Det er også gyldigt at angive app-id'et uden lejer-id'et. I dette tilfælde skal du dog erstatte alisasset `myorg` i datakildens URL-adresse med det faktiske lejer-ID. Power BI kan derefter finde tjenesteprincipalen i den korrekte lejer. Men bedste praksis er at bruge aliasset `myorg` og angive lejer-id'et sammen med app-id'et i bruger-id-parameteren.

### <a name="connecting-with-azure-active-directory-b2b"></a>Oprettelse af forbindelse til Microsoft Azure Active Directory B2B

Med understøttelse af Microsoft Azure Active Directory (Azure AD) Business-to-business (B2B) i Power BI kan du give eksterne gæstebrugere adgang til datasæt via XMLA-slutpunktet. Kontrollér, at funktionen [Del indhold med eksterne brugere](service-admin-portal.md#export-and-sharing-settings) er aktiveret i Power BI-administrationsportalen. Se [Distribuer Power BI-indhold til eksterne gæstebrugere med Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="deploying-a-dataset"></a>Udrulning af et datasæt

Du kan udrulle et tabellarisk modelprojekt i Visual Studio (SSDT) til et Power BI Premium-arbejdsområde på stort set samme måde som til Azure Analysis Services. Når du udruller til et Power BI Premium-arbejdsområde, er der imidlertid nogle yderligere overvejelser. Sørg for at gennemse afsnittet [Udrul modelprojekter fra Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) i artiklen Netværksmulighed for datasæt med XMLA-slutpunktet.

### <a name="deploying-a-new-model"></a>Udrulning af en ny model

I standardkonfigurationen forsøger Visual Studio at behandle modellen som en del af udrulningen for at indlæse data i datasættet fra datakilderne. Som beskrevet i [Udrul modelprojekter fra Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) kan denne handling muligvis ikke udføres, fordi legitimationsoplysningerne for datakilden ikke kan angives som en del af udrulningen. Hvis legitimationsoplysningerne for datakilden ikke allerede er defineret for nogen af dine eksisterende datasæt, skal du i stedet angive legitimationsoplysningerne for datakilden i indstillingerne for datasættet ved hjælp af Power BI-brugergrænsefladen (**Datasæt** > **Indstillinger** > **Legitimationsoplysninger for datakilde** > **Rediger legitimationsoplysninger**). Når du har defineret legitimationsoplysningerne for datakilden, kan Power BI automatisk anvende legitimationsoplysningerne på denne datakilde for ethvert nyt datasæt, efter at udrulningen af metadata er fuldført, og datasættet er blevet oprettet.

Hvis Power BI ikke kan binde dit nye datasæt til legitimationsoplysningerne for datakilden, får du vist fejlmeddelelsen: "Databasen kan ikke behandles. Årsag: Ændringerne blev ikke gemt på serveren." med fejlkoden "DMTS_DatasourceHasNoCredentialError" som vist nedenfor:

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="Fejl i modeludrulning":::

Hvis du vil undgå behandlingsfejl, skal du angive **Installationsindstillinger** > **Behandlingsmuligheder** til **Behandl ikke** som vist på følgende billede. Visual Studio udruller derefter kun metadata. Du kan derefter konfigurere legitimationsoplysningerne for datakilden og klikke på **Opdater nu** for datasættet i Power BI-brugergrænsefladen. Du kan finde oplysninger om fejlfinding af behandlingsproblemer i afsnittet [Opdatering af et datasæt](#refreshing-a-dataset) senere i denne artikel.

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="Fejl i modeludrulning":::

### <a name="new-project-from-an-existing-dataset"></a>Nyt projekt ud fra et eksisterende datasæt

Oprettelse af et nyt tabellarisk projekt i Visual Studio ved at importere metadataene fra et eksisterende datasæt i et Power BI Premium-arbejdsområde understøttes ikke. Du kan dog oprette forbindelse til datasættet ved hjælp af SQL Server Management Studio, scripte metadataene og genbruge dem i andre tabellariske projekter.

## <a name="migrating-a-dataset-to-power-bi"></a>Overførsel af et datasæt til Power BI

Det anbefales, at du angiver kompatibilitetsniveauet 1500 (eller højere) for tabellariske modeller. Dette kompatibilitetsniveau understøtter de fleste egenskaber og datakildetyper. Nyere kompatibilitetsniveauer er bagudkompatible med tidligere niveauer.

### <a name="supported-data-providers"></a>Understøttede dataprovidere

På kompatibilitetsniveauet 1500 understøtter Power BI følgende datakildetyper:

- Providerdatakilder (ældre med en forbindelsesstreng i modellens metadata).
- Strukturerede datakilder (introduceret med kompatibilitetsniveauet 1400).
- Indbyggede M-erklæringer om datakilder (som Power BI Desktop deklarerer dem).

Det anbefales, at du bruger strukturerede datakilder, som Visual Studio opretter som standard, når du gennemgår importdataflowet. Men hvis du planlægger at overføre en eksisterende model til Power BI, der bruger en providerdatakilde, skal du sørge for, at providerdatakilde er baseret på en understøttet dataprovider. Specifikt Microsoft OLE DB-driveren til SQL Server og alle ODBC-drivere fra tredjepart. Hvad angår OLE DB-driveren til SQL Server, skal du ændre datakildedefinitionen til .NET Framework-dataprovider til SQL Server. Hvad angår ODBC-drivere fra tredjepart, der muligvis er utilgængelige i Power BI-tjenesten, skal du i skifte til en struktureret datakildedefinition.

Det anbefales også, at du erstatter den forældede Microsoft OLE DB-driver til SQL Server (SQLNCLI11) i dine SQL Server-datakildedefinitioner med .NET Framework-dataprovideren til SQL Server.

Følgende tabel indeholder et eksempel på en forbindelsesstreng for .NET Framework-dataprovideren til SQL Server, der erstatter en tilsvarende forbindelsesstreng til OLE DB-driveren til SQL Server.

|OLE DB-driver til SQL Server  |.Net Framework-dataprovider til SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>Krydsreferencer til partitionskilder

På samme måde som der er flere datakildetyper, er der også flere partitionskildetyper, som kan medtages i en tabellarisk model for at importere data i en tabel. En partition kan især bruge en forespørgselspartitions kilde eller en M-partitionskilde. Disse partitionskildetyper kan f. eks. henvise til providerdatakilder eller strukturerede datakilder. Selvom tabellariske modeller i Azure Analysis Services understøtter krydsreferencer til disse forskellige datakilder og partitionstyper gennemtvinger Power BI en strengere relation. Forespørgselspartitionskilder skal referere til providerdatakilder, og M-partitionskilder skal referere til strukturerede datakilder. Ander kombinationer understøttes ikke i Power BI. Hvis du vil overføre et dataset med krydsreferencer, beskrives de understøttede konfigurationer i følgende tabel:  

|Datakilde   |Partitionskilde   |Kommentarer   |Understøttes i Power BI Premium med XMLA-slutpunkt   |
|---------|---------|---------|---------|
|Providerdatakilde      |   Forespørgselspartitionskilde      |   AS-programmet bruger den cartridgebaserede forbindelsesstak til at oprette adgang til datakilden.       |     Ja     |
|Providerdatakilde      |   M-partitionskilde       |   AS-programmet oversætter providerdatakilden til en generisk struktureret datakilde og bruger derefter miksprogrammet til at importere dataene.       |    Nej     |
|Struktureret datakilde      |     Forespørgselspartitionskilde     |    AS-programmet ombryder den oprindelige forespørgsel i partitionskilden til et M-udtryk og bruger derefter miksprogrammet til at importere dataene.      |    Nej     |
|Struktureret datakilde      |    M-partitionskilde      |     AS-programmet bruger miksprogrammet til at importere dataene.     |   Ja      |

## <a name="refreshing-a-dataset"></a>Opdatering af et datasæt

XMLA-slutpunkter gør det muligt for dig at udføre opdateringshandlinger mod tabellariske modeller samt datasæt, der er oprettet i Power BI Desktop. Hvis du vil understøtte sidstnævnte, skal du sørge for at angive indstillingen for forbedret lagringsformat. Denne indstilling er påkrævet, hvis du vil udføre behandling eller andre læse-/skrivehandlinger ved hjælp af XMLA-slutpunktet. Du kan finde indstillingen i Power BI Desktop under prøveversionsfunktioner. Når du har angivet indstillingen, kan du udgive PBIX-løsningen igen til Power BI Premium-arbejdsområdet.  

Power BI returnerer følgende fejl, hvis du foretager en opdatering via XMLA-slutpunktet mod en model uden udvidede metadata: "Handlingen understøttes kun på modeller, hvor egenskaben "DefaultPowerBIDataSourceVersion" er angivet til "PowerBI_V3" i PowerBI Premium."

### <a name="data-sources-and-impersonation"></a>Datakilder og repræsentation

Repræsentationsindstillinger, du kan definere for providerdatakilder, er ikke relevante for Power BI. I Power BI bruges der en anden mekanisme, der er baseret på datasætindstillinger, til administration af legitimationsoplysningerne for datakilden. Derfor skal du sikre dig, at du vælger **Tjenestekonto**, hvis du opretter en providerdatakilde.

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="Fejl i modeludrulning":::

### <a name="fine-grained-processing"></a>Detaljeret behandling

Når der udløses en planlagt opdatering eller en opdatering efter behov i Power BI, opdateres hele datasættet normalt i Power BI. I mange tilfælde er det mere effektivt at udføre opdateringer mere selektivt. Du kan udføre detaljerede behandlingsopgaver i SQL Server Management Studio (SSMS) som vist nedenfor eller ved hjælp af værktøjer eller scripts fra tredjepart.

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="Fejl i modeludrulning":::

### <a name="overrides-in-refresh-tmsl-command"></a>Tilsidesættelser i TMSL-kommandoen Opdater

Tilsidesættelser i [kommandoen Opdater (TMSL)](/analysis-services/tmsl/refresh-command-tmsl) giver brugere mulighed for at vælge en anden definition af partitionsforespørgsel eller en anden definition af datakilde for opdateringshandlingen. I øjeblikket **understøttes tilsidesættelser ikke** i Power BI Premium. Fejlen "Binding uden for linje er ikke tilladt i Power BI Premium. Du kan finde flere oplysninger i afsnittet "XMLA read/write support" i produktdokumentationen. returneres.

## <a name="see-also"></a>Se også

[Netværksmulighed for datasæt med XMLA-slutpunktet](service-premium-connect-tools.md)   
[Automatiser opgaver for arbejdsområder og datasæt i Premium med tjenesteprincipaler](service-premium-service-principal.md)   
[Fejlfinding af Analysér i Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)   
[Udrulning af løsning med tabellarisk model](/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current)