---
title: Brug hurtigmålinger til almindelige og effektive beregninger
description: Hurtigmålinger indeholder færdige DAX-formler, der gør det nemt at udføre de mest almindelige beregninger.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 11/22/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8ba43290e0e076963a61a7211ad99e99636ebb2e
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90853373"
---
# <a name="use-quick-measures-for-common-calculations"></a>Brug hurtigmålinger til almindelige beregninger
Du kan bruge *hurtigmålinger* til nemt og hurtigt at udføre almindelige og effektive beregninger. En hurtigmåling kører et sæt af DAX-kommandoer (Data Analysis Expressions) i baggrunden og viser derefter resultaterne, så du kan bruge dem i din rapport. Du behøver ikke at skrive DAX-formlen. Det bliver gjort for dig baseret på det input, du angiver i en dialogboks. Der er mange tilgængelige kategorier med beregninger og måder, som du kan tilpasse hver beregning til dine behov på. Det bedste af det hele er nok, at du kan se den DAX-formel, der udføres af hurtigmålingen, så du kan lære mere om DAX.

## <a name="create-a-quick-measure"></a>Opret en hurtigmåling

Du kan oprette en hurtigmåling i Power BI Desktop ved at højreklikke eller vælge ellipsen **...** ud for et vilkårligt element i ruden **Felter** og derefter vælge **Ny hurtigmåling** i den menu, der vises. 

![Vælg Ny hurtigmåling](media/desktop-quick-measures/quick-measures_01.png)

Du kan også højreklikke eller vælge rullelistepilen ud for en værdi i **Værdier** for en eksisterende visualisering og vælge **Ny hurtigmåling** i menuen. 

Når du vælger **Ny hurtigmåling**, vises vinduet **Hurtigmålinger**, hvor du kan vælge den beregning, du vil bruge, og de felter, der skal beregnes. 

Vælg feltet **Vælg en beregning** for at få vist en lang liste over tilgængelige hurtigmålinger. 

![Tilgængelige hurtigmålinger](media/desktop-quick-measures/quick-measures_04.png)

De fem beregningstyper for hurtigmåling med deres beregninger er følgende:

* **Aggreger pr. kategori**
  * Gennemsnit pr. kategori
  * Varians pr. kategori
  * Maksimum pr. kategori
  * Minimum pr. kategori
  * Vægtet gennemsnit pr. kategori
* **Filtre**
  * Filtreret værdi
  * Forskel fra den filtrerede værdi
  * Procentvis forskel fra den filtrerede værdi
  * Salg fra nye kunder
* **Tidsintelligens**
  * Total for år til dato
  * Total for kvartal til dato
  * Total for måned til dato
  * Ændring år for år
  * Ændring kvartal for kvartal
  * Ændring måned for måned
  * Glidende gennemsnit
* **Totaler**
  * Løbende total
  * I alt for kategori (filtre anvendt)
  * I alt for kategori (filtre ikke anvendt)
* **Matematiske funktioner**
  * Tilføjelse
  * Subtraktion
  * Multiplikation
  * Division
  * Procentvis forskel
  * Korrelationskoefficienten
* **Tekst**
  * Stjerneklassifikation
  * Sammenkædet liste over værdier

Hvis du har ideer til nye hurtigmålinger, du godt kunne tænke dig, underliggende DAX-formler eller andre forslag til hurtigmålinger, kan du se, hvordan du indsender dem, nederst i denne artikel.

> [!NOTE]
> Når du bruger dynamiske forbindelser med SSAS (SQL Server Analysis Services), er visse hurtigmålinger tilgængelige. I Power BI Desktop kan du kun se de hurtigmålinger, som understøttes for den version af SSAS, der oprettes forbindelse til. Hvis du har oprettet forbindelse til en dynamisk SSAS-datakilde, og der er visse hurtigmålinger, som du ikke kan se på listen, skyldes det, at den version af SSAS, du har oprettet forbindelse til, ikke understøtter de DAX-kommandoer, der bruges til at implementere disse hurtigmålinger.

Når du har valgt de beregninger og felter, du vil bruge til hurtigmålingen, skal du vælge **OK**. Den nye hurtigmåling vises i ruden **Felter**, og den underliggende DAX-formel vises på formellinjen. 

## <a name="quick-measure-example"></a>Eksempel på hurtigmåling
Lad os se på en hurtigmåling i funktion.

I følgende matrixvisualisering vises en salgstabel over forskellige produkter. Det er en grundlæggende tabel, der inkluderer den samlede omsætning for hver kategori.

![Matrixvisualisering, der viser en salgstabel](media/desktop-quick-measures/quick-measures_05.png)

Når matrixvisualiseringen er valgt, skal du vælge rullelistepilen ud for **TotalSales** i **Værdier** og vælge **Ny hurtigmåling**. 

I vinduet **Hurtigmålinger** under **Beregning** skal du vælge **Gennemsnit pr. kategori**. 

Træk **Gennemsnitlig enhedspris** fra ruden **Felter** til feltet **Basisværdi**. Lad **Kategori** blive stående i feltet **Kategori**, og vælg **OK**. 

