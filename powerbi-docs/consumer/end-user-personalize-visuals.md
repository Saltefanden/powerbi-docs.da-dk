---
title: Tilpas visualiseringer i en rapport
description: Opret din egen visning af en rapport uden at redigere den.
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/13/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 718363da3bd1f66de199db8d854d8d23d6de3eb5
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256733"
---
# <a name="personalize-visuals-in-a-report"></a>Tilpas visualiseringer i en rapport

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

Det er svært at lave én visualisering, der opfylder alles krav. Når en kollega deler en rapport med dig, vil du muligvis gerne foretage ændringer af visualiseringerne, uden at du skal bede kollegaen om at foretage ændringerne for dig. 

Måske vil du gerne bytte om på aksen, ændre visualiseringstype eller føje noget til værktøjstippet. Med funktionen **Tilpas denne visualisering** kan du selv foretage ændringerne, og når visualiseringen er, som du ønsker det, kan du gemme den som et [bogmærke](end-user-bookmarks.md), du kan vende tilbage til. Du behøver ikke engang at have redigeringstilladelse til rapporten.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize.png" alt-text="Tilpas en visualisering":::
 
## <a name="what-you-can-change"></a>Det kan du ændre

Denne funktion hjælper dig med at få yderligere indsigt via ad hoc-udforskning af visualiseringer i en Power BI-rapport. Her er nogle af de ændringer, du kan foretage. De tilgængelige indstillinger varierer efter visualiseringstype. 

- Ret visualiseringstypen
- Udskift en måling eller dimension
- Tilføj eller fjern en forklaring
- Sammenlign to eller flere målinger
- Skift sammenlægninger osv.

Denne funktion muliggør ikke kun nye udforskningsegenskaber. Den omfatter også måder du kan registrere og dele dine ændringer på:

- Registrer dine ændringer.
- Del dine ændringer.
- Nulstil alle dine ændringer af en rapport.
- Nulstil alle dine ændringer af en visualisering.
- Ryd alle dine seneste ændringer.

> [!IMPORTANT]
> Muligheden for at tilpasse en visualisering skal aktiveres af rapportens *designer*. Hvis du ikke kan se **Tilpas denne visualisering** ![ikonet for Tilpas denne visualisering](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png), har rapportdesigneren ikke aktiveret denne funktion for den aktuelle rapport. Kontakt rapportejeren eller din Power BI-administrator for at få funktionen aktiveret. Hvis du vil have vist kontaktoplysninger for rapportejeren, skal du vælge rapportens navn på menulinjen i Power BI.

## <a name="personalize-visuals-in-the-power-bi-service"></a>Tilpas visualiseringer i Power BI-tjenesten

Når en visualisering tilpasses, kan du udforske dine data på mange måder uden at forlade [læsevisningen af rapporten](end-user-reading-view.md). I følgende eksempler vises forskellige måder, som du kan redigere en visualisering på for at få opfyldt dine behov. 

1. Åbn en rapport i læsevisning i Power BI-tjenesten.

2. I menulinen for visualiseringen skal du vælge ikonet **Tilpas denne visualisering** ![ikonet Tilpas denne visualisering](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png). 

### <a name="change-the-visualization-type"></a>Ret visualiseringstypen

Synes du, at dataene vil give bedre mening som et stablet søjlediagram? Skift **visualiseringstypen**.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Tilpas en visualisering":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Udskift en måling eller dimension
Erstat det felt, der bruges til X-aksen, ved at vælge det felt, du vil erstatte, og vælg derefter et andet felt.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Tilpas en visualisering":::
 
### <a name="add-or-remove-a-legend"></a>Tilføj eller fjern en forklaring
Når du tilføjer en forklaring, kan du farvekode en visualisering baseret på en kategori. I dette eksempel farvekoder vi på baggrund af virksomhedens navn. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Tilpas en visualisering":::

### <a name="change-the-placement-of-fields"></a>Skift placering af felterne

