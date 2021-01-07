---
title: Optimer rapporter til Power BI-mobilapps
description: Få mere at vide om, hvordan du optimerer rapportsider til Power BI-mobilapps ved at oprette en stående version af rapporten specifikt til telefoner og tablets.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.custom: contperf-fy20q4
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 12/22/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 1bfbbcb1b722bbb2504307815860b977a6ab0709
ms.sourcegitcommit: 2adb60a70bfc29c5fdc49cf6defb905e580288ab
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/24/2020
ms.locfileid: "97760731"
---
# <a name="optimize-power-bi-reports-for-the-mobile-app"></a>Optimer Power BI-rapporter til mobilappen

Mobilbrugere kan få vist en Power BI-rapportside i liggende retning. Rapportforfattere kan dog oprette en yderligere visning, der er optimeret til mobilenheder og vises i stående retning. Denne designindstilling, der er tilgængelig i både Power BI Desktop og Power BI-tjenesten, gør det muligt for forfattere at vælge og omarrangere netop de visualiseringer, der giver mening for mobilbrugere, når de er på farten.

![Skærmbillede af mobiloptimerede rapporter i liggende og stående retning.](media/desktop-create-phone-report/desktop-mobile-optimized-report.png)

Power BI indeholder en række funktioner, der kan hjælpe dig med at oprette mobiloptimerede versioner af dine rapporter:
* En mobillayoutvisning, hvor du kan oprette din mobiloptimerede rapport ved at trække og slippe visualiseringer på et lærred, der emulerer en telefon.
* Visualiseringer og udsnitsværktøjer, der kan optimeres til brug på små, mobilskærme.

Disse funktioner gør det muligt at designe og oprette flotte, interaktive, mobiloptimerede rapporter.

## <a name="create-a-mobile-optimized-portrait-version-of-a-report-page"></a>Opret en mobiloptimeret version af en rapportside i stående retning

**Forudsætning**: Det første trin er at designe og oprette rapporten i den almindelige webvisning. Når du har oprettet rapporten, kan du optimere den til telefoner og tablets.

Hvis du vil oprette den mobiloptimerede visning, skal du åbne rapporten enten i Power BI Desktop eller i Power BI-tjenesten. Når rapporten er åben, skal du gå til mobillayoutvisningen:
   * Vælg båndet **Vis** i Power BI Desktop, og vælg derefter **Mobillayout**.
   * Vælg **Rediger rapport > Mobillayout** i Power BI-tjenesten. Hvis indstillingen Rediger ikke er synlig, skal du kigge under **Flere indstillinger (...)** .

   Du kan se et lærred, der kan rulles i, og som er udformet som en telefon, og ruden **Visualiseringer**, hvor alle de visualiseringer, der findes på den oprindelige rapportside, vises.

* De enkelte visualiseringer i ruden **Visualiseringer** vises med deres navn, så du nemt kan identificere dem.
* Hvert enkelt visualisering har også en synlighedsindikator. Synlighedsindikatoren for en visualisering ændres afhængigt af visualiseringens synlighedsstatus i webrapportvisningens aktuelle tilstand. Synlighedsindikatoren er nyttig, når du arbejder med bogmærker.

   ![Mobillayoutvisning](media/desktop-create-phone-report/desktop-mobile-layout.png)

## <a name="add-visuals-to-the-mobile-layout-canvas"></a>Føj visualiseringer til mobillayoutlærredet
Du føjer en visualisering til mobillayoutet ved at trække det fra ruden **Visualiseringer** til telefonlærredet. Når du trækker visualiseringen til lærredet, fastgøres den til gitteret. Alternativt kan du dobbeltklikke på visualiseringen i visualiseringsruden, så føjes visualiseringen til lærredet.

Du kan føje nogle af eller alle visualiseringer på webrapportsiden til den mobiloptimerede rapportside. Du kan kun tilføje de enkelte visualiseringer én gang, og du behøver ikke at inkludere alle visualiseringer.

>[!NOTE]
> Du kan trække skjulte visualiseringer og slippe dem på lærredet. De placeres der, men de vises ikke, medmindre deres synlighedsstatus ændres i den aktuelle webrapportvisning.

