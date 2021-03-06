---
title: Opret parametre for sideinddelte rapporter i Power BI-tjenesten
description: I denne artikel kan du lære, hvordan du opretter parametre for sideinddelte rapporter i Power BI-tjenesten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 09/28/2020
ms.openlocfilehash: 7d874f2c9a7b8381ece151a4ac113bed5662c2e7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418158"
---
# <a name="create-parameters-for-paginated-reports-in-the-power-bi-service"></a>Opret parametre for sideinddelte rapporter i Power BI-tjenesten

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

I denne artikel kan du lære, hvordan du opretter parametre for sideinddelte rapporter i Power BI-tjenesten.  En rapportparameter gør det muligt at vælge rapportdata og variere rapportpræsentationen. Du kan angive en standardværdi og en liste over tilgængelige værdier. Dine rapportlæsere kan ændre valget. De kan også bruge tekstfelterne for parametre til at søge efter værdier. Se [Få vist parametre for sideinddelte rapporter](../consumer/paginated-reports-view-parameters.md) for at se, hvordan erhvervsbrugerne interagerer med parametre i Power BI-tjenesten.  

På følgende illustration ses visningen Design i Power BI Report Builder for en rapport med parametrene @BuyingGroup, @Customer, @FromDate og @ToDate. 
  
![Parametre i Report Builder](media/paginated-reports-parameters/power-bi-paginated-parameters-report-builder.png)
  
1.  Rapportparametrene i ruden Rapportdata.  
  
2.  Tabellen med en af parametrene i datasættet.  
  
3.  Ruden Parametre. Du kan tilpasse layoutet af parametre i ruden Parametre. 
  
4.  Parametrene @FromDate og @ToDate har datatypen **DateTime**. Når du får vist rapporten, kan du enten skrive en dato i tekstfeltet eller vælge en dato i kalenderkontrolelementet. 

5.  En af parametrene i dialogboksen **Egenskaber for datasæt**.  

  
## <a name="create-or-edit-a-report-parameter"></a>Opret eller rediger en rapportparameter  
  
1.  Åbn din sideinddelte rapport i Power BI Report Builder.

1. I ruden **Rapportdata** skal du højreklikke på **Parametre** node > **Tilføj parameter**. Dialogboksen **Egenskaber for rapportparametre** åbnes.  
  
2.  Under **Navn** skal du skrive et navn for parameteren eller acceptere standardnavnet.  
  
3.  Under **Prompt** skal du skrive en tekst, der skal vises ud for tekstfeltet Parameter, når brugeren kører rapporten.  
  
4.  Under **Datatype** skal du vælge datatypen for parameterværdien.  
  
5.  Hvis parameteren kan indeholde en tom værdi, skal du vælge **Tillad tom værdi**.  
  
6.  Hvis parameteren kan indeholde en null-værdi, skal du vælge **Tillad null-værdi**.  
  
7.  Hvis du vil tillade, at en bruger vælger mere end én værdi for parameteren, skal du vælge **Tillad flere værdier**.  
  
8.  Angiv indstillingen synlighed.  
  
    -   Du kan få vist parameteren på værktøjslinjen øverst i rapporten ved at vælge **Synlig**.  
  
    -   Hvis du vil skjule parameteren, så den ikke vises på værktøjslinjen, skal du vælge **Skjult**.  
  
    -   Hvis du vil skjule parameteren og beskytte den mod at blive ændret på rapportserveren, når rapporten er publiceret, skal du vælge **Intern**. Rapportparameteren kan derefter kun vises i rapportdefinitionen. Du skal angive en standardværdi for denne indstilling eller tillade, at parameteren accepterer en null-værdi.  
  
9. Vælg **OK**. 

## <a name="next-steps"></a>Næste trin

Se [få vist parametre for sideinddelte rapporter](../consumer/paginated-reports-view-parameters.md) for at se, hvordan parametrene ser ud i Power BI-tjenesten.

Du kan finde detaljerede oplysninger om parametre i sideinddelte rapporter under [Rapportparametre i Power BI Report Builder](report-builder-parameters.md).
