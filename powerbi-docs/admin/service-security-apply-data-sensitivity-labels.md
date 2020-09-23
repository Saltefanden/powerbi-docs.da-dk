---
title: Sådan anvendes følsomhedsmærkater i Power BI
description: Få mere at vide om,hvordan du anvender følsomhedsmærkater i Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 08/16/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 9c623e180c41d60a35052ffef29e958dde79235d
ms.sourcegitcommit: cb606d3ae95300683caf1853e229d8981302a8e2
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/18/2020
ms.locfileid: "90763683"
---
# <a name="how-to-apply-sensitivity-labels-in-power-bi"></a>Sådan anvendes følsomhedsmærkater i Power BI

Microsoft Information Protection-følsomhedsmærkater til dine rapporter, dashboards, datasæt og dataflows kan beskytte dit følsomme indhold mod uautoriseret dataadgang og -lækage. Hvis du forsyner dine data med følsomhedsmærkater korrekt, sikrer du, at det kun er godkendte personer, som kan få adgang til dine data. I denne artikel kan du se, hvordan du anvender følsomhedsmærkater i dit indhold.

Sådan kan du anvende følsomhedsmærkater i Power BI:
* Du skal have en Power BI Pro-licens og redigeringstilladelser til det indhold, du vil forsyne med en mærkat.
* Du skal tilhøre en sikkerhedsgruppe, der har tilladelse til at anvende følsomhedsmærkater, som beskrevet i artiklen med titlen [Aktivér følsomhedsmærkater i Power BI](./service-security-enable-data-sensitivity-labels.md).
* Alle [licenskrav og andre krav](./service-security-enable-data-sensitivity-labels.md#licensing-and-requirements) skal være opfyldt.

Du kan finde flere oplysninger om følsomhedsmærkater i Power BI under [Følsomhedsmærkater i Power BI](service-security-sensitivity-label-overview.md).

## <a name="applying-sensitivity-labels"></a>Datafølsomhedsmærkater

Når databeskyttelse er aktiveret på din lejer, vises følsomhedsmærkater i kolonnen med følsomhed i listevisningen af dashboards, rapporter, datasæt og dataflow.

![Aktivér følsomhedsmærkater](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-01.png)

**Sådan anvender eller ændrer du en følsomhedsmærkat på en rapport eller et dashboard**
1. Klik på **Flere indstillinger (...)** .
1. Vælg **Indstillinger**.
1. I ruden med indstillinger skal du vælge den relevante følsomhedsmærkat.
1. Gem indstillingerne.

Følgende billede illustrerer disse trin i en rapport

![Angiv følsomhedsmærkater](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-02.png)

**Sådan anvender eller ændrer du en følsomhedsmærkat på et datasæt eller dataflow**

1. Klik på **Flere indstillinger (...)** .
1. Vælg **Indstillinger**.
1. I ruden med indstillinger skal du vælge den relevante følsomhedsmærkat.
1. Anvend indstillingerne.

De følgende to billeder illustrerer disse trin i et datasæt.

Vælg **Flere indstillinger (...)** og derefter **Indstillinger**.

![Åbn indstillinger for datasæt](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-05.png)

Åbn afsnittet med følsomhedsmærkater på siden Indstillinger, vælg den ønskede følsomhedsmærkat, og klik på **Anvend**.

![Vælg følsomhedsmærkat](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-06.png)

## <a name="removing-sensitivity-labels"></a>Fjernelse af følsomhedsmærkater
Hvis du vil fjerne en følsomhedsmærkat fra en rapport, et dashboard, et datasæt eller et dataflow, skal du følge [samme fremgangsmåde som for at anvende mærkater](#applying-sensitivity-labels), men du kan vælge **(Ingen)** , når du bliver bedt om at klassificere dataenes følsomhed. 

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Se [Følsomhedsmærkater i Power BI](service-security-sensitivity-label-overview.md#limitations) for at få vist en liste over begrænsninger for følsomhedsmærkater i Power BI.

## <a name="next-steps"></a>Næste trin

Denne artikel indeholdt en beskrivelse af, hvordan du anvender følsomhedsmærkater i Power BI. Følgende artikler indeholder flere oplysninger om databeskyttelse i Power BI. 

* [Oversigt over følsomhedsmærkater i Power BI](./service-security-sensitivity-label-overview.md)
* [Aktivér følsomhedsmærkater i Power BI](./service-security-enable-data-sensitivity-labels.md)
* [Brug af Microsoft Cloud App Security-kontrolelementer i Power BI](./service-security-using-microsoft-cloud-app-security-controls.md)