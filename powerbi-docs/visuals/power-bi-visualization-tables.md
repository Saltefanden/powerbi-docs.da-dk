---
title: Tabelvisualiseringer i Power BI-rapporter og -dashboards
description: Selvstudium til at arbejde med tabelvisualiseringer i Power BI-rapporter og dashboards, herunder, hvordan du tilpasser kolonnebredder.
author: mihart
ms.author: mihart
ms.reviewer: willt
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/10/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: aa99cd4efed9239d6685d53f2515d16549a0ae72
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418802"
---
# <a name="tables-in-power-bi-reports-and-dashboards"></a>Tabeller i Power BI-rapporter og -dashboards

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]


[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

En tabel er et gitter, der indeholder relaterede data i logiske serier af rækker og kolonner. Den kan også indeholde overskrifter og en række til totaler. Tabeller fungerer godt med kvantitative sammenligninger, hvor du får vist mange værdier for en enkelt kategori. I denne tabel vises f.eks. fem forskellige målinger for **Kategori**.

![Skærmbillede af en tabel, der viser fem forskellige målinger for Kategori.](media/power-bi-visualization-tables/power-bi-table-grid3.png)

Opret tabeller i rapporter, og udfør tværgående fremhævning af elementer i tabellen med andre visualiseringer på samme rapportside. Du kan vælge rækker, kolonner og endda individuelle celler og tværgående fremhævning. Du kan også kopiere og indsætte de enkelte celler og markeringer med flere celler i andre programmer.

## <a name="when-to-use-a-table"></a>Du skal bruge en tabel, til at

Tabeller er et godt valg til at:

* se og sammenligne detaljerede data og nøjagtige værdier (i stedet for visuelle repræsentationer).

* se data i tabelformat.

* se numeriske data efter kategori.

## <a name="prerequisite"></a>Forudsætning

I dette selvstudium bruges [PBIX-filen med eksemplet Detailhandelsanalyse](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Vælg **Fil** > **Åbn** i øverste venstre afsnit af menulinjen
   
2. Find din kopi af **PBIX-filen med eksemplet Detailhandelsanalyse**

1. Åbn **PBIX-filen med eksemplet Detailhandelsanalyse** i rapportvisning ![ikon for skærmbillede af rapportvisning.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Markér ![Skærmbillede af den gule fane.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) for at tilføje en ny side.

> [!NOTE]
> Når du deler din rapport med en Power BI-kollega, kræves det, at I begge har individuelle Power BI Pro-licenser, eller at rapporten er gemt i en Premium-kapacitet.

## <a name="create-a-table"></a>Opret en tabel

Du opretter den tabel, der vises i starten af artiklen, for at få vist salgsværdierne efter varekategori.


1. Vælg **Element** > **Kategori** i ruden **Felter**.

    Power BI opretter automatisk en tabel over alle kategorierne.

    ![resultat af tilføjelse af kategori](media/power-bi-visualization-tables/power-bi-table1.png)

1. Vælg **Sales > Average Unit Price** og **Sales > Last Year Sales**

1. Vælg derefter **Sales > This Year Sales**, og vælg alle tre indstillinger: **Værdi**, **Mål** og **Status**.

1. I ruden **Visualiseringer** skal du finde brønden **Værdier** og vælge værdier, indtil rækkefølgen af dine diagramsøjler matcher det første billede på denne side. Træk værdierne i brønden, om nødvendigt. Du kan nu se følgende under **Værdier**:

    ![Værdibrønd](media/power-bi-visualization-tables/power-bi-table2.png)


## <a name="format-the-table"></a>Formatér tabellen

Du kan formatere en tabel på mange måder. Kun et par af dem beskrives her. Hvis du vil vide mere om andre formateringsindstillinger, kan du åbne ruden **Formatér** (ikonet med malerrullen ![malerrulle](media/power-bi-visualization-tables/power-bi-format.png)) og prøve dig frem.

* Prøv at formatere tabelgitteret. Her tilføjer du et blåt lodret gitter, du tilføjer mellemrum mellem rækkerne og forstørrer kanten og tekststørrelsen en smule.

    ![Gitterkort](media/power-bi-visualization-tables/power-bi-table-gridnew.png)

    ![tabel, der viser resultater](media/power-bi-visualization-tables/power-bi-table-grid3.png)

* I kolonneoverskrifterne skal du ændre baggrundsfarven, tilføje en kant og øge skriftstørrelsen.

    ![Kolonneoverskriftskort](media/power-bi-visualization-tables/power-bi-table-column-headers.png)

    ![overskriftsformatering i tabel](media/power-bi-visualization-tables/power-bi-table-column2.png)

* Du kan også formatere enkelte kolonner og kolonneoverskrifter. Start ved at udvide **feltformateringen**, og vælg den kolonne, der skal formateres, på rullelisten. Afhængigt af kolonneværdierne kan du bruge **feltformatering** til at angive oplysninger som: visningsenheder, skriftfarve, antal decimaler, baggrund, justering med mere. Når du har valgt de ønskede indstillinger, kan du beslutte, om du også vil anvende disse indstillinger til sidehovedet og rækken Totaler.

    ![Feltformatering for This year sales](media/power-bi-visualization-tables/power-bi-field-formatting.png)

    ![Feltformatering for This year sales i tabellen](media/power-bi-visualization-tables/power-bi-field-formatting-1.png)

* Efter lidt yderligere formatering ser den endelige tabel sådan ud.

    ![tabel med al formatering indtil videre](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Betinget formatering

*Betinget formatering* er en type formatering. Power BI kan anvende betinget formatering af alle de felter, du har føjet til **Værdier** i ruden **Visualiseringer**.

![Ruden Visualisering](media/power-bi-visualization-tables/power-bi-table-values.png)

Med betinget formatering af tabeller kan du angive ikoner, URL-adresser, baggrundsfarver og skriftfarver for celler baseret på celleværdier, bl.a. ved hjælp af gradueringsfarver.

1. I ruden **Formatér** skal du åbne kortet **Betinget formatering**.

    ![Kortet Betinget formatering](media/power-bi-visualization-tables/power-bi-conditional.png)

1. Vælg et felt, der skal formateres, og slå skyderen for **Baggrundsfarve** til. I Power BI anvendes en graduering baseret på værdierne i kolonnen. Hvis du vil ændre standardfarverne, skal du vælge **Avancerede kontrolelementer**.

    Hvis du vælger indstillingen **Divergerende**, kan du også konfigurere en valgfri værdi af typen **Centreret**.

    ![skærmen Baggrundsfarveskalaer](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)

    Jeg vil prøve at anvende brugerdefineret formatering til Average Unit Price-værdierne. Vælg **Divergerende**, tilføj nogle farver, og vælg **OK**.

    ![tabel, der viser divergerende farver](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
1. Tilføj et nyt felt i tabellen, der har både positive og negative værdier. Vælg **Sales > Total Sales Variance**.

    ![viser et nyt felt længst til højre](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)

1. Tilføj betinget formatering af datalinje ved at slå skyderen for **Datalinjer** til.  

    ![Kortet Betinget formatering af datalinjer er slået til](media/power-bi-visualization-tables/power-bi-data-bar-matrix.png)

1. Hvis du vil tilpasse datalinjerne, skal du vælge **Avancerede kontrolelementer**. I den viste dialogboks kan du angive farver for **Positiv streg** og **Negativ streg**, markere afkrydsningsfeltet **Vis kun streg** og foretage eventuelle andre ændringer.

    ![afkrydsning af Vis kun streg](media/power-bi-visualization-tables/power-bi-data-bar.png)

1. Vælg **OK**.

    Datalinjerne erstatter de numeriske værdier i tabellen, så det er nemmere at skimme den.

    ![samme tabel, men med søjler i sidste kolonne](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)

1. Føj visualiseringsstikord til din tabel med *betingede ikoner*.  På kortet **Betinget formatering** skal du vælge **Dette års salg** på rullelisten. Slå skyderen for **Ikoner** **Til**.  Hvis du vil tilpasse ikonerne, skal du vælge **Avancerede kontrolelementer**.

    ![Tabel med ikoner tilføjet](media/power-bi-visualization-tables/power-bi-table-icons.png)


## <a name="copy-values-from-power-bi-tables-for-use-in-other-applications"></a>Kopiér værdier fra Power BI-tabeller til brug i andre programmer

Din tabel eller matrix kan have indhold, som du ønsker at bruge i andre programmer, f.eks. Dynamics CRM, Excel og endda andre Power BI-rapporter. Når du højreklikker i en celle i Power BI, kan du kopiere dataene i en enkelt celle eller en markering med flere celler til udklipsholder og indsætte dem i det andet program.

Sådan kopierer du værdien af en enkelt celle:

1. Markér den celle, du vil kopiere.

1. Højreklik i cellen.

1. Vælg **Kopiér** > **Kopiér værdi**.

    ![Skærmbillede, der viser Kopiér valgt med indstillingen Kopiér værdi valgt.](media/power-bi-visualization-tables/power-bi-copy-value.png)

    Den ikke-formaterede celleværdi er nu i din udklipsholder, og du kan indsætte den i et andet program.

Sådan kopierer du mere end en enkelt celle:

1. Markér et celleområde, eller brug **Ctrl** til at markere en eller flere celler.

1. Højreklik i en af de celler, du har markeret.

1. Vælg **Kopiér** > **Kopiér markering**.

    ![Skærmbillede, der viser Kopiér valgt med indstillingen Kopiér markering valgt.](media/power-bi-visualization-tables/power-bi-copy-selection.png)

## <a name="adjust-the-column-width-of-a-table"></a>Tilpas kolonnebredden i en tabel

Nogle gange kan Power BI afskære en kolonneoverskrift i en rapport og på et dashboard. Hvis du vil kunne se hele kolonnenavnet, skal du pege på mellemrummet til højre for overskriften for at få vist dobbeltpilene og klikke og trække.

![videocloseup af ændring af kolonnestørrelse](media/power-bi-visualization-tables/resizetable.gif)


## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

* Når du anvender kolonneformatering, kan du kun vælge én indstilling for justering pr. kolonne: **Automatisk**, **Venstre**, **Centreret**, **Højre**. En kolonne indeholder som regel enten tekst eller tal og ikke en blanding. Hvis en kolonne indeholder både tal og tekst, vil indstillingen **Automatisk** venstrejustere tekst og højrejustere tal. Denne funktionalitet understøtter de sprog, der læses fra venstre mod højre.

* Hvis tekstdataene i cellerne eller overskrifterne i tabellen indeholder nye linjetegn, ignoreres disse tegn, medmindre du slår indstillingen Tekstombrydning til på elementets tilknyttede formateringsrudekort. 

* Power BI beregner den maksimale cellestørrelse baseret på de første tyve kolonner og de første 50 rækker. Celler, der ligger uden for disse punkter, er muligvis ikke korrekt tilpasset.


## <a name="next-steps"></a>Næste trin

* [Trædiagrammer i Power BI](power-bi-visualization-treemaps.md)

* [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
