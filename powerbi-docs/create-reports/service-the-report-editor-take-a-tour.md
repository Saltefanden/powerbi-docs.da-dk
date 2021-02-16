---
title: Præsentation af rapporteditoren
description: I Power BI Desktop og i Power BI-tjenesten er rapporteditor det sted, hvor du designer de rapporter, som slutbrugerne ser. Det er næsten det samme i de to miljøer.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 12/01/2020
LocalizationGroup: Reports
ms.openlocfilehash: 83a68e0d2aec6fa5a47919447872ef440c71792a
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531717"
---
# <a name="tour-the-report-editor-in-power-bi"></a>Præsentation af rapporteditor i Power BI

I Power BI Desktop og i Power BI-tjenesten er *rapporteditor* det sted, hvor du designer rapporter med diagrammer, tabeller, kort og andre visualiseringer, som forbrugerne ser. Det er næsten det samme i de to miljøer. Du starter typisk med at oprette en rapport i Power BI Desktop. Derefter publicerer du den i Power BI-tjenesten, hvor du kan fortsætte med at ændre den. Power BI-tjenesten er også det sted, hvor du opretter de dashboards, der er baseret på dine rapporter.

Når du har oprettet dine dashboards og rapporter, kan du distribuere dem til dine rapportforbrugere. Afhængigt af hvordan du deler dem, kan dine slutbrugere interagere med dem i Læsevisning i Power BI-tjenesten, men ikke redigere dem. Læs mere om, [hvad rapportforbrugere kan gøre i Power BI-tjenesten](../consumer/end-user-reading-view.md). 

Denne video viser rapporteditoren i Power BI Desktop. I denne artikel kan du også se rapporteditoren i Power BI Desktop. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

I Power BI-tjenesten er rapporteditoren kun tilgængelig i redigeringsvisning. Hvis du vil åbne en rapport i Redigeringsvisning, skal du være rapportejer eller rapportforfatter eller være bidragyder til det arbejdsområde, der indeholder rapporten.

![Afsnittene i rapporteditoren](media/service-the-report-editor-take-a-tour/power-bi-report-editor-overview-numbered.png)

Power BI-rapporteditor er inddelt i flere hovedafsnit:  

1. Båndet
1. Rapportlærred
1. Ruden Filtre
1. Ruden Visualiseringer
1. Ruden Felter

## <a name="1-the-ribbon"></a>1. Båndet
Der er mange handlinger tilgængelige på båndet, og der tilføjes hele tiden nye handlinger. Brug indholdsfortegnelsen eller søgefeltet i dokumentationen til Power BI for at få oplysninger om en bestemt handling.


## <a name="2-the-report-canvas"></a>2. Rapportcanvasset
Rapportcanvasset er det sted, dit arbejde vises. Når du bruger ruderne Felter, Filtre og Visualiseringer til at oprette visuelle elementer, bygges og vises de på dit rapportcanvas. Hver fane nederst på canvasset repræsenterer en side i rapporten. Vælg en fane for at åbne siden. 

## <a name="the-report-editor-panes"></a>Rapporteditorens ruder

Tre ruder er synlige, når du åbner en rapport: Filtre, Visualiseringer og Felter. I de første to ruder til venstre, Filtre og Visualiseringer, styrer du, hvordan dine visualiseringer ser ud: type, farver, filtrering og formatering. I den sidste rude til højre, Felter, administrerer du de underliggende data, der bruges i visualiseringerne. Det indhold, der vises i rapporteditoren, varierer i forhold til valg, du foretager på rapportcanvasset. 

Når du f.eks. vælger en individuel visualisering, såsom dette søjlediagram:

![Power BI-rapporteditor](media/service-the-report-editor-take-a-tour/power-bi-report-editor-panes.png)

I ruden **Filtre** vises alle filtre i visualiseringen, på siden eller på alle sider. I dette tilfælde er der filtre på sideniveau, men der er ingen filtre på visualiseringsniveau.

**Øverst i ruden Visualisering** identificeres den type visualisering, der bruges. I dette eksempel bruges et grupperet søjlediagram. 

