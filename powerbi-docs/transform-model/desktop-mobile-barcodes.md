---
title: Kode stregkodefelter i Power BI Desktop for at aktivere filtrering af stregkode scanning i mobilapps
description: Når du mærker et stregkodefelt i din model i Power BI Desktop, kan brugere af mobilapps scanne stregkoder for at få filtrerede data på deres iOS-og Android-telefoner og tablets.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/20/2021
LocalizationGroup: Model your data
ms.openlocfilehash: 4674347d3acd6520d7d156a7d1634a13df611afe
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494395"
---
# <a name="tag-barcode-fields-in-power-bi-desktop-to-enable-barcode-scan-filtering-in-the-mobile-apps"></a>Kode stregkodefelter i Power BI Desktop for at aktivere filtrering af stregkode scanning i mobilapps

I Power BI Desktop kan du [kategorisere data](desktop-data-categorization.md) i en kolonne, så Power BI Desktop ved, hvordan værdier skal behandles i visualiseringer i en rapport. Du kan også kategorisere en kolonne som **stregkode**. Når en person i virksomheden eller organisationen [scanner en stregkode](../consumer/mobile/mobile-apps-scan-barcode-iphone.md) på et produkt ved hjælp af Power bi mobilappen på deres iOS-eller Android-telefon eller tablet, får de vist en rapport, der indeholder den pågældende stregkode. Når de åbner rapporten, filtreres den automatisk efter de data, der er knyttet til den pågældende stregkode.

## <a name="categorize-barcode-data"></a>Kategoriser stregkodedata

Hvis du har en rapport, der indeholder stregkoder: 

1. Skift til data visning i Power BI Desktop.
2. Vælg den kolonne, der indeholder stregkode dataene. Se en liste over [understøttede stregkodeformater](#supported-barcode-formats) nedenfor.
3. Vælg **data kategori** stregkode under fanen **kolonne værktøjer**  >  .
   
    ![Liste over datakategorier](media/desktop-mobile-barcodes/power-bi-desktop-barcode.png)

    >[!WARNING]
    >Undlad at kategorisere mere end én kolonne på tværs af alle datatabeller i en rapport som **stregkode**. Mobile Apps understøtter kun stregkode filtrering for rapporter, der kun indeholder én stregkode kolonne på tværs af alle rapportdata tabeller. Hvis en rapport indeholder mere end én stregkode kolonne, foretages der ingen filtrering.

4. I rapportvisning skal du føje stregkodefeltet til de visuelle elementer, der skal filtreres efter stregkoden.
5. Gem rapporten, og publicer den i Power BI-tjenesten.

Når du nu åbner scanneren på Power BI-apps til iOS-og Android-telefoner og tablets og scanner en stregkode, får du vist denne rapport på listen over rapporter, der indeholder stregkoder. Når du åbner rapporten, filtreres de visuelle elementer efter den kode til produkt stregkode, du har scannet.

## <a name="supported-barcode-formats"></a>Understøttede stregkodeformater
Dette er stregkode formaterne Power BI genkender, om du kan mærke dem i en Power BI rapport: 

* UPCECode 
* Code39Code  
* A39Mod43Code 
* EAN13Code 
* EAN8Code  
* 93Code  
* 128Code 
* PDF417Code 
* Interleaved2of5Code 
* ITF14Code 

## <a name="next-steps"></a>Næste trin
* [Scan en stregkode fra appen Power BI på din iOS-eller Android-telefon eller tablet](../consumer/mobile/mobile-apps-scan-barcode-iphone.md)
* [Problemer med scannings stregkoder](../consumer/mobile/mobile-apps-scan-barcode-iphone.md#issues-with-scanning-a-barcode)
* [Datakategorisering i Power BI Desktop](desktop-data-categorization.md)  
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
