---
title: Optimer et dashboard til mobiltelefoner – Power BI
description: Lær at oprette en tilpasset visning af et dashboard i Power BI-tjenesten, der er specialdesignet til visning på mobiltelefoner.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.custom: contperf-fy21q2
ms.topic: how-to
ms.date: 04/18/2019
LocalizationGroup: Dashboards
ms.openlocfilehash: 3e8733a20a812d74bc09ef1cf91778b5dd37bcfe
ms.sourcegitcommit: a92a3570eb14793a758a32e8fa1a756ec5d83f8c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/21/2020
ms.locfileid: "97708082"
---
# <a name="optimize-a-dashboard-for-mobile-phones---power-bi"></a>Optimer et dashboard til mobiltelefoner – Power BI 
Når du får vist dashboards i stående retning på en telefon, vil du opdage, at dashboardfelterne har den samme størrelse og er placeret efter hinanden et ad gangen. I Power BI-tjenesten kan du oprette en tilpasset visning af et dashboard specifikt til stående retning på telefoner. Selvom du opretter en telefonvisning, vil du se dashboardet, som det ser ud i tjenesten, når du vender telefonen om på siden.

Leder du efter oplysninger om visning af dashboards på en mobilenhed? Prøv i stedet denne hurtig start [Udforsk dashboards og rapporter i Power BI-mobilapps](../consumer/mobile/mobile-apps-quickstart-view-dashboard-report.md).

> [!NOTE]
> Når du redigerer telefonvisningen, kan alle, der ser dashboardet på en telefon, i realtid se de ændringer, du foretager. Hvis du eksempelvis frigør alle felter i dashboardets telefonvisning, har dashboardet på telefonen pludseligt ingen felter. 
> 
> 

## <a name="create-a-phone-view-of-a-dashboard"></a>Opret en telefonvisning af et dashboard
1. Åbn et dashboard i Power BI-tjenesten.
2. Vælg pilen ud for **Webvisning** i øverste højre hjørne > vælg **Telefonvisning**.

    ![Skærmbillede af rullemenuen Webvisning, hvor en pil peger på Telefonvisning.](media/service-create-dashboard-mobile-phone-view/power-bi-service-phone-view-dashboard.png)

    Hvis du ikke er ejeren af dashboardet, kan du ikke se denne indstilling.

    ![Skærmbillede af et telefondashboard, der viser indstillingen Rediger visning, der giver mulighed for at frigøre, tilpasse størrelsen på og omarrangere felter, så de passer til telefonvisningen.](media/service-create-dashboard-mobile-phone-view/power-bi-mobile-edit-phone-view-canvas.png)

    Visningen til redigering af telefonens dashboard åbnes. Her kan du frigøre, tilpasse størrelsen på og omarrangere felter, så de passer til telefonvisningen. Webversionen af dashboardet ændres ikke.


1. Vælg et felt for at trække, tilpasse eller frigøre det. Du kan se, at de andre felter flyttes væk, når du trækker et felt.
   
    ![Skærmbillede af telefonfelter, der viser muligheder for at trække, tilpasse størrelsen af eller frigøre felter.](media/service-create-dashboard-mobile-phone-view/power-bi-unpin-tile-phone-dashboard.png)
   
    De frigjorte felter flyttes til ruden Frigjorte felter, hvor de bliver, medmindre du tilføjer dem igen.
   
    ![Skærmbillede af et telefondashboard, der viser felter i ruden Frigjorte felter.](media/service-create-dashboard-mobile-phone-view/power-bi-mobile-edit-phone-view-post-edit.png)
2. Hvis du skifter mening, skal du vælge **Nulstil felter**, og de vender tilbage til den tidligere størrelse og rækkefølge.
   
    ![Skærmbillede af ruden Frigjorte felter, hvor en pil peger på Nulstil felter.](media/service-create-dashboard-mobile-phone-view/power-bi-service-phone-view-reset-tiles.png)
   
    Størrelsen og formen på felterne på en telefon ændres kun en lille smule, hvis du kun åbner visningen til telefonredigering i Power BI-tjenesten. Så hvis dashboardet skal vende tilbage til den nøjagtige tilstand, før du åbnede det i visningen til telefonredigering, skal du vælge **Nulstil felter**.
3. Når du er tilfreds med telefonens dashboardlayout, skal du vælge pilen ud for **Telefonvisning** i øverste højre hjørne > vælge **Webvisning**.
   
    Power BI gemmer telefonlayoutet automatisk.

## <a name="next-steps"></a>Næste trin
* [Opret rapporter, der er optimeret til Power BI-telefonapps](desktop-create-phone-report.md)
* [Opret dynamiske visualiseringer, der er optimeret til alle størrelser](../visuals/power-bi-report-visualizations.md)
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
