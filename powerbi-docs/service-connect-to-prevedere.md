---
title: Opret forbindelse til Prevedere med Power BI
description: Prevedere til Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 44871137e63572d801525c1f070dac5d07a32308
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-prevedere-with-power-bi"></a>Opret forbindelse til Prevedere med Power BI
Få adgang til eksklusive og vigtige økonomiske oplysninger, der sikkert og proaktivt kan drive din virksomhed fremad.

Opret forbindelse til [Prevedere-indholdspakken](https://app.powerbi.com/getdata/services/prevedere) til Power BI.

>[!NOTE]
>Hvis du ikke er eksisterende Prevedere-bruger, skal du bruge [prøvenøglen](https://prevederepowerbiconnector.azurewebsites.net/static/learnmore.html) for at prøve det.

## <a name="how-to-connect"></a>Sådan opretter du forbindelse
1. Vælg **Hent data** nederst i venstre navigationsrude.
   
   ![](media/service-connect-to-prevedere/getdata.png)
2. Vælg **Hent** i feltet **Tjenester**.
   
   ![](media/service-connect-to-prevedere/services.png)
3. Vælg **Prevedere** og derefter **Hent**.
   
   ![](media/service-connect-to-prevedere/connect.png)
4. Vælg **Nøgle** som **Godkendelsesmetode**, og angiv din Prevedere API-nøgle.
   
    ![](media/service-connect-to-prevedere/creds.png)
5. Vælg **Log på** for at starte importprocessen. Når processen er færdig, vises et nyt dashboard samt rapport og model i navigationsruden. Vælg dashboardet for at få vist dine importerede data.
   
     ![](media/service-connect-to-prevedere/dashboard.png)

**Hvad nu?**

* Prøv at [stille et spørgsmål i feltet Spørgsmål og svar](service-q-and-a.md) øverst i dashboardet
* [Rediger felterne](service-dashboard-edit-tile.md) i dashboardet.
* [Vælg et felt](service-dashboard-tiles.md) for at åbne den underliggende rapport.
* Dit datasæt vil være planlagt til daglig opdatering. Du kan dog ændre tidsplanen for opdatering eller forsøge at opdatere efter behov ved hjælp af **Opdater nu**

## <a name="whats-included"></a>Følgende er inkluderet
Indholdspakken skaffer indsigt i dine salgsprognoser, prognosemodeller, overordnede indikatorer og meget mere.

## <a name="system-requirements"></a>Systemkrav
Denne indholdspakke kræver adgang til en Prevedere API-nøgle eller prøvenøglen (se nedenfor).

## <a name="finding-parameters"></a>Sådan finder du parametre
<a name="FindingParams"></a>

Eksisterende kunder har adgang til deres data ved hjælp af deres API-nøgle. Hvis du endnu ikke er kunde, kan du se et udsnit af dataene og analyserne ved hjælp af [prøvenøglen](https://prevederepowerbiconnector.azurewebsites.net/static/learnmore.html).

## <a name="troubleshooting"></a>Fejlfinding
Det kan tage et stykke tid at indlæse dataene afhængigt af størrelsen på din forekomst.

## <a name="next-steps"></a>Næste trin
[Kom i gang i Power BI](service-get-started.md)

[Hent data i Power BI](service-get-data.md)
