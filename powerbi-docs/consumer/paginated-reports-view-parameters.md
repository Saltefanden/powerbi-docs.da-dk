---
title: Få vist parametre for sideinddelte rapporter i Power BI-tjenesten
description: I denne artikel kan du læse om, hvordan du arbejder med parametre for sideinddelte rapporter i Power BI-tjenesten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 09/28/2020
ms.openlocfilehash: 37ec4b9f38287b893469de2bcf152a6aba9886ad
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/29/2020
ms.locfileid: "91528223"
---
# <a name="view-parameters-for-paginated-reports-in-the-power-bi-service"></a>Få vist parametre for sideinddelte rapporter i Power BI-tjenesten

I denne artikel kan du læse om, hvordan du arbejder med parametre for sideinddelte rapporter i Power BI-tjenesten.  En rapportparameter gør muligt at filtrere rapportdata. Parametre giver en liste over tilgængelige værdier. Du kan vælge en eller flere værdier, eller du kan skrive i et parametertekstfelt for at søge efter værdier. Nogle gange har parametre en standardværdi, og nogle gange skal du vælge en værdi, før du ser rapporten.  

Når du får vist en rapport, der indeholder parametre, viser værktøjslinjen for rapportfremviseren de enkelte parametre, så du kan angive værdier interaktivt. I illustrationen nedenfor vises parameterområdet for en rapport med parametre for **Buying Group**, **Location**, **From Date** og **To Date**.  

## <a name="parameters-pane-in-the-power-bi-service"></a>Ruden Parameters i Power BI-tjenesten

![Få vist sideinddelt rapport med parametre](media/paginated-reports-view-parameters/power-bi-paginated-view-parameters.png)
  
1.  **Ruden Parameters** På værktøjslinjen i rapportfremviseren vises der en prompt, f.eks. "Required", eller en standardværdi for de enkelte parametre.    
  
2.  **Parametrene Invoices From/To Date** De to datoparametre har standardværdier. Hvis du vil ændre datoen, skal du angive en dato i tekstfeltet eller vælge en dato i kalenderen.  
  
3.  **Parameteren Location** Placeringsparameteren er angivet, så du kan vælge en, mange eller alle værdier. 
  
4.  **View Report** Når du har angivet eller ændret parameterværdier, skal du klikke på **View Report** for at køre rapporten. 

5. **Default values** Hvis alle parametre har standardværdier, køres rapporten automatisk ved første visning. Nogle parametre i denne rapport har ikke standardværdier, så du kan ikke se rapporten, før du vælger værdier.  

## <a name="next-steps"></a>Næste trin

[Sideinddelte rapporter i Power BI-tjenesten](end-user-paginated-report.md)
