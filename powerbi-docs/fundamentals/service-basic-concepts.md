---
title: Grundlæggende begreber for designere i Power BI-tjenesten
description: kapaciteter i Power BI-tjenesten, arbejdsområder, dashboards, rapporter, projektmapper, datasæt og dataflow.
author: mihart
ms.author: mihart
manager: kfollis
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: conceptual
ms.date: 11/14/2019
LocalizationGroup: Get started
ms.openlocfilehash: d61ed128827572198e24bb8f31e190f328e273ff
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687564"
---
# <a name="basic-concepts-for-designers-in-the-power-bi-service"></a>Grundlæggende begreber for designere i Power BI-tjenesten

Formålet med denne artikel er at give dig indblik i Power BI-tjenesten: De forskellige elementer, hvordan de arbejder sammen, og hvordan du kan arbejde med dem. Du får muligvis mere ud af den, hvis du allerede har [tilmeldt dig Power BI-tjenesten](service-self-service-signup-for-power-bi.md) og [tilføjet nogle data](../connect-data/service-get-data.md). Som designer starter du normalt en typisk arbejdsgang med at oprette rapporter i Power BI Desktop. Derefter publicerer du dem til Power BI-tjenesten, hvor du kan fortsætte med at ændre dem. Du kan også oprette dashboards baseret på dine rapporter i Power BI-tjenesten. 

Hvis du ikke har dine egne rapporter endnu, kan du i forbindelse med denne artikel installere et af [Power BI-eksemplerne](../create-reports/sample-datasets.md).

![Diagram, der viser et skærmbillede af Power BI-tjenestens startskærm i en browser med nummererede områder angivet nedenfor.](media/service-basic-concepts/power-bi-home-screen.png)

Når du åbner Power BI-tjenesten i en browser, begynder du på startskærmen. Her er de elementer, du kan se:

1. Navigationsrude
2. Microsoft 365-programstarter
3. Power BI-startknap
4. Ikonknapper, herunder indstillinger, hjælp og feedback
5. Søgefelt
6. Foretrukne og hyppige dashboards, rapporter og arbejdsområder
7. Seneste dashboards, rapporter og arbejdsområder
8. Dine arbejdsområder

Du og dine slutbrugere af dine rapporter og dashboards har den samme startoplevelse i Power BI-tjenesten i en browser.

Vi vil gå i dybden med disse funktioner senere, men lad os først se på nogle Power BI-begreber. Eller måske vil du se denne video først.  I videoen gennemgår Will de grundlæggende begreber og giver en præsentation af Power BI-tjenesten.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>


## <a name="power-bi-concepts"></a>Power BI-begreber
De fem overordnede komponenter i Power BI er: *dashboards*, *rapporter*, *projektmapper*, *datasæt* og *dataflow*. De er organiseret i *arbejdsområder*, og de er oprettet på *kapaciteter*.  Det er vigtigt at forstå kapaciteter og arbejdsområder, før vi går videre til de fem overordnede komponenter, så lad os starte der.

## <a name="capacities"></a>Kapaciteter
Kapaciteter er et kernekoncept i Power BI og repræsenterer et sæt ressourcer (lager, processor og hukommelse), der bruges til at hoste og levere dit Power BI-indhold. Kapaciteter er enten _delte_ eller _dedikerede_. En delt kapacitet er delt med andre Microsoft-kunder, mens en dedikeret kapacitet kun er til en enkelt kunde. Dedikerede kapaciteter kræver et [abonnement](../admin/service-premium-what-is.md) og er beskrevet fuldt ud i artiklen [Administration af Premium-kapaciteter](../admin/service-premium-capacity-manage.md).

Som standard oprettes arbejdsområder på en delt kapacitet. I en delt kapacitet kører dine arbejdsbelastninger på databehandlingsressourcer, der deles med andre kunder. Eftersom kapaciteten skal dele ressourcerne, pålægges begrænsninger for at sikre "fair play", f.eks. den maksimale modelstørrelse (1 GB) og den maksimale daglige opdateringshyppighed (otte gange pr. dag).

## <a name="workspaces"></a>Arbejdsområder
Arbejdsområder oprettes på kapaciteter. I bund og grund er arbejdsområder objektbeholdere til dashboards, rapporter, projektmapper, datasæt og dataflow i Power BI.

