---
title: Eksempel på sideinddelte rapporter i Power BI
description: I denne artikel får du mere at vide om, hvordan du downloader og bruger eksempler på sideinddelte rapporter i Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/01/2020
ms.openlocfilehash: cf0e6a6e7cd40a5b8bb97560caf94b71c1b48e7a
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2020
ms.locfileid: "93324004"
---
# <a name="sample-power-bi-paginated-reports"></a>Eksempel på sideinddelte rapporter i Power BI


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

Denne artikel indeholder oplysninger og links til flere eksempler på sideinddelte rapporter i Power BI, der kan hentes og udforskes. De viser typiske måder, du kan bruge sideinddelte rapporter på.

## <a name="prerequisites"></a>Forudsætninger

- Du kan dele disse rapporter online, som de er, uden at det er muligt at redigere dem. Du skal bruge en licens til Power BI Pro for at gøre det. Du kan tilmelde dig en [gratis prøveversion af Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).
- Du skal også have adgang til et Power BI-arbejdsområde i en [Premium-kapacitet](../admin/service-premium-what-is.md).
- [Installér Power BI Report Builder](https://aka.ms/pbireportbuilder) fra Microsoft Download Center for at redigere disse rapporter.
- OK, nu er du klar til at [downloade disse eksempler på sideinddelte rapporter](https://github.com/microsoft/Reporting-Services/tree/master/PaginatedReportSamples) fra GitHub! Du behøver ikke at have en GitHub-konto. 


## <a name="invoice"></a>Faktura

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="Skærmbillede af eksempel på en faktura som en sideinddelt rapport i Power BI.":::


Denne sideinddelte rapport er en komplet faktura. Scenariet for denne rapport er, at du vil have en perfekt faktura, som kan udskrives. Den skal vise det samlede salg med detaljer så som varebeskrivelser, mængder, rabatter og omkostninger.

Dette eksempel fremhæver de entydige egenskaber til oprettelse af ægte fakturaer, f.eks.:  

- Et tablix (det underliggende dataområde for både tabeller og matrixer). Det viser dynamisk genereret brugerspecifikt indhold samt tema.
- Et rektangulært dataområde, der placeres i hver række i tablixet for rapportens brødtekst.
- Rapportelementer som f.eks. tekstfelter og streger.
- En rapportparameter til dynamisk at vælge indholdet. Det viste indhold gælder for et bestemt emne ved hjælp af pladsholdere for udtryk. 

Datakilde: Inkluderet i RDL-filen

## <a name="labels"></a>Etiketter

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="Skærmbillede af etiketter for sideinddelte rapporter.":::

Dette er et eksempel på en komplet sideinddelt rapport. Det er en rapport med flere kolonner, der passer perfekt til udskriftslayoutet for adresseetiketskabelonen. 

Etiketrapporter er enkle, men har et par entydige egenskaber, der kan bruges til at oprette en sideinddelt etiket:

- Et tablix med et fast antal kolonner på tre med en defineret kolonneafstand.
- Et rektangulært dataområde, der gentages på tværs af rækker og kolonner på den udskrevne side.
- En rapportparameter til at vælge det indhold, der skal vises i hvert rektangulære dataområde.

Datakilde: Inkluderet i RDL-filen

## <a name="mailing-letter"></a>Mailbrev

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="Skærmbillede af et eksempel på et brev som en sideinddelt rapport i Power BI.":::

Dette eksempel på en komplet sideinddelt rapport er beregnet til at oprette rigtige mailbreve. Scenariet for denne rapport er, at du vil have et perfekt brev med dynamisk indhold, som kan udskrives.

Dette eksempel har entydige egenskaber, f.eks.: 

- Et rektangulært dataområde, der er placeret i forskellige afsnit i rapportens brødtekst. 
- Billeder for at tilpasse brevet. 
- Et tablixdataområde (det underliggende dataområde for både tabeller og matrixer). Tablixet viser dynamisk genereret brugerspecifikt indhold.
- Rapportelementer som f.eks. tekstfelter og streger.
- En rapportparameter til dynamisk at vælge indholdet. Det viste indhold gælder for et bestemt emne ved hjælp af pladsholdere for udtryk. 

Datakilde: Inkluderet i RDL-filen

## <a name="transcript"></a>Afskrift

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="Skærmbillede af et eksempel på en afskrift som en sideinddelt rapport i Power BI.":::

Scenariet for denne rapport er, at du vil have en perfekt afskrift, som kan udskrives. Det skal indeholde dynamisk indhold med programbeskrivelser og datoer for hver studerende.

Dette eksempel på en komplet sideinddelt rapport har entydige egenskaber som f.eks.: 

- Et tablixdataområde (det underliggende dataområde for både tabeller og matrixer). Tablixet viser dynamisk genereret brugerspecifikt indhold, der gør brug af indlejrede rækkegrupper.
- Rektangulære dataområder, der er placeret i forskellige afsnit i rapportens brødtekst.
- Rapportelementer som f.eks. tekstfelter og streger.

Datakilde: Inkluderet i RDL-filen

## <a name="sales-performance"></a>Salgsresultater

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="Skærmbillede af et eksempel på en sideinddelt rapport over salgsresultater i Power BI.":::

Salgsresultater pr. land er et eksempel på en komplet sideinddelt rapport. Scenariet for denne rapport er, at du vil have en perfekt faktura, som kan udskrives, for at se det samlede salg og detaljer. Følgende funktioner er inkluderet:

- Brugen af en parameter til at udvide detaljerne i tabellen.
- Sidehoveder og sidefødder.
- Rapportelementer som f.eks. tekstfelter, linjer og rektangler ved hjælp af udtrykspladsholdere.
- Datalinjer.
- Tendenslinjer.
- Målerpaneler.

Datakilde: Inkluderet i RDL-filen
  
## <a name="next-steps"></a>Næste trin

[Publicer en sideinddelt rapport i Power BI-tjenesten](../consumer/paginated-reports-view-power-bi-service.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)