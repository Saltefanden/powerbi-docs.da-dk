---
title: Understøttelse af tilstand med høj kontrast i Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du føjer tilstanden med understøttelse af stor kontrast til visualiseringer i Power BI. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: f55427511a76fc65b3ae6b3933dca68ef742039c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889196"
---
# <a name="high-contrast-mode-support-in-power-bi-visuals"></a>Understøttelse af stor kontrast til visualiseringer i Power BI

Indstillingen *stor kontrast* i Windows gør det nemmere at se tekst og apps ved at anvende tydeligere farver. I denne artikel gennemgås det, hvordan du føjer tilstanden med understøttelse af stor kontrast til visualiseringer i Power BI. Du kan finde flere oplysninger under [understøttelse af stor kontrast i Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast).

Hvis du vil se understøttelse af stor kontrast implementeret, skal du gå til [lageret med visualiseringer, PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6).

## <a name="on-initialization"></a>Ved initialisering

ColorPalette-medlemmet af `options.host` har flere egenskaber for tilstand med stor kontrast. Brug disse egenskaber til at afgøre, om tilstanden med stor kontrast er aktiv, og hvilke farver der i givet fald skal bruges.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Kontrollér, om Power BI er i tilstanden med stor kontrast

Hvis `host.colorPalette.isHighContrast` er `true`, er tilstanden med stor kontrast aktiv, og det visuelle element oprettes i overensstemmelse hermed.

### <a name="get-high-contrast-colors"></a>Hent farver med stor kontrast

I tilstanden med stor kontrast bør dit visuelle element være begrænset til følgende indstillinger:

* **Forgrundsfarven** bruges til at tegne streger, ikoner, tekst og konturer eller udfyldning af figurer.
* **Baggrundsfarven** bruges til baggrunden og som fyldfarve for skitserede figurer.
* **Den valgte forgrundsfarve** bruges til at angive et markeret eller aktivt element.
* **Linkfarven** bruges kun til hyperlinktekst.

> [!NOTE]
> Hvis der er behov for en sekundær farve, kan forgrundsfarven bruges sammen med en vis uigennemsigtighed (indbyggede visuelle elementer i Power BI anvender 40 % uigennemsigtighed). Brug dette med måde for at gøre det nemt at se de visuelle detaljer.

Du kan gemme følgende værdier under initialisering:

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

Alternativt kan du gemme objektet `host` under initialisering og få adgang til de relevante `colorPalette`-egenskaber under opdateringen.

## <a name="on-update"></a>Ved opdatering

De specifikke implementeringer af understøttelse med stor kontrast varierer fra visualisering til visualisering og afhænger af detaljerne i det grafiske design. For at gøre vigtige detaljer tydelige ved hjælp af de begrænsede farver kræver tilstanden med stor kontrast normalt et design, der adskiller sig lidt fra standardtilstanden.

Oprindelige visualiseringer i Power BI følger disse retningslinjer:

* Alle datapunkter bruger samme farve (forgrund).
* Tekst, akser, pile, linjer osv. bruger forgrundsfarven.
* Tykke figurer tegnes som konturer med tykke strøg (mindst to pixel) og baggrundsfarvefyld.
* Når datapunkter er relevante, skelnes der mellem forskellige markørfigurer, og til datalinjer bruges der forskellige tankestreger.
* Når et dataelement fremhæves, ændres uigennemsigtigheden for alle andre elementer til 40 %.
* I forbindelse med udsnitsværktøjer bruger aktive filterelementer den farve, der er valgt til forgrunden.

I følgende eksempel med søjlediagrammet tegnes alle linjer med en to pixel tyk forgrundskontur og baggrundsfyld. Sammenlign den måde, det ser ud på, med standardfarver og med et par temaer med stor kontrast:

![Eksempel på søjlediagram med standardfarver](media/high-contrast-support/hc-samplebarchart-standard.png)
![Eksempel på søjlediagram med farvetemaet *Dark #2*](media/high-contrast-support/hc-samplebarchart-dark2.png)
![Eksempel på søjlediagram med farvetemaet *White*](media/high-contrast-support/hc-samplebarchart-white.png)

Næste afsnit viser ét sted i funktionen `visualTransform`, der blev ændret for at understøtte stor kontrast. Det kaldes som en del af gengivelsen under opdateringen.

### <a name="before"></a>Før

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>Efter

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