Visualiseringer kan lægges oven på hinanden, så du kan oprette interaktive rapporter ved hjælp af bogmærker, eller du kan oprette flotte rapporter ved at lægge visualiseringer oven på billeder. Du kan ændre rækkefølgen af visualiseringernes lag i [Valgruden](#set-the-layering-order-of-visuals-on-the-mobile-layout-canvas).

Når du har placeret en visualisering på lærredet, kan du tilpasse dets størrelse ved at trække i de håndtag, der vises omkring visualiseringens kant, når du markerer det. Hvis du vil bevare højde-bredde-forholdet for visualiseringer, mens du tilpasser størrelsen, skal du trykke på tasten **Skift**, mens du trækker i størrelseshåndtagene.

På billedet nedenfor vises det, hvordan du trækker og slipper visualiseringer fra ruden **Visualiseringer** til lærredet, samt hvordan du tilpasser størrelsen på dem og overlejrer dem.

   ![Træk og slip visualiseringer, tilpas størrelsen af visualiseringen, og overlejr visualiseringer](media/desktop-create-phone-report/desktop-mobile-layout-overlay-resize.gif)

Telefonrapportgitteret tilpasses telefoner af forskellig størrelse, så din rapport ser lige så flot ud på telefoner med små som store skærme.

## <a name="set-the-layering-order-of-visuals-on-the-mobile-layout-canvas"></a>Angiv rækkefølgen af visualiseringernes lag på mobillayoutlærredet

Hver gang du trækker en visualisering til lærredet, føjes den til et separat lag oven på de andre visualiseringer, der allerede findes på lærredet. I **Valgruden** kan du ændre rækkefølgen af lagene.

Du åbner **Valgruden** ved at klikke på knappen **Valg** i afsnittet **Vis ruder** under fanen **Vis**. 

I **Valgruden** vises alle visualiseringer, der er på lærredet, på en liste. Rækkefølgen af listen afspejler rækkefølgen af lagene på lærredet – den første angivne visualisering er på det øverste lag, den sidste angivne visualisering er på det nederste lag. Hvis du vil ændre rækkefølgen, kan du enten trække og slippe en visualisering til et andet sted på listen eller markere en visualisering og bruge pileknapperne til at flytte den op eller ned.

**Valgruden** har også en indikation for synlighed for hver visualisering på listen, men det er ikke muligt at ændre synligheden i mobillayoutvisningen. Det skal gøres i den almindelige weblayoutvisning.

![Skærmbillede, der viser valgruden, og hvordan du åbner den.](media/desktop-create-phone-report/selection-pane-mobile-layout.png)

## <a name="remove-visuals-from-the-mobile-layout-canvas"></a>Fjern visualiseringer fra mobillayoutlærredet
Fjern en visualisering fra mobillayoutet ved at klikke på **X** øverst til højre i visualiseringen på telefonlærredet, eller markér visualiseringen, og tryk på **Slet**.

Du kan fjerne alle visualiseringer fra lærredet ved at klikke på viskelæderet i ruden **Visualiseringer**.

Fjernelse af visualiseringer fra mobillayoutlærredet fjerner dem kun fra lærredet. De vises stadig i ruden Visualiseringer, og den oprindelige rapport påvirkes ikke.

## <a name="configure-visuals-and-slicers-for-use-in-mobile-optimized-reports"></a>Konfigurer visualiseringer og udsnitsværktøjer til brug i mobiloptimerede rapporter

### <a name="visuals"></a>Visualiseringer

Som standard er mange visualiseringer, især visualiseringer af typen diagram, dynamiske.  Det betyder, at de ændres dynamisk, så den maksimale mængde data og indsigt vises uanset skærmstørrelse.

Når størrelsen af visualiseringen ændres, prioriteres datavisningen i Power BI. Udfyldning fjernes f.eks., og forklaringen kan automatisk flyttes til toppen af visualiseringen, så visualiseringen fortsat er informativ, selvom den bliver mindre.

![Dynamisk tilpasning af en visualiserings størrelse](media/desktop-create-phone-report/desktop-mobile-layout-responsive-visual.gif)
 
Hvis du af en eller anden grund vil slå den dynamiske funktionsmåde fra, kan du gøre det i afsnittet **Generelt** i visualiseringens formatindstillinger.

### <a name="slicers"></a>Udsnit

Udsnit muliggør filtrering af rapportdata på lærredet. Når du designer udsnit i den almindelige tilstand til rapportoprettelse, kan du modificere nogle udsnitsindstillinger for at gøre dem mere anvendelige i mobiloptimerede rapporter:
* Du kan vælge, om du vil tillade, at rapportlæsere kun vælger ét element eller flere elementer.
* Du kan gøre udsnitsværktøjet lodret, vandret eller dynamisk (dynamiske udsnitsværktøjer skal være vandrette).

Hvis du gør udsnitsværktøjet dynamisk, når du ændrer dets størrelse og form, vises flere eller færre indstillinger. Det kan være højt, kort, bredt eller smalt. Du kan gøre det så lille, at det blot bliver et filterikon på rapportsiden.

![Dynamisk udsnitsværktøj i Power Bi](media/desktop-create-phone-report/desktop-create-phone-report-8.gif)
 
Læs mere om [oprettelse af dynamiske udsnit](power-bi-slicer-filter-responsive.md).

## <a name="publish-a-mobile-optimized-report"></a>Publicer en mobiloptimeret rapport
Hvis du vil publicere en mobiloptimeret version af en rapport, skal du [publicere den primære rapport fra Power BI Desktop til Power BI-tjenesten](desktop-upload-desktop-files.md). Derved publiceres den mobiloptimerede version på samme tid.

## <a name="viewing-optimized-and-unoptimized-reports-on-a-phone-or-tablet"></a>Visning af optimerede og ikke-optimerede rapporter på en telefon eller tablet

I Power BI-mobilapps er mobiloptimerede rapporter angivet med et særligt ikon.

![Ikon for mobiloptimeret rapport](media/desktop-create-phone-report/desktop-create-phone-report-optimized-icon.png)

På telefoner registrerer appen automatisk, om rapporten er mobiloptimeret eller ej.
* Hvis der findes en mobiloptimeret rapport, åbnes rapporten automatisk i mobiloptimeret tilstand i appen.
* Hvis der ikke findes en mobiloptimeret rapport, vises rapporten i ikke-optimeret liggende retning.

Hvis du holder en telefon i liggende retning, åbnes rapporten i den ikke-optimerede visning med det oprindelige rapportlayout, uanset om rapporten er optimeret eller ej.

Hvis du kun optimerer nogle sider, bliver læserne bedt om at skifte til liggende retning, når læserne de kommer til en ikke-optimeret side. Hvis de vender telefonen eller tabletten på siden, kan de se rapportsiden i liggende retning. [Læs mere om interaktion med Power BI-rapporter, der er optimeret til visning i stående retning](../consumer/mobile/mobile-apps-view-phone-report.md).

![Telefonside ikke optimeret](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

## <a name="considerations-when-creating-mobile-optimized-layouts"></a>Overvejelser i forbindelse med oprettelse af mobiloptimerede layout
* I rapporter med flere sider, kan du optimere alle siderne eller kun nogle få.
* Hvis du har defineret en baggrundsfarve for en rapportside, får den mobiloptimerede rapport den samme baggrundsfarve.
* Du kan ikke ændre formatindstillinger kun for den mobiloptimerede rapport. Formateringen er konsistent mellem master- og mobillayout. Skriftstørrelserne er f.eks. de samme.
* Du kan ændre en visualisering, f.eks. formateringen, datasættet, filtrene eller andre egenskaber, ved at vende tilbage til den almindelige tilstand for oprettelse af webrapporter.

## <a name="next-steps"></a>Næste trin
* [Opret en telefonvisning af et dashboard i Power BI](service-create-dashboard-mobile-phone-view.md).
* [Få vist Power BI-rapporter, der er optimeret til din telefon](../consumer/mobile/mobile-apps-view-phone-report.md).
* [Power BI-dokumentation om oprettelse af rapporter og dashboards](./index.yml).
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/).
