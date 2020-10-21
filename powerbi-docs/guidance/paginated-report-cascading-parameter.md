---
title: Anvend overlappende parametre i sideinddelte rapporter
description: Vejledning til design af sideinddelte rapporter ved hjælp af overlappende parametre.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: f239622d8b6012913298212790f7f9aa8c3115a5
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197650"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Anvend overlappende parametre i sideinddelte rapporter

Denne artikel henvender sig til rapportforfattere, der designer [sideinddelte rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md) i Power BI. Den indeholder scenarier til design af overlappende parametre. Overlappende parametre er rapportparametre med afhængigheder. Når en rapportbruger vælger en eller flere parameterværdier, bruges den/de til at angive tilgængelige værdier for en anden parameter.

> [!NOTE]
> En introduktion til overlappende parametre, og hvordan du konfigurerer dem, er ikke omfattet af denne artikel. Hvis du ikke har fuldstændig kendskab til overlappende parametre, anbefaler vi, at du først læser [Føj overlappende parametre til en rapport (Report Builder og SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs).

## <a name="design-scenarios"></a>Designscenarier

Der er to designscenarier til brug af overlappende parametre. De kan bruges effektivt til at:

- Filtrere _store sæt_ elementer
- Præsentere _relevante_ elementer

### <a name="example-database"></a>Eksempeldatabase

De eksempler, der præsenteres i denne artikel, er baseret på en Azure SQL-database. Databasen registrerer salgshandlinger og indeholder forskellige tabeller, der lagrer forhandlere, produkter og salgsordrer.

En tabel med navnet **Reseller** gemmer én post for hver forhandler og indeholder tusindvis af poster. Tabellen **Reseller** har følgende kolonner:

- ResellerCode (heltal)
- ResellerName
- Land-område
- State-Province
- By
- Postnummer

Der er også en tabel med navnet **Sales**. Den gemmer salgsordreposter og har en fremmed nøgle-relation til tabellen **Reseller** i kolonnen **ResellerCode**.

### <a name="example-requirement"></a>Eksempel på krav

Der er et krav om at udvikle en rapport over forhandlerprofiler. Rapporten skal være designet til at vise oplysninger om en enkelt forhandler. Det er ikke hensigtsmæssigt, at rapportbrugeren skal angive en forhandlerkode, da brugerne sjældent kan dem udenad.

## <a name="filter-large-sets-of-items"></a>Filtrer store sæt elementer

Lad os se på tre eksempler, som kan hjælpe dig med at begrænse store sæt tilgængelige elementer, f.eks. forhandlere. De er:

- [Filtrer efter relaterede kolonner](#filter-by-related-columns)
- [Filtrer efter en grupperingskolonne](#filter-by-a-grouping-column)
- [Filtrer efter søgemønster](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filtrer efter relaterede kolonner

I dette eksempel interagerer rapportbrugeren med fem rapportparametre. Brugeren skal vælge land/område, stat/provins, by og derefter postnummer. En endelig parameter viser derefter de forhandlere, der er placeret i den pågældende geografiske placering.

![Skærmbillede af parametre for sideinddelte rapporter i Power BI, der viser filtrering efter relaterede kolonner.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

Sådan kan du udvikle de overlappende parametre:

1. Opret de fem rapportparametre i den korrekte rækkefølge.
2. Opret datasættet **CountryRegion**, der henter entydige værdier for land/område, ved hjælp af følgende forespørgselssætning:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Opret datasættet **StateProvince**, der henter entydige stat-/provinsværdier for det valgte land/område, ved hjælp af følgende forespørgselssætning:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Opret datasættet **City**, der henter entydige byværdier for det valgte land/område og den valgte stat/provins, ved hjælp af følgende forespørgselssætning:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Fortsæt med dette mønster for at oprette datasættet **PostalCode**.
6. Opret datasættet **Reseller** for at hente alle forhandlere for de valgte geografiske værdier ved hjælp af følgende forespørgselssætning:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. For hvert datasæt undtagen det første skal du knytte forespørgselsparametrene til de tilsvarende rapportparametre.

> [!NOTE]
> Alle forespørgselsparametre (har symbolet @ som præfiks), der vises i disse eksempler, kan integreres i SELECT-sætninger eller overføres til lagrede procedurer.
>
> Lagrede procedurer er generelt den bedste designmetode. Det skyldes, at deres forespørgselsplaner cachelagres for at køre hurtigere, og de giver dig mulighed for at udvikle mere avanceret logik, når det er nødvendigt. De understøttes dog ikke i øjeblikket for datakilder, der er baseret på gateways, hvilket betyder SQL Server, Oracle og Teradata.
>
> Endelig skal du altid sikre, at der findes egnede indekser til at understøtte effektiv datahentning. Ellers kan det tage lang tid at udfylde rapportparametrene, og databasen kan blive overbelastet. Du kan finde flere oplysninger om SQL Server-indeksering under [Arkitektur af SQL Server-indeks og designvejledning](/sql/relational-databases/sql-server-index-design-guide).

### <a name="filter-by-a-grouping-column"></a>Filtrer efter en grupperingskolonne

I dette eksempel interagerer rapportbrugeren med en rapportparameter for at vælge det første bogstav i forhandleren. En anden parameter viser derefter de forhandlere, hvis navn begynder med det valgte bogstav.

![Skærmbillede af parametre for sideinddelte rapporter i Power BI, der viser filtrering efter en grupperingskolonne.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

Sådan kan du udvikle de overlappende parametre:

1. Opret rapportparametrene **ReportGroup** og **Reseller** i den rigtige rækkefølge.
2. Opret datasættet **ReportGroup** for at hente de første bogstaver, der bruges af alle forhandlere, ved hjælp af følgende forespørgselssætning:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Opret datasættet **Reseller** for at hente alle forhandlere, der starter med det pågældende bogstav, ved hjælp af følgende forespørgselssætning:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Knyt forespørgselsparameteren for datasættet **Reseller** til den tilsvarende rapportparameter.

Det er mere effektivt at føje grupperingskolonnen til tabellen **Reseller**. Når den er permanent og indekseret, giver den det bedste resultat. Du kan finde flere oplysninger under [Angiv beregnede kolonner i en tabel](/sql/relational-databases/tables/specify-computed-columns-in-a-table).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Denne teknik rummer et endnu større potentiale. Overvej følgende script, der tilføjer en ny grupperingskolonne, til at filtrere forhandlere efter _foruddefinerede felter af bogstaver_. Der oprettes også et indeks for effektivt at hente de data, der kræves af rapportparametrene.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filtrer efter søgemønster

I dette eksempel interagerer rapportbrugeren med en rapportparameter for at angive et søgemønster. En anden parameter viser derefter forhandlere, når navnet indeholder mønsteret.

![Skærmbillede af parametre for sideinddelte rapporter i Power BI, der viser filtrering efter søgemønster.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

Sådan kan du udvikle de overlappende parametre:

1. Opret rapportparametrene **Search** og **Reseller** i den rigtige rækkefølge.
2. Opret datasættet **Reseller** for at hente alle forhandlere, der indeholder søgeteksten, ved hjælp af følgende forespørgselssætning:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Knyt forespørgselsparameteren for datasættet **Reseller** til den tilsvarende rapportparameter.

> [!TIP]
> Du kan forbedre dette design for at give brugerne mere kontrol over rapporterne. Det giver dem mulighed for at definere deres egen værdi, der stemmer overens med et mønster. Søgeværdien "red%" filtrerer f.eks. forhandlere efter navne, der _begynder_ med tegnene "red".
>
> Du kan finde flere oplysninger under [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql#using-the--wildcard-character).

Her kan du se, hvordan du kan give rapportbrugerne mulighed for at definere deres eget mønster.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Mange medarbejdere uden databaseerfaring kender ikke til procent-jokertegnet (%). De er i stedet bekendt med stjernetegnet (*). Hvis du ændrer WHERE-delsætningen, kan du lade dem bruge dette tegn.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Præsenter relevante elementer

I dette scenarie kan du bruge faktadata til at begrænse de tilgængelige værdier. Rapportbrugere får vist de elementer, hvor der er registreret aktivitet.

I dette eksempel interagerer rapportbrugeren med tre rapportparametre. De to første angiver et datointerval for salgsordredatoer. Den tredje parameter viser derefter de forhandlere, hvor der er oprettet ordrer i løbet af den pågældende tidsperiode.

![Skærmbillede af parametre for sideinddelte rapporter i Power BI, der viser tre parametre: Start Order Date, End Order Date og Reseller.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

Sådan kan du udvikle de overlappende parametre:

1. Opret rapportparametrene **OrderDateStart**, **OrderDateEnd** og **Reseller** i den korrekte rækkefølge.
2. Opret datasættet **Reseller** for at hente alle de forhandlere, der oprettede ordrer i perioden, ved hjælp af følgende forespørgselssætning:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Anbefalinger

Vi anbefaler, at du designer dine rapporter med overlappende parametre, når det er muligt. Det skyldes, at de:

- Giver dine brugere intuitive og nyttige oplevelser.
- Er effektive, da de henter mindre sæt af tilgængelige værdier.

Sørg for at optimere dine datakilder ved at:

- Bruge lagrede procedurer, når det er muligt.
- Tilføje relevante indekser for at hente data effektivt.
- Vise kolonneværdier – og endda rækker – for at undgå dyre evalueringer i forespørgselstiden.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Rapportparametre i Power BI Report Builder](../paginated-reports/report-builder-parameters.md)
- [Føj overlappende parametre til en rapport (Report Builder og SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)
