---
title: Foretag fejlfinding af deling af dashboards og rapporter
description: Sådan løser du problemer med deling af Power BI-dashboards og -rapporter med kolleger i og uden for din organisation, og det du skal vide om at dele.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: troubleshooting
ms.date: 06/23/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 89d0ddbbcdd5caf47256fc85864590e55a1caa86
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406658"
---
# <a name="troubleshoot-sharing-dashboards-and-reports"></a>Foretag fejlfinding af deling af dashboards og rapporter

Her er nogle almindelige problemer, der kan opstå, når du deler et dashboard eller en rapport, eller når en anden deler med dig. 

## <a name="dashboard-recipients-see-a-lock-icon-in-a-tile"></a>Dashboardmodtagere får vist et låseikon i et felt

De personer, du deler med, kan få vist et låst felt i et dashboard eller meddelelsen "Tilladelse påkrævet", når de forsøger at få vist en rapport.

![Låst felt i Power Bi](media/service-share-dashboards/power-bi-locked_tile_small.png)

Her er du nødt til at give brugerne tilladelse til at tilgå det underliggende datasæt.

1. Gå til fanen **Datasæt** på listen over indhold.

1. Vælg ellipsen ( **...** ) ud for datasættet, og vælg derefter **Administrer tilladelser**.

    ![Administrer tilladelser](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Vælg **Tilføj bruger**.

    ![Vælg Tilføj bruger](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Angiv de komplette mailadresser til enkeltpersoner, distributionsgrupper eller sikkerhedsgrupper. Du kan ikke dele med dynamiske distributionslister.

    ![Tilføj mailadresser](media/service-share-dashboards/power-bi-add-user-dataset.png)

1. Vælg **Tilføj**.

## <a name="i-cant-share-a-dashboard-or-report"></a>Jeg kan ikke dele et dashboard eller en rapport

Hvis du vil dele et dashboard eller en rapport, skal du have tilladelse til at dele det underliggende indhold igen, dvs. alle relaterede rapporter og datasæt. Hvis du får vist en meddelelse, hvor der står, at du ikke må dele, skal du bede rapportens forfatter om at give dig tilladelse til at dele rapporterne og datasættene igen.

![Meddelelsen "Kan ikke dele"](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)

## <a name="i-dont-have-access-to-a-dashboard-or-report"></a>Jeg har ikke adgang til et dashboard eller en rapport

Hvis du får vist meddelelsen "Anmod om adgang", når du vælger linket til en rapport eller et dashboard, har du ikke tilladelse til at få elementet vist. Du skal [anmode om adgang til det](service-request-access.md).

## <a name="next-steps"></a>Næste trin

- [Del Power BI-dashboards og -rapporter med kolleger og andre](service-share-dashboards.md)
- [Hvordan kan jeg samarbejde på og dele dashboards og rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md)
-  [Del en filtreret Power BI-rapport](service-share-reports.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