Der er to typer arbejdsområder: *Mit arbejdsområde* og *arbejdsområder*.

- *Mit arbejdsområde* er et personligt arbejdsområde til Power BI-kunder, hvor de kan arbejde med dit indhold. Kun du har adgang til dit Mit arbejdsområde. Du kan dele dashboards og rapporter fra Mit arbejdsområde. Hvis du vil samarbejde om dashboards og rapporter eller oprette en app, skal du arbejde i et arbejdsområde.

-  *Arbejdsområder* bruges til at samarbejde og dele indhold med kolleger. Du kan føje kolleger til dine arbejdsområder og samarbejde om dashboards, rapporter, projektmapper og datasæt. Med en enkelt undtagelse skal alle medlemmer af arbejdsområdet have Power BI Pro-licenser. Læs mere om de [nye arbejdsområder](../collaborate-share/service-create-the-new-workspaces.md). 

    Arbejdsområder er også de steder, du opretter, publicerer og administrerer *applikationer* for din organisation. Tænk på arbejdsområder som en form for midlertidige områder og objektbeholdere for det indhold, der udgør en Power BI-applikation. Hvad er en *app*? Det er en samling af dashboards og rapporter, der er skabt til at levere vigtige metrikværdier til Power BI-brugerne i din organisation. Applikationer er interaktive, men forbrugerne kan ikke redigere dem. Appforbrugere (dvs. de kolleger, der har adgang til appsene) behøver ikke nødvendigvis at have Pro-licenser.  

Hvis du vil vide mere om deling generelt, kan du starte med [Måder at dele dashboards for dit arbejde på](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md).

Lad os fortsætte med de fem komponenter i Power BI.

## <a name="dataflows"></a>Dataflow
Et *dataflow* hjælper organisationer med at samle data fra forskellige kilder. De er valgfrie og bruges ofte i komplekse eller større projekter. De repræsenterer data, der er udarbejdet og gjort klar til brug af datasæt. De kan dog ikke bruges direkte som en kilde til rapportering. De kan udnytte den omfattende samling dataforbindelser til Microsoft for at muliggøre indtagelse af data fra det lokale miljø og cloudbaserede datakilder.

Dataflow kan kun oprettes og administreres i arbejdsområder (men ikke *Mit arbejdsområde*), og de gemmes som enheder i CDM (Common Data Model) i Azure Data Lake Storage Gen2. Der er typisk planlagt tilbagevendende opdateringer af dem, så der gemmes opdaterede data. De er gode til at forberede data til brug – og potentiel genbrug – af dine datasæt. Du kan finde flere oplysninger i artiklen [Selvbetjent forberedelse af data i Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md).

Du kan ikke have dashboards og rapporter uden data (dvs. du kan have tomme dashboards og tomme rapporter, men de er ikke nyttige, før de indeholder data), så lad os nu introducere **datasæt**.

## <a name="datasets"></a>Datasæt
Et *datasæt* er en samling af data, som du *importerer* eller *opretter forbindelse* til. Med Power BI kan du oprette forbindelse til og importere alle mulige forskellige datasæt og samle dem alle sammen på ét sted. Datasæt kan også hente data fra dataflow.

Datasæt er knyttet til *arbejdsområder*, og et enkelt datasæt kan være en del af mange arbejdsområder. Når du åbner et arbejdsområde, vises de tilknyttede datasæt under fanen **Datasæt**. Hvert angivet datasæt repræsenterer en enkelt datakilde, f.eks. en Excel-projektmappe på OneDrive, et lokalt SSAS-tabeldatasæt eller et Salesforce-datasæt. Der er mange forskellige understøttede datakilder, og vi tilføjer hele tiden nye. Se listen over [typer af datasæt, du kan bruge med Power BI](../connect-data/service-get-data.md).

I eksemplet nedenfor har jeg valgt arbejdsområdet "Salg og marketing" og klikket på fanen for **datasæt**.

![Skærmbillede af Power BI, der viser et prøvearbejdsområde med Datasæt valgt.](media/service-basic-concepts/power-bi-datasets.png)

**ÉT** datasæt...

