---
title: Dataflowbegrænsninger, begrænsninger og understøttede connectors og funktioner
description: Oversigt over alle egenskaberne i dataflow
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b8811d9b869d4aa3592c9ed3531d067701b544a8
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91637907"
---
# <a name="dataflows-limitations-and-considerations"></a>Begrænsninger og overvejelser i forbindelse med dataflow

Der er nogle få dataflowbegrænsninger på tværs af oprettelse, opdateringer og kapacitetsadministration, som brugerne skal huske. De beskrives i følgende afsnit.

## <a name="dataflow-authoring"></a>Oprettelse af dataflow

Når brugerne opretter dataflow, skal de være opmærksom på følgende:

* Oprettelse af dataflows finder sted i PQO-miljøet (Power Query Online). Se de begrænsninger, der er beskrevet i [Power Query-begrænsninger](https://docs.microsoft.com/power-query/power-query-online-limits).
Da oprettelse af dataflow finder sted i PQO-miljøet (Power Query Online), påvirker opdateringer, der udføres på konfigurationer af arbejdsbelastninger i dataflow, kun opdateringer og har ikke indflydelse på oprettelsesoplevelsen

* Dataflow kan kun ændres af deres ejere

* Dataflow er ikke tilgængelige i *Mit arbejdsområde*

* Dataflow, der bruger gatewaydatakilder, understøtter ikke flere legitimationsoplysninger for den samme datakilde

* Brug af connectoren Web.Page kræver en gateway

## <a name="api-considerations"></a>API-overvejelser

Du kan finde flere oplysninger om understøttede dataflow-REST API'er i [Reference til REST API](https://docs.microsoft.com/rest/api/power-bi/dataflows). Her er nogle ting, du skal være opmærksom på:

* Eksport og import af et dataflow giver det pågældende dataflow et nyt id

* Import af dataflows, der indeholder sammenkædede enheder, retter ikke de eksisterende referencer i dataflowet (disse forespørgsler skal rettes manuelt før import af dataflowet)

* Dataflow kan overskrives med parameteren *CreateOrOverwrite*, hvis de oprindelig er oprettet ved hjælp af import-API'EN

## <a name="dataflows-in-shared"></a>Dataflow i delte

Der er begrænsninger for dataflows i delte kapaciteter:

* Ved opdatering af dataflow er timeouts i delte to timer pr. enhed og tre timer pr. dataflow
* Sammenkædede enheder kan ikke oprettes i delte dataflow, selvom de kan findes i dataflowet, så længe egenskaben *Indlæsning aktiveret* i forespørgslen er deaktiveret
* Beregnede enheder kan ikke oprettes i delte dataflow
* AutoML og Cognitive Services er ikke tilgængelige i delte dataflow
* Trinvis opdatering fungerer ikke i delte dataflow

## <a name="dataflows-in-premium"></a>Dataflow i Premium

Der er følgende begrænsninger og overvejelser i forbindelse med dataflow, der findes i Premium.

**Opdateringer og dataovervejelser:**

* Ved opdatering af dataflows er timeouts 24 timer (der skelnes ikke mellem enheder og/eller dataflow)

* Hvis du ændrer politikken for et dataflow fra trinvis opdatering til en normal opdatering eller omvendt, slettes alle data

* Hvis du ændrer et dataflows skema, slettes alle data

**Sammenkædede og beregnede enheder:**

* Sammenkædede enheder kan gå ned til en dybde på 32 referencer

* Cykliske afhængigheder af sammenkædede objekter er ikke tilladt

* Et linket objekt kan ikke joinforbindes med et almindeligt objekt, der får sine data fra en datakilde i det lokale miljø

* Når en forespørgsel (f.eks. forespørgsel *A*) bruges i beregningen af en anden forespørgsel (forespørgsel *B*) i dataflows, bliver forespørgsel *B* en beregnet enhed. Beregnede enheder kan ikke referere til kilder i det lokale miljø.


**Beregningsprogram:**

* Under brug af beregningsprogrammet er der en omtrentligt startforøgelse af tiden til dataindtag på 10 % til 20 %.

  1. Dette gælder kun for det første dataflow, der er i beregningsprogrammet, og læser data fra datakilden
  2. Den samme forøgelse af tiden finder ikke sted for efterfølgende dataflow, der bruger kilde ét

* Det er kun visse handlinger, der bruger beregningsprogrammet, og kun når det bruges via en sammenkædet enhed eller som en beregnet enhed. Der findes en komplet liste over handlinger i [dette blogindlæg](http://petcu40.blogspot.com/2019/06/m-folding-in-enhanced-engine-of-power.html).


**Kapacitetsadministration:**

* Power BI-Premium-kapaciteter har en intern ressourceadministrator, som begrænser arbejdsbelastningen på forskellige måder, når kapaciteten er ved at køre tør for hukommelse.

  1. Dette begrænsningstryk reducerer antallet af tilgængelige M-objektbeholdere for dataflows
  2. Hukommelsen for dataflow kan indstilles til 100 % med en objektbeholder, der har en passende størrelse til dine datamængder, og arbejdsbelastningen administrerer antallet af objektbeholdere korrekt

* Du kan finde det omtrentlige antal beholdere ved at dividere den samlede hukommelse, der allokeres til arbejdsbelastningen, med den mængde hukommelse, der er allokeret til en objektbeholder

## <a name="dataflow-usage-in-datasets"></a>Brug af dataflow i datasæt

* Når du opretter et datasæt i Power BI Desktop og derefter publicerer det til Power BI-tjenesten, skal du sørge for, at de legitimationsoplysninger, der bruges i Power BI Desktop til datakilden for dataflow, er de samme legitimationsoplysninger, der bruges, når datasættet publiceres til tjenesten.
  1. Hvis disse legitimationsoplysninger ikke er de samme, resulterer det i fejlen *Nøglen blev ikke fundet* ved opdatering af datasæt

## <a name="next-steps"></a>Næste trin
Du kan finde flere oplysninger om dataflow og Power BI i følgende artikler:

* [Introduktion til dataflow og selvbetjent dataforberedelse](dataflows-introduction-self-service.md)
* [Oprettelse af et dataflow](dataflows-create.md)
* [Konfigurer og brug et dataflow](dataflows-configure-consume.md)
* [Konfiguration af dataflowlager til brug af Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [Premium-funktioner for dataflow](dataflows-premium-features.md)
* [AI med dataflow](dataflows-machine-learning-integration.md)

