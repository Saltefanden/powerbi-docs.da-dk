---
title: Scan en stregkode fra Power BI-mobilappen
description: Scan stregkoder i den virkelige verden for at gå direkte til filtrerede BI-oplysninger i Power BI-mobilappen.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/02/2019
ms.openlocfilehash: 5d1534ec3b6ccdf730cd2b255ba1142e80a6f9f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413098"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>Scan en stregkode med din enhed fra Power BI-mobilappen
Scan stregkoder i den virkelige verden for at gå direkte til filtrerede BI-oplysninger i Power BI-mobilappen.


Gælder for:

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPad-tablets](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android-telefon](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android-tablet](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone-telefoner |iPad-tablets |Android-telefoner |Android-tablets |

Lad os sige, at en kollegaer har [mærket et stregkodefelt i en rapport i Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md) og delt rapporten med dig. 

![Skærmbillede af scanning af en produktstregkode, som viser scanneren over stregkoden for en farvet drikkevare.](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Når du scanner en stregkode for produktet med scanneren i Power BI-appen på din enhed, får du vist rapporten (eller listen over rapporter) med denne stregkode. Du kan åbne denne rapport, filtreret til denne stregkode.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Scan en stregkode med Power BI-scanneren
1. Tryk på **Flere indstillinger** (...) på navigationslinjen, og tryk derefter på **Scanner**.

    ![Skærmbillede af indstillingerne under Mere i navigationsruden, hvor Scanner er markeret.](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

2. Hvis kameraet ikke er aktiveret, skal du godkende Power BI-appen for at bruge kameraet. Dette er en engangsgodkendelse. 
4. Ret scanneren mod en stregkode på et produkt. Du vil se en liste over rapporter, der er knyttet til denne stregkode.
5. Tryk på navnet på rapporten for at åbne den på din enhed, hvor den er filtreret automatisk iht. denne stregkode.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Filtrer efter andre stregkoder, mens du befinder dig inde i en rapport
Mens du ser på en rapport, der er filtreret efter en stregkode på din enhed, kan det være du gerne vil filtrere den samme rapport ud fra en anden stregkode.

* Hvis stregkodeikonet har et filter ![Ikonet Filtreret](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), er filtret aktivt, og rapporten er allerede filtreret efter en stregkode. 
* Hvis ikonet ikke indeholder et filter ![Ikonet Ufiltreret](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), er filtret ikke aktivt, og rapporten er ikke filtreret efter en stregkode. 

I begge tilfælde skal du trykke på ikonet for at åbne en lille menu med en flydende scanner.

* Ret scanneren mod det nye element for at ændre filtret for rapporten til en anden stregkodeværdi. 
* Vælg **Ryd stregkodefilter** for at gå tilbage til den ufiltrerede rapport.
* Vælg **Filtrer efter de seneste stregkoder** for at ændre rapportfiltret til en af de stregkoder, du har scannet i den aktuelle session.

## <a name="issues-with-scanning-a-barcode"></a>Problemer med at scanne en stregkode
Her er nogle meddelelser, som du kan få vist, når du scanner en stregkode på et produkt.

### <a name="couldnt-filter-report"></a>"Rapporten kunne ikke filtreres ..."
Den rapport, du vælger at filtrere, er baseret på en datamodel, der ikke indeholder denne stregkodeværdi. For eksempel: Produktet "mineralvand" er ikke omfattet af rapporten.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>Alle/nogle af de visuelle elementer i rapporten indeholder ikke en værdi
Den stregkodeværdi, du scannede, findes i din model, men alle/nogle af de visuelle elementer i rapporten indeholder ikke denne værdi, og derfor returnerer filtreringen en tom tilstand. Prøv at se på andre rapportsider, eller rediger dine egne rapporter i Power BI Desktop, så de indeholder denne værdi 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>"Det ser ud til, at du ikke har nogen rapporter, der kan filtreres efter stregkoder".
Det betyder, at du ikke har rapporter, hvor stregkoder er aktiveret. Stregkodescanneren kan kun filtrere rapporter, som har en kolonne, der er markeret som **Stregkode**.  

Kontrollér, at du eller rapportens ejer har mærket en kolonne som **Stregkode** i Power BI Desktop. Få mere at vide om [markering af et stregkodefelt i Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>"Rapporten kunne ikke filtreres – det ser ud til, at denne stregkode ikke findes i rapportdataene".
Den rapport, du valgte at filtrere, er baseret på en datamodel, der ikke indeholder denne stregkodeværdi. For eksempel: Produktet "mineralvand" er ikke omfattet af rapporten. Du kan scanne et andet produkt, vælge en anden rapport (hvis der findes flere rapporter) eller få vist rapporten ufiltreret. 

## <a name="next-steps"></a>Næste trin
* [Markér et stregkodefelt i Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md)
* [Dashboard-felter i Power BI](../end-user-tiles.md)
* [Dashboards i Power BI](../end-user-dashboards.md)