* kan bruges igen og igen i et enkelt eller i mange arbejdsområder.
* kan bruges i mange forskellige rapporter.
* Visualiseringer fra dette ene datasæt kan vises på mange forskellige dashboards.

  ![Diagram, der viser datasættets relationer til rapport og dashboard.](media/service-basic-concepts/drawing2.png)

Hvis du vil [oprette forbindelse til eller importere et datasæt](../connect-data/service-get-data.md), skal du vælge **Hent Data** nederst i navigationsruden. Følg vejledningen for at oprette forbindelse til eller importere den specifikke kilde og føje datasættet til det aktive arbejdsområde. Nye datasæt markeres med en gul stjerne. Det arbejde, du udfører i Power BI, ændrer ikke det underliggende datasæt.

Datasæt, der tilføjes af ét medlem af arbejdsområdet, er tilgængelige for andre medlemmer af arbejdsområdet med rollen *administrator*, *medlem* eller *bidragyder*.

Datasæt kan opdateres, omdøbes, udforskes og fjernes. Brug et datasæt til at oprette en rapport fra bunden eller ved at køre [hurtig indsigt](../create-reports/service-insights.md).  Hvis du vil se, hvilke rapporter og dashboards der allerede bruger et datasæt, skal du vælge **Få vist relaterede**. Vælg et datasæt for at udforske det. Det, du rent faktisk gør, er at åbne datasættet i rapporteditoren, hvor du virkelig kan begynde at udforske dataene ved at oprette visualiseringer.

Lad os fortsætte med næste emne: rapporter.

### <a name="dig-deeper"></a>Grav dybere
* [Datasæt i Power BI-tjenesten](../connect-data/service-datasets-understand.md)
* [Tilstande for datasæt i Power BI-tjenesten](../connect-data/service-dataset-modes-understand.md)
* [Hvad er Power BI Premium?](../admin/service-premium-what-is.md)
* [Hent data til Power BI](../connect-data/service-get-data.md)
* [Eksempel på datasæt til Power BI](../create-reports/sample-datasets.md)

## <a name="reports"></a>Rapporter
En Power BI-rapport er en eller flere sider med visualiseringer, f.eks. kurvediagrammer, kort og træstrukturdiagrammer. Visualiseringer kaldes også **_visualiseringer_**. Alle visualiseringerne i en rapport stammer fra et enkelt datasæt. Du kan oprette rapporter fra bunden i Power BI, importere dem med dashboards, som kolleger deler med dig, eller Power BI kan oprette dem, når du opretter forbindelse til datasæt fra Excel, Power BI Desktop, databaser og SaaS-programmer.  Når du f.eks. opretter forbindelse til en Excel-projektmappe, der indeholder Power View-ark, opretter Power BI en rapport, der er baseret på de ark. Og når du opretter forbindelse til et SaaS-program, importerer Power BI en færdigbygget rapport.

Der er to forskellige tilstande, hvor du kan få vist og interagere med rapporter: *Læsevisning* og *Redigeringsvisning*. Når du åbner en rapport, åbnes den i Læsevisning. Hvis du har redigeringstilladelser, kan du se **Rediger rapport** i øverste venstre hjørne, og du kan få vist rapporten i Redigeringsvisning.  Hvis en rapport er i et arbejdsområde, kan alle med rollen *administrator*, *medlem* eller *bidragyder* redigere den. De har adgang til alle egenskaberne til udforskning, design, oprettelse og deling i Redigeringsvisning for den pågældende rapport. De personer, de deler rapporten med, kan udforske og interagere med rapporten i Læsevisning.

Når du åbner et arbejdsområde, vises de tilknyttede rapporter under fanen **Rapporter**. Hver rapport på listen repræsenterer én eller flere siders visualiseringer, der er baseret på et af de underliggende datasæt. Du skal markere en rapport for at åbne den.

Når du åbner en app, får du vist et dashboard.  Du kan få adgang til en underliggende rapport ved at vælge et dashboardfelt (mere om felter senere), der er fastgjort fra en rapport. Vær opmærksom på, at ikke alle felter er fastgjort fra rapporter, så du skal muligvis klikke på nogle felter for at finde en rapport.

Rapporten åbnes som standard i Læsevisning.  Du skal blot vælge **Rediger rapport** for at åbne den i Redigeringsvisning (hvis du har de nødvendige tilladelser).

