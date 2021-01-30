---
title: Analysis Services flerdimensionelle data i Power BI Desktop
description: SSAS flerdimensionelle data (SQL Server Analysis Services) i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: b3ff42b33ccf2d93217d9d88ada4dfbe45a5436c
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99085446"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Opret forbindelse til SSAS flerdimensionelle modeller i Power BI Desktop

Med Power BI Desktop har du adgang til *SSAS flerdimensionelle modeller*, der ofte refereres til som *SSAS MD*.

Hvis du vil oprette forbindelse til en SSAS MD-database, skal du vælge **Hent data**, vælge **Database** > **SQL Server Analysis Services-database** og derefter vælge **Opret forbindelse**:

![SSAS-database (SQL Server Analysis Services), dialogboksen Hent data, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

Både Power BI-tjenesten og Power BI Desktop understøtter SSAS flerdimensionelle modeller i liveforbindelsestilstand. Du kan udgive og overføre rapporter, der bruger **SSAS flerdimensionelle modeller**, i livetilstand til Power BI-tjenesten.

## <a name="capabilities-and-features-of-ssas-md"></a>Egenskaber og funktioner i SSAS MD

I følgende afsnit beskrives egenskaber og funktioner i Power BI- og SSAS MD-forbindelser.

### <a name="tabular-metadata-of-multidimensional-models"></a>Metadata for tabeller i flerdimensionelle modeller

I følgende tabel vises overensstemmelsen mellem flerdimensionelle objekter og metadata for tabeller, der returneres til Power BI Desktop. Power BI forespørger modellen efter metadata for tabeller. Når du opretter en visualisering (f.eks en tabel, en matrix, et diagram eller et udsnit), kører Power BI Desktop relevante DAX-forespørgsler i SSAS baseret på de returnerede metadata.

| BISM-flerdimensionelt objekt | Metadata for tabeller |
| --- | --- |
| Kube |Model |
| Kubedimension |Tabel |
| Dimensionsattributter (nøgler), navn |Kolonner |
| Målegruppe |Tabel |
| Måling |Måling |
| Målinger uden tilknyttet målegruppe |I tabellen, der kaldes *Målinger* |
| Målegruppe -> Kubedimensionsrelation |Relation |
| Perspektiv |Perspektiv |
| KPI |KPI |
| Bruger/overordnede/underordnede hierarkier |Hierarkier |

### <a name="measures-measure-groups-and-kpis"></a>Målinger, målegrupper og KPI'er

Målegrupper i en flerdimensionel kube vises som tabeller med fortegnet ∑ ud for dem i ruden **Felter**. Beregnede målinger, der ikke har en tilknyttet målegruppe, er grupperet under en særlig tabel, der kaldes *Målinger*, i metadata for tabeller.

For at hjælpe med at forenkle komplekse modeller i en flerdimensionel model kan du definere et sæt af målinger eller KPI'er i en kube, som skal være placeret i en *visningsmappe*. Power BI genkender visningsmapper i metadata for tabeller og viser målinger og KPI'er i visningsmapperne. KPI'er i flerdimensionelle databaser understøtter *Værdi*, *Mål*, *Statusgrafik* og *Tendensgrafik*.

### <a name="dimension-attribute-type"></a>Dimensionsattributtyper

Flerdimensionelle modeller understøtter også tilknytning af dimensionsattributter med specifikke dimensionsattributtyper. Der vises f.eks. en **Geografi**-dimension, hvor dimensionsattributterne *By*, *Stat/provins*, *Land/område* og *Postnummer* har relevante geografityper tilknyttet, i metadata for tabeller. Power BI genkender metadataene, hvilket giver dig mulighed for at oprette kortvisualiseringer. Du kan genkende disse tilknytninger vha. *kort*-ikonet ud for elementet i ruden **Felt** i Power BI.

Power BI kan også gengive billeder, når du angiver et felt, der indeholder URL-adresser (Uniform Resource Locator) for billederne. Du kan angive disse felter som *ImageURL*-typer i SQL Server Data Tools (eller i Power BI). Typen af oplysninger overføres derefter til Power BI i metadataene for tabeller. Power BI kan derefter hente disse billeder fra URL-adressen og vise dem i visuelle elementer.

### <a name="parent-child-hierarchies"></a>Overordnede/underordnede hierarkier

Flerdimensionelle modeller understøtter overordnede/underordnede hierarkier, som er angivet som et *hierarki* i metadataene for tabeller. Hvert niveau i det overordnede/underordnede hierarki vises som en skjult kolonne i metadataene for tabeller. Nøgleattributten for den overordnede/underordnede dimension vises ikke i metadata for tabeller.

### <a name="dimension-calculated-members"></a>Dimensionsberegnede medlemmer

Flerdimensionelle modeller understøtter oprettelse af forskellige typer af *beregnede medlemmer*. De to mest almindelige typer beregnede medlemmer er:

* Beregnede medlemmer i attributhierarkier, der ikke er sidestillet med *Alle*
* Beregnede medlemmer på brugerhierarkier

I flerdimensionelle modeller vises *beregnede medlemmer på attributhierarkier* som værdier i en kolonne. Der er nogle få ekstra indstillinger og begrænsninger, hvis du viser denne type af beregnet medlem:

* En dimensionsattribut kan have et valgfrit *UnknownMember*.

* En attribut, der indeholder beregnede medlemmer, må ikke være nøgleattribut for dimensionen, medmindre det er den eneste attribut for dimensionen.

* En attribut, der indeholder beregnede medlemmer, må ikke være en overordnet/underordnet attribut.

De beregnede medlemmer af brugerhierarkier vises ikke i Power BI. Du kan i stedet oprette forbindelse til en kube, der indeholder beregnede medlemmer i brugerhierarkier. Du kan dog ikke se de beregnede medlemmer, hvis de ikke overholder de begrænsninger, vi nævnte på listen med punkttegn ovenfor.

### <a name="security"></a>Sikkerhed

Flerdimensionelle modeller understøtter dimensions- og cellesikkerhed vha. *roller*. Når du opretter forbindelse til en kube med Power BI, godkendes og vurderes du for de nødvendige tilladelser. Hvis en bruger anvender *dimensionssikkerhed*, ses de forskellige dimensionsmedlemmer ikke af brugeren i Power BI. Men hvis en bruger har defineret en tilladelse af typen *cellesikkerhed*, hvor visse celler er begrænset, kan denne bruger ikke oprette forbindelse til kuben vha. Power BI.

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Der er visse begrænsninger for brug af SSAS MD:

* Kun Enterprise- og BI-udgaver af SQL Server 2014 understøtter liveforbindelser. I forbindelse med standardversionen af SQL Server kræves der SQL Server 2016 eller nyere til liveforbindelser.

* *Handlinger* og *navngivne sæt* vises ikke for Power BI. Hvis du vil oprette visuelle elementer og rapporter, kan du stadig oprette forbindelse til kuber, der også indeholder handlinger eller navngivne sæt.

* Når Power BI viser metadata for en SSAS-model, kan du ikke altid hente data fra modellen. Dette scenarie kan opstå, hvis du har installeret 32-bit versionen af MSOLAP-provideren, men ikke 64-bit versionen. Problemet kan muligvis løses ved at installere 64-bit-versionen.

* Du kan ikke oprette målinger på *rapportniveau*, når du opretter en rapport, som er direkte forbundet til en flerdimensionel SSAS-model. De eneste målinger, der er tilgængelige, er de målinger, der er defineret i MD-modellen.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Understøttede funktioner i SSAS MD i Power BI Desktop

Forbrug af følgende elementer understøttes i denne version af SSAS MD. Du kan finde flere oplysninger om disse funktioner under [Om Power-visning til flerdimensionelle modeller](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models).

* Standardmedlemmer
* Dimensionsattributter
* Dimensionsattributtyper
* Dimensionsberegnede medlemmer, som:
  * skal være et enkelt reelt medlem, når dimensionen har mere end én attribut,
  * ikke kan være nøgleattributten for dimensionen, medmindre det er den eneste attribut, og
  * ikke kan være en overordnet/underordnet attribut.
* Dimensionssikkerhed
* Få vist mapper
* Hierarkier
* ImageUrl'er
* KPI'er
* KPI-tendenser
* Målinger (med eller uden målegrupper)
* Målinger som variant

## <a name="troubleshooting"></a>Fejlfinding

På følgende liste beskrives alle kendte problemer, når der oprettes forbindelse til SQL Server Analysis Services (SSAS).

* **Fejl: Modelskemaet blev ikke indlæst** – Denne fejl opstår sædvanligvis, når den bruger, der opretter forbindelse til Analysis Services, ikke har adgang til databasen/kuben.
