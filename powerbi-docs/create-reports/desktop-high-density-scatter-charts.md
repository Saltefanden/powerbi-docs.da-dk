---
title: Punktdiagrammer med høj tæthed i Power BI
description: Punktdiagrammer med høj tæthed i Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Create reports
ms.openlocfilehash: a3322a184d00c69e96878ccea6d59d0cb15b7e60
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396860"
---
# <a name="high-density-sampling-in-power-bi-scatter-charts"></a>Udsnit med høj tæthed i Power BI-punktdiagrammer
Fra og med udgivelsen af **Power BI Desktop** fra september 2017 og opdateringerne til **Power BI-tjenesten** findes der en ny udsnitsalgoritme, som forbedrer den måde, punktdiagrammer viser data med høj tæthed på.

Du kan f.eks. oprette et punktdiagram på baggrund af organisationens salgsaktiviteter, hvor hver butik har titusinde datapunkter hvert år. I et sådant punktdiagram tages der et dataudsnit (en relevant repræsentation af dataene til at illustrere, hvordan salget er sket i tidsperioden) ud fra de tilgængelige data, og der oprettes et punktdiagram, der repræsenterer de underliggende data. Dette er almindelig praksis i punktdiagrammer med høj tæthed. Udsnitsfunktionen til data med høj tæthed er blevet forbedret i Power BI. Der er flere oplysninger om dette i denne artikel.

![Skærmbillede af punktdiagram, der viser datastikprøvetagning med høj tæthed.](media/desktop-high-density-scatter-charts/high-density-scatter-charts_01.png)

> [!NOTE]
> Algoritmen **Udsnit med høj tæthed**, der er beskrevet i denne artikel, er tilgængelig i punktdiagrammer i både **Power BI Desktop** og **Power BI-tjenesten**.
> 
> 

## <a name="how-high-density-scatter-charts-work"></a>Sådan fungerer punktdiagrammer med høj tæthed
Tidligere valgte **Power BI** et udsnit af eksempeldatapunkter i alle de underliggende data på en deterministisk måde for at oprette et punktdiagram. Power BI ville specifikt vælge de første og sidste rækker med data i serien af punktdiagrammer, og derefter ville de resterende rækker blive jævnt fordelt, så 3.500 datapunkter i alt ville blive afbilledet i punktdiagrammet. Hvis udsnittet f.eks. havde 35.000 rækker, ville de første og sidste rækker blive valgt til afbildning, og derefter ville hver 10. række også blive afbildet (35.000/10 = hver 10 række = 3.500 datapunkter). Tidligere blev null-værdier eller punkter, der ikke kunne afbildes (f.eks. tekstværdier) i dataserierne, ikke vist, og derfor blev de ikke taget i betragtning, når visualiseringen skulle genereres. Med denne type udsnit var den viste tæthed i punktdiagrammet også baseret på de repræsentative datapunkter. Den visuelle tæthed, der blev antydet, gjaldt dermed for udsnittet af punkter, ikke for de fuldstændige underliggende data.

Når du aktiverer **Stikprøvetagning med høj tæthed**, implementeres en algoritme i Power BI, der fjerner overlappende punkter og sikrer, at punkterne i visualiseringen kan nås, når der interageres med visualiseringen. Algoritmen sikrer også, at alle punkter i datasættet er repræsenteret i visualiseringen Det giver en kontekst for betydningen af de udvalgte punkter i stedet for bare at afbilde et repræsentativt udsnit.

Udsnit af data med høj tæthed tages pr. definition for at kunne oprette visualiseringer forholdsvist hurtigt og bruge disse visualiseringer interaktivt. For mange datapunkter i et visuelt element kan gøre det for tungt og gøre tendenserne mindre synlige. Udsnitsalgoritmen er derfor udviklet for at udvælge data, så man opnår den bedste visualisering og sikrer, at alle data er repræsenteret. I Power BI er algoritmen nu blevet forbedret for at opnå den bedste kombination af svartid, repræsentation og tydelig bevarelse af vigtige punkter i det samlede datasæt.

> [!NOTE]
> Punktdiagrammer, der bruger algoritmen **Udsnit med høj tæthed**, afbildes bedst i firkantede visualiseringer, som det er tilfældet med alle punktdiagrammer.
> 
> 

## <a name="how-the-new-scatter-chart-sampling-algorithm-works"></a>Sådan fungerer den nye algoritme for udsnit i punktdiagrammer
Den nye algoritme for **Stikprøvetagning med høj tæthed** for punktdiagrammer anvender metoder, der registrerer og repræsenterer de underliggende data mere effektivt og fjerner overlappende punkter. Det gøres ved at starte med en lille radius for hvert datapunkt (den synlige cirkelstørrelse for et givet punkt i visualiseringen). Derefter øges radius for alle datapunkterne. Når to (eller flere) datapunkter overlapper hinanden, repræsenterer en enkelt cirkel (med den øgede radiusstørrelse) disse overlappede datapunkter. Algoritmen fortsætter med at øge radius for datapunkterne, indtil radiusværdien resulterer i et rimeligt antal datapunkter – 3.500 – der vises i punktdiagrammet.