I eksemplet nedenfor har jeg valgt arbejdsområdet "Salg og marketing" og klikket på fanen for **rapporter**.

![Skærmbillede af Power B, der viser et prøvearbejdsområde med Rapporter valgt.](media/service-basic-concepts/power-bi-reports.png)

**ÉN** rapport...

* er inkluderet i et enkelt arbejdsområde.
* kan knyttes til flere dashboards i dette arbejdsområde. Felter, der er fastgjort fra denne ene rapport, kan blive vist på flere dashboards.
* kan oprettes ved brug af data fra et datasæt. Power BI Desktop kan kombinere mere end én datakilde til et enkelt datasæt i en rapport, og denne rapport kan importeres i Power BI.

  ![Diagram, der viser rapportens relationer til datasæt og dashboard.](media/service-basic-concepts/drawing3new.png)

### <a name="dig-deeper"></a>Grav dybere
- [Opret en rapport i Power BI-tjenesten ved at importere et datasæt](../create-reports/service-report-create-new.md)
- [Optimer rapporter til Power BI-mobilapps](../create-reports/desktop-create-phone-report.md)

## <a name="dashboards"></a>Dashboards
Et *dashboard* er noget, du opretter **i Power BI-tjenesten**, eller noget en kollega opretter **i Power BI-tjenesten** og deler med dig. Det er et enkelt lærred, der indeholder ingen eller flere felter og widgets. Hvert felt, der er fastgjort fra en rapport eller fra [Spørgsmål og svar ](../consumer/end-user-q-and-a.md), viser en enkelt [visualisering](../visuals/power-bi-report-visualizations.md), der blev oprettet fra et datasæt og fastgjort til dashboardet. Hele rapportsider kan også fastgøres til et dashboard som et enkelt felt. Der er mange forskellige måder at føje felter til dit dashboard; for mange til at dække i dette oversigtsemne. Du kan få mere at vide i [Dashboard-felter i Power BI](../create-reports/service-dashboard-tiles.md).

Hvorfor opretter personer dashboards?  Her er blot nogle af årsagerne:

* for hurtigt at se alle de oplysninger, der er nødvendige for at træffe beslutninger.
* for at overvåge de vigtigste oplysninger om virksomheden.
* for at sikre, at alle kolleger er på samme side og får vist og bruger de samme oplysninger.
* for at overvåge tilstanden for et produkt eller en virksomhed, en afdeling eller marketingkampagne osv.
* for at oprette en tilpasset visning af et større dashboard – alle de målepunkter, der betyder noget for dig.

Når du åbner et arbejdsområde, vises de tilknyttede dashboards under fanen **Dashboards**. Du skal vælge et dashboard for at åbne det. Når du åbner en app, vises et dashboard.  Hvert enkelt dashboard repræsenterer en brugerdefineret visning af nogle undersæt af de underliggende datasæt.  Hvis du ejer dashboardet, har du også redigeringsadgang til den/de underliggende datasæt og rapporter.  Hvis dashboardet er delt med dig, kan du interagere med dashboardet og de underliggende rapporter, men kan ikke gemme ændringer.

Der er mange forskellige måder, som du eller en kollega kan [dele et dashboard](../collaborate-share/service-share-dashboards.md) på. Power BI Pro er påkrævet for at dele et dashboard og muligvis også for at få vist et delt dashboard.

**ÉT** dashboard...

* er knyttet til et enkelt arbejdsområde
* kan vise visualiseringer fra mange forskellige datasæt
* kan vise visualiseringer fra mange forskellige rapporter
* kan vise visualiseringer, der er fastgjort fra andre funktioner (f.eks. Excel)

  ![Diagram, der viser dashboardets relationer til datasættet og rapporten.](media/service-basic-concepts/drawing1.png)

### <a name="dig-deeper"></a>Grav dybere
* [Opret et tomt dashboard, og hent derefter nogle data](../create-reports/service-dashboard-create.md).
* [Dupliker et dashboard](../create-reports/service-dashboard-copy.md)
* [Opret en telefonvisning af et dashboard](../create-reports/service-create-dashboard-mobile-phone-view.md)


