---
title: Få en rundvisning af ruden Rapportfiltre
description: Sådan føjer du et filter til en rapport i Power BI-tjenesten for erhvervsbrugere
author: mihart
ms.reviewer: mihart
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 09/29/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fb283858d9e6fe016e382f4c662de6b66bce0258
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/30/2020
ms.locfileid: "91600813"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Få en præsentation af ruden Rapportfiltre

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

I denne artikel ser vi nærmere på ruden **Filtre** i rapporter i Power BI-tjenesten. Brug filtre for at få ny indsigt i dine data.

Der er mange forskellige måder at filtrere data på i Power BI. I denne artikel forklares det, hvordan du bruger ruden **Filtre**.  Du kan også filtrere ved at vælge datapunkter i en rapportvisualisering for at filtrere de øvrige visualiseringer på siden. Dette kaldes **krydsfiltrering** og **tværgående fremhævning**. Du kan få flere oplysninger om krydsfiltrering og tværgående fremhævning under [Filtre og fremhævning i Power BI-rapporter](../create-reports/power-bi-reports-filters-and-highlighting.md).

![Skærmbillede af en rapport i browseren med en pil, der peger på indstillingen Filtre.](media/end-user-report-filter/power-bi-reports.png)

## <a name="working-with-the-report-filters-pane"></a>Arbejde med ruden Filtre i rapporter

Når en kollega deler en rapport med dig, skal du søge efter ruden **Filtre**. Nogle gange er den skjult langs højre kant af rapporten. Vælg den for at udvide den.

![Skærmbillede af rapporten med ruden Filtre udvidet.](media/end-user-report-filter/power-bi-expand-filters-pane.png)

Ruden **Filtre** indeholder filtre, der er tilføjet i rapporten af rapportens *designer*. *Erhvervsbrugere* som dig selv kan interagere med de eksisterende filtre og gemme ændringer, men forbrugere kan ikke tilføje nye filtre i rapporten. På ovenstående skærmbillede har designeren f.eks. tilføjet tre filtre på sideniveau: **Segment er Alle**, **År er 2014** og **Område er Central**. Du kan interagere med og ændre disse filtre, men du kan ikke tilføje et filter på et fjerde sideniveau.

Nogle af filtrene er skyggelagt, og nogle er ikke. Hvis et filter er skyggelagt, betyder det, at der er anvendt et filter, og nogle af dataene er udeladt. Filterkortet **Område** er f.eks. skyggelagt, og når du udvider kortet, kan du se, at det kun er **Central**, der er valgt på rullelisten. Da Område ligger under overskriften **Filtre på denne side**, er det ikke alle visualiseringer på siden, der viser (udelader) data for områderne **Vest** og **Øst**.

![Skærmbillede af filteret Område er udvidet og viser Central med et flueben.](media/end-user-report-filter/power-bi-filter-region.png)

I Power BI-tjenesten beholder rapporter eventuelle ændringer, du foretager i ruden **Filtre**. Tjenesten overfører også disse ændringer til mobilversionen af rapporten. 

Hvis du vil nulstille ruden **Filtre** til designerens standarder, skal du vælge **Nulstil til standard** i den øverste menulinje.

![Skærmbillede af ikonet Nulstil til standard.](media/end-user-report-filter/power-bi-reset-icon.png) 

> [!NOTE]
> Hvis du ikke kan se indstillingen **Nulstil til standard**, kan den være deaktiveret af *rapportdesigneren*. *Designeren* kan også låse bestemte filtre, så du ikke kan ændre dem.

## <a name="view-all-the-filters-for-a-report-page"></a>Vis alle filtrene for en rapportside

I ruden **Filtre** vises alle de filtre, der er tilføjet af rapportens designer. Ruden **Filtre** er også det område, hvor du kan få vist oplysninger om filtrene og interagere med dem. Gem de ændringer, du foretager, eller brug **Nulstil til standard** for at vende tilbage til de oprindelige filterindstillinger.

Hvis der er ændringer, du vil gemme, kan du også oprette et personligt bogmærke. Du kan finde flere oplysninger under [Hvad er bogmærker?](end-user-bookmarks.md).

I ruden **Filtre** vises og administreres flere typer rapportfiltre: rapport, rapportside og visualisering.

I dette eksempel har vi valgt en visualisering, der indeholder tre filtre: **Producent**, **Måned** og **Enheder i alt**. Der er også filtre på rapportsiden. De er angivet under overskriften **Filtre på denne side**. Hele rapporten har desuden et filter for **Dato**, der er angivet under **Filtre på alle sider**.

![Skærmbillede af en rapport med en visualisering og dens relaterede filtre fremhævet.](media/end-user-report-filter/power-bi-filter-pane.png)

