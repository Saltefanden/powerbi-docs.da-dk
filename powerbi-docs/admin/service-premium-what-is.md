---
title: Hvad er Microsoft Power BI Premium?
description: Power BI Premium indeholder dedikerede kapaciteter til din organisation og giver dig mere pålidelig ydeevne og større datamængder, uden at du skal købe licenser pr. bruger.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 07/28/2020
ms.custom: licensing support
LocalizationGroup: Premium
ms.openlocfilehash: 7f90840284c5b17a118b414db606902789657b7a
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90854684"
---
# <a name="what-is-power-bi-premium"></a>Hvad er Power BI Premium?

Du kan bruge Power BI Premium til at hente dedikerede og forbedrede ressourcer til din organisation, så brugerne i din organisation kan bruge Power BI-tjenesten med bedre ydeevne og svartid. Hvis du f. eks. har et Power BI Premium-abonnement, får du og din organisations brugere adgang til:

> [!div class="checklist"]
> * Større skalering og ydeevne
> * Fleksibilitet til at licensere efter kapacitet
> * Foren selvbetjenings-BI og virksomhedsmæssig BI
> * Udvid BI i det lokale miljø med Power BI-rapportserver
> * Understøttelse af dataopbevaring efter område (Multi-Geo)
> * Del data med alle uden at købe en licens pr. bruger


![Administrationsportal](media/service-premium-what-is/premium-admin-portal.png) 

