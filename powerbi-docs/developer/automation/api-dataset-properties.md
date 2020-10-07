---
title: Egenskaber for Power BI-datasæt
description: Få mere at vide om Power BI-datasæt API'ers egenskaber
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: e0092003cbf019bcf720eeb7aa32e8a9e800f143
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747292"
---
# <a name="dataset-properties"></a>Egenskaber for datasæt

Den aktuelle v1 for datasæts API giver kun mulighed for at oprette et datasæt med et navn og en samling af tabeller. Hver tabel kan have et navn og en samling af kolonner. Hver kolonne har et navn og en datatype. Vi udvider disse egenskaber, især med understøttelse af målinger og relationer mellem tabeller. Den komplette liste over understøttede egenskaber for denne version er som følger:

> [!IMPORTANT]
> Der kan tilgås på siden [Datasæts handlingsgrupper](/rest/api/power-bi/datasets).

## <a name="dataset"></a>Dataset

Navn  |Type  |Beskrivelse  |Skrivebeskyttet  |Påkrævet
---------|---------|---------|---------|---------
id     |  Guid       | Entydigt id for datasættet overalt i systemet.        | Sand        | Falsk        
name     | Streng        | Datasættets brugerdefinerede navn.        | Falsk        | Sand        
tabeller     | Tabel[]        | Samling af tabeller.        |  Falsk       | Falsk        
relationer     | Relation[]        | Samling af relationer mellem tabeller.        | Falsk        |  Falsk  
standardtilstand     | Streng        | Bestemmer, om datasættet sendes via push, streames elle begge dele, med værdierne "Push" og "Streaming".         | Falsk        |  Falsk

## <a name="table"></a>Tabel

Navn  |Type  |Beskrivelse  |Skrivebeskyttet  |Påkrævet
---------|---------|---------|---------|---------
name     | Streng        |  Tabellens brugerdefinerede navn. Bruges også som id for tabellen.       | Falsk        |  Sand       
kolonner     |  Kolonne[]       |  Samling af kolonner.       | Falsk        |  Sand       
målinger     | måling[]        |  Samling af målinger.       | Falsk        |  Falsk       
isHidden     | Boolean        | Hvis true, er tabellen skjult for klientværktøjer.        | Falsk        | Falsk        

## <a name="column"></a>Kolonne

Navn  |Type  |Beskrivelse  |Skrivebeskyttet  |Påkrævet
---------|---------|---------|---------|---------
name     |  Streng        | Kolonnens brugerdefinerede navn.        |  Falsk       | Sand       
dataType     |  Streng       |  Understøttede [EDM-datatyper](/dotnet/framework/data/adonet/entity-data-model-primitive-data-types) og begrænsninger. Se [Begrænsninger for datatypen](#data-type-restrictions).      |  Falsk       | Sand        
formatString     | Streng        | En streng, der beskriver, hvordan værdien skal formateres, når den vises. Hvis du vil vide mere om strengformatering, se [FORMAT_STRING-indholdet](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents).      | Falsk        | Falsk        
sortByColumn    | Streng        |   Strengnavnet på en kolonne i samme tabel, der bruges til at bestille den aktuelle kolonne.     | Falsk        | Falsk       
dataCategory     | Streng        |  Strengværdi, der bruges til datakategorien, som beskriver dataene i denne kolonne. Almindelige værdier omfatter: adresse, by, kontinent, land, billede, BilledUrl, breddegrad, længdegrad, organisation, sted, postnummer, stat eller land, WebUrl       |  Falsk       | Falsk        
isHidden    |  Boolean       |  Egenskaben, der angiver, om kolonnen er skjult i visningen. Standardindstillingen er false.       | Falsk        | Falsk        
summarizeBy     | Streng        |  Standardmetode for sammenlægning til kolonnen. Værdier omfatter: standard, ingen, sum, min, maks, antal, gennemsnit, distinctCount     |  Falsk       | Falsk

## <a name="measure"></a>Måling

Navn  |Type  |Beskrivelse  |Skrivebeskyttet  |Påkrævet
---------|---------|---------|---------|---------
name     | Streng        |  Målingens brugerdefinerede navn.       |  Falsk       | Sand        
udtryk     | Streng        | Et gyldigt DAX-udtryk.        | Falsk        |  Sand       
formatString     | Streng        |  En streng, der beskriver, hvordan værdien skal formateres, når den vises. Hvis du vil vide mere om strengformatering, se [FORMAT_STRING-indholdet](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents).       | Falsk        | Falsk        
isHidden     | Streng        |  Hvis true, er tabellen skjult for klientværktøjer.       |  Falsk       | Falsk       

## <a name="relationship"></a>Relation

Navn  |Type  |Beskrivelse  |Skrivebeskyttet  |Påkrævet 
---------|---------|---------|---------|---------
name     | Streng        | Relationens brugerdefinerede navn. Bruges også som id for relationen.        | Falsk       | Sand        
crossFilteringBehavior     | Streng        |    Relationens filterretning: OneDirection (standard), BothDirections, automatisk       | Falsk        | Falsk        
fromTable     | Streng        | Navnet på fremmed nøgle-tabellen.        | Falsk        | Sand         
fromColumn    | Streng        | Navnet på fremmed nøgle-kolonnen.        | Falsk        | Sand         
toTable    | Streng        | Navnet på tabellen med den primære nøgle.        | Falsk        | Sand         
toColumn     | Streng        | Navnet på kolonnen med den primære nøgle.        | Falsk        | Sand        

## <a name="data-type-restrictions"></a>Begrænsninger for datatypen

Disse begrænsninger gælder for egenskaben dataType.

Datatype  |Begrænsninger  
---------|---------
Int64     |   Int64.MaxValue og Int64.MinValue er ikke tilladt.      
Double     |  Værdierne Double.MaxValue og Double.MinValue er ikke tilladt. NaN understøttes ikke. +Infinity og -Infinity understøttes ikke i visse funktioner (f.eks. Min, Max).       
Boolean     |   Sand eller falsk.
Datetime    |   Under indlæsning af data beregnes værdier baseret på brøkdele af dagen i hele multipler af 1/300 sekunder (3,33 ms).      
Streng     |  Tillader i øjeblikket op til 4.000 tegn pr. strengværdi.
Decimal|præcision = 28, skala = 4

## <a name="example"></a>Eksempel
Følgende kodeeksempel omfatter en række disse egenskaber:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```