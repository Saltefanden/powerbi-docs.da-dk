---
title: Opdatering af data i Power BI
description: I denne artikel beskrives funktionerne til opdatering af data i Power BI og deres afhængigheder på et konceptuelt niveau.
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 06/16/2020
LocalizationGroup: Data refresh
ms.openlocfilehash: 212aa0648a2677536912c15a17ba6916bb871313
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404496"
---
# <a name="data-refresh-in-power-bi"></a>Opdatering af data i Power BI

Power BI gør det muligt for dig at konvertere data til indsigt til handling hurtigt, men du skal sørge for, at Power BI-rapporterne og -dashboardene er opdateret med de nyeste data. Det er ofte kritisk at vide, hvordan man opdaterer dataene, for at kunne levere nøjagtige resultater.

I denne artikel beskrives funktionerne til opdatering af data i Power BI og deres afhængigheder på et konceptuelt niveau. Den indeholder også bedste praksis og tip til at undgå almindelige problemer med opdateringer. Indholdet danner et fundament, som hjælper dig med at forstå, hvordan opdatering af data fungerer. Du kan finde målrettede trinvise instruktioner til at konfigurere opdatering af data i de selvstudier og Sådan gør du-vejledninger, der er angivet under afsnittet Næste trin i slutningen af denne artikel.

## <a name="understanding-data-refresh"></a>Forstå opdatering af data

Når du opdaterer data, skal Power BI sende en forespørgsel til de underliggende datakilder, muligvis indlæse kildedataene i et datasæt og derefter opdatere alle visualiseringer i dine rapporter eller på dine dashboards, der er afhænger af det opdaterede datasæt. Hele processen består af flere faser afhængigt af lagertilstandene for dine datasæt, som forklaret i efterfølgende afsnit.

Du skal være opmærksom på følgende begreber for at forstå, hvordan Power BI opdaterer dine datasæt, rapporter og dashboards:

- **Lagertilstande og typer af datasæt**: De lagertilstande og typer af datasæt, som Power BI understøtter har forskellige opdateringskrav. Du kan vælge mellem at importerer data i Power BI igen for at se eventuelle ændringer eller sende forespørgsler til dataene direkte ved kilden.
- **Power BI-opdateringstyper**: Hvis du kender de forskellige opdateringstyper, kan det hjælpe dig med at forstå, hvor Power BI bruger tiden under en opdateringshandling, uanset hvad detaljerne for datasættet er. Og når du kombinerer disse oplysninger med detaljerne for lagertilstanden, hjælper det dig med at forstå, hvad det er Power BI præcist gør, når du vælger **Opdater nu** for et datasæt.

### <a name="storage-modes-and-dataset-types"></a>Lagertilstande og typer af datasæt

Et Power BI-datasæt kan køre i en af følgende tilstande for at få adgang til data fra en lang række datakilder. Du kan finde flere oplysninger i [Lagringstilstand i Power BI Desktop](../transform-model/desktop-storage-mode.md).

- Importtilstand
- DirectQuery-tilstand
- LiveConnect-tilstand
- Pushtilstand

I følgende diagram vises de forskellige dataflow baseret på lagertilstand. Det vigtigste er, at det kun er Importtilstand for datasæt, der kræver en opdatering af kildedata. De skal opdateres, fordi det kun er denne type datasæt, der importerer data fra dets datakilder, og de importerede data opdateres muligvis enten regelmæssigt elle ad hoc. DirectQuery-datasæt og datasæt i LiveConnect-tilstand til Analysis Services importerer ikke data; de sender forespørgsler til de underliggende datakilder ved hver brugerinteraktion. Datasæt i pushtilstand tilgår ingen datakilder direkte, men forventer, at du sender dataene til Power BI via push. Kravene til opdatering af datasæt varierer afhængigt af typen af lagertilstand/datasæt.

![Lagertilstande og typer af datasæt](media/refresh-data/storage-modes-dataset-types-diagram.png)

#### <a name="datasets-in-import-mode"></a>Datasæt i Importtilstand

Power BI importerer dataene fra de oprindelige datakilder til datasættet. Forespørgsler til Power BI-rapporter og -dashboards, der sendes til datasættet, returnerer resultater fra de importerede tabeller og kolonner. Du kan anse sådan et datasæt for at være en tidsspecifik kopi. Da Power BI kopierer dataene, skal du opdatere datasættet for at hente ændringer fra de underliggende datakilder.

Da Power BI cachelagrer dataene, kan datasæt i Importtilstand have en betydelig størrelse. I følgende tabel kan du se den maksimale størrelse af datasæt pr. kapacitet. Hold dig godt under den maksimale størrelse for datasæt for at undgå opdateringsproblemer, som kan opstå, hvis dine datasæt kræver mere end de maksimale tilgængelige ressourcer under en opdateringshandling.

| Kapacitetstype | Maksimal størrelse af datasæt |
| --- | --- |
| Delte, A1, A2 eller A3 | 1 GB |
| A4 eller P1 | 3 GB |
| A5 eller P2 | 6 GB |
| A6 eller P3 | 10 GB |
| | |

#### <a name="datasets-in-directqueryliveconnect-mode"></a>Datasæt i DirectQuery-/LiveConnect-tilstand

Power BI importerer ikke data via forbindelser, der kører i DirectQuery-/LiveConnect-tilstand. I stedet returnerer datasættet resultaterne fra den underliggende datakilde, når en rapport eller et dashboard sender forespørgsler til datasættet. Power BI transformerer og videresender forespørgslerne til datakilden.

Selvom DirectQuery- og LiveConnect-tilstand er ens i forhold til den måde, som Power BI videresender forespørgsler til kilden på, er det vigtigt at bemærke, at Power BI ikke behøver at transformere forespørgsler i LiveConnect-tilstand. Forespørgslerne føres direkte til den forekomst af Analysis Services, der hoster databasen, uden at forbruge ressourcer på den delte kapacitet eller en Premium-kapacitet.

