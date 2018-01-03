---
title: "Fastgør en hel rapportside til et Power BI-dashboard "
description: "Dokumentationen om, hvordan du fastgør en hel dynamisk rapportside til et Power BI-dashboard fra en rapport."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/28/2017
ms.author: mihart
ms.openlocfilehash: ee8e7541db7f40a5d01607c6551ee734eb9f3d5b
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/13/2017
---
# <a name="pin-an-entire-report-page-as-a-live-tile-to-a-power-bi-dashboard"></a>Fastgør en hel rapportside, som et dynamisk felt, til et Power BI-dashboard
En anden måde at tilføje et nyt [dashboardfelt](service-dashboard-tiles.md) på er ved at fastgøre en hel rapportside.  Dette er en nem metode til at fastgøre mere end én visualisering ad gangen.  Når du fastgør en hel side, er felterne også *dynamiske*, og du kan interagere med dem direkte på dashboardet. Og de ændringer, du foretager af visualiseringerne i rapporteditoren, f.eks. ved at tilføje et filter eller ændre de felter, der bruges i diagrammet, afspejles også i dashboardfeltet.  

> [!NOTE]
> Du kan ikke fastgøre felter fra rapporter, der deles med dig.
> 
> 

## <a name="pin-a-report-page"></a>Fastgør en rapportside
Se Amanda fastgøre en dynamisk rapportside til et dashboard, og følg derefter den trinvise vejledning under videoen for selv at prøve det.

<iframe width="560" height="315" src="https://www.youtube.com/embed/EzhfBpPboPA" frameborder="0" allowfullscreen></iframe>


1. Åbn en rapport i [redigeringstilstand](service-interact-with-a-report-in-editing-view.md).
2. Vælg **Fastgør dynamisk side** på menulinjen, uden at der er valgt visualiseringer.
   
   ![](media/service-dashboard-pin-live-tile-from-report/pbi-pin-live-page.png) 
3. Fastgør feltet til et eksisterende dashboard eller til et nyt dashboard. Læg mærke til den fremhævede tekst: *Med Fastgør dynamisk side kan du få ændringer af rapporter vist i dashboardfeltet, når siden opdateres.*
   
   * Eksisterende dashboard: Vælg navnet på dashboardet på rullelisten. Dashboards, der er blevet delt med dig, vises ikke på rullelisten.
   * Nyt dashboard: Skriv navnet på det nye dashboard.
     
     ![](media/service-dashboard-pin-live-tile-from-report/pbi-pin-live-page-dialog.png)
4. Vælg **Fastgør dynamisk**. En meddelelse om fuldførelse (næsten helt oppe i højre hjørne) giver dig besked om, at siden er blevet føjet til dit dashboard som et felt.

## <a name="open-the-dashboard-to-see-the-pinned-live-tile"></a>Åbn dashboardet for at se det fastgjorte felt
1. Vælg dashboardet med det nye dynamiske felt i navigationsruden. Her kan du f.eks. [omdøbe, ændre størrelse på, sammenkæde og flytte](service-dashboard-edit-tile.md) den fastgjorte rapportside.  
2. Interager med det dynamiske felt.  På skærmbilledet herunder har valg af en søjle i søjlediagrammet filtreret og fremhævet de andre visualiseringer i feltet i tværgående retning.
   
    ![](media/service-dashboard-pin-live-tile-from-report/pbi-live-tile.png)

## <a name="next-steps"></a>Næste trin
[Dashboards i Power BI](service-dashboards.md)

Har du flere spørgsmål? [Prøv Power BI-community'et](http://community.powerbi.com/)
