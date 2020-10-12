---
title: Appen Power BI Premium Metrics
description: Få mere at vide om, hvordan du bruger appen Power BI Premium Metrics til at administrere og foretage fejlfinding af din Premium-kapacitet.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 05/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: ddaafaf175e2cb083e8e8eb494c156f0e9de8e0f
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91633138"
---
# <a name="power-bi-premium-metrics-app"></a>Appen Power BI Premium Metrics

Du kan bruge appen **Power BI Premium Metrics** til at administrere dit Power BI Premium-abonnements tilstand og kapacitet. Administratorer kan bruge appens **Capacity Health Center** til at se og interagere med indikatorer, der overvåger tilstanden af deres Premium-kapacitet. Metrics-appen består af landingssiden, der kaldes **Capacity Health Center**, og detaljer om tre vigtige målepunkter:

* Aktiv hukommelse
* Forespørgselsventetider
* Opdateringsventetider

![Appen Power BI Premium Metrics](media/service-premium-metrics-app/premium-metrics-app-00.png)

I de følgende afsnit beskrives landingssiden og de tre målepunktssider i en rapport i detaljer. 

> [!IMPORTANT]
> Hvis der er et højt forbrug af ressourcer i din Power BI Premium-kapacitet, hvilket medfører problemer med ydeevne eller pålidelighed, kan du modtage notifikationer via mail for at identificere og løse problemet. Dette kan være en strømlinet metode til fejlfinding af overbelastede kapaciteter. Se [notifikationer om kapacitet og pålidelighed](service-interruption-notifications.md#capacity-and-reliability-notifications) for at få flere oplysninger.



## <a name="premium-capacity-health-center"></a>Premium Capacity Health Center

Når du åbner **Power BI Premium Metrics-appen**, får du vist **Capacity Health Center**, der giver en oversigt over din Power BI Premium-kapacitets tilstand.

![Capacity Health Center i Premium Metrics-appen](media/service-premium-metrics-app/premium-metrics-app-01.png)

Fra landingssiden kan du vælge den Power BI Premium-kapacitet, du vil have vist, i tilfælde af at din organisation har flere Premium-abonnementer. Hvis du vil have vist en Premium-kapacitet, skal du vælge rullemenuen øverst på siden med navnet **Vælg en kapacitet for at se dens målepunkter**.

De tre KPI'er viser den aktuelle tilstand for den valgte Premium-kapacitet baseret på de indstillinger, der er anvendt for hver af de tre KPI'er. 

Hvis du vil have vist specifikke oplysninger om de enkelte KPI'er, skal du vælge knappen **Udforsk** nederst i den pågældende KPI, hvorefter den detaljerede side vises. I de følgende afsnit beskrives de enkelte KPI'er og de oplysninger, som siden indeholder.

## <a name="the-active-memory-metric"></a>Målepunktet for den aktive hukommelse

Målepunktet for den **aktive hukommelse** er en del af *kapacitetsplanlægningskategorien* og er en god tilstandsindikator til at vurdere din kapacitets ressourceforbrug, så du kan justere kapaciteten efter behov og planlægge kapacitetens størrelse. 

![KPI for aktiv hukommelse](media/service-premium-metrics-app/premium-metrics-app-02.png)

**Aktiv hukommelses** er den hukommelse, der bruges til at behandle de datasæt, der er i brug i øjeblikket, og som derfor ikke fjernes, når der er behov for hukommelse. Målepunktet for den aktive hukommelse angiver, om din kapacitet kan håndtere ekstra belastning, eller om den allerede er i nærheden af eller over kapaciteten, samt kapacitetens aktuelle belastning. Den aktive hukommelse, der bruges i øjeblikket, betyder, at der er mindre hukommelse til at understøtte yderligere opdateringer og forespørgsler. 

KPI'en for den **aktive hukommelses** måler, hvor mange gange kapacitetens aktive hukommelse har overskredet 70 %-tærsklen på 50 gange (markøren er angivet til 30 % for de seneste syv dage), hvilket angiver, at kapaciteten nærmer sig et punkt, hvor brugerne kan få problemer med ydeevnen i forbindelse med forespørgsler.

Den visuelle måleenhed, der vises i dette afsnit, viser, at kapaciteten i de seneste syv dage, fra det tidspunkt hvor rapporten sidst blev opdateret, har overskredet 70 %-tærsklen fire gange, opdelt i intervaller på en time. Den maksimale værdi for måleren, 168, repræsenterer de seneste syv dage i timer.

Hvis du vil vide mere om detaljerne i KPI'en for den aktive hukommelse, skal du klikke på knappen **Udforsk** for at få vist en rapportside, der indeholder specifikke visualiseringer af dens detaljerede målepunkter, sammen med en fejlfindingsvejledning, der vises i højre kolonne på siden. 

Der er to scenarier, som er forklaret, og som du kan få vist på rapportsiden ved at vælge **Scenarie 1** eller **Scenarie 2** på siden. 

![Skærmbillede, der viser siden med detaljer om aktiv hukommelse.](media/service-premium-metrics-app/premium-metrics-app-03.png)

De fejlfindingsvejledninger, der er knyttet til hvert scenarie, indeholder detaljerede forklaringer af, hvad målepunkterne betyder, så du bedre kan forstå kapacitetens tilstand, og hvad du kan gøre for at afhjælpe eventuelle problemer. 

Disse to scenarier er beskrevet i følgende afsnit.

### <a name="scenario-one---current-load-is-too-high"></a>1\. scenarie – den aktuelle belastning er for høj 

Du kan finde ud af, om der er tilstrækkelig hukommelse til kapaciteten til at fuldføre dens arbejdsbelastninger, i den første visualisering på siden: **A: Procentdel af forbrugt hukommelse**, som viser den hukommelse, der bruges af datasæt, der behandles aktivt, og som derfor ikke kan fjernes.

Alarmtærsklen, som er den røde stiplede linje, markerer hændelser med et hukommelsesforbrug på 90 %.

Advarselstærsklen, som er den gule stiplede linje, markerer hændelser med et hukommelsesforbrug på 70 %. 

Den sorte stiplede linje angiver tendenslinjen for hukommelsesforbruget baseret på den aktuelle kapacitets hukommelsesforbrug i løbet af grafens tidslinje.

Høj forekomst af aktiv hukommelse over alarmtærsklen (den røde stiplede linje) og hukommelsestendenslinjen (den sorte stiplede linje) angiver en belastning af hukommelseskapacitetsforbruget, hvilket kan forhindre yderligere datasæt i at blive indlæst i hukommelsen i den pågældende periode. 

Når du ser sådanne tilfælde, bør du se nærmere på de andre diagrammer på siden for bedre at finde ud af, hvilken og hvorfor så meget hukommelse ofte forbruges, og hvordan du justerer balancen eller optimerer den, eller skalerer kapaciteten op, hvis det er nødvendigt. 

Den anden visualisering på siden **B: Aktive datasæt, der indlæses pr. time** viser antallet af det maksimale antal datasæt, der blev indlæst i hukommelsen, i intervaller på en time. 

Den tredje visualisering, **C: Grunden til, at datasæt er i hukommelsen** er en tabel, der viser datasættet efter arbejdsområdenavn, navn på datasæt, ukomprimeret størrelse af datasæt i hukommelsen, og som forklarer årsagen til, at datasættet indlæses i hukommelsen (f.eks. at det opdateres eller forespørges eller begge dele).

#### <a name="diagnosing-scenario-one"></a>Diagnosticering af det første scenarie

En konsekvent høj udnyttelse af den aktive hukommelse kan resultere i, at datasæt, der bruges aktivt, fjernes, eller forhindre, at nye datasæt indlæses. Følgende trin kan hjælpe dig med at diagnosticere problemer

1. Tag et kig på diagram *A: Procentdel af forbrugt hukommelse*

    **a.** Hvis diagram A viser, at alarmtærskelværdien (90 %) overskrides mange gange og/eller i flere timer i træk, er din kapacitet ved at løbe tør for hukommelse for ofte. I diagrammet nedenfor kan vi se, at advarselstærsklen (70 %) blev overskredet fire gange.

    ![Diagram a, procentdel af forbrugt hukommelse](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** Diagrammet med titlen *B: Aktive datasæt, der indlæses pr. time* viser det maksimale antal entydige datasæt, der indlæses i hukommelsen i intervaller på en time. Hvis du vælger en søjle i visualiseringen, filtreres årsagerne til, hvorfor datasættene er i hukommelsesvisualiseringen.  

    ![Diagram b, brugt hukommelse pr. time](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** Se tabellen **Grunden til, at datasæt er i hukommelsen** for at få vist en liste over de datasæt, der er indlæst i hukommelsen. Sortér efter *Datasætstørrelse (MB)* for at fremhæve de datasæt, der bruger mest hukommelse. Kapacitetshandlinger er klassificeret som enten *interaktive* eller *baggrundshandlinger*. Interaktive handlinger omfatter gengivelse af anmodninger og svar på brugerinteraktioner (filtrering, spørgsmål og svar-forespørgsel, osv.). Det samlede antal forespørgsler og samlede antal opdateringer giver en idé om, hvorvidt der er tunge (forespørgsler) eller interaktive handlinger eller baggrundshandlinger (opdateringer), der udføres på datasættet. Det er vigtigt at forstå, at interaktive handlinger altid går forud for handlinger i baggrunden for at sikre den bedst mulige brugeroplevelse. Hvis der ikke er tilstrækkelige ressourcer, føjes handlinger i baggrunden til en kø og bliver behandlet, når ressourcerne frigøres. Handlinger i baggrunden, f.eks. datasætopdateringer og AI-funktioner, kan stoppes midt i en proces af Power BI-tjenesten og føjes til en kø.
    
    ![tabel c, liste over datasæt](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>Løsninger til første scenarie

Du kan benytte følgende fremgangsmåde til at afhjælpe de problemer, der er knyttet til det første scenarie:

1. **Skaler kapaciteten op** – opskalering af kapaciteten til den næste SKU giver to gange så meget hukommelse i forhold til den aktuelle SKU, hvilket vil lette den belastning, der i øjeblikket er på kapaciteten.

2. **Flyt datasæt til en anden kapacitet** – hvis du har endnu en kapacitet med mere hukommelse, kan du flytte de arbejdsområder, der indeholder de store datasæt, til denne kapacitet.


### <a name="scenario-two---future-load-will-exceed-limits"></a>Andet scenarie – den fremtidige belastning vil overskride grænserne

Du kan finde ud af, om der er tilstrækkelig hukommelse til kapaciteten til at fuldføre dens arbejdsbelastninger, i visualiseringen **A: Procentdel af forbrugt hukommelse** øverst på siden, som viser den hukommelse, der bruges af datasæt, der behandles aktivt, og som derfor ikke kan fjernes. Den sorte stiplede linje fremhæver tendenserne. I en kapacitet hvor hukommelsen belastes, viser den samme visualisering tydeligt, at tendenslinjen for hukommelse (den sorte stiplede linje) er i opadgående retning, hvilket betyder, at den muligvis forhindrer, at ekstra datasæt indlæses i hukommelsen på det pågældende tidspunkt. Tendenslinjen, den sorte stiplede linje, viser væksttendensen baseret på de syv dage med data. 

![Skærmbillede, der viser siden med detaljer om aktiv hukommelse for scenarie to.](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>Diagnosticering af det andet scenarie

Hvis du vil diagnosticere det andet scenarie, skal du finde ud af, om tendenslinjen viser en opadgående tendens i forhold til advarsels- eller alarmtærsklerne. 

1. Overvej **Diagram A:**

    ![Diagram over forbrugt hukommelse](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** Hvis diagrammet viser en opadgående hældning, betyder det, at hukommelsesforbruget er steget i løbet af de seneste syv dage.

    **b.** Med udgangspunkt i den aktuelle stigning skal du forudsige, hvornår tendenslinjen krydser advarselstærsklen (den gule stiplede linje).

    **c.** Fortsæt med at tjekke tendenslinjen mindst hvert andet døgn for at se, om tendensen fortsætter.

#### <a name="remedies-for-scenario-two"></a>Løsninger til andet scenarie

Du kan benytte følgende fremgangsmåde til at afhjælpe de problemer, der er knyttet til det andet scenarie:

1. **Skaler kapaciteten op** – opskalering af kapaciteten til den næste SKU giver to gange så meget hukommelse i forhold til den aktuelle SKU, hvilket vil lette den belastning, der i øjeblikket er på kapaciteten.

2. **Flyt datasæt til en anden kapacitet** – hvis du har endnu en kapacitet med mere hukommelse, kan du flytte de arbejdsområder, der indeholder de store datasæt, til denne kapacitet.


## <a name="the-query-waits-metric"></a>Målepunktet for forespørgselsventetider

**Forespørgselskategorien** angiver, om brugerne kan opleve, at visualiseringer i rapporter er længe om at svare eller slet ikke svarer. **Forespørgselsventetider** er den tid, det tager for forespørgslen at starte udførelsen, fra det tidspunkt hvor den blev udløst. Denne KPI måler, om 25 % eller mere af den valgte kapacitets forespørgsler venter 100 millisekunder eller længere, før de udføres. Der opstår ventetider for forespørgsler, når der ikke er tilstrækkelig tilgængelig CPU til at køre alle ventende forespørgsler. 

![Måler af forespørgselsventetider](media/service-premium-metrics-app/premium-metrics-app-09.png)

Måleren i denne visualisering viser, at i de seneste syv dage, fra det tidspunkt hvor rapporten sidst blev opdateret, ventede 17,32 % af forespørgslerne mere end 100 millisekunder. 

Hvis du vil have flere detaljer om KPI'en Forespørgselsventetider at vide, skal du klikke på knappen **Udforsk** for at få vist en rapportside med en visualisering af relevante målepunkter og en fejlfindingsvejledning i højre kolonne på siden. Fejlfindingsvejledningen indeholder to scenarier, som hver især giver detaljerede forklaringer til målepunktet, kapacitetens tilstand og det, du kan gøre for at afhjælpe problemet.

Vi gennemgår hvert scenarie med forespørgselsventetider i følgende afsnit.

### <a name="scenario-one---long-running-queries-consume-cpu"></a>Første scenarie – langvarige forespørgsler forbruger CPU

I det første scenarie bruger langvarige forespørgsler for meget CPU. 

Du kan undersøge, om dårlig rapportydeevne skyldes en overbelastet kapacitet eller et dårligt udformet datasæt eller en dårligt udformet rapport. Der er flere årsager til, at en forespørgsel kan køre i en længere periode, hvilket er defineret ved, at det tager mere end 10 sekunder at afslutte udførelsen. Datasæts størrelse og kompleksitet samt forespørgslens kompleksitet er blot nogle få eksempler på, hvad der kan medføre en langvarig forespørgsel. 

På rapportsiden vises følgende visualiseringer: 

* Den øverste tabel, der hedder **A: Lange ventetider**, viser datasæt med forespørgsler, der venter. 
* **B: Distribution af lange ventetider pr. time** viser fordelingen af lange ventetider. 
* Diagrammet med titlen **C: Antallet af langvarige forespørgsler pr. time** viser antallet af langvarige forespørgsler, der blev udført, opdelt pr. time.
* Den sidste visualisering, tabel **D: Langvarige forespørgsler**, viser en liste over de langvarige forespørgsler og deres statistik.

![Detaljeside om forespørgselsventetider](media/service-premium-metrics-app/premium-metrics-app-10.png)

Der er trin, du kan udføre for at diagnosticere og afhjælpe problemer med ventetider for forespørgsler, som bliver beskrevet nedenfor.

#### <a name="diagnosing-scenario-one"></a>Diagnosticering af det første scenarie

Først kan du se, om langvarige forespørgsler finder sted, når dine forespørgsler venter. 

![Tabel over lange ventetider](media/service-premium-metrics-app/premium-metrics-app-11.png)

Se **Diagram B**, der viser antallet af forespørgsler, der venter mere end 100 ms. Vælg en af kolonnerne, der viser et højt antal af forespørgselsventetider.

![Distribution af lang ventetid](media/service-premium-metrics-app/premium-metrics-app-12.png)

Når du klikker på en kolonne med et højt antal ventetider, er **Diagram C** filtreret for at vise antallet af langvarige forespørgsler, der kørte i den pågældende periode. Dette er vist på følgende billede:

![Antal af langvarige forespørgsler pr. time](media/service-premium-metrics-app/premium-metrics-app-13.png)

**Diagram D** filtreres desuden også for at vise de forespørgsler, der var langvarige i den valgte tidsperiode.

![Lange forespørgsler](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>Løsninger til første scenarie

Her er de trin, du kan udføre for at løse problemer fra det første scenarie:

1. **Kør PerfAnalyzer for at optimere rapporter og datasæt** – effektivitetsanalysen for rapporter viser effekten af alle interaktioner på en side, herunder hvor lang tid det tager at opdatere den enkelte visualisering, og hvor tiden bruges.

2. **Opskalering af kapaciteten** – opskalering af kapaciteten til den næste SKU, resulterer i dobbelt så meget CPU, hvilket letter den CPU-belastning, der kan få forespørgslerne til at køre i længere tid.

3. **Flyt datasæt til en anden kapacitet** – hvis du har endnu en kapacitet med mere CPU, kan du flytte de arbejdsområder, der indeholder datasættene med de ventende forespørgsler, til denne kapacitet.

### <a name="scenario-two---too-many-queries"></a>Andet scenarie – for mange forespørgsler

I det andet scenarie udføres der for mange forespørgsler.

Når antallet af forespørgsler, der skal udføres, overskrider kapacitetens grænser, placeres forespørgsler i en kø, indtil der er ressourcer tilgængelige til at udføre dem. Hvis størrelsen på køen bliver for stor, kan forespørgsler i den pågældende kø ende med at vente længere end 100 millisekunder.

![Andet scenarie](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>Diagnosticering af det andet scenarie

I **tabel A** skal du vælge et datasæt, der har en høj procentdel af ventetid.

![Tabel over et højt antal ventetider](media/service-premium-metrics-app/premium-metrics-app-16.png)

Når du har valgt et datasæt med højt antal ventetider, filtreres **Diagram B** til at vise distributionen af ventetiden for forespørgslerne i dette datasæt i løbet af de seneste syv dage. Derefter skal du vælge en af kolonnerne i **Diagram B**.

![diagram over distributionen af det høje antal ventetider pr. time](media/service-premium-metrics-app/premium-metrics-app-17.png)

**Diagram C** filtreres derefter til at vise køens længde på det tidspunkt, der er valgt i diagram B.

![længde på forespørgselskø pr. time](media/service-premium-metrics-app/premium-metrics-app-18.png)

Hvis længden af køen har overskredet tærsklen på 20, er det sandsynligt, at forespørgslerne i det valgte datasæt forsinkes, fordi antallet af forespørgsler, der forsøger at køre på samme tid, er for højt.

![Tabel over udførelsen af forespørgsler](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>Løsninger til andet scenarie

Du kan benytte følgende fremgangsmåde til at afhjælpe de problemer, der er knyttet til det andet scenarie:

1. **Skaler kapaciteten op** – opskalering af kapaciteten til den næste SKU giver to gange så meget hukommelse i forhold til den aktuelle SKU, hvilket vil lette den belastning, der i øjeblikket er på kapaciteten.

2. **Flyt datasæt til en anden kapacitet** – hvis du har endnu en kapacitet med mere hukommelse, kan du flytte de arbejdsområder, der indeholder de store datasæt, til denne kapacitet.


## <a name="the-refresh-waits-metric"></a>Målepunktet for opdateringsventetider

Målepunktet for **opdateringsventetider** giver indsigt i, hvornår brugerne kan opleve at få rapportdata, der er for gamle. **Opdateringsventetider** er den tid en given opdatering ventede med at blive udført, fra det tidspunkt den blev udløst efter behov eller planlagt til at køre. Denne KPI måler, om 10 % eller mere af de ventende opdateringsanmodninger venter 10 minutter eller længere. Det sker generelt, hvis der ikke er tilstrækkelig ledig hukommelse eller CPU.

![Måler af opdateringsventetider](media/service-premium-metrics-app/premium-metrics-app-20.png)

Denne måler viser, at i de seneste syv dage fra den seneste opdateringsrapport ventede 3,18 % af opdateringerne mere end 10 minutter. 

Du kan få flere detaljer om KPI'en **Opdateringsventetider** ved at klikke på knappen **Udforsk**, der viser en side med målepunkter og en fejlfindingsvejledning i den højre kolonne på rapportsiden. Vejledningen indeholder detaljerede forklaringer af de målepunkter, der er på siden, og hjælper dig med at forstå kapacitetens tilstand, og hvad du kan gøre for at afhjælpe eventuelle problemer.

![Udforskning af målepunkterne for opdateringsventetider](media/service-premium-metrics-app/premium-metrics-app-21.png)

Vi har gennemgået to scenarier, som du kan få vist på rapportsiden ved at vælge 1. scenarie eller 2. scenarie på siden. Vi gennemgår hvert scenarie i følgende afsnit.

### <a name="scenario-one---not-enough-memory"></a>Første scenarie – ikke tilstrækkelig hukommelse

I det første scenarie er der ikke tilstrækkelig ledig hukommelse til at indlæse datasættet. Der er to situationer, der medfører, at en opdatering begrænses i situationer med utilstrækkelig hukommelse:

1. Der er ikke tilstrækkelig hukommelse til at indlæse datasættet.
2. Opdateringen blev annulleret på grund af en handling med en højere prioritet. 

Prioriteten for indlæsning af datasæt er følgende:

1. Interaktiv forespørgsel
2. Forespørgsel efter behov
3. Planlagt opdatering

Hvis der ikke er tilstrækkelig hukommelse til at indlæse et datasæt til en interaktiv forespørgsel, stoppes planlagte opdateringer, og deres datasæt fjernes, indtil der bliver tilstrækkelig hukommelse til rådighed. Hvis det ikke frigør tilstrækkelig hukommelse, stoppes opdateringer efter behov, og deres datasæt fjernes.

#### <a name="diagnosing-scenario-one"></a>Diagnosticering af det første scenarie

Du diagnosticerer det første scenarie ved først at finde ud af, om begrænsningen skyldes utilstrækkelig hukommelse. Du kan benytte følgende fremgangsmåde.

1. Vælg det datasæt, du er interesseret i, i **tabel A** ved at klikke på det: 

    ![Tabel A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Når et datasæt vælges i **tabel A**, filtreres **diagram B** for at vise, hvornår ventetiden fandt sted.

    ![Diagram B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. **Diagram C** filtreres derefter for at vise eventuelle begrænsninger, hvilket forklares i næste trin. 

2. Kig på resultaterne i **diagram C**, som nu er filtreret. Hvis diagrammet viser, at der er opstået en hukommelsesbegrænsning på de tidspunkter, hvor datasættet ventede, ventede datasættet på grund af problemer med manglende hukommelse.

    ![Diagram C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Til sidst skal du tjekke **diagram D**, som viser de typer opdateringer, der fandt sted, planlagt i forhold til efter behov. Eventuelle opdateringer efter behov, der udføres samtidig, kan være årsagen til begrænsningen.

    ![Diagram D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>Løsninger til første scenarie

Du kan benytte følgende fremgangsmåde til at afhjælpe de problemer, der er knyttet til det første scenarie:

1. **Skaler kapaciteten op** – opskalering af kapaciteten til den næste SKU giver to gange så meget hukommelse i forhold til den aktuelle SKU, hvilket vil lette den belastning, der i øjeblikket er på hukommelsen og CPU'en.

2. **Flyt datasæt til en anden kapacitet** – hvis ventetiden skyldes belastning af hukommelsen, og du har endnu en kapacitet med mere hukommelse, kan du flytte de arbejdsområder, der indeholder de ventende datasæt til denne kapacitet.

3. **Fordel planlagte opdateringer** – fordeling af opdateringerne hjælper med at undgå, at der er for mange opdateringer, der forsøger at køre samtidig.



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>Andet scenarie – ikke nok CPU til opdatering

I det andet scenarie er der ikke tilstrækkelig tilgængelig CPU til at udføre opdateringen. 

I forbindelse med dedikerede kapaciteter begrænser Power BI antallet af opdateringer, der kan ske samtidig. Dette tal svarer til antallet af back end-kerner x 1,5. En dedikeret P1-kapacitet, som har fire back end-kerner, kan f.eks. køre seks opdateringer samtidig. Når det maksimale antal samtidige opdateringer er nået, vil andre opdateringer vente, indtil en opdatering er fuldført.

![Andet scenarie for opdatering](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>Diagnosticering af det andet scenarie

Når du skal diagnosticere det andet scenarie, skal du først afgøre, om begrænsningen skyldes, at du løber ind i den maksimale samtidighed for opdateringer. Du kan benytte følgende fremgangsmåde.

1. Vælg det datasæt, du er interesseret i, i **tabel A** ved at klikke på det: 

    ![Tabel A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Når et datasæt vælges i **tabel A**, filtreres **diagram B** for at vise, hvornår ventetiden fandt sted.

    ![Diagram B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. **Diagram C** filtreres derefter for at vise eventuelle begrænsninger, hvilket forklares i næste trin. 

2. Kig på resultaterne i **diagram C**, som nu er filtreret. Hvis diagrammet viser *maksimal samtidighed* på de tidspunkter, hvor datasættet ventede, ventede datasættet på grund af problemer med utilstrækkelig CPU.

    ![Diagram C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Til sidst skal du tjekke **diagram D**, som viser de typer opdateringer, der fandt sted, planlagt i forhold til efter behov. Eventuelle opdateringer efter behov, der udføres samtidig, kan være årsagen til begrænsningen.

    ![Diagram D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>Løsninger til andet scenarie

1. **Skaler kapaciteten op** – opskalering af kapaciteten til den næste SKU giver dobbelt så meget hukommelse i forhold til den aktuelle SKU og dobbelt så mange samtidige opdateringer i forhold til den aktuelle SKU, hvilket vil lette den belastning, der i øjeblikket er på hukommelsen og CPU'en i kapaciteten.

2. **Flyt datasæt til en anden kapacitet** – hvis ventetiderne skyldes, at den maksimale samtidighed nås, og du har endnu en kapacitet med tilgængelig samtidighed, kan du flytte de arbejdsområder, der indeholder de ventende datasæt, til denne kapacitet.

3. **Fordel planlagte opdateringer** – fordeling af opdateringerne hjælper med at undgå, at der er for mange opdateringer, der forsøger at køre samtidig.



## <a name="next-steps"></a>Næste trin

* [Hvad er Power BI Premium?](service-premium-what-is.md)
* [Hvidbog om Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
* [Hvidbog om planlægning af en Power BI Enterprise-installation](https://aka.ms/pbienterprisedeploy)
* [Aktivering af den udvidede Pro-prøveversion](../fundamentals/service-self-service-signup-for-power-bi.md)
* [Ofte stillede spørgsmål om Power BI Embedded](../developer/embedded/embedded-faq.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
