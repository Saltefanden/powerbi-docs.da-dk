---
title: Samarbejd i Microsoft Teams med Power BI
description: I takt med at en distribueret og ekstern arbejdsstyrke bliver normen, anvender stadig flere organisationer Microsoft Teams til at holde medarbejderne opdateret.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 12/14/2020
ms.openlocfilehash: 7c8fa59521be1cfc8bb25fb04c3904f257fb62be
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926698"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Samarbejd i Microsoft Teams med Power BI

I takt med at en distribueret og ekstern arbejdsstyrke bliver normen, anvender stadig flere organisationer Microsoft Teams til at holde medarbejderne opdateret. I denne artikel gennemgås flere muligheder for at dele og samarbejde om interaktivt Power BI-indhold i Microsoft Teams-kanaler og -chats. 

- Med den opdaterede **Power BI**-fane til Microsoft Teams kan du [integrere interaktive rapporter i Microsoft Teams](service-embed-report-microsoft-teams.md)-kanaler og -chats. Fanen Power BI hjælper dine kolleger med at finde dit teams data og drøfte dataene i dit teams kanaler. 
- Vi opretter et [linkeksempel](service-teams-link-preview.md), når du indsætter et link til dine rapporter, dashboards og apps i Microsoft Teams-meddelelsesfeltet. Linkeksemplet viser oplysninger om linket. 
- Brug [Chat i Microsoft Teams](service-share-report-teams.md), når du får vist rapporter og dashboards i Power BI-tjenesten, til hurtigt at starte samtaler i Microsoft Teams.
- Brug [Power BI-appen i Microsoft Teams](service-microsoft-teams-app.md) for at få adgang til hele den grundlæggende funktionalitet i Power BI-tjenesten i Microsoft Teams.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Skærmbillede af en Power BI-rapport, der er integreret i en Microsoft Teams-kanal.":::

## <a name="requirements"></a>Krav

For at Power BI kan fungere i Microsoft Teams, skal du overordnet sørge for følgende:

- At brugerne har en Power BI Pro-licens, eller at rapporten er indeholdt i en [Power BI Premium-kapacitet (EM- eller P-SKU)](../admin/service-premium-what-is.md) med en Power BI-licens.
- At brugerne er logget på Power BI-tjenesten for at aktivere deres Power BI-licens.
- At brugerne opfylder kravene til at bruge **Power BI**-fanen til Microsoft Teams.

## <a name="grant-access-to-reports"></a>Giv adgang til rapporter

Integrering af en rapport i Microsoft Teams eller afsendelse af et link til et element giver ikke automatisk brugerne tilladelse til at få vist rapporten. Du skal [give brugerne tilladelse til at få vist rapporten i Power BI](service-share-dashboards.md). Du kan bruge en Microsoft 365-gruppe til dit team for at gøre det nemmere.

> [!IMPORTANT]
> Sørg for at gennemse, hvem der kan få vist rapporten, i Power BI-tjenesten, og giv adgang til dem, der er ikke angivet.

Du kan f.eks. sikre, at alle i et team har adgang til rapporter, ved at placere rapporterne i et enkelt arbejdsområde og give Microsoft 365-gruppen for dit team adgang til det.

## <a name="share-with-external-users"></a>Del med eksterne brugere

Du kan integrere en Power BI-rapport i Teams og dele den med eksterne brugere. Du skal benytte denne fremgangsmåde.

1.  Du inviterer den eksterne bruger til organisationen, hvorefter vedkommende accepterer din invitation. Se [Distribuer Power BI-indhold til eksterne gæstebrugere vha. Azure Active Directory B2B](../guidance/whitepaper-azure-b2b-power-bi.md) for at få flere oplysninger.
2.  Giv den eksterne bruger tilladelse til rapporten. Tildeling af individuelle tilladelser fungerer bedst.
3.  Sørg for, at den eksterne bruger har fået tildelt en Power BI-licens. Hvis indholdet er i en Premium-kapacitet, har brugeren kun brug for en gratis licens. Hvis det ikke er tilfældet, kan brugeren [tilmelde sig en individuel gratis prøveversion af Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).

## <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

- Power BI understøtter ikke de samme oversatte sprog som Microsoft Teams. Derfor ser du muligvis ikke den korrekte oversættelse i den integrerede rapport.
- Power BI-dashboards kan ikke integreres i **Power BI**-fanen til Microsoft Teams.
- Brugere uden en Power BI-licens eller en adgangstilladelse til rapporten, får vist meddelelsen "Indholdet er ikke tilgængeligt".
- Du har muligvis problemer med dette, hvis du bruger Internet Explorer 10. <!--You can look at the [browsers support for Power BI](../fundamentals/power-bi-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL-filtre](service-url-filters.md) understøttes ikke med **Power BI**-fanen til Microsoft Teams.
- Den nye **Power BI**-fane ikke tilgængelig i de nationale cloudmiljøer. Der er muligvis en ældre version tilgængelig, som ikke understøtter den nye arbejdsområdeoplevelse eller rapporter i Power BI-apps.
- Når du har gemt fanen, kan du ikke ændre navnet på fanen under fanen Indstillinger. Du kan bruge funktionen **Omdøb** for at ændre navnet.
- Enkeltlogon understøttes ikke for tjenesten til linkeksempler.
- Linkeksempler fungerer ikke i forbindelse med mødechat eller private kanaler.

## <a name="microsoft-power-platform-in-microsoft-teams"></a>Microsoft Power Platform i Microsoft Teams

De øvrige Microsoft Power Platform-apps kan også integreres med Microsoft Teams.

- [Power Platform Administration](/power-platform/admin/about-teams-environment)
- [Power Automate](/power-automate/teams/overview)
- [Power Apps](/powerapps/teams/overview)
- [Power Virtual Agents](/power-virtual-agents/)

## <a name="next-steps"></a>Næste trin

- [Integrer Power BI-indhold i Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Få vist et eksempel på et Power BI-link i Microsoft Teams](service-teams-link-preview.md)
- [Chat i Microsoft Teams direkte fra Power BI-tjenesten](service-share-report-teams.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/).
