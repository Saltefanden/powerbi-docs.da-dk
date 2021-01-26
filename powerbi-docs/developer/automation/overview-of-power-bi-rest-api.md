---
title: Hvad kan jeg bruge Power BI-API'en til i en integreret Power BI-analyse for at få bedre integreret BI-indsigt?
description: Hvad kan jeg bruge Power BI-API'en til? Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 03/25/2019
ms.openlocfilehash: 8fac168bf4e2d1cb7b386a1e22da99f39b579da8
ms.sourcegitcommit: 84f0e7f31e62cae3bea2dcf2d62c2f023cc2d404
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/26/2021
ms.locfileid: "98781578"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>Hvad kan udviklere bruge Power BI-API'en til?

Ved hjælp af REST API for Power BI kan du oprette apps, der kan integreres med Power BI-rapporter, -dashboards og -felter.

Med REST API for Power BI er det muligt at udføre administrationsopgaver på Power BI-objekter som rapporter, datasæt og arbejdsområder.

Her er nogle af de ting, du kan bruge Power BI-API'erne til.

| **Få mere at vide** | **Referer til disse oplysninger** |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| Integrer rapporter, dashboards og felter både for brugere af Power BI og brugere, der ikke anvender Power BI. | [Sådan integreres Power BI-dashboards, -rapporter og -felter](../embedded/embed-sample-for-customers.md) |
| Udfør administrationsopgaver på Power BI-objekter. | [Reference til Power BI REST-API](/rest/api/power-bi/) |
| Udvid en eksisterende forretningsarbejdsproces til at overføre vigtige data til et Power BI-dashboard. | [Send data via push til et dashboard](walkthrough-push-data.md) |
| Godkend til Power BI. | [Godkend til Power BI](../embedded/get-azuread-access-token.md) |

> [!NOTE]
> Power BI-API'erne refererer stadig til arbejdsområder som grupper. Referencer til grupper betyder, at du arbejder med arbejdsområder.

## <a name="api-developer-tools"></a>API-udviklerværktøjer

| Værktøj(er) | Beskrivelse |
|---------|-------------|
| [Værktøj til teststed](https://microsoft.github.io/PowerBI-JavaScript/demo) | Få et komplet eksempel på, hvordan du bruger Power BI integrerede API'er til analyse klient. Med dette værktøj kan du nemt prøve dig frem med forskellige typer Power BI Embedded-eksempler. |
| [Power BI integrerede API'er til analyse klient](/javascript/api/overview/powerbi/) | Du kan få flere oplysninger om Power BI-klient-API'erne. |
| [Postman](https://www.getpostman.com/) | Kør anmodninger, test, find fejl, overvåg, kør automatiserede test og meget mere. |

## <a name="push-data-into-power-bi"></a>Overfør data til Power BI

Du kan bruge Power BI-API'en til at [sende data til et datasæt via push](walkthrough-push-data.md). Denne funktion giver dig mulighed at føje en række til en tabel i et datasæt. De nye data afspejles derefter på felter på et dashboard og i visualiseringer i rapporten.

![Eksempel på pushdata](media/overview-of-power-bi-rest-api/powerbi-push-data.png)

## <a name="github-repositories"></a>GitHub-lagre

* [Eksempler på Power BI Developer](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [.NET-SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [Power BI integrerede API'er til analyse klient](/javascript/api/overview/powerbi/)

## <a name="next-steps"></a>Næste trin

* [Overfør data til et datasæt](walkthrough-push-data.md)
* [Udvikling af en Power BI-cirkelkortvisualisering](../visuals/develop-circle-card.md)
* [Reference til Power BI REST API](rest-api-reference.md)
* [REST-API'er til Power BI](/rest/api/power-bi/)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)