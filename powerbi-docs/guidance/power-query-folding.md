---
title: Vejledning til forespørgselsdelegering i Power BI Desktop
description: Vejledning til opnåelse af Power Query-forespørgselsdelegering i Power BI Desktop.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/09/2019
ms.openlocfilehash: 5e2ec32f3eeaff224256f0a84d2a5c23d3e882a5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419308"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Vejledning til forespørgselsdelegering i Power BI Desktop

Denne artikel er henvendt til designere af datamodeller i Power BI Desktop. Den indeholder den en vejledning til bedste praksis for, hvornår – og hvordan – du opnår Power Query-forespørgselsdelegering.

_Forespørgselsdelegering_ er muligheden for, at en Power Query-forespørgsel genererer en enkelt forespørgselssætning, der henter og transformerer kildedata. Du kan finde flere oplysninger i [Power Query-forespørgselsdelegering](/power-query/power-query-folding).

## <a name="guidance"></a>Vejledning

Vejledningen til forespørgselsdelegering varierer afhængigt af modeltilstanden.

Power Query-forespørgslen skal opnå forespørgselsdelegering for en **DirectQuery-** tabel eller en tabel med **dobbelt** lagringstilstand.

Der kan muligvis opnås forespørgselsdelegering for en **import** tabel. Hvis forespørgslen er baseret på en relationskilde – og når en enkelt SELECT-sætning kan konstrueres – opnås den _bedste ydeevne for dataopdatering_ ved at sikre, at der sker forespørgselsdelegering. Hvis Power Query-miksprogrammet stadig er påkrævet til at behandle transformationer, skal du bestræbe dig på at minimere det arbejde, der skal udføres, især for store datasæt.

Følgende punktopstilling indeholder en specifik vejledning.

- **Deleger så meget behandling som muligt til datakilden**: Når det er umuligt at delegere alle trin i en Power Query, skal du finde det trin, der forhindrer forespørgselsdelegering. Når det er muligt, skal du flytte senere trin længere frem i rækkefølgen, så de kan indregnes i forespørgselsdelegeringen. Bemærk, at Power Query-miksprogrammet kan være smart nok til at ændre rækkefølgen af dine forespørgselstrin, når kildeforespørgslen genereres.

    I forbindelse med en relationsdatakilde kan du overveje at bruge en oprindelig SQL-forespørgsel, hvis det trin, der forhindrer forespørgselsdelegering, kan opnås i en enkelt SELECT-sætning – eller inden for den proceduremæssig logik for en gemt procedure – som beskrevet herunder.

- **Brug en oprindelig SQL-forespørgsel**: Når en Power Query-forespørgsel henter data fra en relationskilde, er det muligt for nogle kilder at bruge en oprindelig SQL-forespørgsel. Forespørgslen kan faktisk være en gyldig sætning, herunder en udførelse af en gemt procedure. Hvis sætningen producerer flere resultatsæt, er det kun det første, der returneres. Parametre kan deklareres i sætningen, og vi anbefaler, at du bruger M-funktionen [Value.NativeQuery](/powerquery-m/value-nativequery). Denne funktion er udviklet til at overføre parameterværdier sikkert og nemt. Det er vigtigt at forstå, at Power Query-miksprogrammet ikke kan delegere senere forespørgselstrin, så du skal medtage al transformationslogik –eller så meget som muligt – i den oprindelige forespørgselssætning.

    Der er to vigtige overvejelser, du skal være opmærksom på, når du bruger oprindelige SQL-forespørgsler:

    - I forbindelse med en DirectQuery-modeltabel skal forespørgslen være en SELECT-sætning, og den kan ikke bruge CTE (Common Table Expression) eller en gemt procedure.
    - Trinvis opdatering kan ikke bruge en oprindelig SQL-forespørgsel. Det ville derfor tvinge Power Query-miksprogrammet til at hente alle kilderækker og derefter anvende filtre for at fastlægge de trinvise ændringer.

    > [!IMPORTANT]
    > En oprindelig SQL-forespørgsel kan potentielt gøre mere end at hente data. Enhver gyldig sætning kan udføres (og muligvis flere gange), herunder én, der ændrer eller sletter data. Det er vigtigt, at du anvender princippet om færrest mulige rettigheder for at sikre, at den konto, der bruges til at få adgang til databasen, kun har læsetilladelse til de påkrævede data.

- **Forbered og transformér data i kilden**: Hvis du identificerer, at visse Power Query-forespørgselstrin ikke kan delegeres, kan det være muligt at anvende transformationerne i datakilden. Du kan opnå transformationerne ved at skrive en databasevisning, der logisk transformerer kildedata. Eller ved fysisk at forberede og materialisere data, før Power BI forespørger dem. Et relationelt data warehouse er et glimrende eksempel på forberedte data, der normalt består af forudintegrerede kilder med organisationsdata.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- Artikel om konceptet Power Query-[forespørgselsdelegering](/power-query/power-query-folding)
- [Trinvis opdatering i Power BI Premium](../admin/service-premium-incremental-refresh.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