## <a name="workbooks"></a>Projektmapper
Projektmapper er en særlig type datasæt. Hvis du har læst afsnittet om **datasæt** ovenfor, ved du stort set alt, du har brug for at vide om projektmapper. Men du undrer dig måske over, hvorfor Power BI nogle gange klassificerer en Excel-projektmappe som et **datasæt** og andre gange som en **projektmappe**.

Når du bruger **Hent data** med Excel-filer, har du mulighed for at *importere* eller *oprette forbindelse* til filen. Når du vælger at oprette forbindelse, vises din projektmappe i Power BI på samme måde, som den ville blive vist i Excel Online. Men i modsætning til Excel Online får du nogle fantastiske funktioner, så du kan fastgøre elementer fra dine regneark direkte i dine dashboards.

Du kan ikke redigere din projektmappe i Power BI. Men hvis du har brug at foretage ændringer, kan du klikke på Rediger og derefter redigere din projektmappe i Excel Online eller åbne den i Excel på din computer. Alle ændringer, du foretager, gemmes i projektmappen på OneDrive.

### <a name="dig-deeper"></a>Grav dybere
* [Hent data fra Excel-projektmappefiler](../connect-data/service-excel-workbook-files.md)
* [Publicer på Power BI fra Excel 2016](../connect-data/service-publish-from-excel.md)


## <a name="a-dashboard-in-my-workspace"></a>Et dashboard i Mit arbejdsområde
Vi har nu været omkring arbejdsområder og komponenter. Lad os opsummere og gennemse de dele, der udgør dashboardet i Power BI-tjenesten.

![Skærmbillede af Power BI-tjenesten i en browser, der viser nummererede funktioner angivet nedenfor.](media/service-basic-concepts/completenewest.png)

### <a name="1-navigation-pane"></a>1. **Navigationsrude**
Brug navigationsruden til at finde og flytte mellem dine arbejdsområder og Power BI-komponenterne: dashboards, rapporter, projektmapper og datasæt.  

  ![Skærmbillede af Power BI-tjenesten, der viser navigationsruden.](media/service-basic-concepts/power-bi-navigation.png)

* Vælg **Hent Data** for at [føje datasæt, rapporter og dashboards til Power BI](../connect-data/service-get-data.md).
* Udvid og skjul navigationsruden med dette ikon ![Skærmbillede af Power BI-tjenesten, der viser ikonet Navigationsrude.](media/service-basic-concepts/expand-icon.png).
* Åbn eller administrer dit foretrukne indhold ved at vælge **Favoritter**.
* Få vist og åbn det indhold, du senest har besøgt, ved at vælge **Seneste**.
* Få vist, åbn eller slet en app ved at vælge **Apps**.
* Har en kollega delt indhold med dig? Vælg **Delt med mig** for at søge efter og sortere dette indhold for at finde det, du har brug for.
* Få vist og åbn dine arbejdsområder ved at vælge **Arbejdsområder**.

Klik én gang på disse elementer:

* på et ikon eller overskriften for at åbne i indholdsvisning
* på en højrepil (>) for at åbne en pop op-menu med favoritter, seneste og arbejdsområder.
* på en dobbeltvinkel for at få vist rullelisten **Mit arbejdsområde** med dashboards, rapporter, projektmapper og datasæt.

### <a name="2-canvas"></a>2. **Canvas**
Da vi har åbnet et dashboard, vises visualiseringsfelter på canvasområdet. Hvis vi f.eks. havde åbnet rapporteditoren, ville en rapportside blive vist i canvasområdet.

Dashboards består af [felter](../create-reports/service-dashboard-tiles.md).  Felter oprettes i rapportens Redigeringsvisning, Spørgsmål og svar og andre dashboards og kan fastgøres fra Excel, SSRS og meget mere. En særlig type felt kaldet en [widget](../create-reports/service-dashboard-add-widget.md) føjes direkte til dashboardet. De felter, der vises på et dashboard, blev specifikt sat der af en rapportforfatter/-ejer.  Dét at føje et felt til et dashboard kaldes *fastgørelse*.

![Skærmbillede af Power BI-tjenesten, der viser dashboard-lærredet.](media/service-basic-concepts/canvas.png)

