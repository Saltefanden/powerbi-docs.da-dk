---
title: COVID-19-sporingseksempel til centralregeringen og delstatsregeringerne i USA
description: Hent og rediger eksempelrapporten med data fra centralregeringen og delstatsregeringerne i USA for COVID-19-pandemien.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 04/28/2020
LocalizationGroup: Samples
ms.openlocfilehash: e6f8e02efa7dc2e56a945aaffcf22d8497052404
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396009"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>COVID-19-sporingseksempel til centralregeringen og delstatsregeringerne i USA

Power BI-teamet har oprettet et COVID-19-sporingseksempel, der gør det muligt for centralregeringen og delstatsregeringerne at publicere eller tilpasse en interaktiv rapport om COVID-19. Ved hjælp af Power BI Desktop, kan de analysere og visualisere COVID-19 data, så de kan holde borgerne informeret på by-, regions- og delstatsniveau samt på nationalt niveau. Når de derefter bruger Power BI publiceret til internettet, kan de dele rapporten offentligt for at informere borgerne. Artiklen indeholder forskellige muligheder for brug af interaktive Power BI-visualiseringer i dit eget offentlige opslag, på din blog eller dit websted.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="COVID-19-eksempel med data fra USA":::

Denne artikel beskriver, hvor du kan:

- Kopiere integreringskode og bruge den på dit eget websted. 
- Foretage tilpasninger, f. eks. formatering af en bestemt stat.
- Publicere i Power BI-tjenesten.
- Publicere på internettet. 
- Mikse disse data med data fra en anden kilde. 

## <a name="prerequisites"></a>Forudsætninger

Før du kan gå i gang med at bruge Power BI til dit opslag, skal du gøre følgende:

