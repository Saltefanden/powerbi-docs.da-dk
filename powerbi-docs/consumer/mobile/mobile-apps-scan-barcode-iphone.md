---
title: Scan stregkode fra mobil-appen Power BI
description: Scan stregkoder i den virkelige verden for at gå direkte til filtrerede BI-oplysninger i Power BI-mobilappen.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/02/2019
ms.openlocfilehash: 28baefb80037d1f78d2a2fd51b3989aa5d2a1ebb
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2021
ms.locfileid: "99533090"
---
# <a name="scan-barcodes-from-the-mobile-app-to-get-filtered-data"></a>Scan stregkoder fra mobilappen for at få filtrerede data 
Scan stregkoder i den virkelige verden, så du kan få dem direkte til filtrerede BI-oplysninger i Power BI-mobilappen.

Gælder for:

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPad-tablets](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android-telefon](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android-tablet](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone-telefoner |iPad-tablets |Android-telefoner |Android-tablets |

Antag, at din organisation har rapporter, der indeholder data, som er blevet [mærket som stregkodedata Power bi desktop](../../transform-model/desktop-mobile-barcodes.md). Når du scanner en produkt stregkode med scanneren i Power BI-appen på din enhed, får du vist en liste over de rapporter, der indeholder stregkodedata. Du kan åbne den rapport, du søger efter, automatisk filtreret efter de oplysninger, du har brug for.

![Skærmbillede af scanning af en produktstregkode, som viser scanneren over stregkoden for en farvet drikkevare.](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Her er eksempler på to scenarier, hvor stregkode scanning er nyttig:
* Forestil dig, at du tjekker lager i et stort supermarked, og mens du er væk i de gange, du har brug for at få oplysninger om bestemte produkter, f. eks. hvor mange lagervarer der er på lager, hvilke afdelinger varerne lagres i osv. Du kan bare åbne Power BIs scanneren på din mobil enhed og scanne et Elements stregkode. Du får vist en liste over rapporter, der indeholder stregkodedata. Du vælger den relevante rapport, og rapporten åbnes, der er filtreret til de relevante data.
* Antag, at maskinerne på en fabrik er identificeret med stregkoder, og at telemetri fra disse maskiner behandles og sendes til Power BI. Når der er tale om teknikere, der kontrollerer maskinens status for gulv, kan de nemt scanne en maskin stregkode og få vist en KPI-rapport om dens ydeevne og status.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Scan en stregkode med Power BI-scanneren
1. Tryk på **Flere indstillinger** (...) på navigationslinjen, og tryk derefter på **Scanner**.

    ![Skærmbillede af indstillingerne under Mere i navigationsruden, hvor Scanner er markeret.](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

1. Hvis kameraet ikke er aktiveret, skal du godkende Power BI-appen for at bruge kameraet. Dette er en engangsgodkendelse. 
1. Peg på scanneren med en stregkode på det element, du er interesseret i. Du får vist en liste over rapporter, der indeholder stregkodefelter.
1. Find den rapport, du søger efter, og tryk på for at åbne den på din enhed, der automatisk filtreres efter den kode, du har scannet. Hvis rapporten ikke indeholder stregkoden, får du meddelelsen "vi kunne ikke filtrere rapporten". Hvis det er tilfældet, kan du gå tilbage til listen og prøve en anden rapport.
    
>[!NOTE]
>Hvis der kun er én rapport med et stregkodefelt, får du ikke vist en liste over rapporter, men i stedet bliver rapporten åbnet direkte og filtreret efter den stregkode, du har scannet. Hvis rapporten ikke indeholder den stregkode, du har scannet, får du også meddelelsen "vi kunne ikke filtrere rapporten".

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Filtrer efter andre stregkoder, mens du befinder dig inde i en rapport
Mens du ser på en rapport, der er filtreret efter en stregkode på din enhed, kan det være du gerne vil filtrere den samme rapport ud fra en anden stregkode.

Tryk på **flere indstillinger (...)** på rapportens handlingslinje, og Find stregkode ikonet.

* Hvis stregkode ikonet er udfyldt, skal du ![Ikonet Filtreret](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), er filtret aktivt, og rapporten er allerede filtreret efter en stregkode. 
* Hvis ikonet er klart ![Ikonet Ufiltreret](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), er filtret ikke aktivt, og rapporten er ikke filtreret efter en stregkode. 

I begge tilfælde skal du trykke på ikonet for at åbne en lille menu med en flydende scanner.

* Ret scanneren mod det nye element for at ændre filtret for rapporten til en anden stregkodeværdi. 
* Vælg **Ryd stregkodefilter** for at gå tilbage til den ufiltrerede rapport.
* Vælg **Filtrer efter de seneste stregkoder** for at ændre rapportfiltret til en af de stregkoder, du har scannet i den aktuelle session.

## <a name="clear-a-barcode-filter"></a>Ryd et stregkode filter
Sådan ryddes stregkode filtreringen i en filtreret rapport:
1. Tryk på **flere indstillinger (...)** på rapportens handlingslinje, og Find det filtrerede ikon for stregkodescanner ikoner ![ ](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) , der angiver, at et filter er aktivt, og tryk på det for at åbne scanneren.
1. Vælg **Ryd stregkodefilter** for at gå tilbage til den ufiltrerede rapport.

## <a name="limitations"></a>Begrænsninger

* Ruden filtre giver ingen indikation af stregkode filtrering. Hvis du vil vide, om en rapport i øjeblikket er filtreret efter en stregkode, skal du kigge på ikonet på menupunktet stregkode scanner:

    ![Ikonet Filtreret](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) Angiver, at rapporten i øjeblikket er filtreret efter en stregkode.
    
    ![Ikonet Ufiltreret](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png) Angiver, at rapporten i øjeblikket ikke er filtreret efter en stregkode. 
* Mobile Apps understøtter kun stregkode filtrering for rapporter, der kun indeholder én stregkode kolonne på tværs af alle rapportdata tabeller. Hvis du scanner en stregkode for en rapport, der har mere end én stregkode kolonne, foretages der ingen filtrering.

## <a name="issues-with-scanning-a-barcode"></a>Problemer med at scanne en stregkode
Her er nogle problemer, der kan opstå, når du scanner en stregkode på et element.

* Du modtager en meddelelse, der **ikke kan filtreres. det ser ud til, at denne stregkode ikke findes i rapportdataene**: det betyder, at værdien af den stregkode, du har scannet, ikke vises i datamodel for den rapport, du valgte at filtrere. Det kan f. eks. være tilfældet, hvis det produkt, hvis stregkode du har scannet, ikke er inkluderet i rapporten. Du kan scanne et andet produkt, vælge en anden rapport (hvis der findes flere rapporter) eller få vist rapporten ufiltreret.

* Du får vist en meddelelse **, når du ikke har nogen rapporter, der kan filtreres efter stregkoder**: det betyder, at du ikke har nogen rapporter med stregkode, der er aktiveret. Stregkodescanneren kan kun filtrere rapporter, som har en kolonne, der er markeret som **Stregkode**. Kontrollér, at du eller rapportens ejer har mærket en kolonne som **Stregkode** i Power BI Desktop. Få mere at vide om [markering af et stregkodefelt i Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md)

* Filtrering returnerer en tom tilstand. Det kan betyde, at den Stregkodeværdi, du scannede, findes i din model, men alle eller nogle af de visuelle elementer i rapporten indeholder ikke denne værdi. Hvis det er tilfældet, kan du prøve at kigge på andre rapportsider eller redigere dine rapporter i Power BI Desktop for at indeholde denne værdi 

## <a name="next-steps"></a>Næste trin
* [Markér et stregkodefelt i Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md)
* [Dashboard-felter i Power BI](../end-user-tiles.md)
* [Dashboards i Power BI](../end-user-dashboards.md)