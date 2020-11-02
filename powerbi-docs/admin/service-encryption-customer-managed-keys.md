---
title: Brug kundeadministrerede nøgler i Power BI
description: Få mere at vide om, hvordan du bruger kundeadministrerede nøgler i Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 10/21/2020
LocalizationGroup: Premium
ms.openlocfilehash: fc93ae0f54bfe4f72ec18687829e9eb78dfaedd7
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349362"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Brug kundeadministrerede nøgler i Power BI

Power BI krypterer inaktive og igangværende data. Power BI bruger som standard Microsoft-administrerede nøgler til kryptering af dine data. Organisationer kan vælge at bruge deres egne nøgler til kryptering af inaktivt brugerindhold i hele Power BI, fra rapportbilleder til importerede datasæt i Premium-kapaciteter. 

## <a name="why-use-customer-managed-keys"></a>Derfor skal du bruge kundeadministrerede nøgler

Med kundeadministrerede nøgler (CMK – customer-managed keys) i Power BI kan organisationer overholde gældende krav til kryptering af inaktive data hos deres udbyder af cloudtjenester (i dette tilfælde Microsoft). CMK tilbydes kun til nye Power BI Premium-kunder, og det giver organisationer mulighed for at kryptere deres Power BI-brugerindhold ved hjælp af en nøgle, som de leverer og administrerer. Hvis du tilbagekalder en kundeadministreret nøgle, bliver brugerindhold i Power BI ulæseligt for alle i løbet af en time, herunder Microsoft. Sammenlignet med BYOK-tilbuddet dækker CMK også brugerindhold, der genereres af tjenesten, foruden de kundedata, der importeres til rapporter og datasæt, som hostes på Premium-kapaciteter. Det gennemtvinger strengere politikker for cachelagring, og der kan kun anvendes en enkelt nøgle til at kryptere alle dataene.


## <a name="how-to-use-customer-managed-keys"></a>Sådan bruger du kundeadministrerede nøgler
Hvis du gerne vil tilmelde dig kundeadministrerede nøgler i Power BI, skal din organisation kontakte organisationens Microsoft-kontoadministrator for at bekræfte, at organisationen overholder visse størrelsesmæssige krav, der kræves for at aktivere CMK.  


## <a name="next-steps"></a>Næste trin

Følgende links indeholder oplysninger, der kan være nyttige i forbindelse med kundeadministrerede nøgler:

* [Medbring dine egne krypteringsnøgler til Power BI](service-encryption-byok.md)
* [Konfigurer understøttelse af Multi-Geo til Power BI Premium](service-admin-premium-multi-geo.md)
* [Sådan fungerer kapaciteter](service-premium-what-is.md#how-capacities-function)
* [Trinvis opdatering](service-premium-incremental-refresh.md)
