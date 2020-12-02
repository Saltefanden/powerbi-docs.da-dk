---
title: Hent yderligere diagnosticeringsoplysninger
description: Disse instruktioner indeholder to potentielle muligheder for manuelt at indsamle flere diagnosticeringsoplysninger fra Power BI-webklienten.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/17/2019
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 856eb4ca9b8c8afab90d351b5a025c2198b393b1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413719"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Hent yderligere diagnosticeringsoplysninger til Power BI

Denne artikel indeholder vejledning i, hvordan du manuelt indsamler flere diagnosticeringsoplysninger fra Power BI-webklienten.

1. Gå til [Power BI](https://app.powerbi.com) med Microsoft Edge eller Internet Explorer.

1. Tryk på **F12** for at åbne udviklerværktøjerne i Microsoft Edge.

   ![Skærmbillede af fanen Elementer i udviklerværktøjerne i Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Vælg fanen **Netværk**. Her vises trafik, der allerede er hentet.

   ![Skærmbillede af fanen Netværk i udviklerværktøjerne i Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Du kan:

    * Navigere i vinduet og gengive et eventuelt problem.

    * Når som helst skjule og få vist vinduet med udviklerværktøjer under sessionen ved at trykke på F12.

1. Hvis du vil stoppe profileringen af sessionen, kan du vælge den røde kvadrat under fanen **Netværk** i området med udviklerværktøjer.

   ![Skærmbillede af fanen Netværk i udviklerværktøjer i Microsoft Edge med stopikonet fremhævet.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Vælg disketteikonet for at eksportere dataene som en HTTP Archive-fil (HAR).

   ![Skærmbillede af fanen Netværk i udviklerværktøjer i Microsoft Edge med disketteikonet fremhævet.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Angiv et filnavn, og gem HAR-filen.

    HAR-filen indeholder alle oplysninger om netværksanmodninger mellem browservinduet og Power BI, inklusive:

    * Aktivitets-id'erne for hver anmodning.

    * Det nøjagtige tidsstempel for hver anmodning.

    * Alle fejloplysninger, der returneres til klienten.

    Denne sporingen vil også indeholde de data, der bruges til at udfylde de visuelle elementer, der vises på skærmen.

1. Du kan levere HAR-filen til supporten til gennemsyn.

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
