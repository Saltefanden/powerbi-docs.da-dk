---
title: Fejlfinding af ikke-understøttet datakilde til opdatering
description: Fejlfinding af ikke-understøttet datakilde til opdatering
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 05/08/2020
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4ab84a4f40acff894416fe2e5b33788c413ad4f5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410752"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Fejlfinding af ikke-understøttet datakilde til opdatering
Du får muligvis vist en fejl, når du forsøger at konfigurere et datasæt til planlagt opdatering.

```output
You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.
```

Det sker, når den datakilde, du har brugt i Power BI Desktop, ikke understøttes til opdatering. Du skal finde den datakilde, du bruger, og holde den op mod listen over understøttede datakilder under [Opdater data i Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Find datakilden
Hvis du ikke er sikker på, hvilken datakilde, der er blevet brugt, kan du finde ud af det ved hjælp af følgende trin i Power BI Desktop.  

1. Kontrollér, at du befinder dig i ruden **Rapport** i Power BI Desktop.  
   ![Rude til skrivebordsrapport](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Vælg **Rediger forespørgsler** fra linjen på båndet.  
   ![Rediger forespørgsler](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Vælg **Avanceret editor**.  
   ![Avanceret editor](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Notér dig den provider, der er angivet som kilde.  I dette eksempel er ActiveDirectory provider.  
   ![Datakildeprovider](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Sammenlign provideren med listen over understøttede datakilder, som findes i [Power BI-datakilder](power-bi-data-sources.md).

> [!NOTE]
> I forbindelse med opdateringsproblemer, der er relateret til dynamiske datakilder, herunder datakilder, der omfatter håndskrevne forespørgsler, skal du se [opdatering og dynamiske datakilder](refresh-data.md#refresh-and-dynamic-data-sources).


## <a name="next-steps"></a>Næste trin
[Dataopdatering](refresh-data.md)  
[Power BI Gateway – Personal](service-gateway-personal-mode.md)  
[On-premises data gateway (Datagateway i det lokale miljø)](service-gateway-onprem.md)  
[Fejlfinding af datagatewayen i det lokale miljø](service-gateway-onprem-tshoot.md)  
[Fejlfinding af Power BI Gateway – Personlig](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