**Nederst i ruden Visualisering** er der tre faner:

![Felter i visualiseringen](media/service-the-report-editor-take-a-tour/power-bi-fields-visualization-pane.png) **Felter** viser felterne i visualiseringen. Du skal muligvis rulle ned for at se alle detaljerne. Dette diagram bruger Butiksnummernavn og Dette års salg.

![Malerrulleikon](media/service-the-report-editor-take-a-tour/power-bi-paint-roller.png) **Formatér** Vælg malerrulleikonet for at få vist formateringsruden for den valgte visualisering.

![ikon med forstørrelsesglas](media/service-the-report-editor-take-a-tour/power-bi-magnifying-glass.png) **Analyse** Vælg ikonet med forstørrelsesglasset for at få vist ruden Analyse.

**I ruden Felter** vises alle tilgængelige tabeller i datamodellen. Når du udvider en tabel, kan du se felterne i den pågældende tabel. Et gult flueben angiver, at mindst ét felt fra den pågældende tabel findes i en visualisering.

Læs videre for at få oplysninger om hver rude.

## <a name="3-the-filters-pane"></a>3. Ruden Filtre
Brug ruden Filtre til at få vist, angive og redigere faste filtre til dine rapporter på side-, rapport-, detaljeadgangs- og visualiseringsniveau. Du kan udføre ad hoc-filtrering på rapportsider og visualiseringer ved at vælge elementer i visualiseringerne eller ved at anvende værktøjer såsom udsnit. Filtrering i ruden Filtre har den fordel, at filtrenes status gemmes sammen med rapporten. 

Ruden Filtre indeholder en anden effektiv funktion: Du kan filtrere ved hjælp af et felt, *der ikke allerede bruges i en af visualiseringerne i din rapport*. Lad mig forklare. Når du opretter en visualisering, føjer Power BI automatisk alle de felter, du bruger i visualiseringerne, til filterområdet i ruden Filtre på visualiseringsniveau. Hvis du vil angive en visualisering, en side, detaljeadgang eller et rapportfilter ved hjælp af et felt, der ikke bruges i en visualisering i øjeblikket, skal du bare trække det til en filterbucket.

Den nye filtervisning giver større fleksibilitet. Du kan f.eks. formatere filtre, så de ligner selve rapporten. Du kan også låse filtre eller skjule dem for dine rapportforbrugere. 

![Ny filteroplevelse](media/service-the-report-editor-take-a-tour/power-bi-filters-pane.png)

Læs mere om [formatering af ruden filtre i den nye filtervisning](power-bi-report-filter.md).

## <a name="4-the-visualizations-pane"></a>4. Ruden Visualiseringer

Selve visualiseringsruden indeholder fire sektioner. Vi starter øverst i ruden.

![Øverst i ruden Visualiseringer](media/service-the-report-editor-take-a-tour/power-bi-visual-pane-icons.png)

Dette er stedet, hvor du vælger en visualiseringstype. De små ikoner viser de forskellige typer visualiseringer, du kan oprette. På billedet herover er boblediagrammet valgt. Hvis du begynder at oprette en visualisering ved at vælge felter uden først at vælge en visualiseringstype, vælger Power BI visualiseringstypen for dig. Du kan bevare Power BI's valg eller ændre typen ved at vælge et andet ikon.

Du kan downloade brugerdefinerede visualiseringer til Power BI Desktop. Deres ikoner vises også i denne rude. 

### <a name="manage-the-fields-in-a-visualization"></a>Administrer felterne i en visualisering

![Nederst i ruden Visualiseringer](media/service-the-report-editor-take-a-tour/power-bi-visualization-field-manager.png)

De buckets (også kaldet *brønde*), der er vist i denne rude, varierer, afhængigt af hvilken visualiseringstype du har valgt.  Hvis du f.eks. har valgt et søjlediagram, kan du se Akse, Forklaring og Værdier. Når du vælger et felt eller trækker det over på lærredet, føjer Power BI dette felt til en af disse buckets.  Du kan også trække felter fra listen Felter direkte til buckets.  Nogle buckets er begrænset til visse datatyper.  For eksempel accepterer **Værdier** ikke felter, der ikke er numeriske. Så hvis du trækker et felt for **Kategori** til bucketen **Værdier**, ændrer Power BI det til **Antal kategori**.