Metoderne i denne algoritme sikrer, at udenforliggende værdier repræsenteres i den visualisering, der genereres. Algoritmen respekterer også skaleringen, når overlappet bestemmes, så der visualiseres eksponentielle skaleringer med nøjagtige gengivelser af de underliggende visualiserede punkter.

Algoritmen bevarer også den overordnede form af punktdiagrammet.

> [!NOTE]
> Når du bruger algoritmen for **Udsnit med høj tæthed** for punktdiagrammer, er målet *korrekt distribution* af dataene, og underforstået visuel tæthed er *ikke* målet. Du kan f.eks. få vist et punktdiagram med mange overlappende cirkler (tæthed) i et bestemt område og forestille dig, hvor mange datapunkter der er samlet der i klynger. Da algoritmen for **Udsnit med høj tæthed** kan bruge én cirkel til at repræsentere mange datapunkter, vises en sådan underforstået visuel tæthed (eller "klyngedannelse") ikke. Hvis du vil have flere detaljer i et bestemt område, kan du bruge udsnitsværktøjerne til at zoome ind.
> 
> 

Desuden kan nogle datapunkter ikke afbildes (f.eks. null-værdier og tekstværdier) og ignoreres derfor, så en anden værdi, der kan afbildes, vælges. Dette sikrer, at punktdiagrammets sande form bevares.

### <a name="when-the-standard-algorithm-for-scatter-charts-is-used"></a>Når standardalgoritmen for punktdiagrammer anvendes
Der er omstændigheder, som gør, at **Stikprøvetagning med høj tæthed** ikke kan anvendes på et punktdiagram, og den oprindelige algoritme anvendes i stedet. Det drejer sig om følgende tilfælde:

* Hvis du højreklikker på en værdi under **Oplysninger** og vælger **Vis elementer uden data** i menuen, returneres punktdiagrammet til den oprindelige algoritme.
  
  ![Skærmbillede af menuen Visualisering med ruden Detaljer, hvor Vis elementer, der ikke har data er markeret.](media/desktop-high-density-scatter-charts/high-density-scatter-charts_02.png)
* Alle værdier på aksen **Afspil** vil medføre, at punktdiagrammet returneres til den oprindelige algoritme.
* Hvis både X og Y-akserne mangler i et punktdiagram, returneres diagrammet til den oprindelige algoritme.
* Brugen af en **Forholdslinje** i ruden **Analyse** rude medfører, at punktdiagrammet returneres til den oprindelige algoritme.
  
  ![Skærmbillede af menuen Visualisering, hvor en pil peger på ruden Analyse og Forholdslinje.](media/desktop-high-density-scatter-charts/high-density-scatter-charts_03.png)

## <a name="how-to-turn-on-high-density-sampling-for-a-scatter-chart"></a>Sådan aktiveres udsnit med høj tæthed for et punktdiagram
Du kan slå **Stikprøvetagning med høj tæthed** til ved at vælge et punktdiagram, gå til ruden **Formatering**, udvide kortet **Generelt** og flytte skyderen **Stikprøvetagning med høj tæthed** i bunden af kortet til indstillingen **Til**.

![Skærmbillede af menuen Visualisering, hvor en pil peger på ruden Formatering, kortet Generelt og skyderen Stikprøvetagning med høj tæthed.](media/desktop-high-density-scatter-charts/high-density-scatter-charts_04.png)

> [!NOTE]
> Når skyderen er aktiveret, forsøger Power BI at bruge algoritmen **Udsnit med høj tæthed**, når det er muligt. Når algoritmen ikke kan bruges (hvis du f.eks. anbringer en værdi på aksen *Afspil*), forbliver skyderen i placeringen **Til**, selvom diagrammet er returneret til standardalgoritmen. Hvis du senere fjerner en værdi fra aksen *Afspil* (eller betingelserne ændres, så det er muligt at bruge algoritmen Udsnit med høj tæthed), bruges udsnit med høj tæthed automatisk til diagrammet, fordi funktionen er aktiveret.
> 
> [!NOTE]
> Datapunkter grupperes eller vælges af indekset. Hvis der er en forklaring, påvirker den ikke udsnittet for algoritmen. Den påvirker kun rækkefølgen i visualiseringen.
> 
> 

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger
Algoritmen Udsnit med høj tæthed er en vigtig forbedring af Power BI, men der er et par ting, du bør være klar over, når du arbejder med værdier med høj tæthed og punktdiagrammer.

* Algoritmen for **Stikprøvetagning med høj tæthed** fungerer kun med direkte forbindelser til modeller, der er baseret på Power BI-tjenesten, importerede modeller eller DirectQuery.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om udsnit med høj tæthed i følgende artikler:

* [Linjeudsnit med høj tæthed i Power BI](desktop-high-density-sampling.md)
* [Tip til sortering og distribution af dataafbildninger i Power BI-rapporter](../guidance/report-tips-sort-distribute-data-plots.md)
