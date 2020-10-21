---
title: Bedste fremgangsmåder for udrulningspipelines
description: Bedste fremgangsmåder for udrulningspipelines i Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 09/15/2020
ms.openlocfilehash: 01cb4c5de2863250f083320e7005c0d589a2da0b
ms.sourcegitcommit: 59d07be9c3e4a2067f6d42c3002a194371bc4341
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/16/2020
ms.locfileid: "92116471"
---
# <a name="deployment-pipelines-best-practices"></a>Bedste praksis for udrulningspipelines

Denne artikel indeholder en vejledning til BI-oprettere, der administrerer deres indhold i hele indholdets livscyklus. I artiklen fokuseres der på at anvende udrulningspipelines som et værktøj til administration af livscyklusser for BI-indhold.

Artiklen er opdelt i fire afsnit:

* **Indholdsforberedelse** – forbered dit indhold til administration af livscyklus.

* **Udvikling** – få mere at vide om de bedste måder at oprette indhold på i udviklingsfasen for udrulningspipelines.

* **Test** – forstå, hvordan du kan bruge testfasen for udrulningspipelines til at teste dit miljø.

* **Produktion** – anvend produktionsfasen til udrulningspipelines, når du gør dit indhold tilgængeligt til forbrug.

## <a name="content-preparation"></a>Indholdsforberedelse

Forbered dit indhold til løbende administration gennem hele dets livscyklus. Sørg for at gennemse oplysningerne i dette afsnit, før du gør et af følgende:

* Frigiver dit indhold til produktion

* Begynder at bruge en udrulningspipeline for et bestemt arbejdsområde

* Publicerer dit arbejde

### <a name="treat-each-workspace-as-a-complete-package-of-analytics"></a>Behandler hvert arbejdsområde som en komplet pakke af analyser

Ideelt set bør et arbejdsområde indeholde en komplet visning af ét aspekt (f.eks. afdeling, forretningsenhed, projekt eller vertikalt) i din organisation. Det gør det lettere at administrere tilladelser for forskellige brugere og tillader, at indholdsfrigivelser for hele arbejdsområdet styres i henhold til en planlagt plan.  

Hvis du bruger [centraliserede datasæt](../connect-data/service-datasets-across-workspaces.md), der benyttes på tværs af organisationen, anbefaler vi, at du opretter to typer arbejdsområder:

* **Modellerings- og dataarbejdsområder** – disse arbejdsområder indeholder alle de centraliserede datasæt

* **Arbejdsområder til rapportering** – disse arbejdsområder indeholder alle afhængige rapporter og dashboards

### <a name="plan-your-permission-model"></a>Planlæg din tilladelsesmodel

