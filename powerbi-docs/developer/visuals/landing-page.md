---
title: Føj en landingsside til dine Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du føjer en startside til Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 4381ecf63c0864c4d68e48959efc14baa9d4553b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886344"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Føj en startside til dine Power BI-visualiseringer

Med API 2.3.0 kan du føje en startside til dine Power BI-visualiseringer. Det gør du ved at føje `supportsLandingPage` til egenskaberne og angive det til true. Denne handling initialiserer og opdaterer din visualisering, før du føjer data til den. Da visualiseringen ikke længere indeholder et vandmærke, kan du designe din egen startside, så den vises i visualiseringen, så længe den ikke indeholder data.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

Følgende billede viser et eksempel på en startside:

![skærmbillede af landingsside](media/landing-page/app-landing-page.png)
