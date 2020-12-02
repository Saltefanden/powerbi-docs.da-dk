---
title: Datavisning i Power BI Desktop
description: Datavisning i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/05/2020
LocalizationGroup: Model your data
ms.openlocfilehash: 500346e9fbdc4302810cce1fe5e49e7fe915a3bb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411212"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Arbejde med Datavisning i Power BI Desktop

Med *Datavisning* kan du få hjælp til at undersøge, udforske og forstå data i din *Power BI Desktop*-model. Det er forskelligt fra den måde, du får vist tabeller, kolonner og data på i *Power-forespørgselseditor*. Med Datavisning får du vist dine data, *når* de er blevet indlæst i modellen.

> [!NOTE]
> Da der i Datavisning vises data efter, hvornår de er indlæst i modellen, er ikonet Datavisning ikke synligt, hvis alle datakilder er baseret på DirectQuery. 

Når du udformer dine data, har du nogle gange brug for at se, hvad der rent faktisk findes i en tabel eller kolonne uden at skulle oprette en visualisering på rapportcanvasset. Du vil muligvis gerne se helt ned på rækkeniveauet. Denne mulighed er især praktisk, når du opretter målinger og beregnede kolonner, eller når du har brug for at identificere en datatype eller datakategori.

Lad os se nærmere på nogle af elementerne i Datavisning.

![Datavisning i Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Ikonet Datavisning**. Vælg dette ikon for at skifte til Datavisning.

2. **Datagitter**. Dette område viser den valgte tabel og alle kolonner og rækker i den. De kolonner, der er skjult i *Rapportvisning*, er nedtonet. Du kan højreklikke på en kolonne for at se indstillingerne.

3. **Båndet Udformning**. Her kan du administrere relationer, oprette beregninger og skifte datatype, format og datakategori for en kolonne.

4. **Formellinje**. Angiv DAX-formler (Data Analysis Expression) for målinger og beregnede kolonner.

5. **Søg**. Søg efter en tabel eller kolonne i modellen.

6. **Listen Felter**. Vælg en tabel eller kolonne, du vil have vist i datagitteret.

## <a name="filtering-in-data-view"></a>Filtrering i datavisning

Du kan også filtrere og sortere data i Datavisning. I hver kolonne vises et ikon, der identificerer sorteringsrækkefølgen, hvis installeret.

![Sortér og filtrer i Datavisning i Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Du kan filtrere de enkelte værdier, eller du kan bruge avanceret filtrering på basis af dataene i kolonnen.

> [!NOTE]
> Når der oprettes en Power BI-model med en anden landestandard end den, du aktuelt anvender i brugergrænsefladen, vises søgefeltet ikke i brugergrænsefladen for Datavisning for andet end tekstfelter. Dette gælder f.eks. for en model, der er oprettet på engelsk (USA), som du får vist på spansk.


## <a name="next-steps"></a>Næste trin

Du kan gøre mange forskellige ting med Power BI Desktop. Du kan finde flere oplysninger om funktionerne i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Oversigt over forespørgsler i Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datatyper i Power BI Desktop](desktop-data-types.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Almindelige forespørgselsopgaver i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