En udrulningspipeline er et Power BI-objekt med egne [tilladelser](deployment-pipelines-process.md#permissions). Desuden indeholder pipelinen arbejdsområder, der har deres egne tilladelser.

Hvis du vil implementere en sikker og enkel arbejdsproces, skal du planlægge, hvem der får adgang til hver del af pipelinen. Nogle af de overvejelser, der skal tages højde for, er:

* Hvem skal have adgang til pipelinen?

* Hvilke handlinger skal brugere med adgang til pipelinen kunne udføre i hver enkelt fase?

* Hvem gennemgår indholdet i testfasen?

* Skal reviewerne i testfasen have adgang til pipelinen?

* Hvem skal overvåge udrulningen til produktionsfasen?

* Hvilket arbejdsområde tildeler du?

* Hvilken fase tildeler du arbejdsområdet til?

* Har du brug for at ændre tilladelserne for det arbejdsområde, du vil tildele?

### <a name="connect-different-stages-to-different-databases"></a>Forbind forskellige faser til forskellige databaser

En produktionsdatabase skal altid være stabil og tilgængelig. Det er bedre ikke at overbelaste den med forespørgsler, der er genereret af BI-oprettere til deres udviklings- eller testdatasæt. Byg separate databaser til udvikling og test. Det er med til at beskytte produktionsdata og overbelaster ikke udviklingsdatabasen med hele mængden af produktionsdata, som kan gøre processerne langsomme.

>[!NOTE]
>Hvis din organisation bruger [delte centraliserede datasæt](../connect-data/service-datasets-share.md), kan du springe denne anbefaling over.

### <a name="use-parameters-in-your-model"></a>Brug parametre i modellen

Eftersom du ikke kan redigere datakilderne for datasæt i Power BI-tjenesten, anbefaler vi, at du bruger [parametre](/power-query/power-query-query-parameters) til at gemme forbindelsesoplysninger som f.eks. forekomstnavne og databasenavne i stedet for at bruge en statisk forbindelsesstreng. Det giver dig mulighed for at administrere forbindelserne via webportalen for Power BI-tjenesten eller [bruge API'er](/rest/api/power-bi/datasets/updateparametersingroup) på et senere tidspunkt.

I udrulningspipelines kan du konfigurere parameterregler for at angive specifikke værdier for udviklings-, test- og produktionsfaser.

Hvis du ikke bruger parametre til forbindelsesstrengen, kan du definere datakilderegler for at angive en forbindelsesstreng for et bestemt datasæt. Dette understøttes dog ikke for alle datakilder i udrulningspipelines. Se [Begrænsninger for dataregler](deployment-pipelines-get-started.md#dataset-rule-limitations) for at kontrollere, om du kan konfigurere regler for datakilden.

Parametre kan bruges på flere måder, f.eks. til at foretage ændringer af forespørgsler, filtre og den tekst, der vises i rapporten.

## <a name="development"></a>Udvikling

Dette afsnit indeholder vejledning i at arbejde med udviklingsfasen i udrulningspipelines.

### <a name="use-power-bi-desktop-to-edit-your-reports-and-datasets"></a>Brug af Power BI Desktop til at redigere rapporter og datasæt

Betragt Power BI Desktop som dit lokale udviklingsmiljø. Power BI Desktop giver dig mulighed for at afprøve, udforske og gennemse opdateringer af rapporter og datasæt. Når arbejdet er fuldført, kan du uploade din nye version til udviklingsfasen. Af følgende årsager anbefales det at redigere PBIX-filer i Desktop (og ikke i Power BI-tjenesten):

* Det er lettere at samarbejde med andre forfattere om den samme PBIX-fil, hvis alle ændringer udføres i det samme værktøj.

 * Hvis der foretages onlineændringer, og PBIX-filen downloades og derefter uploades igen, oprettes der dubletter af rapporter og datasæt.

* Du kan bruge versionsstyring til at holde dine PBIX-filer opdateret.

### <a name="version-control-for-pbix-files"></a>Versionsstyring af PBIX-filer

Hvis du vil administrere versionshistorikken for dine rapporter og datasæt, skal du bruge [Power BI's automatiske synkronisering med OneDrive](../collaborate-share/service-connect-to-files-in-app-workspace-onedrive-for-business.md). Dette sikrer, at filerne er opdateret til den nyeste version. Det gør det også muligt at hente ældre versioner, hvis det er nødvendigt.

>[!NOTE]
>Brug kun automatisk synkronisering med OneDrive (eller et andet lager) sammen med PBIX-filerne i udviklingsfasen af en udrulningspipeline. PBIX-filer bør ikke synkroniseres til test- og produktionsfasen af en udrulningspipeline. Dette vil medføre problemer med at installere indhold på tværs af pipelinen.

### <a name="separate-modeling-development-from-report-and-dashboard-development"></a>Adskil modelleringsudvikling fra rapport- og dashboardudvikling

I forbindelse med udrulninger i store virksomheder anbefales det at opdele udvikling af datasæt og udvikling af rapporter og dashboards. Hvis du kun vil opdatere ændringer i en rapport eller et datasæt, skal du bruge indstillingen til valg af udrulningspipelines.  

Denne fremgangsmåde skal igangsættes fra Power BI Desktop ved at oprette en separat PBIX-fil til datasæt og rapporter. Du kan f.eks. oprette en PBIX-fil til datasættet og uploade den i udviklingsfasen. Senere kan rapportforfatterne oprette en ny PBIX kun for rapporten, og [knytte den til det udgivne datasæt](../connect-data/service-datasets-discover-across-workspaces.md) ved hjælp af en direkte forbindelse. Denne teknik gør det muligt for forskellige forfattere at arbejde separat med modellering og visualiseringer og udrulle dem til produktion uafhængigt af hinanden.

I forbindelse med [delte datasæt](../connect-data/service-datasets-share.md) kan du også bruge denne metode på tværs af arbejdsområder.

### <a name="manage-your-models-using-xmla-readwrite-capabilities"></a>Administrer dine modeller ved hjælp af XMLA-læse/skrive-funktionalitet

Hvis du adskiller modelleringsudvikling fra rapport- og dashboardudvikling, kan du bruge avancerede funktioner, f.eks. versionsstyring, fletning af sammenlignelige ændringer og automatiserede processer. Disse ændringer bør udføres i udviklingsfasen, så det færdiggjorte indhold kan udrulles i test- og produktionsfaserne. Det betyder, at ændringerne gennemgår en ensartet proces med andre afhængige elementer, før de udrulles i produktionsfasen.

Du kan adskille modelleringsudvikling fra visualiseringer ved at administrere et [delt datasæt](../connect-data/service-datasets-share.md) i et eksternt arbejdsområde ved hjælp af XMLA-læse/skrive-funktionalitet. Det delte datasæt kan oprette forbindelse til flere rapporter i forskellige arbejdsområder, der administreres i flere pipelines.

## <a name="test"></a>Test

Dette afsnit indeholder vejledning i at arbejde med testfasen i udrulningspipelines.

### <a name="simulate-your-production-environment"></a>Simuler produktionsmiljøet

Ud over at bekræfte at nye rapporter eller dashboards ser rigtige ud, er det også vigtigt at se, hvordan de fungerer fra slutbrugerens synspunkt. Testfasen i udrulningspipelinene giver dig mulighed for at simulere et reelt produktionsmiljø til testformål.

Sørg for, at disse tre faktorer behandles i dit testmiljø:

* Datamængde

* Forbrugsvolumen

* En kapacitet, der svarer til den i produktion

Når du tester, kan du bruge den samme kapacitet som produktionsfasen. Det kan dog gøre produktionen ustabil under belastningstest. Hvis du vil undgå, at produktionen bliver ustabil, skal du bruge en anden kapacitet med samme mængde ressourcer som produktionskapaciteten til test. Hvis du vil undgå ekstra omkostninger, kan du bruge [Azure A-kapaciteter](../developer/embedded/azure-pbie-create-capacity.md) for kun at betale for testtiden.

![Et diagram, som viser en udrulningspipeline med et testmiljø, der simulerer produktionsmiljøet.](media/deployment-pipelines-best-practices/deployment-pipelines-best-practices-diagram.png)

### <a name="use-dataset-rules-with-a-real-life-data-source"></a>Brug regler for datasæt med en datakilde i realtid

Hvis du bruger testfasen til at simulere dataforbruget i det virkelige liv, anbefales det at adskille datakilderne til udvikling og test. Udviklingsdatabasen bør være forholdsvis lille, og testdatabasen bør være så identisk som muligt som produktionsdatabasen. Brug [regler for datakilde](deployment-pipelines-get-started.md#step-4---create-dataset-rules) til at skifte datakilder i testfasen.

Det er nyttigt at styre den mængde data, du importerer fra din datakilde, hvis du bruger en produktionsdatakilde i testfasen. Det kan du gøre ved at føje en parameter til datakildeforespørgslen i Power BI Desktop. Brug parameterregler til at styre mængden af importerede data, eller rediger parameterens værdi.
Du kan også bruge denne fremgangsmåde, hvis du ikke vil overbelaste din kapacitet.

### <a name="measure-performance"></a>Mål ydeevne

Når du simulerer et produktionstrin, [skal du kontrollere indlæsningen af rapporten og interaktionerne](../guidance/monitor-report-performance.md) og finde ud af, om de ændringer, du har foretaget, påvirker dem.

Det kan også være nødvendigt at [overvåge belastningen af kapaciteten](../admin/service-admin-premium-monitor-capacity.md), så du kan fange ekstreme belastninger, før de når produktionen.  

>[!NOTE]
>Det anbefales, at du overvåger kapacitetsbelastninger igen efter udrulningen af opdateringer til produktionsfasen.

### <a name="check-related-items"></a>Tjek relaterede elementer

Relaterede tidspunkter kan påvirkes af ændringer af datasæt eller rapporter. Under test skal du kontrollere, at dine ændringer ikke påvirker eller går ud over ydeevnen for eksisterende elementer, der kan være afhængige af de opdaterede elementer.

Du kan nemt finde de relaterede elementer ved hjælp af [afstamningsvisningen](../collaborate-share/service-data-lineage.md) i arbejdsområdet.

### <a name="test-your-app"></a>Test din app

Hvis du distribuerer indhold til slutbrugerne via en app, skal du gennemse den nye version af appen, før den kommer i produktion. Eftersom hver enkel fase i udrulningspipelinen har sit eget arbejdsområde, kan du nemt publicere og opdatere apps til udviklings- og testfaser. På den måde kan du teste appen fra slutbrugerens synspunkt.

>[!IMPORTANT]
>Udrulningssprocessen omfatter ikke opdatering af appindholdet eller -indstillingerne. Hvis du vil anvende ændringer på indhold eller indstillinger, skal du manuelt opdatere appen i den påkrævede pipelinefase.

## <a name="production"></a>Produktion

Dette afsnit indeholder vejledning i produktionsfasen i udrulningspipelines.

### <a name="manage-who-can-deploy-to-production"></a>Administrer, hvem der kan udrulle til produktion

Da udrulningen til produktion bør håndteres omhyggeligt, er det en god idé kun at lade bestemte personer administrere denne følsomme handling. Det kan dog være en god ide, at alle BI-oprettere i et bestemt arbejdsområde har adgang til pipelinen. Dette kan gøres ved hjælp [tilladelser til produktionsarbejdsområdet](deployment-pipelines-process.md#permissions).  

Hvis der skal udrulles indhold mellem faserne, skal brugerne have enten medlems- eller administratorrettigheder til begge faser. Sørg for, at det kun er de personer, du vil have til at udrulle til produktionen, der har tilladelser til produktionsarbejdsområdet. Andre brugere kan have rolle som bidragyder til produktionsarbejdsområdet eller læser. De kan få vist indhold i pipelinen, men kan ikke udrulle.

Derudover skal du begrænse adgangen til pipelinen ved kun at aktivere pipelinetilladelser for de brugere, der er en del af processen til indholdsoprettelse.

### <a name="set-rules-to-ensure-production-stage-availability"></a>Angiv regler for at sikre tilgængeligheden af produktionsfasen

[Regler for datasæt](deployment-pipelines-get-started.md#step-4---create-dataset-rules) er en effektiv måde at sikre, at dataene i produktion altid er forbundet og tilgængelige for brugerne. Når der er anvendt regler for datasæt, kan der køre udrulninger, mens du har sikkerhed for, at slutbrugerne får vist de relevante oplysninger uden forstyrrelse.

Sørg for, at du angiver regler for produktionsdatasæt for datakilder og parametre, der er defineret i datasættet.

### <a name="update-the-production-app"></a>Opdater produktionsappen

Udrulning i en pipeline opdaterer indholdet i arbejdsområdet, men ikke automatisk den tilknyttede app. Hvis du bruger en app til indholdsdistribution, skal du huske at opdatere appen, når du har udrullet til produktion, så slutbrugerne straks kan bruge den nyeste version.  

### <a name="quick-fixes-to-content"></a>Hurtige rettelser af indhold

I tilfælde af fejl i produktionen, der kræver en hurtig løsning, må du ikke blive fristet til enten at overføre en ny PBIX-version direkte til produktionsfasen eller foretage en onlineændring i Power BI-tjenesten. Det er ikke muligt at udrulle baglæns til test- og udviklingsfaser, når der allerede findes indhold i disse faser. Derudover er det ikke en god ide at udrulle en programrettelse uden at teste den først. Den rette måde at behandle dette problem på er derfor at implementere rettelsen i udviklingsfasen og sende den til resten af faserne i udrulningspipelinen. På den måde kan du kontrollere, at rettelsen fungerer, før du udruller den til produktion. Udrulning på tværs af pipelinen tager kun nogle få minutter.

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Introduktion til udrulningspipelines](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Kom i gang med udrulningspipelines](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Om processen for udrulningspipelines](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Fejlfinding af udrulningspipelines](deployment-pipelines-troubleshooting.md)