Da Power BI ikke importerer dataene, behøver du ikke at køre en opdatering af data. Power BI udfører dog stadig opdateringer af felter og muligvis opdateringer af rapporten, som det forklares i næste afsnit om opdateringstyper. Et felt er en visualisering i en rapport, som er fastgjort til et dashboard, og opdateringer af felter i dashboards forekommer hver time, så de nyeste resultater vises i felterne. Du kan ændre tidsplanen under indstillingerne for datasæt, som vist på skærmbilledet nedenfor, eller gennemtvinge en opdatering af dashboardet manuelt ved hjælp af indstillingen **Opdater nu**.

![Tidsplan for opdatering](media/refresh-data/refresh-schedule.png)

> [!NOTE]
> Afsnittet **Planlagt opdatering af cache** under fanen **Datasæt** er ikke tilgængelig for datasæt i importtilstand. Disse datasæt kræver ikke en opdatering af separate felter, fordi Power BI opdaterer felterne automatisk under hver planlagt opdatering eller opdatering on-demand af dataene.

#### <a name="push-datasets"></a>Push-datasæt

Pushdatasæt indeholder ikke en formel datakildedefinition, så de kræver ikke, at du udfører en opdatering af data i Power BI. Du kan opdatere dem ved at sende dine data til datasættet via push ved hjælp af en ekstern tjeneste eller en proces, f.eks. Azure Stream Analytics. Dette er en fælles tilgang til analyse i realtid med Power BI. Power BI udfører stadig opdateringer af cachen for alle felter, der bruges oven på et pushdatasæt. Du kan finde en detaljeret gennemgang i [Selvstudium: Stream Analytics og Power BI: Et analysedashboard i realtid til streaming af data](/azure/stream-analytics/stream-analytics-power-bi-dashboard).

> [!NOTE]
> Der er adskillige begrænsninger for Pushtilstand, som dokumenteret i [REST API-begrænsninger i Power BI](../developer/automation/api-rest-api-limitations.md).

### <a name="power-bi-refresh-types"></a>Power BI-opdateringstyper

En handling til opdatering af Power BI kan bestå af flere opdateringstyper, herunder opdatering af data, opdatering af OneDrive, opdatering af forespørgselscacher, opdatering af felter og opdatering af visualiseringer i rapporter. Mens Power BI bestemmer de påkrævede opdateringstrin for et givet datasæt automatisk, skal du vide, hvordan de bidrager til kompleksiteten og varigheden af en opdateringshandling. Du kan se et overblik i følgende tabel.

| Lagertilstand | Opdatering af data | Opdatering af OneDrive | Forespørgselscacher | Opdatering af felter | Visualiseringer i rapporter |
| --- | --- | --- | --- | --- | --- |
| Importér | Planlagt og on-demand | Ja, for forbundne datasæt | Hvis aktiveret for en Premium-kapacitet | Automatisk og on-demand | Nej |
| DirectQuery | Ikke tilgængelig | Ja, for forbundne datasæt | Hvis aktiveret for en Premium-kapacitet | Automatisk og on-demand | Nej |
| LiveConnect | Ikke tilgængelig | Ja, for forbundne datasæt | Hvis aktiveret for en Premium-kapacitet | Automatisk og on-demand | Ja |
| Push | Ikke tilgængelig | Ikke tilgængelig | Ikke praktisk | Automatisk og on-demand | Nej |
| | | | | | |

#### <a name="data-refresh"></a>Opdatering af data

