---
title: Stands din Power BI Embedded-kapacitet midlertidigt, og start den igen på Azure-portalen | Microsoft Docs
description: I denne artikel beskriver vi, hvordan du standser og starter en Power BI Embedded-kapacitet i Microsoft Azure.
author: KesemSharabi
ms.author: kesharab
services: power-bi-embedded
editor: ''
tags: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 09/28/2017
ms.openlocfilehash: 71d3536cdcda5c1b2970385887388ea60b4290af
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417307"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Stands og start din Power BI Embedded-kapacitet på Azure-portalen

I denne artikel beskriver vi, hvordan du standser og starter en Power BI Embedded-kapacitet i Microsoft Azure. Dette antager, at du har oprettet en Power BI Embedded-kapacitet. Hvis du ikke har det, kan du se [Opret Power BI Embedded-kapacitet på Azure-portalen](azure-pbie-create-capacity.md) for at komme i gang.

Hvis du ikke har et Azure-abonnement, skal du oprette en [gratis konto](https://azure.microsoft.com/free/), før du begynder.

## <a name="pause-your-capacity"></a>Stands din kapacitet midlertidigt

Når du standser din kapacitet midlertidigt, faktureres du ikke for den. Det er praktisk at standse kapaciteten midlertidigt, hvis du ikke har behov for den i et stykke tid. Gør følgende for midlertidigt at standse kapaciteten.

> [!NOTE]
> Når du standser kapaciteten midlertidigt, kan det forhindre, at der er indhold, der er tilgængeligt i Power BI. Sørg for at fjerne tildelingen af arbejdsområder fra kapaciteten, inden du midlertidigt standser den, så du undgår afbrydelser.

1. Log på [Azure-portalen](https://portal.azure.com/).

2. Vælg **Alle tjenester** > **Power BI Embedded** for at se dine kapaciteter.

    ![Alle tjenester på Azure-portalen](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Vælg den kapacitet, du vil standse.

    ![Liste over Power BI Embedded-kapaciteter på Azure-portalen](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Vælg **Stands midlertidigt** i oplysningerne om kapacitet.

    ![Stands din kapacitet midlertidigt](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Vælg **Ja** for at bekræfte, at du vil standse kapaciteten.

    ![Bekræft midlertidig standsning](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>Start kapaciteten igen

Du kan genoptage forbrug af kapaciteten ved at starte den igen. Når du starter kapaciteten igen, faktureres du også igen.

1. Log på [Azure-portalen](https://portal.azure.com/).

2. Vælg **Alle tjenester** > **Power BI Embedded** for at se dine kapaciteter.

    ![Alle tjenester på Azure-portalen](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Vælg den kapacitet, du vil starte.

    ![Liste over Power BI Embedded-kapaciteter på Azure-portalen](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Vælg **Start** i oplysningerne om kapacitet.

    ![Start kapaciteten igen](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Vælg **Ja** for at bekræfte, at du vil starte kapaciteten.

    ![Bekræft start](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Hvis der findes indhold, der er tilknyttet kapaciteten, vil det være tilgængeligt, når den starter igen.

## <a name="next-steps"></a>De næste trin

Hvis du vil skalere din kapacitet op eller ned, skal du se [Skalér din Power BI Embedded-kapacitet](azure-pbie-scale-capacity.md).

Hvis du vil i gang med at integrere Power BI-indhold i din app, skal du se [Sådan integrerer du Power BI-dashboards, -rapporter og -felter](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)