---
title: Begrænsninger for Power BI REST API i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: Der er følgende begrænsninger for Power BI REST API'en. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 1196917f0223ccde012d203d75c4e96fbc3b9dcf
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887655"
---
# <a name="power-bi-rest-api-limitations"></a>Begrænsninger for REST-API'er til Power BI  
  
**Til POST-rækker**
  
* Maks. 75 kolonner
* Maks. 75 tabeller
* Maks. 10.000 rækker pr. enkelt anmodning om POST-rækker  
* 1.000.000 rækker tilføjet pr. time pr. datasæt  
* Maks. 5 ventende anmodninger om POST-rækker pr. datasæt  
* 120 anmodninger om POST-rækker pr. minut pr. datasæt
* Hvis tabellen indeholder 250.000 rækker eller flere, 120 anmodninger om POST-rækker pr. time pr. datasæt
* Maks. 200.000 rækker, der lagres pr. tabel i FIFO datasæt
* Maks. 5.000.000 rækker, der lagres pr. tabel i 'none rentention policy'-datasæt  
* 4.000 tegn pr. værdi for strengkolonne i POST-rækkehandling
  
## <a name="see-also"></a>Se også

* [Grænser og begrænsninger for Azure AD-tjenesten](/azure/active-directory/active-directory-service-limits-restrictions)   
* [Oversigt over Power BI REST-API](/rest/api/power-bi/)