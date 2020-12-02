---
title: Nyheder i Power BI-rapportserver
description: Få mere at vide om nyheder i den nyeste version af Power BI-rapportserver. I denne artikel beskrives de primære funktionsområder, og den opdateres, når der udgives nye versioner.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/30/2020
ms.openlocfilehash: 14b629eed17eca2d1e016913dcfffb5858d4ddc3
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2020
ms.locfileid: "96120750"
---
# <a name="whats-new-in-power-bi-report-server"></a>Nyheder i Power BI-rapportserver

Få mere at vide om de nyeste versioner af Power BI-rapportserver og Power BI Desktop optimeret til Power BI-rapportserver. I denne artikel beskrives de primære funktionsområder, og den opdateres, hver gang der udgives en ny version. Se [Ændringslog for Power BI-rapportserver](changelog.md) for at få mere at vide om, hvad der er nyt i Power BI-rapportserver og Power BI Desktop, der er optimeret til Power BI-rapportserver.

Download [Power BI-rapportserver og Power BI Desktop optimeret til Power BI-rapportserver](https://powerbi.microsoft.com/report-server/).

## <a name="october-2020"></a>Oktober 2020

Det følgende er en komplet liste over nye og opdaterede funktioner. Du kan finde flere oplysninger i [Blogindlægget om Power BI-rapportserver fra oktober 2020](https://powerbi.microsoft.com/blog/power-bi-report-server-october-2020-feature-summary/). 

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop optimeret til Power BI-rapportserver

Her er nogle af de nye funktioner.

**Moderne bånd**  

Det moderne bånd fås nu i Power BI Desktop optimeret til Power BI-rapportserver. Vi vil fortsætte med at foretage tilføjelser og føje flere funktioner til båndet. Se [Brug af det opdaterede bånd i Power BI Desktop](../create-reports/desktop-ribbon.md) for at få mere at vide om ændringerne og fordelene.

:::image type="content" source="media/whats-new/report-server-new-ribbon.png" alt-text="Skærmbillede af det nye bånd i Power BI Desktop optimeret til Power BI-rapportserver.":::

**Hierarki-udsnitsværktøjer**

Du kan oprette det, der kaldes et *hierarki-udsnitsværktøj*, til at filtrere flere relaterede felter i et enkelt udsnit. Nu hvor det er offentligt tilgængelig, er der blevet tilføjet yderligere funktioner:

- Nye indstillinger for ikonerne for udvid/skjul.
- Ikonerne skaleres nu med skriftstørrelsen.
- Brugerdefinerbar indrykning for underordnede elementer.
- Yderligere tilpasning af teksten i udsnittets header.

:::image type="content" source="media/whats-new/report-server-slicer-hierarchy.png" alt-text="Hierarki-udsnitsværktøj i Power BI Desktop optimeret til Power BI-rapportserver.":::

Se [Udsnit i Power BI](../visuals/power-bi-visualization-slicers.md) i dokumentationen for at få flere oplysninger.

**Forbedringer af mobiloprettelse** 

I denne version introducerer vi en forbedret funktionalitet til oprettelse af mobillayout og yderligere funktioner til mobillayout. Da flere og flere organisationer benytter Power BI-mobilapps, har vi modtaget feedback om at få flere muligheder og forbedringer til mobiloprettelse. Forbedringerne i denne version vil hjælpe dig med lettere at oprette overbevisende interaktive rapporter, der er optimeret til mobilenheder.

Her er de nye funktioner til oprettelse af mobiloptimerede rapporter:  

- Ny telefonemulator  
- Opdateret visualiseringsrude  
- Understøttelse af overlejrede visualiseringer  
- Bogmærker, der er tilgængelige i mobillayoutvisningen  
- Deaktivering af gitterlinjer og fastgørelse til gitter  

:::image type="content" source="media/whats-new/report-server-mobile-layout.png" alt-text="Forbedret mobillayout i Power BI Desktop optimeret til Power BI-rapportserver.":::

Se dette blogindlæg [Forbedringer af mobiloprettelse](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2020-feature-summary/#_mobile) for at få flere oplysninger.

**Dataforberedelse: automatisk tabelregistrering fra Excel-filer**

Denne nye funktion i Excel Connector identificerer automatisk sektioner i hvert Excel-regneark til udtrækning til en tabel. Den viser dem under gruppen Foreslåede tabeller i navigatoren. Tidligere skulle data formateres som en tabel eller et navngivet område i Excel. Ellers skulle du kassere de relevante rækker/kolonner med bestemte transformeringer, f.eks. ved at springe rækker over og fjerne kolonner fra regnearksobjekter, som i Ark1 i følgende eksempel. Hvis du vil bruge denne funktion, skal du aktivere den i dialogboksen **Indstillinger**.

:::image type="content" source="media/whats-new/report-server-excel-table.png" alt-text="Genkendelse af en Excel-tabel i Power BI Desktop optimeret til Power BI-rapportserver.":::

**Udformning: metadata for forbedrede datasæt**

Tidligere var det kun de forespørgsler, der kunne indlæses, og som blev genereret i Power-forespørgsel, der blev knyttet til datamodellen. Nu er alle forespørgsler knyttet til objekter i datamodellen. Forespørgslerne gendannes baseret på datamodellen, når du åbner den pågældende PBIX-fil.

Denne backend-opdatering vil blive yderligere forbedret i fremtiden. 

Eksempel:

- Når eksterne værktøjer tilføjes i Power BI Desktop (i øjeblikket som prøveversion), vises de tabeller, du tilføjer via disse eksterne værktøjer, nu som forespørgsler, når du åbner din rapport igen.
- Hvis du har prøvet at eksportere en PBIT-fil og udpakke filen, kan du nu se modellen i JSON og får ikke længere fejl om beskadigede filer. 

Hvis du har en ældre PBIX, der ikke automatisk kan opdateres, f.eks. på grund af ikke-anvendte ændringer, skal du opgradere din model korrekt, før du kan foretage yderligere udformningsændringer. 

**Understøttelse af Windows 7 stopper**

Understøttelsen af Windows 7 ophørte efter 10 år den 14. januar 2020. I tråd med dette vil vi stoppe understøttelsen af Power BI Desktop i Windows 7 den 31. januar 2021. Herefter understøttes Power BI Desktop udelukkende i Windows 8 og nyere. Januar 2021-udgivelsen af Power BI Desktop optimeret til rapportserver understøttes i henhold til den moderne politik for livscyklus. Det vil med andre ord sige, at den understøttes fuldt ud indtil den næste version (der er planlagt til maj 2021). Efter maj 2021 vil den kun modtage sikkerhedsopdateringer indtil januar 2022. Al support stopper efter januar 2022. Se [Supporttidslinje for Power BI-rapportserver](support-timeline.md) for at få flere oplysninger. 

**Komplet liste over opdateringer**

Her er en komplet liste over opdateringerne i oktober-udgaven af Power BI Desktop optimeret til Power BI-rapportserver. 

**Rapportering**

- Moderne bånd
- Lærredsvandmærker
- Det samlede antal mærkater for stablede visualiseringer
- Der er tilføjet en generel visuel indstilling til at vedligeholde lagrækkefølgen
- Gradueringsforklaring
- Relativt tidsfilter
- Mulighed for yderligere at tilpasse overskriftsteksten i udsnitsværktøjet
- Forbedringer af hierarkiske udsnitsværktøjer

    - Nye indstillinger for ikonerne for udvid/skjul
    - Ikonerne skaleres nu med skriftstørrelsen
    - Mulighed for at tilpasse indrykning for underordnede elementer

- Forbedringer af mobiloprettelse

    - Ny telefonemulator
    - Opdateret visualiseringsrude
    - Understøttelse af overlejrede visualiseringer
    - Bogmærker, der er tilgængelige i mobillayoutvisningen
    - Deaktivering af gitterlinjer og fastgørelse til gitter  

**Visualiseringer**

- Formateringsindstillinger for punkter i kurvediagram 

**Modellering**

- Metadata for forbedrede datasæt
- Forbedringer af ydeevnen til IF- og SWITCH-funktioner
- Understøttelse af Excel-økonomifunktioner
- Modelvisning aktiveret til Live Connect
- Opdateringer af modelvisning 

**Dataforberedelse**

- Automatisk tabelregistrering fra Excel-filer  
- Automatisk tabelregistrering fra JSON-filer  
- Global indstilling til deaktivering af automatisk typeregistrering 

**Andet**  

- Eksportér datakilde til PBIDS i Power BI Desktop
- Annullering af velkomstbillede på stationære computere 

### <a name="power-bi-report-server"></a>Power BI-rapportserver

**Skift forbindelsesstrenge til datakilden i Power BI-rapporter ved hjælp af PowerShell**

I versionen af Power BI-rapportserver fra oktober aktiverer vi muligheden for at opdatere forbindelser for Power BI-rapporter til DirectQuery og opdatering. Dette er også en banebrydende ændring af, hvordan du kunne konfigurere dette i tidligere versioner. Du kan få mere at vide i [Skift forbindelsesstrenge til datakilden i Power BI-rapporter ved hjælp af PowerShell – Power BI-rapportserver](connect-data-source-apis.md). 

## <a name="may-2020"></a>Maj 2020

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop optimeret til Power BI-rapportserver

Blandt de fremhævede elementer i denne opdatering er de hierarkiske udsnitsværktøjer og visualiseringer med opdelingstræ og forespørgselsdiagnosticering. Det følgende er en komplet liste over nye og opdaterede funktioner. Du kan finde flere oplysninger i [Blogindlægget om Power BI-rapportserver fra maj 2020](https://powerbi.microsoft.com/blog/power-bi-report-server-may-2020-feature-summary/). 

#### <a name="reporting"></a>Rapportering

- Hierarkisk udsnitsværktøj
- Nye handlingstyper for knapper:

    - Sidenavigation
    - Detaljeadgang

- Knapper understøtter nu udfyldningsbilleder
- Sortering af tabeller med flere kolonner
- Dobbelt akse til kurvediagrammer
- Valg med rektangel for visuelle elementer
- Betinget formatering af totaler og subtotaler i tabel og matrix
- Dialogboksen Tilpas tema
- Registrering af betinget formatering
- Fordelingstræ
- Opdateringer til filterrude:

    - Ny oplevelse af filterruden
    - Filterrudesøgning
    
#### <a name="modeling"></a>Modellering

- Nye DAX-funktioner:

    - FirstNonBlankValue
    - LastNonBlankValue
    - Coalesce

- Standard DAX-separatorer

#### <a name="visualizations"></a>Visualiseringer

- Nye visualiseringsikoner
- Visuelle baggrundsskygger

#### <a name="data-preparation"></a>Dataforberedelse

- Forespørgselsdiagnosticering

#### <a name="other"></a>Andet

- Brug af systemets standardlegitimationsoplysninger for webproxy

### <a name="power-bi-report-server"></a>Power BI-rapportserver

#### <a name="power-bi-visuals-api"></a>Visualiserings-API i Power BI

API-version 3.2 leveres med denne udgivelse.

## <a name="january-2020"></a>Januar 2020

Du kan finde flere oplysninger i blogindlægget om Power BI-rapportserver fra januar 2020.

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop optimeret til Power BI-rapportserver

Denne udgivelse indeholder mange nye funktioner, f.eks. betinget formatering af knapper, forbedringer af dataprofilering og flere formateringsindstillinger for KPI'er og tabelvisualiseringer. Her er en opsummeret liste over opdateringer:

**Rapportering**

- Angivelse af en værdi for en tabelkolonne eller en matrix som en brugerdefineret URL-adresse
- Formateringsindstillinger for KPI-visualiseringer
- Opdateringer af oplevelsen med filterruden

**Analyse**

- Knapper med betinget formatering
- Indlæs mere for at få indsigt i analyser
- Ny DAX-funktion: Kvartal

**Dataforberedelse**

- Forbedringer af dataprofilering

**Andet**

- Nyt filformat: .pbids
- Forbedringer af ydeevnen i forbindelse med udformningshandlinger

**Rapportering**

*Angiv en værdi for en tabelkolonne eller en matrix som en brugerdefineret URL-adresse*

Du kan angive en værdi for en tabelkolonne eller en matrix som en brugerdefineret URL-adresse. Du finder denne nye indstilling under kortet til betinget formatering i formateringsruden.

*Formateringsindstillinger for KPI-visualiseringer*

Med denne måneds udgivelse har KPI'er fået nye formateringsindstillinger:

- Tekstformatering for indikator (skrifttypeserie, farve og justering)
- Tendens for aksegennemsigtighed
- Tekstformatering for mål og afstand (mærkattekst, skrifttypeserie, farve og størrelse)
- Afstand i forbindelse med tekstformatering (mærkattekst, positiv retning, skrifttypeserie, farve og størrelse)
- Tilføjelse af en datomærkat med formatering (skrifttypeserie, farve og størrelse)

Du kan bruge betinget formatering til nogle af disse nye formateringsindstillinger:

- Skrifttypefarve for indikator
- Skrifttypefarve for mål og skrifttypefarve for målafstand
- De gode/dårlige/neutrale statusfarver
- Skrifttypefarve for dato

*Opdateringer af oplevelsen med filterruden*

Som en del af den generelle tilgængelighed af den nye filteroplevelse fra den [nyeste udgivelse](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane) har vi strømlinet processen for at overføre aktuelle rapporter til den nye rude. Første gang, du åbner Power BI-rapportserver, kan du se en dialogboks til automatisk opdatering af filterruden. Disse opdateringer omfatter også bannere i rapportserver, når rapporter skal overføres til den nye oplevelse.

**Analyse**

*Betinget formatering af knapper*

Disse opdateringer af betinget formatering er alle sammen relateret til knapper. Du kan nu angive formatering dynamisk for følgende egenskaber:

- Skriftfarve for knaptekst
- Knaptekst
- Stregfarve for ikon
- Konturfarve
- Udfyldningsfarve
- Værktøjstip til knap (under handlingskortet)

*Indlæs mere for at få indsigt i analyser*

Når du kører funktionen Analysér for at finde indsigt i dine data, f.eks. Forklar forøgelsen, kører vi kun modeller til maskinel indlæring i en bestemt tidsperiode, så du kan få vist indsigt rettidigt. Hvis der er mange data, der skal analyseres, kan du nu vælge at fortsætte med at køre analysen efter den første timeout.

*Ny DAX-funktion: Quarter*

I denne måned har vi en ny DAX-funktion, Quarter. Funktionen Quarter returnerer det kvartal, der svarer til en bestemt dato.

**Dataforberedelse**

*Forbedringer af dataprofilering*

I denne måned introducerer vi nogle vigtige forbedringer af vores egenskaber til dataprofilering i Power Query-editor, herunder:

- Flere grupperingsindstillinger for visualiseringen med distribution af værdien for ruden Kolonneprofil, helt specifikt efter kolonnetype, sammen med det eksisterende kriterie "Efter værdi".
- Tekst: Efter tekstlængde (antal tegn).
- Antal: Efter tegn (positiv/negativ) og paritet (lige/ulige).
- Dato/Datetime: Efter år, måned, dag, uge i året, ugedag, AM/PM-tid og time inden for en dag.
- Og meget mere for andre datatyper, f.eks. logisk sand/falsk.

*Filtermuligheder*

Du havde allerede mulighed for at benytte dig af adskillige specifikke grupperingskriterier i distributionsruden Kolonneprofiler. Nu kan du også filtrere fra forklaringer for hver af værdierne i distributionsdiagrammet, når der anvendes grupperingskriterier. Du kan f.eks. udelade alle værdier, der ligger i en bestemt måned, fra ruden Dataprofiler for en Dato/Datetime-kolonne.

**Andet**

*Nyt filformat: .pbids*

I denne måned udgiver vi et nyt filformat: .pbids, som du kan bruge til at strømline oplevelsen "Hent data" for rapportforfattere i din organisation. Det anbefales, at administratorer opretter disse filer for almindeligt anvendte forbindelser.

Når en rapportforfatter åbner en. pbids-fil, spørger Power BI Desktop efter godkendelse for at oprette forbindelse til den datakilde, der er angivet i filen. Brugeren vælger derefter de tabeller, der skal indlæses i modellen. Brugerne skal muligvis også vælge databasen, hvis der ikke blev angivet en i filen. Herfra kan rapportforfatteren begynde at oprette visualiseringer.

Find oplysninger og eksempler under afsnittet [Brug .pbids-filer til at hente data](../connect-data/desktop-data-sources.md#using-pbids-files-to-get-data) i artiklen "Datakilder i Power BI Desktop".

*Forbedringer af ydeevnen i forbindelse med udformningshandlinger*

Vi har foretaget en forbedring af ydeevnen i Analysis Services-programmet, så udformningshandlinger bliver hurtigere, f.eks. tilføjelse af målinger eller beregnede kolonner og oprettelse af relationer. Mængden af forbedringer, der vises, afhænger af modellen, men vi har set en forbedring af ydeevnen på 20 gange så meget for nogle kunder i forbindelse med handlinger såsom at åbne en fil og tilføje en måling.

Det er alt for denne udgivelse af Power BI-rapportserver i januar 2020. Fortsæt med at sende feedback, og glem ikke at [stemme på funktioner, du gerne vil se i Power BI](https://ideas.powerbi.com/forums/265200-power-bi).

### <a name="power-bi-report-server"></a>Power BI-rapportserver

#### <a name="export-to-excel-from-power-bi-reports"></a>Eksportér til Excel fra Power BI-rapporter

Eksport til Excel fra en Power BI-rapport i Power BI-rapportserver fungerer nu på samme måde som eksport til Excel fra en Power BI-rapport i Power BI-tjenesten. Du kan eksportere direkte til Excel-formatet .xlsx, og eksportgrænsen er 150.000 rækker.

#### <a name="azure-sql-managed-instance-support"></a>Understøttelse af Azure SQL Managed Instance

Du kan nu hoste et databasekatalog, der bruges til Power BI-rapportserver, i en Azure SQL Managed Instance (MI), der hostes enten på en virtuel maskine eller i dit datacenter. Understøttelse er begrænset til at brug af legitimationsoplysninger for databasen for forbindelsen til SQL MI.

#### <a name="power-bi-premium-dataset-support"></a>Understøttelse af Power BI Premium-datasæt

Du kan oprette forbindelse til Power BI-datasæt ved hjælp af enten Microsoft Report Builder eller SQL Server Data Tools (SSDT). Du kan derefter publicere disse rapporter til Power BI-rapportserver ved hjælp af SQL Server Analysis Services-netværksmuligheder. Brugerne skal bruge et gemt brugernavn og en gemt adgangskode til Windows for at aktivere scenariet.

#### <a name="alttext-alternative-text-support-for-report-elements"></a>Understøttelse af AltText (alternativ tekst) for rapportelementer

Når du opretter rapporter, kan du bruge værktøjstip til at angive tekst for hvert element i rapporten. Skærmlæserteknologier bruger disse værktøjstip.

#### <a name="azure-active-directory-application-proxy-support"></a>Understøttelse af proxyprogram til Azure Active Directory

Med proxyprogram til Azure Active Directory behøver du ikke længere at administrere din egen webprogramproxy for at tillade sikker adgang via web- eller mobilprogrammer. Du kan finde flere oplysninger under [Fjernadgang til programmer i det lokale miljø via proxyprogram til Azure Active Directory](/azure/active-directory/manage-apps/application-proxy).

#### <a name="custom-headers"></a>Brugerdefinerede headere

Angiver headerværdier for alle URL-adresser, der svarer til det angivne søgemønster. Brugerne kan opdatere værdien for den brugerdefinerede header med en gyldig XML for at angive headerværdier for de valgte URL-adresser til anmodninger. Administratorer kan tilføje et hvilket som helst antal headere i XML-filen. Du kan finde flere oplysninger under [CustomHeaders](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders) i artiklen **Siden Avancerede serveregenskaber** til Reporting Services.

#### <a name="transparent-database-encryption"></a>Gennemsigtig databasekryptering

Power BI-rapportserver understøtter nu gennemsigtig databasekryptering for katalogdatabasen til Power BI-rapportserver for Enterprise- og Standard-udgaverne.

#### <a name="power-bi-visuals-api"></a>Visualiserings-API i Power BI

API-version 2.6.0 leveres med denne udgivelse.

#### <a name="microsoft-report-builder-update"></a>Opdatering til Microsoft Report Builder

Den netop udgivne version af Report Builder er fuldt kompatibel med versionerne 2016, 2017 og 2019 af Reporting Services. Den er også kompatibel med alle udgivne og understøttede versioner af Power BI-rapportserver.

## <a name="september-2019"></a>September 2019

Du kan finde flere oplysninger om de nye funktioner i blogindlægget [Power BI-rapportserver – september 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/).

Opdateringen af Power BI-rapportserver fra september 2019 er fyldt med Power BI-rapportfunktioner. Her er nogle af højdepunkterne:

- **Filtre til udsnit på visualiseringsniveau** Du kan føje et filter til udsnit på visualiseringsniveau. Det fungerer på samme måde som alle andre filtre på visualiseringsniveau, hvor det kun er selve udsnittet, der filtreres, og ingen andre visualiseringer. Dette filter er praktisk til at filtrere tomme felter fra, eller hvis du vil bruge målefiltre.
- **Ikonsæt for tabel og matrix** Med KPI-ikoner kan du angive regler for visning af forskellige ikonsæt i din tabel og matrix på samme måde som ikonsæt i Excel.
- **Gruppering af visualiseringer** Du kan nu gruppere visualiseringer, figurer, tekstfelter, billeder og knapper på en rapportside ligesom i PowerPoint. Når du grupperer objekter, kan du flytte og tilpasse størrelsen af dem samtidigt. Gruppering gør det nemmere at arbejde i en rapport med mange objekter, der ligger i lag på hver side.
- **Nye standardtemaer** Vi opdaterer de temaer, der er tilgængelige til rapporter og ændrer standardtemaet for nye rapporter, så det passer sammen med de nye JSON-temamuligheder. Det nye standardtema passer både bedre til Microsofts designsprog og følger bedste praksis for design af visualiseringer. 
- **Opdateret design af ruden** Vi har opdateret en stor del af grænsefladen. Vi har opdateret alle ruderne, sidefoden og visningsskifteren til en lysere farve, opdateret afstand og introduceret nye ikoner. Det nye design er det første skridt til at opdatere hele grænsefladen.

Her er den komplette liste over funktioner. 

### <a name="reporting"></a>Rapportering

- Opdateret design af ruden
- Filtre på visualiseringsniveau for udsnit
- Sortering i ruden til effektivitetsanalyse
- Værktøjstip til header for visualisering
- Tilpasning af mærkaten I alt for tabeller og matrixer
- Understøttelse af synkroniseringsudsnit for hierarkisk udsnit
- Ensartede skrifttypestørrelser på tværs af visualiseringer
- Ikonsæt til tabel og matrix
- Understøttelse af procent i forbindelse med betinget formatering efter regler
- Ny filtreringsrude er nu generelt tilgængelig
- Understøttelse af datafarver, når der bruges afspilningsakser i punktdiagrammer
- Forbedringer af ydeevnen, når der bruges relativ dato og rullemenu med udsnit
- Gruppering af visualiseringer
- Farve- og tekstklasser i temaer
- Nye standardtemaer

### <a name="analytics"></a>Analyse

- Brugerdefinerede formatstrenge
- Betinget formatering af opdateringer til formateringsindstillinger

    - Baggrunds- og titelfarver i visualiseringer
    - Kortfarver
    - Udfyldning og farver i måler
    - Alternativ tekst
    - Kantfarve

- Advarsler om betinget formatering
- Forbedring af identificerbarhed af detaljeadgang
- Nye DAX-udtryk: REMOVEFILTERS og CONVERT
- Ny sammenligningsoperator til DAX: ==

### <a name="data-preparation"></a>Dataforberedelse

- Forbedringer af M Intellisense
- Ny transformering: Opdel kolonne efter positioner
- Kopiér til udklipsholder fra dataprofilering


## <a name="may-2019"></a>Maj 2019

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop til Power BI-rapportserver

Du kan finde flere oplysninger om de nye funktioner i blogindlægget [Power BI-rapportserver – maj 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/).

Her er nogle af højdepunkterne i denne version:

#### <a name="performance-analyzer"></a>Effektivitetsanalyse 

Hvis din rapport kører langsommere end forventet, kan du prøve Effektivitetsanalyse i Power BI Desktop. Når du starter det, oprettes der en logfil med oplysninger om alle de handlinger, du foretager i rapporten. Læse mere om [Effektivitetsanalyse](../create-reports/desktop-performance-analyzer.md).

#### <a name="new-modeling-view"></a>Ny udformningsvisning

I den nye Udformningsvisning i Power BI Desktop kan du få vist og arbejde med komplekse datasæt, der indeholder mange tabeller. Højdepunkterne omfatter flere diagramlayout og masseredigering af kolonner, målinger og tabeller. Læs mere om [Udformningsvisning](../transform-model/desktop-modeling-view.md).

#### <a name="accessible-visual-interaction"></a>Tilgængelig interaktion med visualiseringer

Nu kan du få adgang til datapunkter i mange af de indbyggede visualiseringer ved hjælp af tastaturnavigation. Læs mere om [tilgængelighed i Power BI-rapporter](../create-reports/desktop-accessibility-overview.md).

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>Handlinger med titler og URL-adresser i forbindelse med betinget formatering

Power BI-rapporter er interaktive. Det giver mening, at titler i en rapport er dynamiske, så de afspejler rapportens aktuelle tilstand. Du kan bruge den samme udtryksbundne formatering til at gøre URL-adresserne til dine knapper, figurer og billeder dynamiske. Læs mere om [udtryksbaserede titler](../create-reports/desktop-conditional-format-visual-titles.md).

#### <a name="cross-highlight-by-axis-labels"></a>Krydsfremhævning af aksemærkater

Vælg kategorimærkaterne på aksen i en visualisering for at krydsfremhæve andre elementer på en side, ligesom du ville vælge datapunkter i en visualisering. Læs mere om [krydsfremhævning](../create-reports/power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

#### <a name="all-the-new-features"></a>Alle de nye funktioner

Her er en liste over alle de nye funktioner:

#### <a name="reporting"></a>Rapportering

- Krydsfremhævning af et enkelt punkt i kurvediagrammer 
- Tekstombrydning i titler 
- Opdatering af standardinteraktion i visualiseringer til krydsfiltrering ¬
- Afrundede hjørner for visuelle kanter 
- Udsnit til enkelt valg  
- Understøttelse af termisk kort til Bing Kort  
- Krydsfremhævning af aksemærkater  
- Formatering af standardværktøjstip  
- Understøttelse af statisk URL-adresse til knapper, figurer og billeder  
- Indstillinger for sidejustering   
- Forbedringer af valgrude  
- Tilgængelig interaktion med visualiseringer  
- Betinget formatering af titler i visualiseringer  
- Betinget formatering af handlinger for URL-adresser til knapper, figurer og billeder
- Ruden Effektivitetsanalyse
- Tastaturnavigation i tabel og matrix
- Styring af linjedatamærkatens position
- Styring af tekststørrelse for visuelle KPI-indikatorer

#### <a name="analytics"></a>Analyse

- Visning af datoer som et hierarki er nu generelt tilgængelig  

#### <a name="modeling"></a>Modellering

- Ny udformningsvisning er nu generelt tilgængelig
- Nye DAX-funktioner
- Opdatering til DAX-funktionen ALLSELECTED
- Deaktiver automatisk datering af tabeller i nye rapporter

### <a name="power-bi-report-server"></a>Power BI-rapportserver

#### <a name="support-for-trusted-visuals"></a>Understøttelse af visualiseringer, der er tillid til

Vi har tilføjet understøttelse af visualiseringer, der er tillid til, i Power BI-rapportserver. Vi understøtter i øjeblikket visualiseringerne Mapbox og PowerOn. ESRI, Visio og PowerApps understøttes ikke i denne version.

#### <a name="improved-security-features"></a>Forbedrede sikkerhedsfunktioner

**RestrictedResourceMimeTypeForUpload**, som administratorer kan bruge til at angive en kommasepareret liste over forbudte MIME-typer, f.eks. text/html.

## <a name="january-2019"></a>Januar 2019

Understøttelse af disse funktioner i Power BI-rapporter:

[**Sikkerhed på rækkeniveau**](row-level-security-report-server.md) Konfiguration af sikkerhed på rækkeniveau med Power BI-rapportserver kan begrænse adgang til datakilder for bestemte brugere. Filtre begrænser adgangen til data på rækkeniveau, og du kan definere filtre inden for roller.

[**Udvid og skjul i matrixrækkeoverskrifter**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) Vi har tilføjet muligheden for at udvide eller skjule enkelte rækkeoverskrifter, hvilket er en af de visuelle funktioner, der har været mest efterspurgt.

[**Kopiér og indsæt mellem .pbix-filer**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) Du kan kopiere visuelle elementer mellem .pbix-filer enten fra genvejsmenuen for det visuelle element eller med standardtastaturgenvejen Ctrl + C og indsætte dem i en anden rapport med Ctrl + V.

[**Smarte justeringshjælpelinjer**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) De smarte justeringshjælpelinjer vises, når du flytter objekter på rapportsiden, f.eks. som i PowerPoint, så du kan justere alt på siden. Du kan se de smarte hjælpelinjer, hver gang du trækker eller ændrer størrelsen på noget på siden. Når du flytter et objekt i nærheden af et andet, fastgøres det i en position, der er justeret i forhold til det andet objekt.

**Tilgængelighedsfunktioner** Der er for mange tilgængelighedsfunktioner til at vise dem allesammen: f.eks. [understøttelse af tilgængelighed til ruden med listen over felter](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). Ruden med listen over felter er fuldt tilgængelig. Du kan navigere rundt i ruden ved blot at bruge tastaturet og en skærmlæser, og du kan bruge genvejsmenuen til at føje felter til din rapportside.

#### <a name="power-bi-visuals"></a>Power BI-visualiseringer

- API-version 2.3.0 leveres med denne udgivelse.

### <a name="administrator-settings"></a>Administratorindstillinger

Administratorer kan angive følgende egenskaber for serverfarmen under Avancerede egenskaber i SSMS:

**AllowedResourceExtensionsForUpload** Et sæt udvidelser til ressourcer, der kan uploades til rapportserveren. Udvidelser til indbyggede filtyper som &ast;.rdl og &ast;.pbix behøver ikke at være inkluderet. Standarden er "&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx ". 

**SupportedHyperlinkSchemes** Angiver en kommasepareret liste over de URI-skemaer, der kan defineres i de linkhandlinger, der har tilladelse til at blive gengivet, eller "&ast;" for at aktivere alle linkskemaer. Indstillingen "http, https" ville f.eks. tillade links til "https://www. contoso.com", men ville fjerne link til "mailto:bill@contoso.com" eller "javascript:window.open(‘ www.contoso.com’, ‘_blank’)". Standarden er "&ast;".

## <a name="august-2018"></a>August 2018

I august 2018 kommer der mange nye funktioner i Power BI Desktop, som er optimeret til Power BI-rapportserver. Her er de nye funktioner efter område:

- [Rapportering](#reporting)
- [Analyse](#analytics)
- [Modellering](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Højdepunkter i august 2018-versionen

Blandt de mange nye funktioner er følgende funktioner særligt interessante. Du kan finde flere oplysninger i dette [blogindlæg](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/).

#### <a name="report-theming"></a>Rapporttemaer

I august 2018-versionen af Power BI-rapportserver har vi tilføjet rapporttemaer, så du hurtigt kan anvende farver i hele din rapport, så den matcher et tema eller virksomhedens branding. Når du importerer et tema, bliver alle dine diagrammer automatisk opdateret til at bruge temafarverne, og du har adgang til temafarverne i farvepaletten. Du kan uploade en temafil ved hjælp af indstillingen **Importér tema** under knappen **Skift tema**.

En temafil er en JSON-fil, der indeholder alle de farver, du vil bruge i din rapport, sammen med en standardformatering, du vil anvende på visualiseringer.
Her er et eksempel på et JSON-tema, der kun opdaterer standardfarverne i rapporten:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Betinget formatering af et andet felt

Muligheden for at formatere en kolonne efter et andet felt i modellen er en af de betydelige forbedringer af betinget formatering.

#### <a name="conditional-formatting-by-values"></a>Betinget formatering efter værdier

En anden ny type betinget formatering er **Formatér efter feltværdi**. Med Formatér efter feltværdi kan du bruge et mål eller en kolonne, der specificerer en farve, enten ved at angive en heksadecimal kode eller et navn for at anvende farven som baggrundsfarve eller skriftfarve.

#### <a name="report-page-tooltips"></a>Værktøjstip for rapportside

Funktionen med værktøjstip på rapportsiden er inkluderet i august 2018-opdateringen af Power BI-rapportserver. Med denne funktion kan du designe en rapportside, der skal bruges som et brugerdefineret værktøjstip til andre visualiseringer i din rapport.

#### <a name="log-axis-improvements"></a>Forbedringer af logaritmisk akse

Vi har forbedret den logaritmiske akse i dine kartesiske diagrammer væsentligt. Det er nu muligt at vælge en logaritmisk skala for den numeriske akse i et kartesisk diagram, herunder kombinationsdiagrammer, når du har data, som er udelukkende positive eller udelukkende negative.

#### <a name="sap-hana-sso-direct-query"></a>SAP HANA SSO Direct Query

SAP HANA SSO Direct Query understøttes nu med Kerberos for Power BI-rapporter.

>[!Note]
>Dette scenarie understøttes kun, når SAP HANA behandles som en relationel datakilde med rapporter, du har oprettet i Power BI Desktop.  Hvis du vil aktivere dette i Power BI Desktop, skal du gå til DirectQuery-menuen under Indstillinger, markere "Behandl SAP HANA som en relationel kilde" og klikke på OK.

#### <a name="power-bi-visuals"></a>Power BI-visualiseringer

- Med denne version leveres API version 1.13.0.

- Nu kan Power BI-visuals gå tilbage til en tidligere version, der er kompatibel med den aktuelle version af server-API'en (hvis tilgængelig).

### <a name="reporting"></a>Rapportering 

- [Rapporttemaer](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Knapper til at udløse handlinger](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Stregtyper i kombinationsdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Forbedret standardsortering af visualiseringer](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Numerisk udsnit](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Synkronisering af avancerede udsnit](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Forbedringer af logaritmisk akse](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Indstillinger for datamærkater for tragtformet diagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Angiv stregbredden til nul](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [Understøttelse af stor kontrast i rapporter](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Kontrolelementet kranseradius](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Kontrolelement med navne på placering af cirkel- og kransediagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Formatér datamærkater separat for hver måling i et kombinationsdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [Ny visuel overskrift med større fleksibilitet og flere formateringsmuligheder](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Formatering af baggrund](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Værktøjstip til tabel og matrix](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Slå værktøjstip for visualiseringer fra](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Tilgængelighed for udsnit](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [Forbedringer til fanen Formatering](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Understøttelse af trinvise linjer i kurve- og kombinationsdiagrammer](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [Bedre sorteringsfunktioner](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Udskriv rapporter via Eksportér til PDF (i Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Opret bogmærkegrupper](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Tilpasning af udsnit](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Værktøjstip for rapportside](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Analyse

- [Ny DAX-funktion: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Mål detaljeadgang](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Betinget formatering af et andet felt](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Betinget formatering efter værdier](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modellering

- [Filtrering og sortering i datavisning](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Forbedret formatering af landestandarder](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Datakategorier til målinger](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [Statistiske DAX-funktioner](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>Maj 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Konfigurer Power BI iOS-mobilapps eksternt for rapportservere

Som it-administrator kan du bruge din organisations MDM-værktøj til eksternt at konfigurere adgang til en rapportserver for Power BI iOS-mobilapps. Se [Konfigurer Power BI iOS-mobilapps eksternt for rapportservere](configure-powerbi-mobile-apps-remote.md) for at få flere oplysninger.

## <a name="march-2018"></a>Marts 2018

Den nye version af Power BI Desktop optimeret til Power BI-rapportserver fra marts 2018 indeholder en lang række nye funktioner. Her er de nye funktioner efter område:

- [Visualisering](#visuals-updates)
- [Rapportering](#reporting)
- [Analyse](#analytics)
- [Ydeevne](#performance)
- [Rapportserver](#report-server)
- [Andet](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Højdepunkter i marts 2018-versionen

Blandt de mange nye funktioner er følgende funktioner særligt interessante.

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[Regelbaseret betinget formatering til tabel og matrix](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Opret regler baseret på betingelser. Du kan f.eks. farvelægge baggrunden eller vælge skrifttypefarven for en kolonne baseret på tabellens eller matrixens specifikke forretningslogik.

#### <a name="show-and-hide-pages"></a>[Vis og skjul sider](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Du ønsker at give læserne adgang til din rapport, men nogle af siderne er ikke helt færdige. Nu kan du skjule dem, til de er færdige. Du kan også skjule sider i den normale navigation og give læsere adgang til en side ved hjælp af bogmærker eller detaljeadgang.

#### <a name="bookmarking"></a>[Bogmærker](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Opret bogmærker, som fortæller om dataene i din rapport.

- [Tværgående fremhævning til bogmærker](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): Bogmærker bevarer og viser rapportsidens tværgående fremhævninger på det tidspunkt, bogmærket blev oprettet.
- [Større fleksibilitet med bogmærker](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): Bogmærker afspejler de egenskaber, du angiver i din rapport, og påvirker udelukkende de visualiseringer, du vælger.

#### <a name="multi-select-data-points-across-multiple-charts"></a>[Markér flere datapunkter på tværs af diagrammer](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Markér flere datapunkter i flere diagrammer, og anvend krydsfiltrering på hele siden.

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[Synkroniser udsnitsværktøjer på tværs af flere sider i en rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Et udsnitsværktøj kan anvendes på én, to eller flere sider i en rapport.

#### <a name="quick-measures"></a>[Hurtigmålinger](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Opret nye målinger baseret på eksisterende målinger og numeriske kolonner i en tabel.

#### <a name="drilling-down-filters-other-visuals"></a>[Detaljeudledning filtrerer andre visualiseringer](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Når du foretager detaljeudledning i en bestemt kategori i en visualisering, kan du vælge at filtrere alle visualiseringerne på siden efter den pågældende kategori.

### <a name="visuals-updates"></a>Opdateringer til visualiseringer

- [Cellejustering for tabel og matrix](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Vis enheder og præcisionskontrolelementer for kolonnerne Tabel og Matrix](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Overløb af datamærkater i søjlediagrammer i visualiseringer](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Styr baggrundsfarve for datamærkat i kartesiske elementer og visualiseringer med kort](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Kontrolelement til udfyldning af værktøjslinje/kolonne](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Forøge område, der bruges til akseetiketter i diagrammer](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Punktvisualiseringer på baggrund af x- og y-aksegrupperinger](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Stikprøvetagning med høj tæthed for kort, baseret på breddegrad og længdegrad](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Dynamiske udsnitsværktøjer](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Føj en ankerdato til et relativt datoudsnit](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Rapportering

- [Slå overskriften i visualiseringer fra i Læsetilstand for en rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Rapportindstillinger til langsomme datakilder](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Forbedret standardplacering af visualiseringer](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Kontrollér arrangering af visualiseringer i valgruden](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Lås objekter i din rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Søgning i ruderne Formatering og Analyse](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Ruden Feltegenskaber og feltbeskrivelser](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Analyse

- [UTCNOW() og UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Markér brugerdefineret datotabel](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Detaljeudledning filtrerer andre visualiseringer](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Formatering på celleniveau for flerdimensionelle AS-modeller til kort med flere rækker](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Ydeevne

- [Forbedring af ydeevnen ved filtrering](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Forbedring af ydeevnen for DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Forbedring af ydeevnen ved åbn og gem](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Forbedring af "Vis elementer uden data"](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>Rapportserver

#### <a name="export-to-accessible-pdf"></a>Eksport til tilgængelig PDF

Når du eksporterer en sideinddelt rapport (RDL) til PDF, kan du nu eksportere til en tilgængelig/tagget PDF-fil. Filen fylder mere, men skærmlæsere og andre hjælpemidler har nemmere ved at læse og navigere i den. Tilgængelig PDF aktiveres ved at angive indstillingen **AccessiblePDF** under enhedsoplysninger til **Sand**. Se [PDF-indstillinger for enhedsoplysninger](/sql/reporting-services/pdf-device-information-settings) og [Ændring af indstillinger for enhedsoplysninger](/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).

### <a name="other-improvements"></a>Andre forbedringer

- [Forbedret Tilføj kolonne fra eksempler](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Hurtiglink til rådgivningstjenester](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Forbedret fejlrapportering](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Visning af tidligere fejl, du har oplevet](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>Oktober 2017

### <a name="power-bi-report-data-sources"></a>Power BI-rapportdatakilder

Power BI-rapporter i Power BI-rapportserver kan oprette forbindelse til en række forskellige datakilder. Du kan importere data og planlægge dataopdateringer, eller du kan forespørge på dem direkte ved hjælp af DirectQuery eller en liveforbindelse til SQL Server Analysis Services. Se listen over datakilder, der understøtter planlagt opdatering, og dem, der understøtter DirectQuery, i "Power BI-rapportdatakilder i Power BI-rapportserver".

### <a name="scheduled-data-refresh-for-imported-data"></a>Planlagt dataopdatering for importerede data

I Power BI-rapportserver kan du konfigurere planlagt opdatering af data for at sikre, at dataene er opdateret i Power BI-rapporter ved hjælp af en integreret model i stedet for en liveforbindelse eller DirectQuery. Med en integreret model importerer du dataene, så forbindelsen til den oprindelige datakilde afbrydes. Den skal opdateres for at holde dataene friske, og planlagt opdatering er måden at gøre det på. Læs mere om planlagt opdatering til Power BI-rapporter i Power BI-rapportserver.

### <a name="editing-power-bi-reports-from-the-server"></a>Redigering af Power BI-rapporter fra serveren

Du kan åbne og redigere Power BI-rapportfiler (.pbix) fra serveren, men du får den oprindelige fil tilbage, du har uploadet. **Hvis dataene er blevet opdateret af serveren, opdateres dataene ikke, første gang du åbner filen**. Du skal opdatere manuelt lokalt for at se ændringen.

### <a name="large-file-uploaddownload"></a>Upload/download af store filer

Du kan uploade filer på op til 2 GB, men som standard er denne grænse indstillet til 1 GB i indstillingerne for rapportserver i SQL Server Management Studio (SSMS).  Disse filer gemmes, som de er, i databasen til SharePoint, og der kræves ingen særlig konfiguration for SQL Server-kataloget.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Få adgang til delte datasæt såsom OData-feeds

Du kan få adgang til delte datasæt fra Power BI Desktop med et OData-feed. Du kan få mere at vide i [Få adgang til delte datasæt såsom OData-feeds på Power BI-rapportserver](access-dataset-odata.md).

### <a name="scale-out"></a>Scale-out

Denne udgave understøtter scale-out. Brug en belastningsjustering, og angiv servertilknytning for at få den bedste oplevelse. Scenariet er endnu ikke optimeret til scale-out, så du får vist modeller, som kan være replikeret på tværs af flere noder. Scenariet fungerer uden Network Load Balancer og sticky sessions. Du vil dog ikke kun se et overforbrug af hukommelse på tværs af noder, fordi modellen indlæses N gange, men ydeevnen sænkes mellem forbindelserne, da modellen streames, når den rammer en ny node mellem anmodningerne.  

### <a name="administrator-settings"></a>Administratorindstillinger

Administratorer kan angive følgende egenskaber for serverfarmen under Avancerede egenskaber i SSMS:

- EnableCustomVisuals: Sand/falsk
- EnablePowerBIReportEmbeddedModels: Sand/falsk
- EnablePowerBIReportExportData: Sand/falsk
- MaxFileSizeMb: Standarden er nu 1000
- ModelCleanupCycleMinutes: Hvor ofte der kontrolleres for at fjerne modeller fra hukommelsen
- ModelExpirationMinutes: Hvor lang tid, før en model er udløbet og fjernes, baseret på sidste gang den blev brugt
- ScheduleRefreshTimeoutMinutes: Hvor længe dataopdateringen kan vare for en tilstand. Standarden er to timer.  Der er ingen fastsat øvre grænse.

**Konfigurationsfil rsreportserver.config**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>Udvikler-API

Udvikler-API'en (REST-API), der blev introduceret i SSRS 2017, er blevet udvidet til Power BI-rapportserver for at fungere sammen med både Excel-filer og .pbix-filer. En potentiel use case er programmeringsmæssigt at downloade filer fra serveren, opdatere dem og publicere dem igen. Dette er eksempelvis den eneste måde, hvorpå du kan opdatere Excel-projektmapper med PowerPivot-modeller.

Der er en ny separat API til store filer, som vil blive opdateret i Power BI-rapportserverversionen af Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>Hukommelsesfodaftryk for SQL Server Analysis Services (SSAS) og Power BI-rapportserver

Power BI-rapportserver hoster nu SQL Server Analysis Services (SSAS) internt. Dette er ikke specifikt for planlagt opdatering. At hoste SSAS kan markant udvide hukommelsesfodaftrykket for rapportserveren. AS.ini-konfigurationsfilen findes på servernoderne, så hvis du kender SSAS, kan du opdatere indstillingerne, herunder største hukommelsesgrænse og cachelagring på disk osv. Se [Serveregenskaber i Analysis Services](/sql/analysis-services/server-properties/server-properties-in-analysis-services), for at få mere at vide.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Få vist og interager med Excel-projektmapper

Excel og Power BI indeholder en portefølje af værktøjer, som er de eneste af deres slags i branchen. Tilsammen giver de forretningsanalytikere mulighed for nemmere at indsamle, forme, analysere og udforske deres data visuelt. Foruden at få vist Power BI-rapporter i webportalen kan virksomhedsbrugerne nu gøre det samme med Excel-projektmapper i Power BI-rapportserver, hvilket giver dem én samlet placering til at publicere og få vist deres Microsoft BI-indhold til selvbetjening.

Vi har udgivet en [gennemgang af, hvordan du tilføjer Office Online Server (OOS) i miljøet i din prøveversion af Power BI-rapportserver](excel-oos.md). Kunder, der har en volumenlicenskonto, kan downloade OOS fra Volume License Service Center uden omkostninger og få skrivebeskyttet funktionalitet. Efter konfigurationen kan brugerne få vist og interagere med Excel-projektmapper, der:

- ikke har nogen afhængigheder af eksterne data
- har en direkte forbindelse til en ekstern SQL Server Analysis Services-datakilde
- har en PowerPivot-datamodel.

### <a name="support-for-new-table-and-matrix-visuals"></a>Understøttelse af nye tabel- og matrixvisuals

Power BI-rapportserver understøtter nu de nye Power BI-tabel- og matrixvisuals. Hvis du vil oprette rapporter med disse visuals, skal du bruge en opdateret version af Power BI Desktop-udgave til versionen fra oktober 2017. Den kan ikke installeres side om side med versionen af Power BI Desktop fra juni 2017. Hvis du vil have den seneste version af Power BI Desktop, skal du vælge **Avancerede indstillinger for hentning af filer** på [siden til download af Power BI-rapportserver](https://powerbi.microsoft.com/report-server/).

## <a name="june-2017"></a>Juni 2017

- Power BI-rapportserver er blevet gjort offentligt tilgængeligt (GA).

## <a name="may-2017"></a>Maj 2017

- Prøveversion af Power BI-rapportserver gjort tilgængelig
- Mulighed for at publicere Power BI-rapporter i det lokale miljø
  - understøttelse af Power BI-visuals
  - Kun understøttelse af **Analysis Services-liveforbindelser*, men med flere datakilder på vej.
  - Appen Power BI - Mobil er blevet opdateret til at vise Power BI-rapporter, der hostes i Power BI-rapportserver
- Forbedret samarbejde i rapporter med kommentarer

## <a name="next-steps"></a>Næste trin

Kontrollér disse kilder for at holde dig ajour med nye funktioner i Power BI-rapportserver.

- [Microsoft Power BI-blog](https://powerbi.microsoft.com/blog/)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
