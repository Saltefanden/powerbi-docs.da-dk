---
title: Arbejde med aggregeringer (sum, gennemsnit osv.) i Power BI-tjenesten
description: Få mere at vide om, hvordan du tilpasser aggregeringen i et diagram (sum, gennemsnit, maksimum osv.) i Power BI-tjenesten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 06/16/2020
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 4ed1d6c68549e621f42b23d05a061e7fe1c9e230
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395411"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Arbejde med aggregeringer (sum, gennemsnit osv.) i Power BI-tjenesten

## <a name="what-is-an-aggregate"></a>Hvad er en aggregering?

Du kan sommetider få brug for matematisk at kombinere værdier i dine data. Den matematiske handling kan f.eks. være sum, gennemsnit, maksimum, antal, osv. Når du kombinerer værdier i dine data, kaldes det *aggregering*. Resultatet af den matematiske handling er en *aggregering*.

Når Power BI-tjenesten og Power BI Desktop opretter visualiseringer, aggregerer de muligvis dine data. Ofte er aggregeringen lige hvad du har brug for, men andre gange vil du måske aggregere værdierne på en anden måde.  F.eks. en sum i forhold til et gennemsnit. Der er flere forskellige måder at administrere og ændre den aggregering, som Power BI bruger i en visualisering, på.

Lad os først se på *datatyper*, fordi datatypen bestemmer, hvordan og om Power BI kan aggregere den.

## <a name="types-of-data"></a>Datatyper

De fleste datasæt har mere end én type data. På det mest grundlæggende niveau er dataene enten numeriske, eller også er de ikke. Power BI kan aggregere numeriske data ved hjælp af en sum, et gennemsnit, antal, minimum, varians og meget mere. Tjenesten kan selv aggregere tekstdata, ofte kaldet *kategoriske* data. Hvis du prøver at aggregere et kategorisk felt ved at placere det i et udelukkende numerisk interval, som f.eks. **Værdier** eller **Værktøjstip**, vil Power BI tælle forekomsterne af hver kategori eller tælle de særskilte forekomster af hver kategori. Særlige datatyper, som datoer, har et par af deres egne aggregerede indstillinger: tidligste, seneste, første og sidste.

I eksemplet nedenfor:

- **Solgte enheder** og **Produktionspris** er kolonner, der indeholder numeriske data

- **Segment**, **Land**, **Produkt**, **Måned** og **Månedsnavn** indeholder kategoriske data

   ![Skærmbillede af et eksempel på et datasæt.](media/service-aggregates/power-bi-aggregate-chart.png)

Når du opretter en visualisering i Power BI, aggregerer tjenesten numeriske felter (standarden er *sum*) over nogle kategorifelter.  For eksempel "Solgte enheder ***efter produkt** _", "Solgte enheder _*_efter måned_*_" og "Produktionspris _*_efter segment_*_". Power BI refererer til nogle numeriske felter som _*målinger**. Det er nemt at identificere målinger i Power BI-rapporteditoren – listen **Felter** viser målinger med symbolet ∑ ud for dem. Du kan finde flere oplysninger under [Rapporteditoren... få en introduktion](service-the-report-editor-take-a-tour.md).

