---
title: DAX-eksempelmodel
description: DAX-eksempelmodel til understøttelse af referenceartikler.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/25/2020
ms.openlocfilehash: b2930003da1593ef5d5888c611af6700e00d3d07
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394054"
---
# <a name="dax-sample-model"></a>DAX-eksempelmodel

Power BI Desktop-eksempelmodellen til **Adventure Works DW 2020** er designet til at understøtte din DAX-læring. Modellen er baseret på [Adventure Works-data warehouse-eksemplet](/sql/samples/adventureworks-install-configure#data-warehouse-downloads) til AdventureWorksDW2017 – dataene er imidlertid blevet ændret, så de passer til målsætningerne i eksempelmodellen.

## <a name="scenario"></a>Scenarie

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="Der vises et billede af Adventure Works-firmalogoet.":::

Virksomheden Adventure Works repræsenterer en cykelproducent, der sælger cykler og tilbehør til globale markeder. Virksomheden opbevarer deres data warehouse-data i en Azure-SQL Database.

## <a name="model-structure"></a>Modelstruktur

Modellen har syv tabeller:

|Tabel|Beskrivelse|
|-----|-------|
|**Kunde**|Beskriver kunder og deres geografiske placering. Kunderne køber produkter online (internetsalg).|
|**Dato**|Der er tre relationer mellem tabellerne **Date** og **Sales**, for ordredato, afsendelsesdato og forfaldsdato. Ordredatorelationen er aktiv. Virksomheden rapporterer salg ved hjælp af et regnskabsår, der begynder den 1. juli hvert år. Tabellen er markeret som en datotabel ved hjælp af kolonnen **Date**.|
|**Product**|Gemmer kun færdige produkter.|
|**Reseller**|Beskriver forhandlere og deres geografiske placering. Forhandlere videresælger produkter til deres kunder.|
|**Salg**|Gemmer rækker på salgsordrelinjeniveau. Alle økonomiske værdier er i amerikanske dollars (USD). Den tidligste ordredato er den 1. juli 2017, og den seneste ordredato er den 15. juni 2020.|
|**Sales Order**|Beskriver salgsordrer og ordrelinjenumre og også salgskanalen, som enten **Reseller** eller **Internet**. Denne tabel har en en til en-relation med tabellen **Sales**.|
|**Sales Territory**|Salgsdistrikter er organiseret i grupper (North America, Europe og Pacific), lande og områder. Kun USA sælger produkter på områdeniveau.|

Modellen indeholder ingen DAX-beregninger.

## <a name="download-sample"></a>Hent eksempel

Du kan hente en Power BI Desktop-eksempelmodelfil [her](https://aka.ms/dax-docs-sample-file).

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Henvisning til DAX (Data Analysis Expressions)](/dax/)
- Læringsforløb: [Brug DAX i Power BI Desktop](/learn/paths/dax-power-bi/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)