I denne artikel introduceres vigtige funktioner i Power BI Premium. Hvor det er nødvendigt, leveres der links til flere artikler med mere detaljerede oplysninger. Du kan finde flere oplysninger om Power BI Pro og Power BI Premium i afsnittet _Sammenligning af Power BI-funktioner_ under [Power BI-priser](https://powerbi.microsoft.com/pricing/).

## <a name="subscriptions-and-licensing"></a>Abonnementer og licenser

Power BI Premium er et Microsoft 365-abonnement på lejerniveau, der er tilgængeligt i to SKU-serier (lagerenheder):

- **P**-SKU'er (P1-P5) til integrering og virksomhedsfunktioner kræver en månedlig eller årlig forpligtelse, faktureres månedsvis og indeholder en licens til at installere Power BI-rapportserveren i det lokale miljø.

- **EM**-SKU'er (EM1-EM3) til integrering i _organisationer_ kræver en årlig forpligtelse og faktureres månedsvis. EM1- og EM2-SKU'er er kun tilgængelige via volumenlicensplaner. Du kan ikke købe dem direkte.

Der er en alternativ metode til at købe et **Power BI Embedded**-abonnement i Azure. Der er et enkelt **A**-SKU (A1-A6) SKU-serie, der ikke kræver nogen forpligtelse, og som faktureres på timebasis for brug af rebrandet Power BI i programmer, på portaler og på websteder eller som en måde at teste P- eller EM-kapaciteter på. Alle SKU'er leverer v-kerner for at oprette kapaciteter, men EM-SKU'erne er begrænset til integrering i mindre størrelsesorden. EM1-, EM2-, A1- og A2-SKU'er med mindre end fire v-kerner kører ikke på dedikeret infrastruktur.

Selvom denne artikel fokuserer på P-SKU'er, er meget af det, der beskrives, også relevant for A-SKU'er. I modsætning til SKU'erne for Premium-abonnementet kræver Azure-SKU'er ingen tidsmæssig binding og faktureres på timebasis. De leverer fuld elasticitet, hvilket gør det muligt at skalere op og ned, afbryde midlertidigt, genoptage og slette. 

Azure Power BI Embedded ligger ganske vist uden for denne artikels rammer, men er beskrevet i afsnittet [Testmetoder](service-premium-capacity-optimize.md#testing-approaches) i artiklen Optimering af Premium-kapaciteter som en praktisk og økonomisk mulighed for at teste og måle arbejdsbelastninger. Du kan få mere at vide om Azure-SKU'er i [dokumentationen til Azure Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/).

### <a name="purchasing"></a>Indkøb

Power BI Premium-abonnementer købes af administratorer i Microsoft 365 Administration. Kun globale administratorer eller faktureringsadministratorer kan købe SKU'er. Når de er blevet købt, modtager lejeren et tilsvarende antal v-kerner, som kan tildeles til kapaciteter, der kaldes *gruppering af v-kerner*. Køb af en P3-SKU giver f.eks. lejeren 32 v-kerner. Du kan finde flere oplysninger under [Sådan køber du Power BI Premium](service-admin-premium-purchase.md).

## <a name="dedicated-capacities"></a>Dedikerede kapaciteter

Med Power BI Premium får du *dedikerede kapaciteter*. I modsætning til en delt kapacitet, hvor arbejdsbelastninger kører på databehandlingsressourcer, der deles med andre kunder, er en dedikeret kapacitet udelukkende til brug af en organisation. Den isoleres med dedikerede databehandlingsressourcer, som sikrer en pålidelig og konsekvent ydeevne for det indhold, der hostes. Bemærk, at følgende ressourcer gemmes i en delt kapacitet i stedet for i din dedikerede kapacitet:

* Excel-projektmapper (medmindre data importeres først i Power BI Desktop)
* [Send datasæt via push](/rest/api/power-bi/pushdatasets)
* [Streamingdatasæt](../connect-data/service-real-time-streaming.md#set-up-your-real-time-streaming-dataset-in-power-bi)
* [Spørgsmål og svar](../create-reports/power-bi-tutorial-q-and-a.md)

Der er placeret arbejdsområder i kapaciteter. Hver bruger af Power BI har et personligt arbejdsområde, der er kendt som **Mit arbejdsområde**. Der kan oprettes flere arbejdsområder – kendt som **arbejdsområder** – for at muliggøre samarbejde. Arbejdsområder, herunder personlige arbejdsområder, oprettes som standard i den delte kapacitet. Når du har Premium-kapaciteter, kan både Mine arbejdsområder og arbejdsområder tildeles til Premium-kapaciteter.

### <a name="capacity-nodes"></a>Kapacitetsnoder

Som beskrevet i afsnittet [Abonnementer og licenser](#subscriptions-and-licensing) er der to Power BI Premium SKU-serier: **EM** og **P**. Alle Power BI Premium-SKU'er er tilgængelige som *kapacitetsnoder*, som hver især repræsenterer en bestemt mængde ressourcer, der består af processor, hukommelse og lager. Ud over ressourcer har hver SKU en driftsmæssig begrænsning for antallet af DirectQuery-forbindelser og direkte forbindelser pr. sekund samt antallet af parallelle modelopdateringer.

Behandling opnås ved et angivet antal v-kerner, der er ligeligt fordelt mellem backend og frontend.

De **virtuelle back end-kerner** er ansvarlige for Power BI-kernefunktionalitet, herunder behandling af forespørgsler, administration af cache, kørsel af R-tjenester, opdatering af model og gengivelse af rapporter og billeder på serversiden. Backend-v-kerner tildeles en fast mængde hukommelse, der primært bruges til at hoste modeller, som også kaldes aktive datasæt.

**Frontend-v-kerner** er ansvarlige for webtjenesten, dashboardet og dokumentstyringen af rapporter, administration af adgangsrettigheder, planlægning, API'er, uploads og downloads og generelt alt, hvad der er relateret til brugeroplevelsen.

Lagerpladsen er angivet til **100 TB pr. kapacitetsnode**.

Ressourcerne og grænserne for hver Premium-SKU (og A-SKU'er i en tilsvarende størrelse) er beskrevet i følgende tabel:

| Kapacitetsnoder | V-kerner i alt | Backend-v-kerner | RAM (GB) | Frontend-v-kerner | DirectQuery/direkte forbindelser (pr. sek.) | Parallel opdatering af modeller |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 3 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4/A7 <sup>[1](#limit)</sup>| 64 | 32 | 200 | 32 | 240 | 48 |
| P5/A8 <sup>[1](#limit)</sup>| 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

<a name="limit">1</a> – Kun efter speciel anmodning. For meget store modeller, der er større end 100 GB.

>[!NOTE]
>Det kan være en fordel at bruge en enkelt større SKU (f.eks. én P2-SKU) til at kombinere mindre SKU'er (f.eks. to P1-SKU'er). Du kan f.eks. bruge større modeller og opnå bedre parallelitet med P2.

### <a name="capacity-workloads"></a>Kapacitetsarbejdsbelastninger

Kapacitetarbejdsbelastninger er tjenester, som gøres tilgængelige for brugere. Som standard understøtter Premium- og Azure-kapaciteter kun den datasætarbejdsbelastning, der er knyttet til kørende Power BI-forespørgsler. Arbejdsbelastningen for datasæt kan ikke deaktiveres. Yderligere arbejdsbelastninger kan aktiveres for [AI (Cognitive Services)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [Dataflows](../transform-model/service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) og [Sideinddelte rapporter](../paginated-reports/paginated-reports-save-to-power-bi-service.md). Disse arbejdsbelastninger understøttes kun i Premium-abonnementer. 

Hver ekstra arbejdsbelastning gør det muligt at konfigurere den maksimale hukommelse (som en procentdel af den samlede tilgængelige hukommelse), der kan bruges af arbejdsbelastningen. Standardværdier for maksimumhukommelse bestemmes af SKU. Du kan maksimere din kapacitets tilgængelige ressourcer ved at aktivere disse yderligere arbejdsbelastninger, når de bruges. Og du kan kun ændre hukommelsesindstillinger, når du har bestemt, at standardindstillingerne ikke opfylder dine krav til kapacitetsressourcer. Arbejdsbelastninger kan aktiveres og konfigureres for en kapacitet af kapacitetsadministratorer ved hjælp af **Kapacitetsindstillinger** på [administrationsportalen](service-admin-portal.md) eller ved hjælp af [REST-API'er for kapaciteter](/rest/api/power-bi/capacities).  

![Aktivér arbejdsbelastninger](media/service-admin-premium-workloads/admin-portal-workloads.png)

Du kan få mere at vide under [Konfigurer arbejdsbelastninger i en Premium-kapacitet](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>Sådan fungerer kapaciteter

Power BI-tjenesten udnytter hele tiden kapacitetsressourcerne bedst muligt uden at overskride de grænser, der er pålagt kapaciteten.

Kapacitetshandlinger er klassificeret som enten *interaktive* eller *baggrundshandlinger*. Interaktive handlinger omfatter gengivelse af anmodninger og svare på Brugerinteraktioner (filtrering, spørgsmål og svar-forespørgsel, osv.). Som hovedregel er importmodelforespørgsler meget krævende for hukommelsesressourcerne, mens modelforespørgsler om DirectQuery og direkte forbindelser er krævende for CPU'en. Handlinger i baggrunden omfatter opdateringer af dataflows og importmodeller samt cachelagring af dashboardforespørgsler.

Det er vigtigt at forstå, at interaktive handlinger altid går forud for handlinger i baggrunden for at sikre den bedst mulige brugeroplevelse. Hvis der ikke er tilstrækkelige ressourcer, føjes handlinger i baggrunden til en kø for at blive behandlet, når ressourcerne frigøres. Handlinger i baggrunden, f.eks. datasætopdateringer, kan stoppes midt i processen af Power BI-tjenesten og føjes til en kø.

Importmodeller skal være fuldt indlæst i hukommelsen, så de kan forespørges eller opdateres. Power BI-tjenesten administrerer hukommelsesforbrug ved hjælp af avancerede algoritmer for at sikre maksimal anvendelse af den tilgængelige hukommelse, og det kan medføre overallokering af kapaciteten: Selvom det er muligt for en kapacitet at lagre mange importmodeller (op til 100 TB pr. Premium-kapacitet), når deres kombinerede disklager overskrider den understøttede hukommelse (og ekstra hukommelse kræves til forespørgsler og opdateringer), kan de ikke alle indlæses i hukommelsen på samme tid.

Importmodeller indlæses derfor i og fjernes fra hukommelsen i henhold til forbrug. En importmodel indlæses, når den forespørges (interaktiv handling) og endnu ikke er i hukommelsen, eller når den skal opdateres (handling i baggrunden).

Sletning af en model fra hukommelsen kaldes *fjernelse*. Det er en handling, som Power BI kan udføre hurtigt afhængigt af størrelsen på modellerne. Hvis kapaciteten ikke oplever noget pres på hukommelsen, indlæses modellerne i hukommelsen og forbliver der. Men hvis der ikke er tilstrækkelig hukommelse til at indlæse en model, skal Power BI-tjenesten først frigøre hukommelse. Den frigør hukommelse ved at registrere modeller, der er blevet inaktive, ved at søge efter modeller, som ikke har været anvendt i de sidste tre minutter \[[1](#endnote-1)\], og fjerner dem derefter. Hvis der ikke er nogen inaktive modeller at fjerne, forsøger Power BI-tjenesten at fjerne modeller, der er indlæst til handlinger i baggrunden. En sidste udvej efter 30 sekunder med mislykkede forsøg \[[1](#endnote-1)\] er at afbryde den interaktive handling. I dette tilfælde får rapportbrugeren besked om fejlen med et forslag om at prøve igen om et øjeblik. I nogle tilfælde fjernes modeller fra hukommelsen pga. servicehandlinger.

Det er vigtigt at understrege, at fjernelse af datasæt er en normal og forventet funktionsmåde. Den har til formål at maksimere forbruget af hukommelse ved at indlæse og fjerne modeller, hvis størrelse tilsammen kan overskride den tilgængelige hukommelse. Dette er tilsigtet og åbenlyst for rapportbrugerne. Høje fjernelsesrater betyder ikke nødvendigvis, at kapaciteten har fået tildelt utilstrækkelige ressourcer. De kan dog blive et problem, hvis svartiden for forespørgsler eller opdateringer bliver påvirket af de høje fjernelsesrater.

Opdateringer af importmodeller er altid hukommelseskrævende, da modeller skal indlæses i hukommelsen. Der kræves ekstra hukommelse til behandling. En fuld opdatering kan bruge ca. dobbelt så meget hukommelse, der kræves af modellen. Dette sikrer, at modellen kan forespørges, selv når den behandles, da forespørgsler sendes til den eksisterende model, indtil opdateringen er fuldført, og de nye modeldata er tilgængelige. En trinvis opdatering kræver mindre hukommelse og kan fuldføres hurtigere og kan derfor i høj grad reducere belastningen af kapacitetsressourcer. Opdateringer kan også være CPU-krævende for modeller, især dem med komplekse Power-transformationer eller beregnede tabeller/kolonner, som er komplekse eller baseret på store tabeller.

Opdateringer af f.eks. forespørgsler kræver, at modellen indlæses i hukommelsen. Hvis der ikke er tilstrækkelig hukommelse, vil Power BI-tjenesten forsøge at udsætte inaktive modeller, og hvis det ikke er muligt (da alle modeller er aktive), sættes opdateringsjobbet i kø. Opdateringer er typisk CPU-krævende, endda endnu mere krævende end forespørgsler. Der er derfor kapacitetsbegrænsninger for antallet af samtidige opdateringer, der er angivet til 1,5 gange antallet af backend-v-kerner, rundet op. Hvis der er for mange samtidige opdateringer, sættes en planlagt opdatering i kø. Når disse situationer opstår, tager det længere tid at fuldføre opdateringen. Opdateringer efter behov, f.eks. dem, der udløses af en brugeranmodning eller et API-kald, forsøger igen tre gange \[[1](#endnote-1)\]. Hvis der stadig ikke er tilstrækkelige ressourcer, mislykkes opdateringen.

Afsnitsnoter:   
<a name="endnote-1"></a>\[1\] Kan ændres.

### <a name="regional-support"></a>Områdesupport

Når du opretter en ny kapacitet, kan globale administratorer og administratorer af Power BI-tjenesten angive et område, hvor arbejdsområder, der er tildelt til kapaciteten, placeres. Dette kaldes **Multi-Geo**. Med Multi-Geo kan organisationer opfylde krav til dataplacering ved at implementere indhold i datacentre i et bestemt område, også selvom det er forskelligt fra det område, som Microsoft 365-abonnementet gælder for. Du kan få mere at vide under [Multi-Geo-understøttelse i Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Kapacitetsadministration

Administration af Premium-kapaciteter omfatter oprettelse eller sletning af kapaciteter, tildeling af administratorer, tildeling af arbejdsområder, konfiguration af arbejdsbelastninger, overvågning og udførelse af justeringer til optimering af kapacitetsydeevnen. 

Globale administratorer eller administratorer af Power BI-tjenesten kan oprette Premium-kapaciteter fra tilgængelige v-kerner eller redigere eksisterende Premium-kapaciteter. Når der oprettes en kapacitet, angives kapacitetens størrelse og det geografiske område, og der tildeles mindst én kapacitetsadministrator. 

Når der oprettes kapaciteter, udføres de fleste administrative opgaver på [administrationsportalen](service-admin-portal.md).

![Administrationsportal](media/service-premium-what-is/premium-admin-portal.png)

Kapacitetsadministratorer kan tildele arbejdsområder til kapaciteten, administrere brugertilladelser og tildele andre administratorer. Kapacitetsadministratorer kan også konfigurere arbejdsbelastninger, justere hukommelsesallokeringer og om nødvendigt genstarte en kapacitet, hvilket medfører nulstilling af handlinger, hvis en kapacitet overbelastes.

![Administrationsportal](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Kapacitetsadministratorer kan også sikre, at en kapacitet kører, som den skal. De kan overvåge kapacitetens tilstand direkte via administrationsportalen eller ved hjælp af programmet Premium Capacity Metrics.

Du kan få mere at vide om oprettelse af kapaciteter, tildeling af administratorer og tildeling af arbejdsområder under [Administration af Premium-kapaciteter](service-premium-capacity-manage.md). Du kan få mere at vide om roller under [Administratorroller, der er relateret til Power BI](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Overvågning

Overvågning af Premium-kapaciteter giver administratorer en forståelse af, hvordan kapaciteter kører. Kapaciteter kan overvåges ved hjælp af administrationsportalen og [appen Power BI Premium Capacity Metrics](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics).

Overvågning på portalen giver et hurtigt overordnet overblik over målepunkter og angiver belastninger, der er placeret, og de ressourcer, der er brugt af din kapacitet. Det vises som et gennemsnit for de seneste syv dage. 

![Administrationsportal](media/service-premium-what-is/premium-admin-portal-health.png)

Programmet **Power BI Premium Capacity Metrics** giver de mest detaljerede oplysninger om ydeevnen af dine kapaciteter. Programmet indeholder et overordnet dashboard og mere detaljerede rapporter.

![Appdashboardet Målepunkter](media/service-admin-premium-monitor-capacity/app-dashboard.png)

I programmets dashboard kan du klikke på en celle med målepunkter for at åbne en detaljeret rapport. Rapporter indeholder detaljerede målepunkter og en filterfunktion til detailudledning af de vigtigste oplysninger, du skal bruge for at sikre, at dine kapaciteter kører, som de skal.

![Periodiske spidsbelastninger af forespørgselsventetider indikerer en potentiel CPU-mætning](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Du kan få mere at vide om overvågning af kapaciteter under [Overvågning på Power BI-administrationsportalen](service-admin-premium-monitor-portal.md) og [Overvågning med programmet Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md).

### <a name="optimizing-capacities"></a>Optimering af kapaciteter

Det er vigtigt, at du udnytter dine kapaciteter bedst muligt, for at sikre, at brugerne får den bedste ydeevne, og at du får mest muligt ud af din investering i Premium. Ved at overvåge vigtige målepunkter kan administratorer afgøre, hvordan de bedst foretager fejlfinding i forbindelse med flaskehalse og foretager de nødvendige handlinger. Du kan få mere at vide under [Optimering af Premium-kapaciteter](service-premium-capacity-optimize.md) og [Premium-kapacitetsscenarier](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>REST-API'er for kapaciteter

Power BI REST-API'er indeholder en samling [kapacitets-API'er](/rest/api/power-bi/capacities). Administratorer kan bruge disse API'er til at administrere mange aspekter af dine Premium-kapaciteter via programmering, herunder aktivering og deaktivering af arbejdsbelastninger, tildeling af arbejdsområder til en kapacitet og meget mere.

## <a name="large-datasets"></a>Store datasæt

Afhængigt af SKU'en understøtter Power BI Premium upload af Power BI Desktop-modelfiler (.pbix) med en størrelse på højst **10 GB**. Når modellen er indlæst, kan den publiceres til et arbejdsområde, der er tildelt til en Premium-kapacitet. Datasættet kan derefter opdateres til en størrelse på op til **12 GB**.

### <a name="size-considerations"></a>Overvejelser i forbindelse med størrelse

Store datasæt kan være ressourcekrævende. Du skal som minimum have en P1- eller en A4-SKU for datasæt, der er større end 1 GB. Selvom publicering af store datasæt til arbejdsområder, som understøttes af A-SKU'er op til A3, kan fungere, vil en opdatering af dem ikke fungere.

I følgende tabel vises de anbefalede SKU'er for upload af .pbix-filer eller publicering til Power BI-tjenesten:

   |SKU  |.pbix-størrelse   |
   |---------|---------|
   |P1/A4    | < 3 GB        |
   |P2/A5    | < 6 GB        |
   |P3/A6, P4, P5    | op til 10 GB   |

Power BI Embedded A4-SKU'en er lig med P1-SKU'en, A5-SKU'en = P2 og A6-SKU'en = P3.

Hvis du aktiverer [store modeller](service-premium-large-models.md) på et datasæt, kan størrelsen af .pbix-filen stadig være gældende i forbindelse med filupload eller publicering. Datasæt kan dog blive meget større end disse begrænsninger, når trinvis opdatering kombineres med store modeller. I forbindelse med store modeller begrænses størrelsen af datasættet kun til størrelsen af Power BI Premium-kapaciteten.

Dine .pbix-filer repræsenterer data i en *stærkt komprimeret tilstand*. Dataene udvides sandsynligvis, når de indlæses i hukommelsen, og herfra udvides de måske gentagne gange under dataopdatering.

Planlagt opdatering af store datasæt kan tage lang tid og være ressourcekrævende. Det er vigtigt, at du ikke planlægger for mange overlappende opdateringer. Vi anbefaler, at du konfigurerer en [trinvis opdatering](service-premium-incremental-refresh.md), fordi det er hurtigere og mere pålideligt og forbruger færre ressourcer.

Den første rapportindlæsning af store datasæt kan tage lang tid, hvis det er et stykke tid siden, det sidste datasæt blev brugt. En linje for længere rapportindlæsninger viser indlæsningens status.

Selvom hukommelses- og tidsbegrænsninger pr. forespørgsel er meget større i Premium-kapacitet, så anbefales det, at du bruger filtre og udsnitsværktøj til at begrænse visuelle elementer, så der kun vises det mest nødvendige.

## <a name="incremental-refresh"></a>Trinvis opdatering

En trinvis opdatering gør det nemmere at opbevare og vedligeholde store datasæt i Power BI Premium og Power BI Pro. En trinvis opdatering har mange fordele, f.eks. er opdateringer hurtigere, fordi det kun er data, der er ændret, som skal opdateres. Opdateringer er mere pålidelige, fordi det ikke længere er nødvendigt at vedligeholde langtidskørende forbindelser til ustabile datakilder. Forbrug af ressourcer reduceres, fordi der skal opdateres færre data, hvilket betyder et mindre overordnet forbrug af hukommelsen og andre ressourcer. Politikker om trinvis opdatering er defineret i **Power BI Desktop** og anvendes, når de er publiceret på et arbejdsområde i en Premium-kapacitet. 

![Detaljer om opdatering](media/service-premium-incremental-refresh/refresh-details.png)

Du kan få mere at vide under [Trinvis opdatering i Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Sideinddelte rapporter

Sideinddelte rapporter, der understøttes på P1-P3- og A4-A6-SKU'er, er baseret på RDL-teknologi (Report Definition Language) i SQL Server Reporting Services. De er baseret på RDL-teknologien, men er ikke det samme som Power BI-rapportserveren, som er en rapporteringsplatform, der kan downloades, og som du kan installere i det lokale miljø. Også inkluderet i Power BI Premium. Sideinddelte rapporter formateres, så de passer til en side, der kan udskrives eller deles. Data vises i en tabel, også selvom tabellen strækker sig over flere sider. Ved hjælp af det gratis Windows-skrivebordsprogram [**Power BI Report Builder**](https://aka.ms/pbireportbuilder) kan brugere oprette sideinddelte rapporter og publicere dem til tjenesten.

I Power BI Premium er sideinddelte rapporter en arbejdsbelastning, der skal aktiveres for en kapacitet ved hjælp af administrationsportalen. Kapacitetsadministratorer kan aktivere og derefter angive mængden af hukommelse som en procentdel af kapacitetens overordnede hukommelsesressourcer. I modsætning til andre typer arbejdsbelastninger kører Power BI Premium sideinddelte rapporter i et afgrænset område i kapaciteten. Den maksimale hukommelse, der angives for dette område, bruges, uanset om arbejdsbelastningen er aktiv eller ej. Standarden er 20 %. 

Du kan få mere at vide under [Sideinddelte rapporter i Power BI Premium](../paginated-reports/paginated-reports-report-builder-power-bi.md). Du kan få mere at vide om aktivering af arbejdsbelastningen for sideinddelte rapporter under [Konfigurer arbejdsbelastninger](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Power BI-rapportserver
 
Power BI-rapportserveren er inkluderet i Power BI Premium og er en rapportserver med en webportal i *det lokale miljø*. Du kan opbygge dit BI-miljø lokalt og distribuere rapporter bag din virksomheds firewall. Med rapportserveren får brugere adgang til omfattende, interaktive funktioner til virksomhedsrapportering i SQL Server Reporting Services. Brugere kan udforske data og hurtigt finde mønstre, så de kan træffe bedre og hurtigere beslutninger. Rapportserveren giver dig styring på dine egne betingelser. Hvis og når tiden er inde, gør Power BI-rapportserveren det nemt at overføre til cloudmiljøet, hvor din organisation kan drage fordel af alle funktioner i Power BI Premium.

Du kan få mere at vide under [Power BI-rapportserver](../report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Ubegrænset indholdsdeling

Med Premium kan alle – uanset om de befinder sig i eller uden for organisationen – få vist dit Power BI-indhold, herunder sideinddelte og interaktive rapporter, uden at købe individuelle licenser. 

![Indholdsdeling](media/service-premium-what-is/premium-sharing.png)

Premium muliggør omfattende distribution af indhold for Pro-brugere uden at kræve Pro-licenser for modtagere, der får vist indholdet. Pro-licenser kræves for oprettere af indhold. Oprettere opretter forbindelse til datakilder og modeldata og opretter rapporter og dashboards, der er pakket som arbejdsområdeapps. Brugere uden en Pro-licens kan stadig få adgang til et arbejdsområde, der er i en Power BI Premium-kapacitet, så længe de har rollen Fremviser. 

Du kan få mere at vide under [Power BI-licenser](service-admin-licensing-organization.md).

## <a name="analysis-services-in-power-bi-premium-preview"></a>Analysis Services i Power BI Premium (prøveversion)

Under overfladen styres Power BI Premium-arbejdsområder og -datasæt af det gennemtestede Microsoft-program **Analysis Services Vertipaq**. Analysis Services understøtter programmerings- og klientprogrammer og -værktøjer via klientbiblioteker og API'er, der understøtter XMLA-protokollen med åbne standarder. Arbejdsbelastninger for datasæt i en Power BI Premium-kapacitet understøtter som standard *skrivebeskyttede* forbindelser fra klientprogrammer og værktøjer fra Microsoft og tredjeparter via **XMLA-slutpunkter**. Kapacitetsadministratorer kan også vælge at deaktivere eller tillade *læse-/skrive*handlinger via slutpunktet.

Med skrivebeskyttet adgang kan Microsoft-værktøjer, f.eks.SSMS (SQL Server Management Studio) og SQL Server Profiler, og tredjepartsapps, f.eks. DAX Studio og programmer til datavisualisering, kan oprette forbindelse til og forespørge om Premium-datasæt ved hjælp af XMLA, DAX, MDX, DMV'er og sporingshændelser. Med læse-/skriveadgang kan værktøjer til modellering af virksomhedsdata, f. eks. Visual Studio med Analysis Services-projektudvidelse eller Tabular Editor med åben kildekode, udrulle tabellariske modeller som et datasæt til et Premium-arbejdsområde. Og med værktøjer som SSMS kan administratorer bruge TMSL (Tabular Model Scripting Language) til scenarier med script af metadataændringer og avancerede dataopdateringer. 

Du kan få mere at vide under [Netværksmulighed for datasæt med XMLA-slutpunktet](service-premium-connect-tools.md).

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)


## <a name="next-steps"></a>Næste trin

> [!div class="nextstepaction"]
> [Administration af Premium-kapaciteter](service-premium-capacity-manage.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)