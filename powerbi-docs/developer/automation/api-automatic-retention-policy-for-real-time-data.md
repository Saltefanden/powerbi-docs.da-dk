---
title: API'er til integrerede Power BI-analyser ved hjælp af en automatisk opbevaringspolitik for data i realtid, der muliggør bedre integreret BI-indsigt
description: Få mere at vide om politikken for automatisk opbevaring i Power BI-tjenesten. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 81c975332abc4cb599a7172f1697c1b06ea34eba
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887724"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Politik for automatisk opbevaring for data i realtid

Politikken for automatisk opbevaring i Power BI-tjenesten er en parameter for en forespørgselsstreng, som gør det muligt for en standardopbevaringspolitik at rydde op i gamle data automatisk, samtidig med at en konstant strøm af nye data overføres til dit dashboard. Den første opbevaringspolitik kaldes *FIFO (først ind – først ud)*. Når den er aktiveret, samles dataene i en tabel, indtil den når 200.000 rækker. Når der er flere end 200.000 rækker med data, slettes de ældste rækker fra datasættet. På den måde gemmes mellem 200.000 og 210.000 rækker med de nyeste data.  
  
<center>

![opbevaringspolitik](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Politikkerne for opbevaring er aktiveret, når du opretter dine datasæt. Du skal blot føje parameteren "default retention policy" til dit kald til POST-datasæt og angive den til lig med *basicFIFO*.  

```console
POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}
```