Du kan få mere at vide om dette i [Dashboards](#dashboards) (ovenfor).

### <a name="3-qa-question-box"></a>3. **Boks med spørgsmål og svar**
Én måde at udforske dine data er at stille et spørgsmål og lade Power BIs Spørgsmål og svar give dig et svar i form af en visualisering. Spørgsmål og svar kan bruges til at føje indhold til et dashboard eller en rapport.

Spørgsmål og svar søger efter et svar i den/de datasæt, der har forbindelse til dashboardet.  Et forbundet datasæt er et datasæt, der har mindst ét felt, der er fastgjort til dette dashboard.

![Skærmbillede af Power BI-tjenesten, der viser Spørgsmål og svar-feltet.](media/service-basic-concepts/power-bi-qna.png)

Så snart du begynder at skrive dit spørgsmål, fører Spørgsmål og svar dig til siden Spørgsmål og svar. Mens du skriver, hjælper Spørgsmål og svar dig med at stille det rette spørgsmål og finde det bedste svar med omformuleringer, autofyld, forslag og meget mere. Når du har en visualisering (svar), som du synes om, kan du fastgøre den til dashboardet. Du kan få mere at vide i [Spørgsmål og svar i Power BI](../consumer/end-user-q-and-a.md).

### <a name="4-icons-in-the-black-header-bar"></a>4. **Ikoner på den sorte overskriftslinje**
Ikonerne øverst til højre er dine ressourcer til indstillinger, beskeder, downloads samt til at få hjælp fra og give feedback til Power BI-teamet.  

![Skærmbillede af Power BI-tjenesten, der viser ikonknapperne.](media/service-basic-concepts/power-bi-icons.png)

### <a name="5-dashboard-title-navigation-path-or-breadcrumbs"></a>5. **Dashboardtitel** (navigationssti eller brødkrummer)
Det er ikke altid nemt at finde ud af, hvilket arbejdsområde og dashboard der er aktivt, og Power BI opretter derfor en navigationssti for dig.  I dette eksempel vises arbejdsområdet (Mit arbejdsområde) og dashboardoverskriften (Eksempel på detailhandelsanalyse).  Hvis vi har åbnet en rapport, føjes navnet på rapporten til slutningen af navigationsstien.  Hver del i stien er et aktivt hyperlink.  

Bemærk ikonet "C" efter dashboardtitlen. Dette dashboard er markeret med [dataklassifikationsmærket](../create-reports/service-data-classification.md) "fortrolig". Mærket angiver dataenes fortroligheds- og sikkerhedsniveau. Hvis din administrator har slået dataklassificering til, har hvert enkelt dashboard et standardtagsæt. Dashboardejere skal ændre mærket, så det stemmer overens med deres dashboards korrekte sikkerhedsniveau.

![Skærmbillede af Power BI-tjenesten, der viser ikonet Dataklassificering.](media/service-basic-concepts/power-bi-title.png)

### <a name="6-microsoft-365-app-launcher"></a>6. **Microsoft 365-programstarter**
Appstarteren giver nem adgang til alle dine Microsoft 365-apps med et enkelt klik. Her kan du hurtigt starte din mail, dine dokumenter, din kalender med mere.

![Skærmbillede af Power BI-tjenesten, der viser Office-app-starteren.](media/service-basic-concepts/power-bi-waffle.png)

### <a name="7-power-bi-home"></a>7. **Power BI-startside**
Hvis du vælger **Power BI**, vender du tilbage til din Power BI-startside.

   ![Skærmbillede af Power BI-tjenesten, der viser ikonet, som fører tilbage til startsiden for Power BI.](media/service-basic-concepts/version-new.png)

### <a name="8-labeled-icons-in-the-gray-menu-bar"></a>8. **Navngivne ikoner på den grå menulinje**
Dette område på skærmen indeholder flere indstillinger til at interagere med indholdet (i dette tilfælde dashboardet).  Ud over de navngivne ikoner, som du kan se, vises der også indstillinger til at kopiere, udskrive og opdatere dashboardet og meget mere, når du vælger **Flere indstillinger (…)** .

   ![Skærmbillede af Power BI-tjenesten, der viser mærkede ikonknapper.](media/service-basic-concepts/power-bi-labeled-icons.png)

## <a name="next-steps"></a>Næste trin
- [Hvad er Power BI?](power-bi-overview.md)  
- [Power BI-videoer](videos.md)  
- [Rapporteditoren – få en introduktion](../create-reports/service-the-report-editor-take-a-tour.md)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)