---
title: Anvend detaljeadgang på rapportsiden
description: Vejledning til arbejde med detaljeadgang på rapportsider.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/28/2019
ms.openlocfilehash: 4aa7c3992183dad6fad30e31e31e935fbaa29c32
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418480"
---
# <a name="use-report-page-drillthrough"></a>Anvend detaljeadgang på rapportsiden

Denne artikel henvender sig til rapportforfattere, der designer Power BI-rapporter. Den indeholder forslag og anbefalinger til oprettelse af [detaljeadgang på rapportsider](../create-reports/desktop-drillthrough.md).

Det anbefales, at du designer din rapport for at gøre det muligt for rapportbrugere at opnå følgende flow:

1. Få vist en rapportside.
2. Identificer et visuelt element for at analysere det mere i dybden.
3. Højreklik på det visuelle element for at få detaljeadgang.
4. Udfør supplerende analyser.
5. Vend tilbage til kilderapportsiden.

## <a name="suggestions"></a>Forslag

Vi foreslår, at du overvejer to forskellige former for detaljeadgangsscenarier:

- [Ekstra dybde](#additional-depth)
- [Bredere perspektiv](#broader-perspective)

### <a name="additional-depth"></a>Ekstra d dybde

Når der vises opsummerede resultater på din rapportside, kan en side med detaljeadgang føre rapportbrugere til detaljer på transaktionsniveau. Denne designmetode gør det muligt for dem at få vist supplerende transaktioner, og kun når det er nødvendigt.

Det følgende eksempel viser, hvad der sker, når en rapportbruger opretter detaljeadgang fra en månedlig salgsoversigt. Detaljeadgangssiden indeholder en detaljeret liste over ordrer for en bestemt måned.

![I et matrixvisual med titlen "Sales Summary" grupperes salg efter år og måned for rækkerne og land for kolonnerne. Der vises også en side med detaljeadgang.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Bredere perspektiv

Med en detaljeadgangsside kan du opnå det modsatte af ekstra dybde. Dette scenarie er fremragende til detaljeadgang i en holistisk visning.

I det følgende eksempel vises det, hvad der sker, når en rapportbruger opretter detaljeadgang fra et postnummer. På detaljeadgangssiden vises der generelle oplysninger om det pågældende postnummer.

![Et tabelvisual indeholder tre kolonner: Zip Code, Average of Violation Points og Average of Grade Rating. Detaljeadgangssiden vises også.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Anbefalinger

Vi anbefaler følgende fremgangsmåder på tidspunktet for oprettelse af rapportdesignet:

- **Typografi:** Overvej at designe din detaljeadgangsside, så du kan bruge samme tema og typografi som i rapporten. På denne måde føler brugerne, at de ser den samme rapport.
- **Detaljeadgangsfiltre:** Angiv detaljeadgangsfiltre, så du kan få vist et realistisk resultat, når du designer detaljeadgangssiden. Sørg for at fjerne disse filtre, før du publicerer rapporten.
- **Yderligere funktioner:** En detaljeadgangsside er som enhver anden rapportside. Du kan endda forbedre den med yderligere interaktive funktioner, herunder udsnitsværktøjer og filtre.
- **Tomme:** Undgå at tilføje visuals, der kan vises som BLANK eller producere fejl, når der anvendes detaljeadgangsfiltre.
- **Sidesynlighed:** Overvej at skjule detaljeadgangssider. Hvis du beslutter at beholde en detaljeadgangsside, skal du sørge for at tilføje en knap, der gør det muligt for brugerne at rydde alle tidligere angivne detaljeadgangsfiltre. Tildel et [bogmærke](../create-reports/desktop-bookmarks.md) til knappen. Bogmærket skal være konfigureret til at fjerne alle filtre.
- **Knappen Tilbage:** Der tilføjes automatisk en tilbage [knap](../create-reports/desktop-buttons.md), når du tildeler et detaljeadgangsfilter. Det er en god idé at beholde den. På denne måde kan dine rapportbrugere nemt vende tilbage til kildesiden.
- **Søgning:** Vær med til at fremme kendskabet til en detaljeadgangsside ved at angive teksten til ikonet for visualheaderen eller føje instruktioner til et tekstfelt. Du kan også designe en overlejring som beskrevet i [dette blogindlæg-](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/).

> [!TIP]
> Det er også muligt at konfigurere detaljeadgang til dine sideinddelte Power BI-rapporter. Det kan du gøre ved at føje links til Power BI-rapporter. Links kan definere [URL-parametre](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/).

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Brug detaljeadgang i Power BI Desktop](../create-reports/desktop-drillthrough.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
