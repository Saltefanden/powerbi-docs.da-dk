---
title: Overvåg Power BI Premium-kapacitet med programmet Premium Capacity Metrics
description: Brug Power BI-administrationsportalen og Power BI Premium-appen Capacity Metrics
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 05/18/2020
LocalizationGroup: Premium
ms.openlocfilehash: e13e3ec52ab9eecf3f98b5610df9d83243d7c092
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/30/2020
ms.locfileid: "91599819"
---
# <a name="monitor-premium-capacities-with-the-app"></a>Overvåg Premium-kapaciteter vha. appen

Overvågning af dine kapaciteter er afgørende for at træffe beslutninger om den bedste måde, du kan udnytte dine ressourcer i Premium-kapaciteten på. Du kan overvåge kapacitet via administrationsportalen eller programmet **Power BI Premium Capacity Metrics**. Denne artikel indeholder en beskrivelse af brugen af programmet Premium Capacity Metrics. Programmet giver de mest detaljerede oplysninger om ydeevnen af dine kapaciteter. Hvis du vil have et overblik over målepunkter for den gennemsnitlige brug på et højere niveau for de seneste syv dage, skal du bruge administrationsportalen. Du kan finde flere oplysninger om overvågning på portalen under [Overvåg Premium-kapaciteter på administrationsportalen](service-admin-premium-monitor-portal.md).

