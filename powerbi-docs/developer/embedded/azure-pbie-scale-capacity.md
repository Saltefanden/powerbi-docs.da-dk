---
title: Skaler din Power BI Embedded-kapacitet | Microsoft Docs
description: I denne artikel beskriver vi, hvordan du skalerer en Power BI Embedded-kapacitet i Microsoft Azure.
author: KesemSharabi
ms.author: kesharab
services: power-bi-embedded
editor: ''
tags: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/31/2019
ms.openlocfilehash: 0b44c9326b11491e5b9f42b4110da482f52b58dc
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417261"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Skaler din Power BI Embedded-kapacitet på Azure-portalen

I denne artikel beskriver vi, hvordan du skalerer en Power BI Embedded-kapacitet i Microsoft Azure. Du kan bruge skalering til at øge eller mindske størrelsen på din kapacitet.

Dette antager, at du har oprettet en Power BI Embedded-kapacitet. Hvis du ikke har det, kan du se [Opret Power BI Embedded-kapacitet på Azure-portalen](azure-pbie-create-capacity.md) for at komme i gang.

> [!NOTE]
> En skalering kan tage omkring et minut. I løbet af den periode vil kapaciteten ikke være tilgængelig. Integreret indhold kan muligvis ikke indlæses.

## <a name="scale-a-capacity"></a>Skaler en kapacitet

1. Log på [Azure-portalen](https://portal.azure.com/).

2. Vælg **Alle tjenester** > **Power BI Embedded** for at se dine kapaciteter.

    ![Alle tjenester på Azure-portalen](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Vælg den kapacitet, du vil skalere.

    ![Liste over Power BI Embedded-kapaciteter på Azure-portalen](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. Vælg **Prisniveau** under **Skaler** i din kapacitet.

    ![Indstilling for prisniveau under skalering](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    Dit aktuelle prisniveau er angivet med et blåt omrids.

    ![Det aktuelle prisniveau er angivet med et blåt omrids](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. Hvis du vil skalere op eller ned, skal du vælge det nye niveau, du vil skifte til. Når du vælger et nyt niveau, vises det valgte niveau med et blåt omrids. Vælg **Vælg** for at skalere til det nye niveau.

    ![Vælg nyt niveau](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    Det kan tage et minut eller to at skalere til din nye kapacitet.

6. Du kan bekræfte dit niveau under oversigtsfanen. Det aktuelle prisniveau vises.

    ![Bekræft det aktuelle niveau](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Næste trin

Hvis du vil standse din kapacitet midlertidigt eller starte den, skal du se [Stands din Power BI Embedded-kapacitet midlertidigt, og start den igen på Azure-portalen](azure-pbie-pause-start.md).

Hvis du vil i gang med at integrere Power BI-indhold i din app, skal du se [Sådan integrerer du Power BI-dashboards, -rapporter og -felter](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