For Power BI-brugere betyder opdatering af data typisk import af data fra de oprindelige datakilder til et datasæt enten på baggrund af en tidsplan for opdatering eller en opdatering on-demand. Du kan udføre flere opdateringer af datasæt dagligt, hvilket kan være nødvendigt, hvis den underliggende kildedata ændres ofte. Power BI begrænser datasæt på en delt kapacitet til otte daglige opdateringer. Hvis datasættet befinder sig på en Premium-kapacitet, kan du planlægge op til 48 opdateringer pr. dag under indstillingerne for datasættet. Du kan finde flere oplysninger under [Konfigurer planlagt opdatering](#configure-scheduled-refresh) senere i denne artikel. Datasæt på en Premium-kapacitet med [XMLA-slutpunktet](../admin/service-premium-connect-tools.md), der er aktiveret til læsning/skrivning, understøtter ubegrænsede opdateringshandlinger, når de konfigureres programmeringsmæssigt med TMSL eller PowerShell.

Det er også vigtigt at fremhæve, at begrænsningen for delt kapacitet for daglige opdateringer gælder for både planlagte opdateringer og API-opdateringer. Du kan også udløse en opdatering on-demand ved at vælge **Opdater nu** i menuen for datasættet, som vist på følgende skærmbillede. Opdateringer on-demand er ikke inkluderet i begrænsningen for opdateringer. Bemærk også, at datasæt på en Premium-kapacitet ikke pålægger begrænsninger for API-opdateringer. Hvis du er interesseret i at skabe din egen opdateringsløsning ved hjælp af REST API til Power BI, skal du se [Datasæt – Opdater datasæt](/rest/api/power-bi/datasets/refreshdataset).

![Opdater nu](media/refresh-data/refresh-now.png)

> [!NOTE]
> Opdateringer af data skal fuldføres på mindre end 2 timer for en delt kapacitet. Hvis dit datasæt kræver længerevarende opdateringshandlinger, kan du overveje at flytte datasættet til en Premium-kapacitet. For Premium er den maksimale opdateringsvarighed 5 timer.

#### <a name="onedrive-refresh"></a>Opdatering af OneDrive

Hvis du har oprettet dit datasæt og dine rapporter på baggrund af en Power BI Desktop-fil, en Excel-projektmappe eller en fil med kommaseparerede værdier (.csv) på OneDrive eller SharePoint Online, udfører Power BI en anden type opdatering, der er kendt som opdatering af OneDrive. Du kan finde flere oplysninger under [Hent data fra filer til Power BI](service-get-data-from-files.md).

I modsætning til en opdatering af datasæt, hvor Power BI importerer data fra en datakilde til et datasæt, synkroniseres datasæt og rapporter med deres kildefiler under en opdatering af OneDrive. Power BI kontrollerer som standard ca. hver time, om et datasæt, der er forbundet til en fil på OneDrive eller SharePoint Online, kræver synkronisering.

Power BI udfører en opdatering på baggrund af et element-id i OneDrive, så du skal overveje opdateringer i forhold til udskiftning grundigt. Når du angiver en OneDrive-fil som datakilde, refererer Power BI til filens element-id, når der opdateres. Overvej følgende scenarie: Du har en masterfil _A_ og en arbejdskopi af filen _B_, og du konfigurerer OneDrive-opdatering for fil B. Hvis du derefter _overskriver_ fil B med fil A, sletter overskrivningen den gamle fil B og opretter en ny fil B med et andet element-id, hvilket betyder, at OneDrive-opdateringen mislykkes. Hvis du vil undgå denne situation, kan du i stedet overføre og erstatte fil B, der bevarer samme element-id.

Du kan flytte filen til en anden placering (f.eks. ved hjælp af træk og slip), og opdateringen vil fortsat fungere, da Power BI stadig kender fil-id'et. Hvis du kopierer filen til en anden placering, oprettes der dog en ny forekomst af filen og et nyt fil-id. Derfor er din Power BI-filreference ikke længere gyldig, og opdateringen vil mislykkes.

> [!NOTE]
> Det kan tage Power BI op til 60 minutter at opdatere et datasæt, selvom synkroniseringen er fuldført på din lokale computer, og efter du har brugt *Opdater nu* i Power BI-tjenesten.

Hvis du vil se tidligere synkroniseringscyklusser, skal du kigge på OneDrive-fanen i opdateringshistorikken. På følgende skærmbillede kan du se en fuldført synkroniseringscyklus for et prøvedatasæt.

![Opdater historik](media/refresh-data/refresh-history.png)

Som skærmbilledet oven for viser har Power BI identificeret denne opdatering af OneDrive som en **Planlagt** opdatering, men det er ikke muligt at konfigurere opdateringsintervallet. Du kan kun deaktivere opdatering af OneDrive under indstillingerne for datasættet. Deaktivering af en opdatering er nyttigt, hvis du ikke ønsker, at dine datasæt og rapporter i Power BI opfanger eventuelle ændringer fra kildefilerne automatisk.

Bemærk, at afsnittene **Legitimationsoplysninger til OneDrive** og **Opdatering af OneDrive** kun vises på siden med indstillingerne for datasæt, hvis datasættet er forbundet til en fil i OneDrive eller SharePoint Online, som vist på følgende skærmbillede. Disse afsnit vises ikke for datasæt, der ikke er forbundet til kildefiler i OneDrive eller SharePoint Online.

![Legitimationsoplysninger til OneDrive og opdatering af OneDrive](media/refresh-data/onedrive-credentials-refresh.png)

Hvis du deaktiverer opdatering af OneDrive for et datasæt, kan du stadig synkronisere dine datasæt on-demand ved at vælge **Opdater nu** i menuen for datasættet. Som en del af opdateringen on-demand kontrollerer Power BI, om kildefilen på OneDrive eller SharePoint Online er nyere end datasættet i Power BI, og synkroniserer datasættet, hvis det er tilfældet. Disse aktiviteter vises i **opdateringshistorikken** som opdateringer on-demand på fanen **OneDrive**.

Husk, at der ikke hentes data fra de oprindelige datakilder ved en opdatering af OneDrive. I forbindelse med opdatering af OneDrive opdateres ressourcerne i Power BI blot med metadataene og dataene fra .pbix-, .xlsx- eller .csv-filen, som vist i følgende diagram. Power BI udløser desuden en opdatering af data som en del af opdateringen on-demand for at sikre, at datasættet indeholder de nyeste data fra datakilderne. Du kan bekræfte dette ved at se **opdateringshistorikken**, hvis du skifter til fanen **Planlagt**.

![Diagram over opdatering af OneDrive](media/refresh-data/onedrive-refresh-diagram.png)

Hvis du bevarer opdatering af OneDrive aktiveret for et datasæt, der er forbundet med OneDrive eller SharePoint Online, og du vil udføre en opdatering af data efter en plan, skal du sørge for at konfigurere tidsplanen, så Power BI udfører opdateringen af dataene efter opdateringen af OneDrive. Hvis du f.eks. har oprettet din egen tjeneste eller proces for at opdatere kildefilen i OneDrive eller SharePoint Online hver nat kl. 1, kan du konfigurere en planlagt opdatering til kl. 2.30 for at give Power BI nok tid til at fuldføre opdateringen af OneDrive, før opdateringen af data startes.

#### <a name="refresh-of-query-caches"></a>Opdatering af forespørgselscacher

Hvis dit datasæt befinder sig på en Premium-kapacitet, kan du muligvis forbedre ydeevnen af alle tilknyttede rapporter og dashboards ved at aktivere cachelagring af forespørgsel, som vist på følgende skærmbillede. Ved cachelagring af forespørgsler beordres Premium-kapaciteten til at bruge dens lokale cachelagringstjeneste til at bevare forespørgselsresultaterne, derved undgår man, at den underliggende datakilde skal beregne disse resultater. Du kan finde flere oplysninger i [Cachelagring af forespørgsel i Power BI Premium](power-bi-query-caching.md).

![Cachelagring af forespørgsel](media/refresh-data/query-caching.png)

Efter en opdatering af data er tidligere cachelagrede forespørgselsresultater dog ikke længere gyldige. Power BI kasserer disse cachelagrede resultater og skal genopbygge dem. Derfor er cachelagring af forespørgsel muligvis ikke så nyttig i forbindelse med rapporter og dashboards, der er knyttet til datasæt, som du opdaterer meget ofte, f.eks. 48 gange om dagen.

#### <a name="tile-refresh"></a>Opdatering af felter

Power BI bevarer en cache for hver feltvisualisering på dine dashboards og opdaterer proaktivt feltcacherne, når data ændres. Med andre ord forekommer opdatering af felter automatisk efter en opdatering af data. Dette er tilfældet for både planlagte opdateringer og opdateringer on-demand. Du kan desuden gennemtvinge en opdatering af felter ved at vælge **Flere indstillinger** (...) i øverste højre hjørne af et dashboard og derefter vælge **Opdater dashboardfelter**.

![Opdater dashboardfelter](media/refresh-data/refresh-dashboard-tiles.png)

Da det forekommer automatisk, kan du anses opdatering af felt for at være en indbygget del af opdatering af data. Du vil måske bl.a. bemærke, at varigheden af opdateringen øges i forhold til antallet af felter. Spildet i forbindelse med opdatering af feltet kan være markant.

Power BI bevarer som standard en enkelt cache for hvert felt, men hvis du bruger dynamisk sikkerhed til at begrænse adgang til data baseret på brugerroller, som beskrevet i artiklen [Sikkerhed på rækkeniveau med Power BI](../admin/service-admin-rls.md), så skal Power BI opretholde en cache for hver rolle og hvert felt. Antallet af feltcacher ganges med antallet af roller.

Situationen kan blive endnu mere involveret, hvis dit datasæt bruger en dynamisk forbindelse til en Analysis Services-datamodel med sikkerhed på rækkeniveau, som fremhævet i selvstudiet [Dynamisk sikkerhed på rækkeniveau med Analysis Services-tabelmodel](desktop-tutorial-row-level-security-onprem-ssas-tabular.md). I denne situation skal Power BI bevare og opdatere en cache for hvert felt og hver bruger, der nogensinde har fået vist dashboardet. Det er ikke ualmindeligt, at den del af opdateringen af data, der vedrører opdatering af feltet, langt overskrider den tid, det tager at hente dataene fra kilden. Du kan finde flere oplysninger om opdatering af felter i [Fejlfinding af feltfejl](refresh-troubleshooting-tile-errors.md).

#### <a name="refresh-of-report-visuals"></a>Opdatering af visualiseringer i rapporter

Denne opdateringsproces er mindre vigtig, da den kun er relevant for dynamiske forbindelser til Analysis Services. For disse forbindelser cachelagrer Power BI den sidste tilstand for visualiseringerne i rapporten, så Power BI ikke behøver at sende en forespørgsel til Analysis Services-tabelmodellen igen, når du får vist rapporten igen. Når du interagerer med rapporten, f.eks. ved at ændre et rapportfilter, sender Power BI en forespørgsel til tabelmodellen og opdaterer visualiseringerne i rapporten automatisk. Hvis du har mistanke om, at der vises forældede data i en rapport, kan du også vælge knappen Opdater i rapporten for at udløse en opdatering af alle visualiseringer i rapporten, som vist på følgende skærmbillede.

![Opdater visualiseringer i rapporter](media/refresh-data/refresh-report-visuals.png)

## <a name="review-data-infrastructure-dependencies"></a>Gennemse afhængigheder af infrastrukturen for data

Uanset hvad lagertilstanden er, kan ingen opdatering af data fuldføres, medmindre de underliggende datakilder er tilgængelige. Der er tre primære scenarier for adgang til data:

- Et datasæt bruger datakilder, der er placeret i det lokale miljø
- Et datasæt bruger datakilder i cloudmiljøet
- Et datasæt bruger data fra kilde både i det lokale miljø og i cloudmiljøet

### <a name="connecting-to-on-premises-data-sources"></a>Oprettelse af forbindelse til data i det lokale miljø

Hvis dit datasæt bruger en datakilde, som Power BI ikke kan få adgang til via en direkte netværksforbindelse, skal du konfigurere en gatewayforbindelse for dette datasæt, før du kan aktivere en tidsplan for opdatering eller udføre en opdatering af data on-demand. Du kan finde flere oplysninger om datagateways, og hvordan de fungerer, i [Hvad er datagateways i det lokale miljø?](service-gateway-onprem.md)

Du har følgende muligheder:

- Vælg en datagateway til virksomheder med den påkrævede datakildedefinition
- Udrul en personlig datagateway

> [!NOTE]
> Du kan finde en liste over typer af datakilder, der kræver en datagateway, i artiklen [Administrer din datakilde – Import/Planlagt opdatering](service-gateway-enterprise-manage-scheduled-refresh.md).

#### <a name="using-an-enterprise-data-gateway"></a>Brug af en datagateway til virksomheder

Microsoft anbefaler at bruge en datagateway til virksomheder frem for en personlig gateway til at oprette forbindelse mellem et datasæt og en datakilde i det lokale miljø. Sørg for, at gatewayen er konfigureret korrekt, hvilket betyder, at gatewayen skal have de nyeste opdateringer og alle nødvendige datakildedefinitioner. En datakildedefinition giver Power BI forbindelsesoplysningerne for en bestemt kilde, herunder forbindelsesslutpunkter, godkendelsestilstand og legitimationsoplysninger. Du kan finde flere oplysninger om administration af datakilder via en gateway i [Administrer din datakilde – Import/Planlagt opdatering](service-gateway-enterprise-manage-scheduled-refresh.md).

Det er forholdsvist ligetil at oprette forbindelse mellem et datasæt og en gateway til virksomheder, hvis du er gatewayadministrator. Med administratorrettigheder kan du straks opdatere gatewayen og tilføje manglende datakilder, hvis det er nødvendigt. Du kan faktisk føje en manglende datakilde til din gateway direkte fra siden med indstillinger for datasæt. Udvid til/fra-knappen for at få vist datakilderne, og vælg linket **Føj til gateway**, som vist på følgende skærmbillede. Hvis du ikke er gatewayadministrator, skal du i stedet kontakte en gatewayadministrator for at tilføje den påkrævede definition af datakilden.

> [!NOTE]
> Det er kun gatewayadministratorer, der kan føje datakilder til en gateway. Sørg også for, at din gatewayadministration føjer din brugerkonto til listen over brugere, der har tilladelse til at bruge datakilden. På siden med indstillinger for datasæt kan du kun vælge en virksomhedsgateway med en tilsvarende datakilde, som du har tilladelse til at bruge.

![Føj til gateway](media/refresh-data/add-to-gateway.png)

Sørg for at knytte den korrekte datakildedefinition til datakilden. Som ovenstående skærmbillede illustrerer, kan gatewayadministratorer oprette flere definitioner, der hver især har forskellige legitimationsoplysninger, i en enkelt gateway, som opretter forbindelse til den samme datakilde. I det viste eksempel ville en datasætejer i salgsafdelingen vælge datakildedefinitionen AdventureWorksProducts-Sales, mens en datasætejer i supportafdelingen ville knytte datasættet til datakildedefinitionen AdventureWorksProducts-Support. Hvis navnene på datakildedefinitionerne ikke er intuitive, kan du kontakte gatewayadministratoren for at få afklaret, hvilken definition du skal vælge.

> [!NOTE]
> Et datasæt kan kun bruge en enkelt gatewayforbindelse. Det er med andre ord ikke muligt at få adgang til datakilder i det lokale miljø på tværs af flere gatewayforbindelser. Derfor skal du føje alle påkrævede datakildedefinitioner til den samme gateway.

#### <a name="deploying-a-personal-data-gateway"></a>Udrulning af en personlig datagateway

Hvis du har ikke adgang til en datagateway til virksomheder, og du er den eneste person, der administrerer datasæt, så du behøver ikke at dele datakilder med andre, kan du udrulle en datagateway i personlig tilstand. I afsnittet **Gatewayforbindelse** under **Du har ingen personlige gateways installeret** skal du vælge **Installér nu**. Der er flere begrænsninger for den personlige datagateway, som beskrevet i [Datagateway i det lokale miljø (personlig tilstand)](service-gateway-personal-mode.md).

I modsætning til en datagateway til virksomheder behøver du ikke at føje datakildedefinitioner til en personlig gateway. Du kan i stedet administrere konfigurationen af datakilden ved hjælp af afsnittet **Legitimationsoplysninger for datakilde** under indstillingerne for datasæt, som vist på følgende skærmbillede.

![Konfigurer legitimationsoplysninger for datakilden for gatewayen](media/refresh-data/configure-data-source-credentials-gateway.png)


### <a name="accessing-cloud-data-sources"></a>Adgang til datakilder i cloudmiljøet

Datasæt, der bruger datakilder i cloudmiljøet, f.eks. Azure SQL DB, kræver ikke en datagateway, hvis Power BI kan etablere en direkte netværksforbindelse til kilden. Du kan derfor administrere konfigurationen af disse datakilder ved hjælp af afsnittet **Legitimationsoplysninger for datakilde** under indstillingerne for datasæt. Som vist på følgende skærmbillede behøver du ikke konfigurere en gatewayforbindelse.

![Konfigurer legitimationsoplysninger for datakilden uden en gateway](media/refresh-data/configure-data-source-credentials.png)

> [!NOTE]
> Hver bruger kan kun have ét sæt legitimationsoplysninger pr. datakilde på tværs af alle de datasæt, de ejer, uanset hvilke arbejdsområder datasættene er placeret på. 

### <a name="accessing-on-premises-and-cloud-sources-in-the-same-source-query"></a>Adgang til kilder i det lokale miljø og cloudmiljøet i den samme kildeforespørgsel

Et datasæt kan hente data fra flere kilder, og disse kilder kan være placeret i det lokale miljø eller i cloudmiljøet. Men som tidligere nævnt kan et datasæt kun bruge en enkelt gatewayforbindelse. Selvom der ikke nødvendigvis kræves en gateway til datakilder i cloudmiljøet, kræves der en gateway, hvis et datasæt opretter forbindelse til kilder både i det lokale miljø og cloudmiljøet i en enkelt mikset forespørgsel. I dette scenarie skal Power BI også bruge en gateway til datakilder i cloudmiljøet. Følgende diagram viser, hvordan sådan et datasæt tilgår dets datakilder.

![Datakilder i cloudmiljøet og det lokale miljø](media/refresh-data/cloud-on-premises-data-sources-diagram.png)

> [!NOTE]
> Hvis et datasæt bruger separate miksforespørgsler til at oprette forbindelse til kilder i det lokale miljø og cloudmiljøet, bruger Power BI en gatewayforbindelse til at nå ud til kilder i det lokale miljø og en direkte netværksforbindelse til kilder i cloudmiljøet. Hvis en miksforespørgsel fletter eller tilføjer data fra kilder i det lokale miljø eller cloudmiljøet, skifter Power BI til gatewayforbindelsen for kilder i cloudmiljøet.

Power BI-datasæt er afhængige af Power-forespørgsel for at få adgang til og hente kildedata. På følgende miksliste kan du se et grundlæggende eksempel på en forespørgsel, der fletter data fra en kilde i det lokale miljø og en kilde i cloudmiljøet.

```
Let

    OnPremSource = Sql.Database("on-premises-db", "AdventureWorks"),

    CloudSource = Sql.Databases("cloudsql.database.windows.net", "AdventureWorks"),

    TableData1 = OnPremSource{[Schema="Sales",Item="Customer"]}[Data],

    TableData2 = CloudSource {[Schema="Sales",Item="Customer"]}[Data],

    MergedData = Table.NestedJoin(TableData1, {"BusinessEntityID"}, TableData2, {"BusinessEntityID"}, "MergedData", JoinKind.Inner)

in

    MergedData
```

Der er to muligheder for at konfigurere en datagateway til at understøtte fletning eller tilføjelse af data fra kilder i det lokale miljø og cloudmiljøet:

- Føj en datakildedefinition for kilden i cloudmiljøet til datagatewayen udover til kilder i det lokale miljø.
- Markér afkrydsningsfeltet **Tillad, at brugerens datakilder i cloudmiljøet opdateres via denne gatewayklynge**.

![Opdater via gatewayklynge](media/refresh-data/refresh-gateway-cluster.png)

Hvis du markerer afkrydsningsfeltet **Tillad, at brugerens datakilder i cloudmiljøet opdateres via denne gatewayklynge i gatewaykonfigurationen**, som vist på skærmbilledet ovenfor, kan Power BI bruge den konfiguration, som brugeren har defineret for kilden i cloudmiljøet under **Legitimationsoplysninger for datakilde** i indstillingerne for datasættet. Dette kan hjælpe med at reducere spildet for gatewaykonfigurationen. Hvis du derimod vil have større kontrol over de forbindelser, som din gateway etablerer, skal du ikke markere dette afkrydsningsfelt. I dette tilfælde skal du føje en eksplicit datakildedefinition for hver kilde i cloudmiljøet, du vil understøtte, til din gateway. Det er også muligt at markere afkrydsningsfeltet og føje eksplicitte datakildedefinitioner for dine kilder i cloudmiljøet til en gateway. I dette tilfælde bruger gatewayen datakildedefinitionerne for alle matchende datakilder.

### <a name="configuring-query-parameters"></a>Konfiguration af forespørgselsparametre

Miks- eller M-forespørgsler, som du opretter ved hjælp af Power-forespørgsel, kan variere i kompleksitet fra trivielle trin til parameteriserede konstruktioner. På følgende liste kan du se et eksempel på små miksforespørgsel, der bruger to parametre kaldet _SchemaName_ og _TableName_ til at få adgang til en bestemt tabel i en AdventureWorks-database.

```
let

    Source = Sql.Database("SqlServer01", "AdventureWorks"),

    TableData = Source{[Schema=SchemaName,Item=TableName]}[Data]

in

    TableData
```

> [!NOTE]
> Forespørgselsparametre understøttes kun for datasæt i Importtilstand. DirectQuery-/LiveConnect-tilstand understøtter ikke definitioner for forespørgselsparametre.

Du skal konfigurere forespørgselsparametrene for mikset under indstillingerne for datasættet for at sikre, at et parameteriseret datasæt tilgår de korrekte data. Du kan også opdatere parametrene programmatisk ved hjælp af [REST API'en for Power BI](/rest/api/power-bi/datasets/updateparametersingroup). På følgende skærmbillede kan du se den brugergrænseflade, du skal bruge til at konfigurere forespørgselsparametrene for et datasæt, der bruger ovenstående miksforespørgsel.

![Konfigurer forespørgselsparametre](media/refresh-data/configure-query-parameters.png)




## <a name="refresh-and-dynamic-data-sources"></a>Opdatering og dynamiske datakilder
 
En *dynamisk datakilde* er en datakilde, hvor nogle eller alle de oplysninger, der kræves for at oprette forbindelse, ikke kan bestemmes, før Power Query kører forespørgslen, da dataene er genereret i kode eller returneres fra en anden datakilde. Eksempler: navnet på forekomsten og databasen for en SQL Server-database, stien til en CSV-fil eller URL-adressen til en webtjeneste. 
 
I de fleste tilfælde kan Power BI-datasæt, der bruger dynamiske datakilder, ikke opdateres i Power BI-tjenesten. Der er nogle få undtagelser, hvor dynamiske datakilder kan opdateres i Power BI-tjenesten, f.eks. Når du bruger RelativePath og forespørgselsindstillingerne med M-funktionen web.Contents. Forespørgsler, der refererer til Power Query-parametre, kan også opdateres.
 
Hvis du vil afgøre, om din dynamiske datakilde kan opdateres, skal du åbne dialogboksen **Indstillinger for datakilde** i **Power Query-editor** og derefter vælge **datakilder i den aktuelle fil**. I det vindue, der vises, skal du holde øje med den følgende advarselsmeddelelse, som vist på følgende billede:
 
> [!NOTE]
> Visse datakilder er muligvis ikke angivet på grund af håndskrevne forespørgsler.

![Indikator for dynamisk datakilde](media/refresh-data/dynamic-data-source.png)

Hvis denne advarsel findes i dialogboksen **Indstillinger for datakilde** vises en dynamisk datakilde, der ikke kan opdateres i Power BI-tjenesten.

## <a name="configure-scheduled-refresh"></a>Konfigurer planlagt opdatering

Etablering af forbindelse mellem Power BI og dine datakilder er klart den største udfordring ved at konfigurere en opdatering af data. De resterende trin er relativt enkle og omfatter angivelse af tidsplanen for opdateringen og aktivering af meddelelser om fejl under opdateringen. Du kan finde en trinvis vejledning i Sådan gør du-vejledningen [Konfiguration af planlagt opdatering](refresh-scheduled-refresh.md).

### <a name="setting-a-refresh-schedule"></a>Angivelse af en tidsplan for opdatering

I afsnittet **Planlagt opdatering** angiver du hyppigheden og tidspunktet for opdateringen af et datasæt. Som tidligere nævnt kan du konfigurere op til otte daglige tidspunkter, hvis dit datasæt befinder sig på en delt kapacitet eller 48 tidspunkter i forbindelse med Power BI Premium. På følgende skærmbillede kan du se en tidsplan for opdatering angivet i et 12-timers interval.

![Konfigurer planlagt opdatering](media/refresh-data/configure-scheduled-refresh.png)

Når du har konfigureret en tidsplan for opdatering, kan du på siden med indstillinger for datasættet se oplysninger om det næste opdateringstidspunkt, som vist på skærmbilledet ovenfor. Hvis du vil opdatere dataene hurtigere, f.eks. for at teste din gateway og konfigurationen af din datakilde, kan du udføre en opdatering efter behov ved hjælp af indstillingen **Opdater nu** i menuen for datasæt i navigationsruden. Opdateringer on-demand påvirker ikke det næste planlagte opdateringstidspunkt.

Bemærk også, at det konfigurerede opdateringstidspunkt muligvis ikke er præcist det tidspunkt, hvor Power BI starter den næste planlagte proces. Power BI starter planlagte opdateringer efter bedste evne. Målet er at starte opdateringen inden for 15 minutter fra det planlagte tidspunkt, men der kan opstå en forsinkelse på op til én time, hvis tjenesten ikke kan tildele de påkrævede ressourcer hurtigere.

> [!NOTE]
> Power BI deaktiverer din tidsplan for opdatering efter fire fejl i træk, eller når tjenesten registrerer en uoprettelig fejl, der kræver en opdatering af konfigurationen, f.eks. ugyldige eller udløbne legitimationsoplysninger. Det er ikke muligt at ændre grænsen for gentagne fejl.

### <a name="getting-refresh-failure-notifications"></a>Få meddelelser om mislykket opdatering

Power BI sender som standard meddelelser om mislykket opdatering via mail til ejeren af datasættet, så ejeren kan reagere i tide, hvis der opstår opdateringsfejl. Power BI sender dig også en meddelelse, når tjenesten deaktiverer din tidsplan på grund af gentagne fejl. Microsoft anbefaler, at du markerer afkrydsningsfeltet **Send meddelelse om mislykket opdatering via mail til mig**.

Det er også en god idé at angive yderligere modtagere ved hjælp af tekstfeltet **Send en mail til disse brugere, når opdateringen mislykkes**. Foruden ejeren af datasættet modtager de angivne modtagere meddelelser om opdateringsfejl. Det kan være en kollega, der tager sig af dine datasæt, mens du er på ferie. Det kan også være mailaliasset for dit supportteam, der tager sig af opdateringsproblemer for din afdeling eller organisation. Det kan være nyttigt at sende meddelelser om opdateringsfejl til andre foruden ejeren af datasættet for at sikre, at problemerne bliver opdaget og håndteret rettidigt.

Bemærk, at Power BI ikke kun sender meddelelser om mislykkede opdateringer, men også når tjenesten afbryder en planlagt opdatering midlertidigt på grund af inaktivitet. Power BI anser et datasæt for at være inaktivt, hvis et dashboard eller en rapport, der er baseret på det pågældende datasæt, ikke er blevet besøgt af en bruger i to måneder. I denne situation sender Power BI en mail til ejeren af datasættet, hvor der står, at tjenesten midlertidigt har afbrudt tidsplanen for opdatering af datasættet. På følgende skærmbillede kan du se et eksempel på sådan en meddelelse.

![Mail om midlertidig afbrydelse af opdatering](media/refresh-data/email-paused-refresh.png)

For at fortsætte den planlagte opdatering skal du gå til en rapport eller et dashboard, som er skabt ved hjælp af dette datasæt, eller manuelt opdatere datasættet ved hjælp af indstillingen **Opdater nu**.

### <a name="checking-refresh-status-and-history"></a>Kontrol af status for opdatering og historik

Ud over at få meddelelser om mislykkede opdateringer er det en god idé at kontrollere dine datasæt for opdateringsfejl regelmæssigt. En hurtig måde at gøre det på er ved at se på listen over datasæt i et arbejdsområde. Der står et lille advarselsikon ud for datasæt med fejl. Vælg advarselsikonet for at få yderligere oplysninger, som vist på følgende skærmbillede. Du kan finde flere oplysninger om fejlfinding af specifikke opdateringsfejl i [Scenarier i forbindelse med fejlfinding af opdatering](refresh-troubleshooting-refresh-scenarios.md).

![Advarsel om opdateringsstatus](media/refresh-data/refresh-status-warning.png)

Advarselsikonet hjælper med at indikere aktuelle problemer med datasættet, men det er også en god idé at kontrollere opdateringshistorikken regelmæssigt. Som navnet antyder, kan du i opdateringshistorikken se statussen for tidligere synkroniseringscyklusser. En gatewayadministrator kan f.eks. have opdateret et udløbet sæt legitimationsoplysninger til en database. Som du kan se på følgende skærmbillede, viser opdateringshistorikken, hvornår en berørt opdatering er begyndt at virke igen.

![Meddelelser om opdateringshistorik](media/refresh-data/refresh-history-messages.png)

> [!NOTE]
> Du kan finde et link til at få vist opdateringshistorikken under indstillingerne for datasættet. Du kan også hente opdateringshistorikken programmatisk ved hjælp af [REST API'en for Power BI](/rest/api/power-bi/datasets/getrefreshhistoryingroup). Ved hjælp af en brugerdefineret løsning kan du overvåge opdateringshistorikken for flere datasæt på en centraliseret måde.

## <a name="automatic-page-refresh"></a>Automatisk sideopdatering

Automatisk sideopdatering fungerer på rapportsideniveau og giver rapportforfattere mulighed for at angive et opdateringsinterval for visuelle elementer på en side, der kun er aktiv, når siden forbruges. Automatisk sideopdatering er kun tilgængelig for DirectQuery-datakilder. Minimumsintervallet for opdateringen afhænger af, hvilken type arbejdsområde rapporten er publiceret i, samt kapacitetsadministratorens indstillinger for Premium-arbejdsområder og [integrerede arbejdsområder](../developer/embedded/embedding.md).

Få mere at vide om automatisk sideopdatering i artiklen [Automatisk sideopdatering](../create-reports/desktop-automatic-page-refresh.md).

## <a name="best-practices"></a>Bedste praksis

Det er en af de vigtigste dele af bedste praksis at kontrollere opdateringshistorikken regelmæssigt for sine datasæt, da du på den måde kan sikre, at dine rapporter og dashboards bruger de mest aktuelle data. Hvis du finder problemer, bør du løse dem straks og kontakte ejerne af datakilden og gatewayadministratorer, hvis det er nødvendigt.

Derudover bør du overveje følgende anbefalinger til at etablere og bevare pålidelige processer for opdatering af dine datasæt:

- Planlæg dine opdateringer til mindre travle tidspunkter, især hvis dine datasæt befinder sig på Power BI Premium. Hvis du distribuerer opdateringscyklusser for dine datasæt på tværs af et bredere tidsvindue, kan du hjælpe med at undgå spidsbelastninger, der ellers kan overbelaste tilgængelige ressourcer. Forsinkelser af start af en opdateringscyklus er en indikator for overbelastning af ressourcen. Hvis en Premium-kapacitet er helt opbrugt, springer Power BI muligvis tilmed en opdateringscyklus over.
- Vær opmærksom på grænser for opdatering. Hvis kildedata ændres ofte, eller du har en betragtelig datamængde, kan du overveje at bruge DirectQuery-/LiveConnect-tilstand i stedet for Importtilstand, hvis den øgede belastning på kilden og indvirkning på ydeevnen af forespørgsler er acceptabel. Undgå at opdatere et datasæt i Importtilstand konstant. Der er dog flere begrænsninger for DirectQuery-/LiveConnect-tilstanden, f.eks. en grænse på en million pr. række i forbindelse med returnering af data og en grænse på 225-sekunders svartid i forbindelse med kørsel af forespørgsler, som dokumenteret i [Brug DirectQuery i Power BI Desktop](desktop-use-directquery.md). Disse begrænsninger kan kræve, at du alligevel skal bruge Importtilstand. I forbindelse med meget store datamængder bør du overveje at bruge [sammenlægninger i Power BI](../transform-model/desktop-aggregations.md).
- Bekræft, at opdateringstidspunktet for dit datasæt ikke overstiger den maksimale opdateringsvarighed. Brug Power BI Desktop til at tjekke opdateringsvarigheden. Hvis det tager mere end 2 timer, bør du overveje at flytte dit datasæt til Power BI Premium. Dit datasæt kan muligvis ikke opdateres på en delt kapacitet. Du bør også overveje at bruge [gradvis opdatering i Power BI Premium](../admin/service-premium-incremental-refresh.md) i forbindelse med datasæt, der er større end 1 GB eller tager flere timer at opdatere.
- Optimer dine datasæt, så det kun er de tabeller og kolonner, der bruges i dine rapporter og dashboards, der inkluderes. Optimer din miksforespørgsler, og undgå definitioner for dynamisk datakilder og dyre DAX-beregninger, hvis det er muligt. Undgå specifikt DAX-funktioner, der tester hver række i en tabel, på grund af højt forbrug af hukommelse og behandlingsspild.
- Anvend de samme indstillinger for beskyttelse af personlige oplysninger som i Power BI Desktop for at sikre, at Power BI kan generere effektive kildeforespørgsler. Husk på, at Power BI Desktop ikke publicerer indstillinger for beskyttelse af personlige oplysninger. Du skal manuelt anvende indstillingerne i definitionerne for datakilder efter publicering af dit datasæt.
- Begræns antallet af visualiseringer på dine dashboards, især hvis du bruger [sikkerhed på rækkeniveau](../admin/service-admin-rls.md). Som beskrevet tidligere i denne artikel, kan et overdrevet stort antal felter på dashboardet øge opdateringsvarigheden.
- Brug en pålidelig udrulning af en datagateway til virksomheder til at forbinde dine datasæt med datakilder i det lokale miljø. Hvis du opdager mislykkede opdateringer i forbindelse med gateways, f.eks. hvis gatewayen ikke er tilgængelig, eller den er overbelastet, skal du kontakte gatewayadministratorerne for enten at føje yderligere gateways til en eksisterende klynge eller udrulle en ny klynge (opskalering i forhold til udskalering).
- Brug separate datagateways i forbindelse med Import-datasæt og DirectQuery-/LiveConnect-datasæt, så dataimporten under den planlagte opdatering ikke påvirker ydeevnen af rapporter og dashboards oven i DirectQuery-/LiveConnect-datasæt, som sender forespørgsler til datakilderne ved hver brugerinteraktion.
- Sørg for, at Power BI kan sende meddelelser om mislykkede opdateringer til din postkasse. Spamfiltre kan blokere mails eller flytte dem til en særskilt mappe, hvor du måske ikke bemærker dem med det samme.


## <a name="next-steps"></a>Næste trin

[Konfiguration af planlagt opdatering](refresh-scheduled-refresh.md)  
[Værktøjer til fejlfinding af opdateringsfejl](service-gateway-onprem-tshoot.md)  
[Fejlfinding i forbindelse med opdatering af scenarier](refresh-troubleshooting-refresh-scenarios.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
