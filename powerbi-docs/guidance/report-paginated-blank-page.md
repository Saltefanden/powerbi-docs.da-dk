---
title: Undgå tomme sider ved udskrivning af sideinddelte rapporter
description: Vejledning i design af sideinddelte rapporter for at undgå tomme sider, når de udskrives.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: c4768f6150d3d68826a846649a161069cef30ed0
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088183"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Undgå tomme sider ved udskrivning af sideinddelte rapporter

Denne artikel henvender sig til rapportforfattere, der designer [sideinddelte rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md) i Power BI. Den indeholder anbefalinger, der kan hjælpe dig med at undgå tomme sider, når din rapport eksporteres til et hårdt sideformat – f.eks. PDF eller Microsoft Word – eller udskrives.

## <a name="page-setup"></a>Sideopsætning

Egenskaber for rapportsidestørrelsen bestemmer sideretning, dimensioner og margener. Få adgang til disse rapportegenskaber ved at:

- Bruge **Egenskabssiden** for rapporter: Højreklik på det mørkegrå område uden for rapportlærredet, og vælg derefter _Rapportegenskaber_.
- Bruge ruden med [**Egenskaber**](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane): Klik på det mørkegrå område uden for rapportlærredet for at vælge rapportobjektet. Sørg for, at ruden **Egenskaber** er åben.

På siden **Sideopsætning** på **egenskabssiden** i rapporten får du en brugervenlig grænseflade til at få vist og opdatere indstillingerne for sideopsætning.

![Billedet viser vinduet Rapportegenskaber med siden Sideopsætning fremhævet.](media/report-paginated-blank-page/report-page-setup-properties.png)

Sørg for, at alle egenskaber for sidestørrelsen er konfigureret korrekt:

|Egenskab|Anbefaling|
|---------|---------|
|Sideenheder|Vælg de relevante enheder – tommer eller centimeter.|
|Retning|Vælg den korrekte indstilling – stående eller liggende.|
|Papirstørrelse|Vælg en papirstørrelse, eller tildel brugerdefinerede værdier for bredde og højde.|
|Margener|Angiv de relevante værdier for venstre, højre, top og bund margener.|
|||

## <a name="report-body-width"></a>Bredde på rapportens brødtekst

Egenskaberne for sidestørrelse bestemmer den plads, der er tilgængelig for rapportobjekter. Rapportobjekter kan være dataområder, datavisualiseringer eller andre rapportelementer.

En almindelig årsag til, at blanke sider udskrives, er, at bredden af rapportens brødtekst _overstiger den tilgængelige sideplads_.

Du kan kun få vist og angive bredden af brødteksten i rapporten ved hjælp af ruden **Egenskaber**. Klik først et vilkårligt sted i et tomt område af rapportens brødtekst.

![Billedet viser ruden Egenskaber og fremhæver egenskaben for bredden af rapportens brødtekst.](media/report-paginated-blank-page/report-body-properties-width.png)

Sørg for, at breddeværdien ikke overstiger den tilgængelige sidebredde. Du kan få hjælp i følgende formel:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Det er ikke muligt at reducere bredden af rapportens brødtekst, når der allerede er rapportobjekter i det område, du vil fjerne. Du skal først flytte eller tilpasse størrelsen på disse objekter, før du reducerer bredden.
>
> Bredden på brødteksten i en rapport kan også øges automatisk, når du tilføjer nye objekter eller tilpasser størrelsen eller flytter eksisterende objekter. Brødteksten i rapportdesigneren gøres altid bredere, så den passer til placeringen og størrelsen af de indeholdte objekter.

## <a name="report-body-height"></a>Højde på rapportens brødtekst

En anden årsag til, at en tom side udskrives, er, at der er overskydende plads i rapportens brødtekst efter det sidste objekt.

Vi anbefaler, at du altid reducerer brødtekstens højde for at fjerne eventuel efterfølgende plads.

![Billede viser et rapportdesign. Området under tablixdataområdet fremhæves og markeres som unødvendigt.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Indstillinger for sideskift

Alle dataområder og datavisualiseringer har indstillinger for sideskift. Du kan få adgang til disse indstillinger på den tilhørende egenskabsside eller i ruden **Egenskaber**.

Sørg for, at egenskaben **Tilføj sideskift efter** ikke unødvendigt er aktiveret.

![Billedet viser tablixvinduet Egenskaber. Egenskaben Tilføj sideskift efter er aktiveret.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Anvend objektbeholdermellemrum

Hvis du stadig har problemer med tomme sider, kan du også prøve at deaktivere rapportegenskaben **ConsumeContainerWhitespace**. Den kan kun angives i ruden **Egenskaber**.

![Billedet viser ruden Egenskaber og fremhæver egenskaben ConsumeContainerWhitespace.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Den er som standard aktiveret. Den bestemmer, om det mindste mellemrum i objektbeholdere, f.eks. rapportens brødtekst eller et rektangel, skal forbruges. Kun mellemrum til højre for og nedenunder indholdet påvirkes.

## <a name="printer-paper-size"></a>Størrelsen på printerpapir

Hvis du f.eks. udskriver rapporten på papir, skal du kontrollere, at det korrekte papir er i printeren. Den fysiske papirstørrelse skal svare til [rapportens papirstørrelse](#page-setup).

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Hvad er sideinddelte rapporter i Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Sideinddeling i sideinddelte rapporter i Power BI](../paginated-reports/paginated-reports-pagination.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)