Du kan finde flere oplysninger i [Føj visualiseringer til en Power BI-rapport](../visuals/power-bi-report-add-visualizations-i.md).

Denne del af ruden indeholder også indstillinger for at styre [detaljeadgang](desktop-drillthrough.md) og filtreringsfunktionalitet.

### <a name="format-your-visuals"></a>Formatér dine visuelle elementer
Vælg ikonet med malerullen for at åbne ruden Formatér. De tilgængelige indstillinger afhænger af den valgte type visualisering.

![Ruden Formatering i rapporteditoren](media/service-the-report-editor-take-a-tour/power-bi-visual-pane-format.png)

Der er omfattende formateringsmuligheder.  Udforsk selv for at få mere for at vide, eller gå til disse artikler:

* [Tilpas visualiseringstitel, -baggrund og -forklaring](../visuals/power-bi-visualization-customize-title-background-and-legend.md)
* [Farveformatering](../visuals/service-getting-started-with-color-formatting-and-axis-properties.md)
* [Tilpas egenskaber for x- og y-akse](../visuals/power-bi-visualization-customize-x-axis-and-y-axis.md)

### <a name="add-analytics-to-your-visualizations"></a>Føj analyser til din visualiseringer
Vælg forstørrelsesglasikonet for at få vist ruden Analystics. De tilgængelige indstillinger afhænger af den valgte type visualisering.

![Ruden Analyse i rapporteditoren](media/service-the-report-editor-take-a-tour/power-bi-visual-pane-analytics.png)

I ruden Analytics i Power BI-tjenesten kan du føje dynamiske referencelinjer til visuelle elementer og sætte fokus på vigtige tendenser eller indsigter. Du kan finde flere oplysninger under [Ruden Analyse i Power BI Desktop](../transform-model/desktop-analytics-pane.md).

## <a name="5-the-fields-pane"></a>5. Ruden Felter
Ruden Felter indeholder tabellerne, mapperne og felterne i dine data, som er tilgængelige for dig, så du kan bruge dem til at oprette visualiseringer.

:::row:::
    :::column:::
        ![Ruden Felter](media/service-the-report-editor-take-a-tour/power-bi-fields-list.png)
    :::column-end:::
    :::column:::
        <ul><li>Træk et felt til siden for at starte en ny visualisering.  Du kan også trække et felt til en eksisterende visualisering for at føje feltet til den pågældende visualisering.<br><br></li> <li>Når du markerer afkrydsningsfeltet ud for et felt, føjer Power BI dette felt til den aktive (eller nye) visualisering. Og den beslutter også, hvilken bucket dette felt skal placeres i.  Skal feltet f.eks. bruges som en forklaring, akse eller værdi? Power BI gætter på bedste vis, og du kan om nødvendigt flytte det fra denne bucket til en anden. <br><br></li><li>Uanset hvad, føjes hvert enkelt felt til ruden Visualiseringer i rapporteditoren.</li></ul>
    :::column-end:::
:::row-end:::

I Power BI Desktop har du også mulighed for at vise/skjule felter, tilføje beregninger osv.

## <a name="the-field-icons"></a>Feltikonerne

Power BI bruger en række forskellige ikoner til at angive typerne af felter i en rapport. Når du genkender dem, forstår du bedre, hvordan de fungerer i forskellige visualiseringer. Se [afsnittet med ikoner for feltlisten i Brug af feltliste i Power BI Desktop](../transform-model/desktop-field-list.md#field-list-changes) for at se en komplet liste.

## <a name="next-steps"></a>Næste trin
[Opret en rapport](service-report-create-new.md)

Læs mere om rapporter i programmerne [Power BI-tjenesten](service-report-create-new.md), [Power BI Desktop](desktop-report-view.md) og [Power BI – Mobil](../consumer/mobile/mobile-apps-view-phone-report.md).

[Grundlæggende begreber for Power BI-designere](../fundamentals/service-basic-concepts.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