- Download den gratis [Power BI Desktop](https://powerbi.microsoft.com/desktop/)-app.
- Tilmeld dig [Power BI-tjenesten](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Mulighed 1: Færdigbygget integreringskode

Microsoft har publiceret eksempelrapporten og oprettet en integreringskode til publicering på internettet. Du kan bruge integreringskoden til at integrere hele eksemplet, herunder den nationale visning, og foretage en detailudledning på delstats- og regionsniveau på dit eget websted. Før du publicerer disse data, anbefaler vi, at du gennemgår [ansvarsfraskrivelserne](#disclaimers) i denne artikel.

Hvis du vil medtage den interaktive grafik på dit websted, skal du kopiere og indsætte følgende integreringskode til det sted, hvor grafikelementet skal vises på din webside.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

Integreringskoden er et HTML iFrame-element, som du kan indsætte på en vilkårlig HTML-side. Juster bredden og højden på iFrame-elementet, så det passer til dit websted. Eksempelrapporten er oprettet med størrelsesforholdet 16:9, så vælg en størrelse, hvor dette forhold bevares. Når grafikken er implementeret korrekt, vises den uden ekstra grå kanter. Det er nyttigt at [gennemse tip og trick til tilpasning af iFrame-størrelsen](../collaborate-share/service-publish-to-web.md#tips-for-iframe-height-and-width), når du foretager disse ændringer.

## <a name="option-2-customize-the-sample-power-bi-file"></a>Mulighed 2: Tilpas Power BI-eksempelfilen

Power BI-filen indeholder dataene og den interaktive grafik i et. pbix-filformat, som du kan redigere i Power BI Desktop.  

En typisk tilpasning er at filtrere rapporten til en bestemt stat og derefter oprette din egen integreringskode til publicering på internettet for din brugerdefinerede rapport.

USAFacts-data leveres i henhold til en Creative Commons-licens, der kræver en kildeangivelse. Før du publicerer dataene, skal du gennemse [ansvarsfraskrivelserne](#disclaimers).

For at komme i gang skal du [downloade. pbix-filen (her)](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>Opdater din rapport 

1. Download den nyeste version af den gratis app [Power BI Desktop](https://powerbi.microsoft.com/desktop/), hvis du ikke allerede har gjort det. 

2. Download [.pbix-filen](https://go.microsoft.com/fwlink/?linkid=2125058), hvis du ikke allerede har gjort det, og åbn den i Power BI Desktop.

3. Hvis du vil filtrere din rapport til en bestemt stat, skal du vælge pilen for at udvide ruden Filtre.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Udvid ruden Filtre":::

4. Vælg den stat, du er interesseret i. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Vælg en stat":::

5. Hvis du vil gemme filen, skal du vælge **Filer** > **Gem**. 

### <a name="refresh-your-report"></a>Opdater rapporten 

1. Vælg knappen **Opdater**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Knappen Opdater":::

2. Vælg **Anonym** > **Opret forbindelse**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Vælg Anonym":::

 
3. Vælg **Ignorer niveauer for beskyttelse af personlige oplysninger**, hvis de vises > **Gem**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Vælg niveauer for beskyttelse af personlige oplysninger":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Publicer rapporten i Power BI-tjenesten

Når du har tilpasset din rapport, som du ønsker, kan du [følge de trin, der er beskrevet her, for at publicere din rapport](../create-reports/desktop-upload-desktop-files.md) i Power BI-tjenesten.

### <a name="configure-scheduled-refresh"></a>Konfigurer planlagt opdatering

Hvis du vil holde dataene i rapporten opdateret, kan du [konfigurere en planlagt opdatering](../connect-data/refresh-scheduled-refresh.md), når du publicerer din rapport.

Når du følger trinnene, skal du vælge følgende indstillinger:

1. Godkendelsesmetode for legitimationsoplysninger for datakilde: Anonym
2. Indstilling for niveau for beskyttelse af personlige oplysninger for denne datakilde: Offentlig

Hvis du vil teste indstillingen for opdatering, skal du vælge indstillingen [Opdater nu](../connect-data/refresh-data.md#data-refresh), der er tilgængelig i datasætelementet.

De opdaterede data indlæses, hver gang tidsplanen kører. De underliggende data leveres af USAFacts og opdateres muligvis ikke så ofte som din tidsplan for opdatering. Se [USAFacts-webstedet](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) for at vide, hvornår de underliggende data senest blev opdateret. 

Hvis du vil publicere den tilpassede rapport på dit websted, er det bedst at konfigurere den planlagte opdatering, så den kører mindst lige så ofte som opdateringerne af USAFacts-dataene. Da USAFacts kan opdatere deres data på forskellige tidspunkter hver dag, kan du konfigurere flere opdateringer hver dag. 

### <a name="create-a-publish-to-web-embed-code"></a>Opret en integreringskode til publicering på internettet 

Hvis du vil integrere din brugerdefinerede rapport på dit eget websted, skal du følge vejledningen til, hvordan du kan [oprette din egen integreringskode til publicering på internettet](../collaborate-share/service-publish-to-web.md#create-embed-codes-with-publish-to-web).

Når du publicerer din integreringskode, kan du bruge iFrame i bekræftelsesdialogboksen til at integrere på dit websted.

Hvis du foretager ændringer i rapporten i Power BI Desktop, kan du publicere og erstatte den eksisterende rapport i Power BI-tjenesten. Integreringskoden ændres ikke. Det tager ca. en time, før ændringer i rapporten eller opdaterede data vises på dit websted. 

## <a name="option-3-mash-up-data-from-another-source"></a>Mulighed 3: Miks data fra en anden kilde 

Du kan også mikse dataene i denne rapport med data fra en anden kilde. Følgende eksempel er baseret på data fra [Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19). Før du publicerer disse data, anbefaler vi, at du gennemgår [ansvarsfraskrivelserne](#disclaimers) i denne artikel.

1. Vælg **Hent** > **Web**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Knappen Hent data":::

2. Angiv følgende URL-adresse:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Vælg data fra internettet":::

3. Vælg **OK**. 

    > [!NOTE]
    > Linket, der er publiceret af Johns Hopkins University, kan ændre sig. Se [Johns Hopkins GitHub-siden](https://github.com/CSSEGISandData/COVID-19) for at få de seneste oplysninger.

4. Vælg **Indlæs** for at indlæse datasættet for det samlede antal bekræftede sager i hele verden.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Indlæs data fra internettet":::

    I artiklen [Opret forbindelse til websider fra Power BI Desktop](../connect-data/desktop-connect-to-web.md) kan du finde flere oplysninger om indlæsning af data fra internettet.
    
Du kan derefter bruge Power BI Desktop til at visualisere dataene. Følg til sidst fremgangsmåden i **Mulighed 2:** [Publicer din rapport til Power BI-tjenesten](#publish-your-report-to-the-power-bi-service) for at publicere rapporten og oprette en brugerdefineret integreringskode. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Mulighed 4: Brug Skabelonappen Sporing af COVID-19 i USA

Hvis du vil have en mulighed mere, har Power BI-teamet oprettet *skabelonappen* Sporing af COVID-19 i USA, så du kan komme i gang med det samme. Skabelonapps er bundtede rapporter, dashboards og datasæt for en bestemt datakilde. Du kan downloade dem fra AppSource, bruge dem eller ændre dem, så de passer til dine behov, og distribuere dem til dine kolleger. 

Denne skabelonapp til sporing af COVID-19 i USA indeholder en færdigbygget rapport over COVID-19-målepunkter, som du kan bruge, som den er, tilpasse direkte i Power BI-tjenesten eller downloade for at tilføje andre datakilder, hvis det er nødvendigt. Få mere at vide om, hvordan du installerer [skabelonappen til sporing af COVID-19 i USA](../connect-data/service-connect-to-covid-19-tracking.md), og kom i gang med det samme.

## <a name="about-the-data-source-for-this-report"></a>Om datakilden for denne rapport
Denne interaktive rapport samler data fra Centers for Disease Control and Prevention (CDC) og de offentlige sundhedsmyndigheder på delstatsniveau og lokalt niveau. Data på landeniveau bekræftes ved at referere direkte til myndighederne på delstatsniveau og lokalt niveau (link).

Data leveres af USAFacts. På grund af data opdateringernes hyppighed afspejler de muligvis ikke de præcise tal, der er rapporteret af de offentlige myndigheder eller nyhedsmedierne. Du kan finde flere oplysninger eller hente dataene ved at besøge [USAFacts-webstedet](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

## <a name="disclaimers"></a>Ansvarsfraskrivelser

Denne rapport og dataene leveres "som de er og forefindes", "med alle fejl" og uden garanti af nogen art. Microsoft giver ingen udtrykkelige garantier, påtager sig intet ansvar og fraskriver sig udtrykkeligt alle underforståede garantier, herunder garanti for salgbarhed, egnethed til et bestemt formål og ikke-krænkelser.

USAFacts-data er tilgængelige i henhold til en Creative Commons-licens. Hvis du vil bruge den, skal du citere USAFacts som dataprovideren og oprette et link tilbage til USAFacts. Hvis du vil se den nøjagtige fremgangsmåde i forbindelse med kildeangivelse, skal du se afsnittet **#MadewithUSAFacts** på USAFacts-siden [Coronavirus in the United States: Mapping the COVID-19 outbreak in the states and counties](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

Johns Hopkins University-data er copyright 2020 Johns Hopkins University, alle rettigheder forbeholdes. Det er udelukkende offentliggjort med henblik på uddannelsesmæssige og akademiske forskningsformål. Her er de komplette [vilkår for anvendelse](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) for dataene, der vises i et mikset eksempel. Du kan finde flere oplysninger på [Johns Hopkins University-webstedet](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Næste trin

[Hent eksempler til Power BI](../create-reports/sample-datasets.md)




