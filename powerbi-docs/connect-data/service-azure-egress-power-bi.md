---
title: Udgående data i Power BI og Azure
description: Forstå gebyrer for udgående data i Azure og Power BI, afhængigt af lejerplacering og Power BI Premium
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Data from databases
ms.openlocfilehash: ec47968294e0fd905d1733bdb30ae1840069aed7
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597484"
---
# <a name="power-bi-and-azure-egress"></a>Udgående data i Power BI og Azure

Der kan påløbe gebyrer for båndbredde for data, der flyttes ud af Azure-datacentre (udgående data). Når du bruger Power BI sammen med Azure-datakilder, kan du undgå gebyrer for udgående data i Azure ved at sørge for, at din Power BI-lejer er i samme område som dine Azure-datakilder.

Når din Power BI-lejer er installeret i det samme Azure-område, som du installerer dine datakilder i, skal du ikke betale gebyrer for udgående data for planlagte opdateringer og DirectQuery-interaktioner. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Sådan afgør du, hvor din Power BI-lejer er placeret

Du kan finde ud af, hvor din Power BI-lejer er placeret, i artiklen [Hvor findes min Power BI-lejer](../admin/service-admin-where-is-my-tenant-located.md).

For Power BI Premium Multi-Geo-kunder forholder det sig sådan, at hvis din Power BI-lejer ikke er i den optimale placering for nogle af dine Azure-baserede datakilder, kan du installere Power BI Premium Multi-Geo i det ønskede Azure-område og få fordel af at have din Power BI-lejer og Azure-datakilder i det samme Azure-område.

## <a name="next-steps"></a>Næste trin

Du kan få flere oplysninger om Power BI Premium eller Multi-Geo i følgende ressourcer:

* [Prisoplysninger for Azure-båndbredde](https://azure.microsoft.com/pricing/details/bandwidth/)
* [Hvad er Microsoft Power BI Premium?](../admin/service-premium-what-is.md)
* [Sådan køber du Power BI Premium](../admin/service-admin-premium-purchase.md)
* [Multi-Geo-understøttelse af Power BI Premium (prøveversion)](../admin/service-admin-premium-multi-geo.md)
* [Hvor findes min Power BI-lejer?](../admin/service-admin-where-is-my-tenant-located.md)
* [Ofte stillede spørgsmål om Power BI Premium](../admin/service-premium-faq.md)