Ved hjælp af træk og slip kan du ændre placeringen af felterne i samme visuelle egenskab eller også på tværs af forskellige visuelle egenskaber. Du kan f.eks. hurtigt flytte et felt i forklaringen til aksen i en visualisering.

:::image type="content" source="media/end-user-personalize-visuals/personalize-drag-and-drop.png" alt-text="Tilpas en visualisering":::

Du kan også hurtigt ændre rækkefølgen af kolonnerne i en tabel eller matrix.

:::image type="content" source="media/end-user-personalize-visuals/personalize-reorder-columns.png" alt-text="Tilpas en visualisering":::

### <a name="compare-two-or-more-different-measures"></a>Sammenlign to eller flere forskellige målinger
Du kan sammenligne værdier for forskellige målinger ved hjælp af ikonet + for at tilføje flere målinger for en visualisering. Hvis du vil fjerne en måling, skal du vælge **Flere indstillinger (...)** og vælge **Fjern felt**.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Tilpas en visualisering":::

### <a name="change-aggregations"></a>Skift sammenlægninger
Du kan ændre, hvordan en måling beregnes, ved at ændre sammenlægningerne i ruden **Tilpas**. Vælg **Flere indstillinger (...)** , og vælg den aggregering, du vil bruge.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Tilpas en visualisering":::

### <a name="capture-changes"></a>Registrer ændringer 
Ved hjælp af personlige bogmærker kan du registrere dine ændringer, så du kan vende tilbage til din tilpassede visning. Vælg **Bogmærker** > **Personlige bogmærker**, og giv bogmærket et navn. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Tilpas en visualisering":::
 
Du kan også gøre bogmærket til din standardvisning.

### <a name="share-changes"></a>Del ændringer 
Hvis du har tilladelse til at læse og dele igen, kan du vælge at inkludere dine ændringer, når du deler rapporten.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Tilpas en visualisering":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Nulstil alle dine ændringer af en rapport

I øverste højre hjørne af dit rapportlærred skal du vælge **Nulstil til standard**. Herved fjernes alle dine ændringer af rapporten, og der vendes tilbage til forfatterens seneste gemte visning af rapporten.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Tilpas en visualisering":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Nulstil alle dine ændringer af en visualisering

I menulinjen for visualiseringen skal du vælge **Nulstil denne visualisering** for at fjerne alle dine ændringer af en bestemt visualisering og vende tilbage til forfatterens seneste gemte visning af den pågældende visualisering.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Tilpas en visualisering":::
 
### <a name="clear-recent-changes"></a>Ryd seneste ændringer

Vælg viskelæderikonet for at rydde alle seneste ændringer, du har foretaget, siden du åbnede ruden **Tilpas**.  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Tilpas en visualisering":::

## <a name="limitations"></a>Begrænsninger

Der er i øjeblikket nogle få begrænsninger for funktionen, som du skal være opmærksom på.

- **Tilpas denne visualisering** kan slås fra for en hel rapport eller for en bestemt visualisering. Hvis du ikke har mulighed for at tilpasse en visualisering, skal du kontakte Power BI-administratoren eller rapportens ejer. Hvis du vil have vist kontaktoplysninger for rapportejeren, skal du vælge rapportens navn på menulinjen i Power BI.
- Brugerudforskninger bevares ikke automatisk. Du skal gemme din visning som et personligt bogmærke for at registrere dine ændringer.
- Denne funktion understøttes i Power BI-mobilapps til iOS- og Android-tablets og i Power BI Windows-appen. Den understøttes ikke i Power BI-mobilapps til telefoner. Ændringer af visualiseringer, som du gemmer som et personligt bogmærke, mens du er i Power BI-tjenesten, bevares i alle Power BI-mobilapps.

## <a name="next-steps"></a>Næste trin
[Kopiér en rapportvisualisering som et statisk billede](../visuals/power-bi-visualization-copy-paste.md)    
Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
