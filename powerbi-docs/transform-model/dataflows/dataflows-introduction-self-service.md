---
title: Introduktion til dataflow og selvbetjent dataforberedelse
description: Oversigt over, hvad Power BI-dataflow er, og hvornår de skal bruges
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 23ead6afd508cc0e61ae29d65926372561a6375a
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396282"
---
# <a name="introduction-to-dataflows-and-self-service-data-prep"></a>Introduktion til dataflow og selvbetjent dataforberedelse

Efterhånden som datamængden vokser, stiger behovet for at konvertere dataene i korrekt udformede oplysninger, som der kan handles på. Vi vil gerne have data, der er klar til analyse, til udfyldning af visuelle elementer, rapporter og dashboards, så vi hurtigt kan konvertere vores datamængder til viden, som der kan handles på. Med selvbetjening til dataforberedelse til big data i Power BI kan du gå fra data til Power BI-indsigt med bare nogle få klik.

![flow af data](media/dataflows-introduction-self-service-flow.png)

## <a name="when-to-use-dataflows"></a>Hvornår bruger du dataflow?

Dataflow er udviklet til at understøtte følgende scenarier:

* Opret transformationslogik, der kan genbruges og deles af mange datasæt og rapporter i Power BI. Dataflow fremmer muligheden for at genbruge de underliggende dataelementer, så du undgår at skulle oprette separate forbindelser med datakilderne i dit cloudmiljø eller dit lokale miljø.

* Fremviser dataene i dit eget Azure Data Lake Gen 2-lager, hvilket gør det muligt for dig at oprette forbindelse mellem andre Azure-tjenester og de rå underliggende data.

* Opret en enkelt kilde til sandhed ved at tvinge analytikere til at oprette forbindelse til dataflow i stedet for at oprette forbindelse til de underliggende systemer, hvilket giver dig kontrol over, hvilke data der oprettes adgang til, og hvordan data vises for rapportoprettere. Du kan også knytte dataene til branchestandarddefinitioner, så du kan oprette overskuelige udvalgte visninger, som kan bruges sammen med andre tjenester og produkter i Microsoft Power Platform.

* Hvis du vil arbejde med store datamængder og udføre ETL i stor målestok, skaleres dataflow med Power BI Premium mere effektivt og giver dig større fleksibilitet. Dataflow understøtter en lang række kilder i cloudmiljøet og det lokale miljø. 

* Undgå, at analytikere får direkte adgang til den underliggende datakilde. Da rapportoprettere kan bygge oven på dataflow, kan det være mere praktisk for dig kun at give nogle få personer adgang til underliggende datakilder og derefter give adgang til de dataflow, som analytikerne skal bygge oven på. Denne fremgangsmåde reducerer belastningen af de underliggende systemer og giver administratorer større kontrol over, hvornår systemerne belastes af opdateringer.

Når du har oprettet et dataflow, kan du bruge Power BI Desktop og Power BI-tjenesten til at oprette datasæt, rapporter, dashboards og apps, der udnytter Common Data Model, til at få omfattende indsigt i dine forretningsaktiviteter. Planlægningen af opdateringen af dataflow styres direkte fra det arbejdsområde, hvor dit dataflow er oprettet, på samme måde som dine datasæt.

## <a name="next-steps"></a>Næste trin
Denne artikel giver et overblik over selvbetjent dataforberedelse af big data i Power BI og de mange måder, du kan bruge det på. 

Du kan finde flere oplysninger om dataflow og Power BI i følgende artikler:

* [Oprettelse af et dataflow](dataflows-create.md)
* [Konfigurer og brug et dataflow](dataflows-configure-consume.md)
* [Konfiguration af dataflowlager til brug af Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [Premium-funktioner for dataflow](dataflows-premium-features.md)
* [AI med dataflow](dataflows-machine-learning-integration.md)
* [Begrænsninger og overvejelser i forbindelse med dataflow](dataflows-features-limitations.md)


Du kan finde flere oplysninger om Common Data Model i denne oversigtsartikel:
* [Common Data Model – oversigt](/powerapps/common-data-model/overview)