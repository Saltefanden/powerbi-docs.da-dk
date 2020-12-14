---
title: Flyt dit integrerede Power BI-program til produktion
description: Få mere at vide om, hvilke trin der kræves for at flytte dit Power BI-program til produktion.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 6132066f9b724cf5658d3e66ccb835bb23b93d39
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2020
ms.locfileid: "96907678"
---
# <a name="move-your-embedded-app-to-production"></a>Flyt et integreret program til produktion

Når du har fuldført udviklingen af dit program, skal du understøtte dit arbejdsområde med en kapacitet for at flytte det til produktion.

> [!Important]
> Alle arbejdsområder (dem, der indeholder rapporter eller dashboards, og dem, der indeholder datasættene) skal være tildelt en kapacitet.

## <a name="create-a-capacity"></a>Opret kapacitet

Når du opretter en kapacitet, kan du drage fordel af at have en ressource for dine kunder. Du kan vælge mellem to kapacitetstyper:

* **Power BI Premium** – Et Microsoft 356-abonnement på lejerniveau er tilgængeligt i to SKU-serier, *EM* og *P*. Når du integrerer Power BI-indhold, kaldes denne løsning for *integrering i Power BI*. Du kan finde flere oplysninger om dette abonnement under [Hvad er Power BI Premium?](../../admin/service-premium-what-is.md)

* **Azure Power BI Embedded** – Du kan købe en kapacitet på [Microsoft Azure-portalen](https://portal.azure.com). Dette abonnement bruger *A*-SKU'erne. Du kan finde flere oplysninger om, hvordan du opretter en kapacitet til Power BI Embedded, under [Opret kapacitet til Power BI Embedded på Azure-portalen](azure-pbie-create-capacity.md).

    > [!NOTE]
    > Med A-SKU'er kan du ikke få adgang til Power BI-indhold med en GRATIS Power BI-licens.

### <a name="capacity-specifications"></a>Specifikationer for kapacitet

I nedenstående tabel beskrives ressourcerne og begrænsningerne for hver SKU. Hvis du vil finde ud af, hvilken kapacitet der passer bedst til dine behov, skal du se tabellen [Hvilken SKU skal jeg købe til mit scenarie?](./embedded-faq.md#which-solution-should-i-choose)

| Kapacitetsnoder | V-kerner i alt | Backend-v-kerner | RAM (GB) | Frontend-v-kerner | DirectQuery/direkte forbindelser (pr. sek.) | Parallel opdatering af modeller |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>Udviklingstest

I forbindelse med udviklingstest kan du bruge integrerede prøveversionstokens med en Pro-licens. Brug en kapacitet for at integrere i et produktionsmiljø.

Antallet af prøveversionstokens til integrering, som en *tjenesteprincipal* eller *masterbruger* (masterkonto) i Power BI kan generere, er begrænset. Brug API'en [Tilgængelige funktioner](/rest/api/power-bi/availablefeatures/getavailablefeatures) til at kontrollere procentdelen af dit aktuelle integrerede forbrug. Forbrugsmængden vises pr. tjenesteprincipal eller hovedkonto.

Hvis du løber tør for integreringstokens under test, skal du købe en Power BI Embedded- eller Premium-[kapacitet](embedded-capacity.md). Der er ingen grænse for, hvor mange integreringstokens du kan generere med en kapacitet.

## <a name="assign-a-workspace-to-a-capacity"></a>Tildel et arbejdsområde til en kapacitet

Når du har oprettet en kapacitet, kan du tildele dit arbejdsområde til kapaciteten.

Alle arbejdsområder, der indeholder Power BI-ressourcer, som er relateret til det integrerede indhold (herunder datasæt, rapporter og dashboards), skal tildeles til kapaciteter. Hvis en integreret rapport og det datasæt, der er bundet til det, f.eks. er placeret i forskellige arbejdsområder, skal begge arbejdsområder tildeles til kapaciteter.

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>Tildel et arbejdsområde til en kapacitet ved hjælp af en tjenesteprincipal

Hvis du vil tildele en kapacitet til et arbejdsområde ved hjælp af en [tjenesteprincipal](embed-service-principal.md), skal du bruge [REST API'en til Power BI](/rest/api/power-bi/capacities/groups_assigntocapacity). Når du bruger REST API'er til Power BI, skal du sørge for at bruge [objekt-id'et for tjenesteprincipalen](embed-service-principal.md).

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>Tildel et arbejdsområde til en kapacitet ved hjælp af en masterbruger

Følg nedenstående trin for at tildele en kapacitet til et arbejdsområde ved hjælp af en **masterbruger**.

1. Åbn arbejdsområdet i **Power BI-tjenesten**, og vælg 

1. I **Power BI-tjenesten** skal du udvide arbejdsområder og vælge ellipsen for det arbejdsområde, du bruger til at integrere dit indhold i. Vælg derefter **Rediger arbejdsområder**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="Et skærmbillede, der viser indstillingsmenuen for arbejdsområdet på portalen for Power BI-tjenesten.":::

2. Vælg fanen **Premium**, og gør følgende:

    * Aktivér **Kapacitet**.

    * Vælg den kapacitet, du har oprettet.

    * Vælg **Gem**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="Et skærmbillede, der viser fanen med indstillinger for et Premium-arbejdsområde på portalen for Power BI-tjenesten.":::

    Når du har tildelt dit arbejdsområde til en kapacitet, vises der en diamant ud for det 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="Et skærmbillede, der viser diamanten ud for et arbejdsområde med en Premium-kapacitet på portalen for Power BI-tjenesten.":::

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Kapacitet og SKU'er i Power BI Embedded-analyser](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Kapacitetsplanlægning i Power BI Embedded-analyser](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[Overvejelser i forbindelse med generering af et integreringstoken](generate-embed-token.md)