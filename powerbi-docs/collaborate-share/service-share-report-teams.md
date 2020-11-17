---
title: Del direkte i Microsoft Teams fra Power BI-tjenesten
description: Du kan dele Power BI-dashboards og -rapporter direkte i Microsoft Teams fra Power BI-tjenesten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 07/31/2020
ms.openlocfilehash: ae3f6b5f3026adf127b53dd07118fe05e4c06a00
ms.sourcegitcommit: 1b3a626c5ca612a7f23058f8e5cc0147a94db51c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348076"
---
# <a name="share-directly-to-microsoft-teams-from-the-power-bi-service"></a>Del direkte i Microsoft Teams fra Power BI-tjenesten

Du kan dele Power BI-dashboards, -rapporter og -visualiseringer direkte i Microsoft Teams fra Power BI-tjenesten. Brug funktionen **Del i Teams** til hurtigt at starte samtaler, når du får vist rapporter og dashboards i Power BI-tjenesten.

## <a name="requirements"></a>Krav

Hvis du vil bruge **Del i Teams**-funktionalitet i Power BI, skal du sørge for følgende:

- Power BI-administratorer har ikke deaktiveret lejerindstillingen **Del i Teams** på Power BI-administrationsportalen. Denne indstilling giver organisationer mulighed for at skjule **Del i Teams**-knapper. Du kan finde flere oplysninger i artiklen om [Power BI-administrationsportalen](../admin/service-admin-portal.md#share-to-teams-tenant-setting).

Under [Samarbejd i Microsoft Teams med Power BI](service-collaborate-microsoft-teams.md) kan du se, hvordan Power BI og Microsoft Teams arbejder sammen, herunder andre krav.

## <a name="share-power-bi-content-to-microsoft-teams"></a>Del Power BI-indhold i Microsoft Teams

Følg disse trin for at dele links til rapporter, dashboards og visualiseringer i Power BI-tjenesten med Microsoft Teams-kanaler og -chats.

1. Vælg en af disse indstillinger:

   * **Del i Teams** på handlingslinjen i et dashboard eller en rapport:

       ![Skærmbillede af knappen Del i Teams på handlingslinjen.](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * **Del i Teams** i genvejsmenuen for en enkelt visualisering:
    
      ![Skærmbillede af knappen Del i Teams i en genvejsmenu for en visualisering.](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. Vælg det team eller den kanal, du vil sende linket til, i dialogboksen **Del i Microsoft Teams**. Du kan tilføje en meddelelse, hvis du vil. Du bliver muligvis bedt om at logge på Microsoft Teams først.

    ![Skærmbillede af dialogboksen Del i Microsoft Teams med oplysninger og meddelelse.](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. Vælg **Del** for at sende linket.
    
1. Linket føjes til eksisterende samtaler eller starter en ny chat.

    ![Skærmbillede af Microsoft Teams-samtale med link til et Power BI-element.](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. Vælg linket for at åbne elementet i Power BI-tjenesten.

1. Hvis du har brugt genvejsmenuen for et bestemt visual, fremhæves visual'et, når rapporten åbnes.

    ![Skærmbillede af Power BI-rapport, der er åbnet med en bestemt visualisering fremhævet.](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

- Brugere uden en Power BI-licens eller en adgangstilladelse til rapporten, får vist meddelelsen "Indholdet er ikke tilgængeligt".
- **Del i Teams**-knapperne fungerer muligvis ikke, hvis din browser bruger strenge indstillinger for beskyttelse af personlige oplysninger. Brug indstillingen **Har du problemer? Prøv at åbne i et nyt vindue**, hvis dialogboksen ikke åbnes korrekt.
- **Del i Teams** omfatter ikke et linkeksempel.
- Linkeksempler og **Del i Teams** giver ikke brugere tilladelse til at få vist elementet. Tilladelser skal administreres separat.
- Knappen **Del i Teams** er ikke tilgængelig i genvejsmenuer for visualiseringer, når en rapportforfatter angiver **Flere indstillinger** til **Fra** for visualiseringen.
- I afsnittet [Kendte problemer og begrænsninger](service-collaborate-microsoft-teams.md#known-issues-and-limitations) i artiklen "Samarbejd i Microsoft Teams" kan du finde andre problemer.

## <a name="next-steps"></a>Næste trin

- [Samarbejd i Microsoft Teams med Power BI](service-collaborate-microsoft-teams.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/).