![Skærmbillede af Power BI Desktop, der viser indstillingen Filtre i ruden Felter.](media/desktop-quick-measures/quick-measures_06.png)

Når du vælger **OK**, sker der flere interessante ting.

![Ny hurtigmåling i visualiseringen, formellinjen og listen Felter](media/desktop-quick-measures/quick-measures_07.png)

1. Der vises en ny kolonne i matrixvisualiseringen, der indeholder den beregnede **gennemsnitlige enhedspris pr. kategori**.
   
2. DAX-formlen for den nye hurtigmåling vises på formellinjen. Du kan finde flere oplysninger om DAX-formlen i [næste afsnit](#learn-dax-by-using-quick-measures).
   
3. Den nye hurtigmåling vises valgt og fremhævet i ruden **Felter**. 

Den nye hurtigmåling kan bruges til alle visualiseringer i rapporten og ikke kun den visualisering, du har oprettet den for. I følgende billede kan du se en hurtig visualisering af et søjlediagram, der er oprettet ved hjælp af det nye felt med hurtigmålinger.

![Ny visualisering af søjlediagram baseret på feltet med hurtigmålinger](media/desktop-quick-measures/quick-measures_09.png)

## <a name="learn-dax-by-using-quick-measures"></a>Lær at bruge DAX ved hjælp af hurtigmålinger
En stor fordel ved hurtigmålinger er, at du får vist den DAX-formel, som implementerer målingen. Når du vælger en hurtigmåling i ruden **Felter**, vises **formellinjen** med den DAX-formel, som blev oprettet i Power BI for at implementere målingen.

![Formel for hurtigmåling på formellinjen](media/desktop-quick-measures/quick-measures_10.png)

Formellinjen viser ikke kun formlen bag målingen, men den viser dig også, hvordan du opretter de DAX-formler, som ligger til grund for hurtigmålingerne.

Forestil dig, at du skal udføre en År for år-beregning, men at du ikke er sikker på, hvordan du skal strukturere DAX-formlen, eller du måske slet ikke ved, hvor du skal starte. I stedet for at hive dig i håret kan du oprette en hurtigmåling ved hjælp af beregningen **Ændring år for år** og se, hvordan den vises i din visualisering, og hvordan DAX-formlen virker. Derefter kan du enten foretage ændringer direkte i DAX-formlen eller oprette en lignende måling, som opfylder dine behov og forventninger. Det er som at have en lærer, der lynhurtigt svarer på dine Hvad nu hvis-spørgsmål med bare nogle få klik. 

Du kan altid slette hurtigmålingerne i din model, hvis du ikke kan lide dem. Det gør du ved at højreklikke eller vælge **...** ud for målingen og derefter vælge **Slet**. Du kan også omdøbe en hurtigmåling ved at vælge **Omdøb** i menuen. 

![Slet eller omdøb en hurtigmåling](media/desktop-quick-measures/quick-measures_11.png)

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser
Der er nogle få begrænsninger og overvejelser, du skal være opmærksom på.

- Du kan bruge alle de hurtigmålinger, der er føjet til ruden **Felter**, i alle visualiseringer i rapporten.
- Du kan altid se den DAX-formel, der er tilknyttet en hurtigmåling, ved at vælge målingen på listen **Felter** og derefter se formlen på formellinjen.
- Du kan kun bruge hurtigmålinger, hvis du kan redigere modellen. Det kan du ikke altid, når du arbejder med visse dynamiske forbindelser. Dynamiske SSAS-tabelforbindelser understøttes som tidligere beskrevet.
- Du kan ikke oprette tidsintelligente hurtigmålinger, når du arbejder i DirectQuery-tilstand. De DAX-funktioner, der bruges i disse hurtigmålinger, har indflydelse på ydeevnen, når de oversættes til de T-SQL-sætninger, der sendes til din datakilde.

> [!IMPORTANT]
> Der bruges kun kommaer som separatorer i argumenter i DAX-sætninger til hurtigmålinger. Hvis din version af Power BI Desktop er på et sprog, hvor der bruges decimalkomma, vil hurtigmålingerne ikke virke korrekt.

### <a name="time-intelligence-and-quick-measures"></a>Time intelligence og hurtigmålinger
Du kan bruge dine egne brugerdefinerede datotabeller med hurtigmålinger for time intelligence. Hvis du bruger en ekstern model i tabelformat, skal du sikre dig, at den primære datokolonne i tabellen blev markeret som en datotabel, som beskrevet i [Angiv mærke som datotabel, der skal bruges sammen med time intelligence](/sql/analysis-services/tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular), da den blev bygget. Hvis du importerer din egen datotabel, skal du sørge for at markere den som en datotabel, som beskrevet i [Angiv og brug datotabeller i Power BI Desktop](desktop-date-tables.md).

### <a name="additional-information-and-examples"></a>Yderligere oplysninger og eksempler
Har du en idé til en hurtigmåling, som ikke allerede findes? Fantastisk! Se siden med [idéer til Power BI](https://go.microsoft.com/fwlink/?linkid=842906), og send dine idéer og DAX-formler til de hurtigmålinger, du godt kunne tænke dig i Power BI Desktop. Vi vil overveje at føje dem til listen over hurtigmålinger i en fremtidig version.