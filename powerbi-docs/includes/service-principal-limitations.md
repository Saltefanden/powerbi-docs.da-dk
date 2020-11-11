---
title: Begrænsninger for tjenesteprincipal
description: Begrænsninger for tjenesteprincipal
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: f55cf56edbc26d58dcfb5d67f46a908625ebcf30
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/10/2020
ms.locfileid: "94425315"
---
## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

* Tjenesteprincipalen fungerer kun med [nye arbejdsområder](../collaborate-share/service-create-the-new-workspaces.md).
* **Mit arbejdsområde** understøttes ikke til brug sammen med tjenesteprincipalen.
* Der kræves en kapacitet for at kunne flytte til produktion.
* Du kan ikke logge på Power BI-portalen ved hjælp af en tjenesteprincipal.
* Der kræves rettigheder som Power BI-administrator for at kunne aktivere tjenesteprincipalen under Indstillinger for udvikler på Power BI-administrationsportalen.
* Programmer til [integration i din organisation](../developer/embedded/embed-sample-for-your-organization.md) kan ikke bruge en tjenesteprincipal.
* Administration af [dataflow](../transform-model/dataflows/dataflows-introduction-self-service.md) understøttes ikke.
* Tjenesteprincipaler understøtter i øjeblikket ingen administrator-API'er.
* Når du bruger en tjenesteprincipal med en [Azure Analysis Services](/azure/analysis-services/analysis-services-overview)-datakilde, skal selve tjenesteprincipalen have tilladelser til en forekomst af Azure Analysis Services. Brug af en sikkerhedsgruppe, der indeholder tjenesteprincipalen til dette formål, fungerer ikke.