![Skærmbillede af Power BI, hvor listen Felter er kaldt.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Hvorfor fungerer aggregeringer ikke, som jeg vil have dem til?

Det kan være forvirrende at arbejde med aggregater i Power BI-tjenesten. Du har måske et numerisk felt, hvor Power BI ikke tillader, at du ændrer sammenlægningen. Eller måske har du et felt, som f.eks. et år, som du ikke vil aggregere, men kun vil tælle antallet af forekomster af.

Det underliggende problem er typisk feltdefinitionen i datasættet. Det kan være ejeren af datasættet, der har defineret feltet som tekst, hvilket forklarer, hvorfor Power BI ikke kan opsummere eller beregne et gennemsnit. Desværre [kan kun datasættets ejer ændre måden, hvorpå et felt er kategoriseret](../transform-model/desktop-measures.md). Så du kan løse problemet, hvis du har ejertilladelser til datasættet, enten i Desktop eller det program, der blev brugt til at oprette datasættet (f.eks. Excel). Ellers skal du kontakte ejeren af datasættet for at få hjælp.  

Der findes et særligt afsnit sidst i denne artikel kaldet [**Tip og fejlfinding**](#considerations-and-troubleshooting). Her kan du finde tips og vejledning. Hvis du ikke kan finde løsningen her, kan du stille dit spørgsmål i [Power BI-community-forummet](https://community.powerbi.com). Du får hurtigt svar direkte fra Power BI-teamet.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Tilpas måden, hvorpå et numerisk felt aggregeres

Lad os antage, at du har et diagram, der sammenlægger solgte enheder for forskellige produkter, men du hellere vil beregne gennemsnittet.

1. Opret et **grupperet søjlediagram**, der anvender en måling og en kategori. I dette eksempel bruger vi Solgte enheder efter Produkt.  Power BI opretter som standard et diagram, der sammenlægger solgte enheder (træk målingen til brønden **Værdi**) for hvert produkt (træk kategorien til brønden **Akse**).

   ![Skærmbillede af diagrammet, ruden Visualiseringer og listen Felter, hvor Sum er kaldt ud.](media/service-aggregates/power-bi-aggregate-sum.png)

1. Højreklik på målenheden i ruden **Visualiseringer**, og vælg den type aggregering, du skal bruge. I dette tilfælde vælger vi **Gennemsnit**. Hvis du ikke ser den aggregering, du skal bruge, kan du se afsnittet [**Tip og fejlfinding**](#considerations-and-troubleshooting).

   ![Skærmbillede af aggregeringslisten med Gennemsnit valgt og kaldt ud.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > De tilgængelige indstillinger i rullemenuen varierer afhængig af 1) det valgte felt og 2) den måde, som datasættets ejer har kategoriseret dette felt på.

1. Din visualisering bruger nu aggregeret efter gennemsnit.

   ![Skærmbilledet af diagrammet viser nu Gennemsnit af solgte enheder efter produkt.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Metoder til at aggregere dine data

Nedenfor følger nogen af indstillingerne, der kan være tilgængelige ved aggregering af et felt:

- **Opsummer ikke**. Når du har valgt denne indstilling, behandler Power BI hvert felt særskilt og opsummerer dem ikke. Brug denne indstilling, hvis du har en numerisk id-kolonne, som tjenesten ikke skal summere.

- **Sum**. Lægger alle værdier i feltet sammen.

- **Gennemsnit**. Beregner et matematisk gennemsnit af værdierne.

- **Minimum**. Viser den mindste værdi.

- **Maksimum**. Viser den største værdi.

- **Antal (ikke tomme)** . Tæller antallet af værdier i det pågældende felt, der ikke er tomme.

- **Antal (distinkt).** Tæller antallet af forskellige værdier i det pågældende felt.

- **Standardafvigelse.**

- **Varians**.

- **Median**.  Viser median (middel)-værdien. Denne værdi har det samme antal elementer over og under.  Hvis der er to medianer, beregner Power BI gennemsnittet af dem.

F.eks. disse data:

| Land | Beløb |
|:--- |:--- |
| USA |100 |
| Storbritannien |150 |
| Canada |100 |
| Tyskland |125 |
| Frankrig | |
| Japan |125 |
| Australien |150 |

Giver de følgende resultater:

- **Opsummer ikke**: Hver enkelt værdi vises særskilt

- **Sum**: 750

- **Gennemsnit**: 125

- **Maksimum**:  150

- **Minimum**: 100

- **Antal (ikke tomme):** 6

- **Antal (specifikt):** 4

- **Standardafvigelse:** 20.4124145...

- **Afvigelse:** 416.666...

- **Median:** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Opret en aggregering ved hjælp af et kategorifelt (tekstfelt)

Du kan også aggregere et felt, der ikke er et numerisk felt. Hvis du f.eks. har et felt med produktnavn, kan du tilføje det som en værdi og derefter indstille det til **Antal** **Adskilt antal**, **Første** eller **Sidste**.

1. Træk feltet **Produkt** til brønden **Værdier**. Brønden **Værdier** bruges typisk til numeriske felter. Power BI genkender, at dette felt er et tekstfelt, angiver aggregeringen til **Opsummer ikke** og giver dig en tabel med én kolonne.

   ![Skærmbillede af feltet Produkt i brønden Værdier.](media/service-aggregates/power-bi-aggregate-value.png)

1. Hvis du ændrer aggregeringen fra standarden **Opsummer ikke** til **Antal (adskilt)** , tæller Power BI antallet af forskellige produkter. I dette tilfælde er der fire.
  
   ![Skærmbillede af det samlede antal produkter.](media/service-aggregates/power-bi-aggregate-count.png)

1. Hvis du desuden ændrer aggregeringen til **Antal**, så tælles det samlede antal i Power BI. I dette tilfælde er der syv poster for **Produkt**.

   ![Skærmbillede af antallet af produkter.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Ved at trække det samme felt (i dette tilfælde **Produkt**) til brønden **Værdi** og lade standardaggregeringen være **Opsummer ikke**, opdeler Power BI antallet af produkter.

   ![Skærmbillede af produktet og antallet af produkter.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

Spørgsmål:  Hvorfor har jeg ikke en indstilling for **Opsummer ikke**?

Svar:  Det felt, du har valgt, er sandsynligvis en beregnet måling i en flerdimensionel model eller en måling oprettet i Excel eller [Power BI Desktop](../transform-model/desktop-measures.md). Hver måling har sin egen hårdt kodede formel. Du kan ikke ændre den aggregering, som Power BI bruger. F.eks, hvis det er en sum, kan den kun være en sum. Listen **Felter** viser *målinger* med lommeregnersymbolet.

Spørgsmål:  Mit felt **er** numerisk, så hvorfor kan jeg kun vælge **Antal** og **Distinkt antal**?

Svar 1:  Den sandsynlige forklaring er, at datasættets ejer *ikke* har klassificeret feltet som et tal. Hvis et datasæt f.eks. har feltet **År**, kan ejeren af datasættet kategorisere værdien som tekst. Det er mere sandsynligt, at Power BI tæller feltet **År** (f.eks. antallet af personer, der er født i 1974). Det er mindre sandsynligt, at Power BI sammenlægger eller udregner gennemsnittet. Hvis du er ejeren, kan du åbne datasættet i Power BI Desktop og bruge fanen **Udformning** for at ændre datatypen.

Svar 2: Hvis feltet har et lommeregnerikon, betyder det, at det er en *måling*. Hver måling har sin egen formel, som kun ejeren af datasættet kan ændre. Den beregning, som Power BI bruger, kan være en simpel aggregering, f.eks. et gennemsnit eller en sum. Det kan også være noget mere kompliceret, som f.eks. en "procentdel af bidraget til forældrekategori" eller "løbende totalværdi siden årets begyndelse". Power BI sammenlægger eller beregner ikke gennemsnittet af resultaterne. Det genberegner i stedet blot (ved hjælp af den kodede formel) hvert datapunkt.

Svar 3:  En anden mulighed er, at du har valgt at benytte feltet i en *bucket*, der kun tillader kategoriværdier.  Hvis dette er tilfældet, så har du kun adgang til antal og distinkt antal.

Svar 4:  En fjerde mulighed er, at du bruger feltet for en akse. Eksempelvis på en akse i et søjlediagram – her vises én søjle i Power BI for hver distinkte værdi – her vises slet ikke aggregerede feltværdier.

>[!NOTE]
>Undtagelsen for denne regel er punktdiagrammer, som *kræver* aggregerede værdier for X- og Y-akserne.

Spørgsmål:  Hvorfor kan jeg kan ikke aggregere tekstfelter til SSAS-datakilder (SQL Server Analysis Services)?

Svar:  Dynamiske forbindelser til flerdimensionelle SSAS-modeller tillader ikke en hvilken som helst aggregering på klientsiden, herunder først, sidst, gennemsnit, min., maks. og sum.

Spørgsmål:  Jeg har et punktdiagram, og jeg vil *ikke* have, at mit felt foretager sammenlægninger.  Hvordan?

Svar:  Føj feltet til din bucket af typen **Oplysninger** og ikke til dine buckets af typen X- eller Y-akser.

Spørgsmål:  Når jeg føjer et tekstfelt til en visualisering, så indstilles de fleste af dem automatisk til sum, men nogle indstilles automatisk til gennemsnit eller antal eller en anden sammenlægning.  Hvorfor er standardakkumuleringen ikke altid den samme?

Svar:  Datasætejere kan angive standardopsummeringen for hvert enkelt felt. Hvis du er ejer af et datasæt, skal du ændre standardopsummeringen på fanen **Udformning** i Power BI Desktop.

Spørgsmål:  Jeg er datasætejer, og jeg vil gerne sikre, at et felt aldrig sammenlægges.

Svar:  På fanen **Uformning** i Power BI Desktop skal du angive **Datatype** til **Tekst**.

Spørgsmål:  Jeg kan ikke se **Opsummer ikke** på rullelisten.

Svar:  Prøv at fjerne feltet og tilføje det igen.

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
