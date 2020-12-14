---
title: Fastgør et felt til et Power BI-dashboard fra en rapport
description: Fastgør et felt til et Power BI-dashboard fra en rapport.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: lJKgWnvl6bQ
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 12/03/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: ad3a38fa8aef4f5404196213ebd3c7b26d3fc3b8
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2020
ms.locfileid: "96578400"
---
# <a name="pin-a-tile-to-a-power-bi-dashboard-from-a-report"></a>Fastgør et felt til et Power BI-dashboard fra en rapport

Én måde at tilføje et [dashboardfelt](../consumer/end-user-tiles.md) på er inde fra en [Power BI-rapport](../consumer/end-user-reports.md). Når du vælger et af disse felter, åbnes det i rapporten.

En hel rapportside kan fastgøres til et dashboard, hvilket kaldes fastgørelse af et *dynamisk* felt. Det kaldes et dynamisk felt, fordi du kan interagere med det på dashboardet. I modsætning til de enkelte visualiseringsfelter synkroniseres ændringer, der foretages i rapporten, automatisk med dashboardet. Du kan få mere at vide under [Fastgør en hel rapportside](#pin-an-entire-report-page).

Du kan ikke fastgøre felter fra rapporter, der er blevet delt med dig, eller fra Power BI Desktop. 

> [!TIP]
> Da nogle visualiseringer bruger baggrundsbilleder, fungerer fastgørelsen muligvis ikke, hvis baggrundsbilledet er for stort. Prøv at reducere størrelsen på billedet eller at bruge billedkomprimering.  
> 
> 

## <a name="pin-a-tile-from-a-report"></a>Fastgør et felt fra en rapport
Se Amanda oprette et dashboard ved at fastgøre visuals og billeder fra en Power BI-rapport.
    

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

Nu skal du oprette dit eget dashboard ved hjælp af en af Power BI-eksempelrapporterne.

1. Peg på den visualisering i rapporten, som du vil fastgøre, og vælg derefter fastgørelsesikonet. ![Tegnestiftikon](media/service-dashboard-pin-tile-from-report/pbi_pintile_small.png). Power BI åbner skærmbilledet **Fastgør til dashboard**.
   
     ![Fastgør til dashboardvindue](media/service-dashboard-pin-tile-from-report/pbi_themes2.png)
2. Vælg, om du vil fastgøre til et eksisterende dashboard eller et nyt dashboard.
   
   * **Eksisterende dashboard**: Vælg navnet på dashboardet på rullelisten. Dashboards, der er blevet delt med dig, vises ikke på rullelisten.
   * **Nyt dashboard**: Indtast navnet på det nye dashboard.
3. I nogle tilfælde kan det element, du er ved at fastgøre, allerede anvende et *tema*. Det kan f.eks. være visuals, der er fastgjort fra en Excel-projektmappe. Hvis det er tilfældet, skal du vælge, hvilket tema der skal anvendes på feltet.
4. Vælg **Fastgør**.
   
   En meddelelse om fuldførelse (i nærheden af øverste højre hjørne) informerer dig om, at visualiseringen blev føjet til dit dashboard som et felt.
   
   ![Meddelelse om fuldførelse](media/service-dashboard-pin-tile-from-report/pinsuccess.png)
5. Vælg dashboardet med det nye felt i navigationsruden. [Rediger feltets visning og funktion](service-dashboard-edit-tile.md), eller vælg feltet for at vende tilbage til rapporten.

## <a name="pin-an-entire-report-page"></a>Fastgør en hel rapportside
En anden mulighed er at fastgøre en hel rapportside til et dashboard, som er en nem måde at fastgøre mere end én visualisering ad gangen på. Når du fastgør en hel side, er felterne *dynamiske*. Det vil sige, at du kan interagere med dem på dashboardet. De ændringer, du foretager på visualiseringer i rapporteditoren, f.eks. ved at tilføje et filter eller ændre de felter, der bruges i diagrammet, afspejles også i dashboardfeltet.  

Du kan få mere at vide under [Fastgør en hel rapportside](service-dashboard-pin-live-tile-from-report.md).

## <a name="limitations"></a>Begrænsninger
Nogle af formateringsindstillingerne eller temaerne for rapporten anvendes ikke på visualiseringer, når du fastgør dem til et dashboard.
- Indstillinger for kant, skygge og baggrund ignoreres i det fastgjorte felt.
- For kortvisualiseringer vises den tekst, der bruges til værdien, i dashboards ved hjælp af "DIN"-skrifttypefamilien med sort tekst. Du kan ændre tekstfarven for alle felterne på et dashboard ved [at oprette et brugerdefineret dashboardtema](service-dashboard-themes.md).
- Betinget formatering anvendes ikke.
- Størrelsen af visualiseringer tilpasses, så den passer til størrelsen af feltet. Det kan resultere i forskelle i layoutet, ligesom hvis størrelsen af visualiseringen var blevet tilpasset i rapporten.

## <a name="next-steps"></a>Næste trin
- [Dashboards til brugere af Power BI-tjenesten](../consumer/end-user-dashboards.md)
- [Dashboardfelter i Power BI](../consumer/end-user-tiles.md)
- [Rapporter i Power BI](../consumer/end-user-reports.md)
- [Opdatering af data i Power BI](../connect-data/refresh-data.md)
- [Grundlæggende begreber for designere i Power BI-tjenesten](../fundamentals/service-basic-concepts.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