Programmet opdateres jævnligt med nye funktioner og funktionalitet. Sørg for, at du kører den nyeste version. Når en ny version bliver tilgængelig, modtager du en [meddelelse](../connect-data/service-template-apps-install-distribute.md#update-a-template-app).

> [!IMPORTANT]
> Hvis der er et højt forbrug af ressourcer i din Power BI Premium-kapacitet, hvilket medfører problemer med ydeevne eller pålidelighed, kan du modtage notifikationer via mail for at identificere og løse problemet. Dette kan være en strømlinet metode til fejlfinding af overbelastede kapaciteter. Se [notifikationer om kapacitet og pålidelighed](service-interruption-notifications.md#capacity-and-reliability-notifications) for at få flere oplysninger.

## <a name="install-the-app"></a>Installér programmet

Gå til [Opret forbindelse til Power BI Premium Capacity Metrics](../connect-data/service-connect-to-pbi-premium-capacity-metrics.md) for at se, hvordan du installerer appen og opretter forbindelse til data. Alternativt kan du [gå direkte til appen](https://go.microsoft.com/fwlink/?linkid=2114036).

## <a name="get-app-refresh-history"></a>Få historik over programopdateringer

Sådan kontrollerer du, hvornår appen Premium Capacity Metrics blev opdateret sidst:

1. Gå til det arbejdsområde, der blev installeret sammen med appen.

   ![Gå til apparbejdsområde.](media/service-admin-premium-monitor-capacity/settings-refresh-history.png)

1. Klik på knappen **Planlæg opdatering** ud for datasættet.

   ![Knappen Planlæg opdatering](media/service-admin-premium-monitor-capacity/schedule-refresh.png)

   Den seneste opdatering vises. Klik på **Opdater historik** for at se planlagte opdateringer og opdateringer efter behov.

   ![Seneste opdatering](media/service-admin-premium-monitor-capacity/settings-last-refresh.png)

## <a name="monitor-capacities-with-the-app"></a>Overvåg kapaciteter vha. appen

Nu, hvor du har installeret programmet, kan du se målepunkter for kapaciteterne i din organisation. Appen indeholder et Dashboard med oversigter over målepunkter og detaljerede rapporter for målepunkter.

### <a name="dashboard"></a>Dashboard

Hvis du vil se et dashboard med en oversigt over de vigtigste målepunkter for kapaciteter, som du er administrator for, skal du under **Dashboards** klikke på **Capacity Metrics i Power BI Premium**. Der vises et dashboard.

![Appdashboardet Målepunkter](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Dashboardet indeholder følgende målepunkter:

#### <a name="top"></a>Øverst

| Metrikværdi | Beskrivelse |
| --- | --- |
| Version | Appversion. | 
| Kapaciteter | Antallet af kapaciteter, som du er administrator for. | 
| Arbejdsområder | Antallet af arbejdsområder i dine kapaciteter, som rapporterer målepunkter.|
|||

#### <a name="system-summary"></a>Systemoversigt

| Metrikværdi | Beskrivelse |
| --- | --- |
| Kapacitet med højeste CPU-udnyttelse | Kapacitet med det maksimale antal gange, hvor CPU'en overskred 80 % af tærsklerne i løbet af de seneste syv dage. |
| Antal gange med højeste CPU-udnyttelse | Antal gange, hvor CPU'en for den navngivne kapacitet overskred 80 % af tærsklerne i løbet af de seneste syv dage. | 
| Kapacitet med maksimal udnyttelse af hukommelsen | Kapacitet med det maksimale antal gange, hvor den maksimale grænse for hukommelsen blev nået i løbet af de seneste syv dage opdelt i buckets på tre minutter.  |
| Antal gange med maksimal udnyttelse af hukommelsen| Antallet af gange, hvor den navngivne kapacitet nåede den maksimale grænse for hukommelsen i løbet af de seneste syv dage opdelt i buckets på tre minutter. |
|||

#### <a name="dataset-summary"></a>Oversigt over datasæt

| Metrikværdi | Beskrivelse |
| --- | --- |
| Datasæt | Det samlede antal datasæt på tværs af alle arbejdsområder i dine kapaciteter.|
| Den gennemsnitlige størrelse af datasæt (MB) | Den gennemsnitlige størrelse af datasæt på tværs af alle arbejdsområder i dine kapaciteter.|  
| Antal gennemsnitlige indlæste datasæt | Det gennemsnitlige antal datasæt, der indlæses i hukommelsen. |  
| Datasæt – gennemsnitligt aktivt datasæt (%)| Det gennemsnitlige antal aktive datasæt i løbet af de seneste syv dage. Et datasæt defineres som aktivt, hvis brugeren har interageret med visualiseringerne i løbet af de seneste tre minutter. |
| CPU – maksimale datasæt (%)| Det maksimale CPU-forbrug af arbejdsbelastninger i datasæt i løbet af de seneste syv dage. |
| CPU – gennemsnitlige datasæt (%)| Det gennemsnitlige CPU-forbrug af arbejdsbelastninger i datasæt i løbet af de seneste syv dage. |
| Hukommelse – gennemsnitlige datasæt (GB) | Det gennemsnitlige hukommelsesforbrug af arbejdsbelastninger i datasæt i løbet af de seneste syv dage. |
| Hukommelse – maksimale datasæt (GB) | Det maksimale hukommelsesforbrug af arbejdsbelastninger i datasæt i løbet af de seneste syv dage.|
| Fjernelser af datasæt | Det samlede antal datasæt, der er blevet fjernet pga. stort hukommelsesforbrug. |
| Antal gange med høj udnyttelse af DirectQuery/liveforbindelse| Antal gange, hvor DirectQuery/liveforbindelse overskred 80 % af tærsklerne i løbet af de seneste syv dage opdelt i buckets på tre minutter. |
| Antal gange med maksimal udnyttelse af DirectQuery/liveforbindelse| De fleste antal gange, hvor DirectQuery/liveforbindelser overskred 80 % i løbet af de seneste syv dage opdelt i buckets på én time. |
| Maksimal høj udnyttelse af DirectQuery/liveforbindelse | Det maksimale antal gange, hvor DirectQuery/liveforbindelser overskred 80 % af tærsklerne i løbet af de seneste syv dage opdelt i buckets på tre minutter.|
| Maksimalt antal forekomster af DirectQuery/liveforbindelse | UTC-tidspunkt, hvor DirectQuery/liveforbindelser overskred 80 % flest gange på én time. |
| Opdateringer i alt | Det samlede antal opdateringer i løbet af de seneste syv dage. |
| Opdateringspålidelighed (%) | Det samlede antal vellykkede opdateringer delt med det samlede antal opdateringer i løbet af de seneste syv dage. |
| Gennemsnitlig varighed af opdateringer (minutter) | Gennemsnitlig mængde tid brugt på at fuldføre opdateringen. |
| Gennemsnitlig ventetid for opdateringer (minutter)| Gennemsnitlig mængde tid, før opdateringen starter. |
| Forespørgsler i alt |  Det samlede antal forespørgsler, der er kørt i løbet af de seneste syv dage. |
| Samlet antal ventende forespørgsler | Det samlede antal forespørgsler, som skulle vente, før de blev udført. |
| Gennemsnitlig varighed af forespørgsler (ms) | Den gennemsnitlige tid, det tager at fuldføre forespørgsler. |
| Gennemsnitlig ventetid for forespørgsler (ms) | Den gennemsnitlige tid, som forespørgsler ventede på systemressourcer, før de blev udført. |
|||

#### <a name="dataflow-summary"></a>Oversigt over dataflow

| Metrikværdi | Beskrivelse |
| --- | --- |
| Dataflow |  Det samlede antal dataflow på tværs af alle arbejdsområder i dine kapaciteter.|
| Opdateringer i alt | Det samlede antal opdateringer i løbet af de seneste syv dage.|  
| Gennemsnitlig varighed af opdateringer (minutter) | Den tid, det tager at fuldføre opdateringen. |
| Gennemsnitlige ventetider for opdateringer (minutter) | Den mellemliggende tid mellem det planlagte tidspunkt og det faktiske starttidspunkt for opdateringen.|
| CPU – maksimale dataflow (%) | Det maksimale CPU-forbrug af arbejdsbelastninger i dataflow i løbet af de seneste syv dage. |
| CPU – gennemsnitlige dataflow (%) | Det gennemsnitlige CPU-forbrug af arbejdsbelastninger i dataflow i løbet af de seneste syv dage. |
| Hukommelse – maksimale dataflow (GB) | Det maksimale hukommelsesforbrug af arbejdsbelastninger i dataflow i løbet af de seneste syv dage. |
| Hukommelse – gennemsnitlige dataflow (GB) | Det gennemsnitlige hukommelsesforbrug af arbejdsbelastninger i dataflow i løbet af de seneste syv dage. |
|||

#### <a name="paginated-report-summary"></a>Oversigt over sideinddelt rapport

| Metrikværdi | Beskrivelse |
| --- | --- |
| Sideinddelte rapporter |  Det samlede antal sideinddelte rapporter på tværs af alle arbejdsområder i dine kapaciteter. |
| Visninger i alt | Det samlede antal gange, som alle rapporter er blevet set af brugere. | 
| Rækker i alt | Det samlede antal rækker med data i alle rapporter.|
| Tid i alt | Den samlede tid, det tager for alle faser (datahentning, -behandling og -gengivelse) i alle rapporter, i millisekunder. |
| CPU – maksimalt forbrug for sideinddelte rapporter (%) | Det maksimale CPU-forbrug af arbejdsbelastninger i sideinddelte rapporter i løbet af de seneste syv dage. |
| CPU – gennemsnitligt forbrug for sideinddelte rapporter (%) | Det gennemsnitlige CPU-forbrug af arbejdsbelastninger i sideinddelte rapporter i løbet af de seneste syv dage. |
| Hukommelse – maksimalt forbrug for sideinddelte rapporter (GB) | Det maksimale hukommelsesforbrug af arbejdsbelastninger i sideinddelte rapporter i løbet af de sidste syv dage. |
| Hukommelse – gennemsnitligt forbrug for sideinddelte rapporter (GB) | Det gennemsnitlige hukommelsesforbrug af arbejdsbelastninger i sideinddelte rapporter i løbet af de sidste syv dage. |
|||

#### <a name="ai-summary"></a>Oversigt over kunstig intelligens

| Metrikværdi | Beskrivelse |
| --- | --- |
| Funktionsudførelse med kunstig intelligens | Det samlede antal udførelser i løbet af de seneste syv dage. |
| Pålidelighed af funktionsudførelse med kunstig intelligens (%) | Antallet af vellykkede udførelser delt med det samlede antal udførelser i løbet af de seneste syv dage. |
| Maks. CPU (%)| Det maksimale CPU-forbrug af arbejdsbelastningen med kunstig intelligens i løbet af de seneste syv dage. |
| Maks. hukommelse (GB) | Det maksimale hukommelsesforbrug af arbejdsbelastningen med kunstig intelligens i løbet af de seneste syv dage.|
| Maks. ventetid for funktionsudførelse med kunstig intelligens (MS) | Den maksimale tid, der går, før udførelsen startes. |
| Gennemsnitlig ventetid for funktionsudførelse med kunstig intelligens (MS)| Den gennemsnitlige tid, der går, før udførelsen startes. |
| Maks. varighed af funktionsudførelse med kunstig intelligens (MS) | Den maksimale tid til at fuldføre udførelsen. |
| Gennemsnitlig varighed af funktionsudførelse med kunstig intelligens (MS)| Den gennemsnitlige tid til at fuldføre udførelsen. |
| | |

### <a name="reports"></a>Rapporter

Rapporter giver mere detaljerede målepunkter. Hvis du vil se rapporter for kapaciteter, som du er administrator for, skal du under **Rapporter** klikke på **Capacity Metrics i Power BI Premium**. Eller klik på en celle med et målepunkt på dashboardet for at gå til den underliggende rapport. 

Nederst i rapporten er der fem *faner*:

[**Datasæt**](#datasets) – Giver detaljerede målepunkter for tilstanden af Power BI-datasættene i dine kapaciteter.
[**Sideinddelte rapporter**](#paginated-reports) – Giver detaljerede målepunkter for tilstanden af sideinddelte rapporter i dine kapaciteter.
[**Dataflow**](#dataflows) – Giver detaljerede målepunkter for opdatering af dataflow i dine kapaciteter.
[**Kunstig intelligens**](#ai) – Giver detaljerede målepunkter for tilstanden af funktionerne med kunstig intelligens, som bruges i dine kapaciteter.
[**Ressourceforbrug**](#resource-consumption) – Giver detaljerede målepunkter for ressourcer, herunder hukommelse og høj CPU-udnyttelse.
[**Id'er og oplysninger**](#ids-and-info) – Indeholder navne, id'er og ejere for kapaciteter, arbejdsområder og arbejdsbelastninger.

Hver fane åbner en side, hvor du kan filtrere målepunkter efter kapacitet og datointerval. Hvis der ikke er valgt nogen filtre, viser rapporten som standard målepunkter for den seneste uge for alle kapaciteter, der rapporterer målepunkter. 

### <a name="datasets"></a>Datasæt

På siden Datasæt er der forskellige *områder*, som indeholder **Opdateringer**, **Varighed af forespørgsler**, **Ventetider for forespørgsler** og **Datasæt**. Brug knapperne øverst på siden til at navigere til forskellige områder.

#### <a name="refreshes-area"></a>Området Opdateringer

| Rapportsektion | Metrikværdier |
| --- | --- |
| Opdateringer |  Antal i alt: Det samlede antal opdateringer for hvert datasæt.<br>  Pålidelighed: Procentdelen af fuldførte opdateringer for hvert datasæt.<br>  Gennemsnitlig ventetid: Den gennemsnitlige mellemliggende tid mellem det planlagte tidspunkt og starttidspunktet for en opdatering af datasættet i minutter.<br>  Maksimal ventetid: Den maksimale ventetid for datasættet i minutter.<br>  Gennemsnitlig varighed: Den gennemsnitlige varighed af opdateringen af datasættet i minutter.<br>  Maksimal varighed: Varigheden af den længstvarende opdatering af datasættet i minutter. |
| Top 5-datasæt efter Gennemsnitlig varighed (minutter) |  De fem datasæt med den længstvarende gennemsnitlige opdateringsvarighed i minutter. |
| Top 5-datasæt efter Gennemsnitlig ventetid (minutter) |  De fem datasæt med den længstvarende gennemsnitlige opdateringsventetid i minutter. |
| Opdateringsantal og hukommelsesforbrug pr. time (GB) |  Succeser, fejl og hukommelsesforbrug opdelt i buckets af en times varighed rapporteret i UTC-tid. |
| Gennemsnitlig opdateringsventetid pr. time (minutter) |  Den gennemsnitlige opdateringsventetid opdelt i buckets på én time rapporteret i UTC-tid. Flere tilfælde af høje opdateringsventetider kan være tegn på, at kapaciteten snart er brugt op. |
|  |  |

#### <a name="query-durations-area"></a>Område for forespørgselsvarigheder

| Rapportsektion | Metrikværdier |
| --- | --- |
| Forespørgselsvarigheder |  Data i dette afsnit er opdelt i udsnit efter datasæt, arbejdsområde og buckets pr. time for de seneste syv dage.<br>  I alt: Det samlede antal forespørgsler, der er kørt for datasættet.<br>  Gennemsnit: Den gennemsnitlige varighed af forespørgsler for datasættet i millisekunder<br>  Maksimum: Varigheden af den længstvarende forespørgsel i datasættet i millisekunder.|
| Distribution af forespørgselsvarighed |  Histogrammet med forespørgselsvarighed er opdelt i buckets efter forespørgselsvarigheder (i millisekunder) i følgende kategorier: intervaller af < = 30 ms, 30-100 ms, 100-300 ms, 300 ms-1 sek., 1-3 sek., 3-10 sek., 10-30 sek. og > 30 sek. Lange forespørgselsvarigheder og lange ventetider betyder, at kapaciteten er overbelastet. Det kan også betyde, at et enkelt datasæt forårsager problemer, og at der er behov for yderligere undersøgelser. |
| Top 5-datasæt efter Gennemsnitlig varighed |  De fem datasæt med den længstvarende gennemsnitlige forespørgselsvarighed i millisekunder. |
| Distributioner af forespørgselsvarighed pr. time |  Antallet af forespørgsler og gennemsnitlig varighed (i millisekunder) i forhold til hukommelsesforbrug i GB opdelt i buckets på én time rapporteret i UTC-tid. |
| DirectQuery/liveforbindelser (> 80 % udnyttelse) |  Det antal gange, en DirectQuery eller liveforbindelse overskred CPU-udnyttelsen på 80 % opdelt i buckets på én time rapporteret i UTC-tid. |
|  |  |

#### <a name="query-waits-area"></a>Område for ventetider for forespørgsler

| Rapportsektion | Metrikværdier |
| --- | --- |
| Forespørgselsventetider |  Data i dette afsnit er opdelt i udsnit efter datasæt, arbejdsområde og buckets pr. time for de seneste syv dage.<br>  I alt: Det samlede antal forespørgsler, der er kørt for datasættet.<br>  Antal ventende: Antallet af forespørgsler i datasættet, der har ventet på systemressourcer, før udførelsen startes.<br>  Gennemsnit: Den gennemsnitlige ventetid for forespørgsler for datasættet i millisekunder.<br>  Maksimum: Varigheden af den længstventende forespørgsel i datasættet i millisekunder.|
| Top 5 datasæt efter Gennemsnitlig ventetid |  De fem datasæt med den længstvarende gennemsnitlige ventetid inden udførelsen af en forespørgsel i millisekunder. |
| Distribution af ventetid |  Histogrammet med forespørgselsvarighed er opdelt i buckets efter forespørgselsvarigheder (i millisekunder) i følgende kategorier: intervaller af <= 50 ms, 50-100 ms, 100-200 ms, 200-400 ms, 400 ms-1 sek., 1-5 sek. og > 5 sek. |
| Distribution af forespørgselsventetid pr. time |  Mængde af forespørgselsventetid og den gennemsnitlige ventetid (i millisekunder) i forhold til hukommelsesforbrug i GB opdelt i buckets på én time rapporteret i UTC-tid. |
|  |  |

#### <a name="datasets-area"></a>Området Datasæt

| **Rapportafsnit** | **Målepunkter** |
| --- | --- |
| Størrelser af datasæt  |  Maksimumstørrelse: Den maksimale størrelse af datasættet i MB for den viste periode. |
| Antal fjernelser af datasæt |  I alt: Det samlede antal *fjernelser* af datasættet for hver enkelt kapacitet. Når en kapacitet står over for øget hukommelsesforbrug, fjerner noden et eller flere datasæt fra hukommelsen. Datasæt, der er inaktive (uden forespørgsels-/opdateringshandlinger, der udføres i øjeblikket), ryddes først. Derefter er fjernelsesrækkefølgen baseret på en måling af 'mindst brugt for nylig'.|
| Antal indlæste datasæt pr. time |  Antal datasæt, der er indlæst i hukommelsen, i forhold til hukommelsesforbrug i GB opdelt i buckets på én time rapporteret i UTC-tid. |
| Fjernelser af datasæt og hukommelsesforbrug pr. time |  Fjernelser af datasæt i forhold til hukommelsesforbrug i GB opdelt i buckets på én time rapporteret i UTC-tid. |
| Procentdel af forbrugt hukommelse |  Samlet antal aktive datasæt i hukommelsen som en procentdel af den samlede hukommelse. Delta mellem Aktiv og Alle definerer datasæt, der kan fjernes. Vises pr. time for de seneste syv dage. |
|  |  |

### <a name="paginated-reports"></a>Sideinddelte rapporter

| **Rapportafsnit** | **Målepunkter** |
| --- | --- |
| Samlet forbrug |  Visninger i alt: Antallet af gange, som rapporten er blevet set af brugere.<br>  Rækkeantal: Antallet af rækker med data i rapporten.<br>  Hentning (gns.): Den gennemsnitlige mængde tid, det tager at hente data til rapporten, i millisekunder. Lange varigheder kan være et tegn på langsomme forespørgsler eller andre datakildeproblemer. <br>  Behandling (gns.): Den gennemsnitlige mængde tid, det tager at behandle dataene til rapporten, i millisekunder.<br> Gengivelse (gns.): Den gennemsnitlige mængde tid, det tager at gengive en rapport i browseren, i millisekunder.<br>  Tid i alt: Den mængde tid, det tager for alle faserne i rapporten, i millisekunder. |
| Top 5-rapporter efter Gennemsnitlig datahentningstid |  De fem rapporter med den længstvarende gennemsnitlige datahentningstid i millisekunder. |
| Top 5-rapporter efter Gennemsnitlig rapportbehandlingstid |  De fem rapporter med den længstvarende gennemsnitlige rapportbehandlingstid i millisekunder. |
| Resultater pr. time |  Succeser, fejl og hukommelsesforbrug opdelt i buckets på én time rapporteret i UTC-tid. |
| Varigheder pr. time |  Datahentning i forhold til behandlings- og gengivelsestid opdelt i buckets på én time rapporteret i UTC-tid. |
|  |  |

### <a name="dataflows"></a>Dataflow

| **Rapportafsnit** | **Målepunkter** |
| --- | --- |
| Opdateringer |  I alt: Det samlede antal opdateringer for hvert dataflow.<br>  Pålidelighed: Procentdelen af fuldførte opdateringer for hvert dataflow.<br>  Gennemsnitlig ventetid: Den gennemsnitlige mellemliggende tid mellem det planlagte tidspunkt og starttidspunktet for en opdatering af dataflowet i minutter.<br>  Maksimal ventetid: Den maksimale ventetid for dataflowet i minutter.<br>  Gennemsnitlig varighed: Den gennemsnitlige varighed af opdateringen af dataflowet i minutter.<br>  Maksimal varighed: Varigheden af den længstvarende opdatering af dataflowet i minutter. |
| Top 5-dataflow efter Gennemsnitlig opdateringsvarighed |  De fem dataflow med den længstvarende gennemsnitlige opdateringsvarighed i minutter. |
| Top 5-dataflow efter Gennemsnitlig ventetid |  De fem dataflow med den længstvarende gennemsnitlige opdateringsventetid i minutter. |
| Gennemsnitlige opdateringsventetider pr. time |  Den gennemsnitlige opdateringsventetid opdelt i buckets på én time rapporteret i UTC-tid. Flere tilfælde af høje opdateringsventetider kan være tegn på, at kapaciteten snart er brugt op. |
| Opdateringsantal og hukommelsesforbrug pr. time |  Succeser, fejl og hukommelsesforbrug opdelt i buckets på én time rapporteret i UTC-tid. |
|  |  |

### <a name="ai"></a>AI

| **Rapportafsnit** | **Målepunkter** |
| --- | --- |
| Hukommelsesforbrug med kunstig intelligens | Hukommelsesforbrug i GB opdelt i buckets på én time rapporteret i UTC-tid. |
| Funktionsudførelse med kunstig intelligens og gennemsnitlig ventetid pr. time | Fuldførelser med kunstig intelligens og gennemsnitlig ventetid i millisekunder opdelt i buckets på én time rapporteret i UTC-tid. |
| Samlet forbrug | Samlet antal: Antallet af funktioner med kunstig intelligens i et arbejdsområde eller dataflow. <br> Pålidelighed af system: Procentdelen af fuldførte udførelser.<br> Gns. ventetid: Den gennemsnitlige mellemliggende tid mellem det planlagte tidspunkt og starttidspunktet for en udførelse i millisekunder.<br> Maksimal ventetid: Maksimal ventetid i millisekunder.<br> Gns. varighed: Den gennemsnitlige varighed af en udførelse i millisekunder.<br> Maksimal varighed: Varigheden af den længstvarende forespørgsel i millisekunder.<br> Gns. samlet størrelse: Den gennemsnitlige størrelse i byte af input- og outputdata for funktionen med kunstig intelligens. |
| | |

### <a name="resource-consumption"></a>Ressourceforbrug

| **Rapportafsnit** | **Målepunkter** |
| --- | --- |
| CPU-forbrug |  Maksimalt CPU-forbrug i timen efter arbejdsbelastning som en procentdel af den samlede CPU-kapacitet. Vises pr. time for de seneste syv dage. |
| Hukommelsesforbrug |  Det maksimale hukommelsesforbrug i timen i GB efter arbejdsbelastning (hele linjer) overlejret af grænser for arbejdsbelastning (stiplede linjer). Vises pr. time for de seneste syv dage. |
|  |  |

### <a name="ids-and-info"></a>Id'er og Oplysninger

Fanen **Id'er og oplysninger** indeholder områder for **Kapaciteter**, **Arbejdsområder**, **Datasæt**, **Sideinddelte rapporter** og **Dataflow**.

#### <a name="capacities-area"></a>Området Kapaciteter

| Rapportsektion | Metrikværdier |
| --- | --- |
| Oplysninger om SKU og arbejdsbelastning | Indstillinger for SKU og arbejdsbelastninger for kapaciteten. |
| Administratorer | Navnene på administratorerne for kapaciteten. |
|||

#### <a name="workspaces-area"></a>Området Arbejdsområder

| Rapportsektion | Metrikværdier |
| --- | --- |
| Arbejdsområder | Navne og id'er for alle arbejdsområder. |
|||

#### <a name="datasets-area"></a>Området Datasæt

| Rapportsektion | Metrikværdier |
| --- | --- |
| Datasæt | Navne og id'er for arbejdsområder for alle datasæt. |
|||

#### <a name="paginated-reports-area"></a>Området Sideinddelte rapporter

| Rapportsektion | Metrikværdier |
| --- | --- |
| Sideinddelte rapporter | Navne, navne på arbejdsområder og id'er for alle sideinddelte rapporter. |
|||

#### <a name="dataflows-area"></a>Området Dataflow

| Rapportsektion | Metrikværdier |
| --- | --- |
| Dataflow | Navne på dataflow og arbejdsområder samt id'er for alle dataflow. |
|||

## <a name="monitor-power-bi-embedded-capacity"></a>Overvåg Power BI Embedded-kapacitet

Du kan bruge programmet Power BI Premium Capacity Metrics til at overvåge *A SKU*-kapaciteter i Power BI Embedded. Disse kapaciteter vises i rapporten, hvis du er administrator af kapaciteten. Men opdatering af rapporten mislykkes, medmindre du tildeler visse tilladelser til Power BI på dine A SKU'er:

1. Åbn din kapacitet på Azure-portalen.

1. Klik på **Adgangskontrol (IAM)** , og føj derefter appen **Power BI Premium** til rollen Læser. Hvis du ikke kan finde appen ved hjælp af navnet, kan du også tilføje den ved hjælp af klientidentifikatoren: `cb4dc29f-0bf4-402a-8b30-7511498ed654`.

    ![Tilladelser til Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Du kan overvåge Power BI Embedded-kapacitetsforbrug i appen eller på Azure-portalen, men ikke på Power BI-administrationsportalen.


## <a name="next-steps"></a>Næste trin

> [!div class="nextstepaction"]
> [Optimering af kapaciteter i Power BI Premium](service-premium-capacity-optimize.md)