Ud for nogle af filtrene vises teksten **(Alle)**. **(Alle)** betyder, at alle værdier er inkluderet i filteret. På skærmbilledet ovenfor viser **Segment (Alle)**, at denne rapportside indeholder data om alle produktsegmenterne. 

Alle, der er tilladelse til at få vist denne rapport, kan arbejde med disse filtre.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Vis kun de filtre, der anvendes på en visualisering

Hvis du vil se nærmere på de filtre, der påvirker en bestemt visualisering, skal du holde markøren over visualiseringen for at få vist filterikonet ![Skærmbillede af filterikonet](media/end-user-report-filter/power-bi-filter-icon.png). Vælg filterikonet for at se et pop op-vindue med alle de filtre, udsnitsværktøjer m.m., der påvirker den pågældende visualisering. Filtrene i pop op-vinduet indeholder de samme filtre, der vises i ruden **Filtre**, samt eventuel yderligere filtrering, der påvirker den valgte visualisering.

![Skærmbillede af en liste over filtre med pile, der peger på de steder, hvor filtrene vises i ruden Filtre.](media/end-user-report-filter/power-bi-filters-hover.png)

Her er de filtertyper, der kan vises i denne visning:

- Grundlæggende filtre
- Udsnit
- Tværgående fremhævning
- Tværgående filtrering
- Avancerede filtre
- Top N-filtre
- Filtre for Relativ dato
- Udsnitsværktøjer til synkronisering
- Filtre for Inkluder/Ekskluder
- Filtre sendt via en URL-adresse

I dette eksempel:
1. **Inkluderet** fortæller os, at visualiseringen er krydsfiltreret. Det betyder, at staterne Alabama og Texas er valgt i en af de andre visualiseringer på denne rapportside. I dette tilfælde er det kortvisualiseringen. Valget af disse to stater har forhindret, at data for alle andre stater vises i det valgte søjlediagram.  

1. **Dato** er et filter, der anvendes på alle sider i denne rapport.

1. **Område er Central** og **År er 2014** er filtre, der anvendes for denne rapportside.

4. **Producent er VanArsdel, Natura, Aliqui eller Pirum** er et filter, der er anvendt på denne visualisering.


### <a name="search-in-a-filter"></a>Søg i et filter

Et filter kan nogle gange have en lang liste over værdier. Brug søgefeltet til at søge efter og vælge den ønskede værdi.

![Skærmbillede af, hvordan du kan søge i et filter.](media/end-user-report-filter/power-bi-search-filter.png)

### <a name="display-filter-details"></a>Vis filteroplysninger

Hvis du vil forstå et filter, skal du udvide det og se nærmere på de tilgængelige værdier og antal.  Hvis du vil udvide filteret, skal du vælge pilen ud for filternavnet.
  
![Skærmbillede af et filter, der viser det vestlige område som valgt.](media/end-user-report-filter/power-bi-filters-expand.png)

### <a name="change-filter-selections"></a>Rediger filtervalg

En metode til at søge efter dataindsigt er at interagere med filtrene. Du kan ændre filtervalg ved hjælp af rullepilen ud for feltets navn.  Afhængigt af det filter og den datatype, der filtreres i Power BI, vil dine muligheder variere fra enkle valg på en liste til at angive dato- eller talområder. I det avancerede filter nedenfor har vi ændret filteret **Antal enheder i alt ÅTD** på træstrukturen til at være mellem 2.000 og 3.000. Bemærk, at Pirum fjernes fra træstrukturen med denne ændring.
  
![Skærmbillede af en rapport og dens filtre, der viser, at en træstrukturvisualisering er valgt.](media/end-user-report-filter/power-bi-treemap-filter.png)

> [!TIP]
> Hvis du vil vælge mere end én filterværdi ad gangen, skal du holde CTRL-tasten nede. De fleste filtre understøtter valg af flere værdier.

### <a name="reset-filter-to-default"></a>Nulstil filter til standard

Hvis du vil annullere alle ændringer du har foretaget i filtrene, skal du vælge **Nulstil til standard** fra den øverste menulinje.  Med dette valg vender filtrene tilbage til deres oprindelige tilstand, som var angivet af rapportens designer.

![Skærmbillede af indstillingen Nulstil til standard.](media/end-user-report-filter/power-bi-reset-icon.png)

### <a name="clear-a-filter"></a>Ryd et filter

Hvis du vil nulstille et filter til (Alle), skal du rydde det ved at vælge viskelæderikonet ud for navnet på filteret.

![Skærmbillede af viskelæderikonet.](media/end-user-report-filter/power-bi-erase.png)
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Næste trin

Få mere at vide om, hvordan og hvorfor [visualiseringer krydsfiltrerer og krydsfremhæver hinanden på en rapportside](end-user-interactions.md)
