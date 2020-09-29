---
title: Integrer Power BI-rapporter i Microsoft Teams
description: Du kan nemt integrere interaktive Power BI-rapporter i Microsoft Teams-kanaler og -chats. .
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 09/21/2020
ms.openlocfilehash: 0abaf886806ea783bb478f47d020daeea7829da5
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965123"
---
# <a name="embed-power-bi-content-in-microsoft-teams"></a>Integrer Power BI-indhold i Microsoft Teams

Du kan nemt integrere interaktive Power BI-rapporter i Microsoft Teams-kanaler og -chats. 

## <a name="requirements"></a>Krav

Hvis du vil bruge fanen **Power BI** i Microsoft Teams, skal du sørge for følgende:

- Microsoft Teams har **Power BI**-fanen.
- Hvis du vil tilføje en rapport i Microsoft Teams via **Power BI**-fanen, skal du mindst have rollen Læser i det arbejdsområde, der hoster rapporten. Se [Roller i de nye arbejdsområder](service-new-workspaces.md#roles-in-the-new-workspaces) for at få oplysninger om de forskellige roller.
- Brugerne skal have tilladelse til at få vist rapporten, før de kan se den under **Power BI**-fanen til Microsoft Teams.
- Brugere skal være Microsoft Team-brugere med adgang til kanaler og chats.

Under [Samarbejd i Microsoft Teams med Power BI](service-embed-report-microsoft-teams.md) kan du se, hvordan Power BI og Microsoft Teams arbejder sammen, herunder andre krav.

## <a name="embed-a-report-in-microsoft-teams"></a>Integrer en rapport i Microsoft Teams

Hvis du vil integrere din rapport i en Microsoft Teams-kanal eller -chat, skal du benytte denne fremgangsmåde.

1. Åbn en kanal eller chat i Microsoft Teams, og vælg ikonet **+** .

    ![Skærmbillede af Føj en fane til en kanal eller chat.](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

1. Vælg **Power BI**-fanen.

    ![Skærmbillede af listen over Microsoft Teams-faner, der viser Power BI.](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

1. Du kan benytte indstillingerne til at vælge en rapport fra et arbejdsområde eller en Power BI-app.

    ![Skærmbillede af indstillinger for Power BI-fanen til Microsoft Teams.](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

1. Fanenavnet opdateres automatisk, så det passer til rapportnavnet, men du kan ændre det.

1. Vælg **Gem**.

### <a name="reports-you-can-embed-on-the-power-bi-tab"></a>Rapporter, du kan integrere under Power BI-fanen

Du kan integrere følgende typer rapporter på **Power BI**-fanen:

- Interaktive og sideinddelte rapporter.
- Rapporter i **Mit arbejdsområde**, i den nye arbejdsområdeoplevelse og i klassiske arbejdsområder.
- Rapporter i Power BI-apps.

## <a name="start-a-conversation"></a>Start en samtale

Når du føjer en Power BI-rapportfane til Microsoft Teams, opretter Microsoft Teams automatisk en fanesamtale til rapporten.

- Vælg ikonet **Vis fanesamtale** i øverste højre hjørne.

    ![Skærmbillede af ikonet Vis fanesamtale.](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    Den første kommentar er et link til rapporten. Alle i den pågældende Microsoft Teams-kanal kan se og diskutere rapporten i samtalen.

    ![Skærmbillede af Fanesamtale.](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

- Når du eksporterer data fra en visualisering i en Power BI-rapport i Microsoft Teams, gemmes de automatisk i mappen Hentede filer. Det er en Excel-fil med navnet "data (*n*).xlsx", hvor *n* er det antal gange, du har eksporteret data til den samme mappe.
- Du kan ikke integrere Power BI-dashboards i **Power BI**-fanen til Microsoft Teams.
- [URL-filtre](service-url-filters.md) understøttes ikke med **Power BI**-fanen til Microsoft Teams.
- Den nye **Power BI**-fane ikke tilgængelig i de nationale cloudmiljøer. Der er muligvis en ældre version tilgængelig, som ikke understøtter den nye arbejdsområdeoplevelse eller rapporter i Power BI-apps.
- Når du har gemt fanen, kan du ikke ændre navnet på fanen under fanen Indstillinger. Du kan bruge funktionen **Omdøb** for at ændre navnet.
- I afsnittet [Kendte problemer og begrænsninger](service-collaborate-microsoft-teams.md#known-issues-and-limitations) i artiklen "Samarbejd i Microsoft Teams" kan du finde andre problemer.

## <a name="next-steps"></a>Næste trin

- [Samarbejd i Microsoft Teams med Power BI](service-collaborate-microsoft-teams.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/).
