---
title: Konfigurer certificering af datasæt og dataflow (prøveversion)
description: Få mere at vide om, hvordan du konfigurerer certificeringsprocessen for datasæt og dataflow i din organisation.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 05/15/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 11079e2ab1578cfe5db352e7e3286d491bdfca2c
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/26/2020
ms.locfileid: "91374907"
---
# <a name="set-up-dataset-and-dataflow-certification-preview"></a>Konfigurer certificering af datasæt og dataflow (prøveversion)

Din organisation kan certificere datasæt og dataflows, der er den autoritative kilde til vigtige oplysninger.

Du er som Power BI-administrator ansvarlig for at konfigurere certificeringsprocessen for din organisation. Det betyder følgende:
* Aktiverer af certificering på din lejer.
* Angivelse af definitioner af en liste over grupper og brugere, der har tilladelse til at certificere datasæt og dataflows.
* Angivelse af URL-adressen til organisationens certificeringspolitik for datasæt, hvis der findes en sådan.

Certificering af datasæt og dataflwos er en del *godkendelsen* af datasættet eller dataflowet. Se [godkendelse af datasæt](../connect-data/service-datasets-promote.md) og [godkendelse af dataflow](../transform-model/service-dataflows-promote-certify.md) for at få flere oplysninger.


## <a name="set-up-certification"></a>Konfiguration af certificering

1. Gå til lejerindstillingerne i administrationsportalen.
1. Under indstillinger for eksport og deling skal du udvide afsnittet Certificering.

   ![Konfigurer certificering af datasæt og dataflow](media/service-admin-setup-certification/service-admin-certification-setup-dialog.png)

1. Slå **Aktiveret** til.
1. Hvis din organisation har en offentliggjort certificeringspolitik for datasætcertificering, kan du angive dens URL-adresse her. Dette bliver linket til **at få mere at vide** afsnittet Certificering i [dialogboksen med indstillinger for godkendelsen](../connect-data/service-datasets-promote.md#request-dataset-certification) 
1. Angiv de grupper og brugere, der har tilladelse til at certificere datasæt og dataflows. Disse godkendte certificeringseksperter kan bruge knappen Certificering i afsnittet Certificering i dialogboksen med indstillinger for godkendelsen af [datasættet](../connect-data/service-datasets-promote.md#request-dataset-certification) eller [dataflowet](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow).
1. Klik på **Anvend**.

## <a name="next-steps"></a>Næste trin
* [Fremhæv datasæt](../connect-data/service-datasets-promote.md)
* [Certificer datasæt](../connect-data/service-datasets-certify.md)
* [Fremhæv datasæt](../transform-model/service-dataflows-promote-certify.md#promote-a-dataflow)
* [Certificer datasæt](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
