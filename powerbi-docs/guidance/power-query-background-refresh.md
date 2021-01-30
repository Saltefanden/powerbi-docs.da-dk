---
title: Deaktiver baggrundsopdatering i Power Query
description: Vejledning til deaktivering af baggrundsopdatering i Power Query.
author: peter-myers
ms.author: kfollis
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: e620841089cd7a039fc157fe8b3f8f0857773cb8
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087447"
---
# <a name="disable-power-query-background-refresh"></a>Deaktiver baggrundsopdatering i Power Query

Denne artikel er henvendt til udviklere af importdatamodeller, der arbejder med Power BI Desktop.

Når Power Query importerer data, cachelagres der som standard også op til 1000 rækker med eksempeldata for hver forespørgsel. Eksempeldataene er en hjælp, så du kan få en hurtig visning af kildedata og resultater af transformationer for hvert trin i dine forespørgsler. De gemmes separat på disken og ikke i Power BI Desktop-filen.

Når Power BI Desktop-filen indeholder mange forespørgsler, kan hentning og lagring af eksempeldata imidlertid forlænge den tid, det tager at fuldføre en opdatering.

## <a name="recommendation"></a>Anbefaling

Du opnår en hurtigere opdatering ved at indstille Power BI Desktop-filen til at opdatere eksempelcachen _i baggrunden_. Du aktiverer den i Power BI Desktop ved at vælge _Filer > Indstillinger og indstillinger > Indstillinger_ og derefter vælge siden _Dataindlæsning_. Du kan derefter aktivere indstillingen **Tillad, at forhåndsvisning af data downloades i baggrunden**. Bemærk, at denne indstilling kun kan angives for den aktuelle fil.

![Skærmbillede af Power BI Desktop med indstillinger for baggrundsdata.](media/power-query-background-refresh/power-query-options-background-data.png)

Aktivering af baggrundsopdatering kan resultere i, at eksempeldata bliver forældede. Hvis det sker, får du en meddelelse med den følgende advarsel i Power Query-editor:

![Skærmbillede af Power BI Desktop med advarsel fra Power Query-editor om gamle eksempeldata.](media/power-query-background-refresh/power-query-preview-data-old.png)

Det er altid muligt at opdatere eksempelcachen. Du kan opdatere den til en enkelt forespørgsel eller til alle forespørgsler ved hjælp af kommandoen **Opdater eksempel**. Du finder den på båndet **Hjem** i Power Query-editor.

![Skærmbillede af Power BI Desktop med kommandoer i Power Query-editor til opdatering af eksempeldata.](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Power Query-dokumentation](/power-query/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
