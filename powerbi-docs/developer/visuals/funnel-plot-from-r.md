---
title: Byg en tragtformet afbildning fra R-script til R-visualisering
description: I denne artikel beskrives det, hvordan du opretter en tragtformet afbildning fra R-script til R Power BI-visualiseringen.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: 7ef9b75f01dedaf55be77312f07217593d886ef0
ms.sourcegitcommit: 5c09d121d3205e65fb33a2eca0e60bc30e777773
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/18/2020
ms.locfileid: "97675275"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>Selvstudium: Byg en tragtformet afbildning fra R-script til R-visualisering
I denne artikel beskrives det, hvordan du opretter en tragtformet afbildning ved hjælp af R-script i R-visualisering trin for trin.

I denne artikel får du mere at vide om, hvordan du opretter:

> [!div class="checklist"]
>
> * et R-script til RStudio
> * en R-visualisering i Power BI
> * et *PNG-baseret* R-drevet visuelt element i Power BI
> * et *HTML-baseret* R-drevet visuelt element i Power BI

En tragtformet afbildning er en nem måde at bruge, fortolke og vise mængden af forventet variation på. **Tragten** er udformet ved hjælp af tillidsgrænser, og udenforliggende værdier vises som prikker uden for tragten.

I dette eksempel bruges den tragtformede afbildning til at sammenligne og analysere forskellige sæt af datasæt.  

> [!NOTE]
> Kildefiler kan hentes under hvert sæt med trin.

## <a name="build-an-r-script-with-dataset"></a>Byg et R-script med datasæt

1. Download et [minimalt R-script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) og dets datatabel, [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv).

1. Rediger derefter scriptet for at afspejle [dette script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r). Dette tilføjer håndtering af indtastningsfejl og brugerparametre for at styre afbildningens udseende.

## <a name="build-a-report"></a>Opret en rapport

Rediger derefter scriptet for at afspejle [dette script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r). Dette indlæser *.csv* i stedet for *read.csv* i Power BI Desktop-arbejdsområdet, og der oprettes en tabel med navnet **Cancer Mortality**. Se resultaterne i følgende [PBIX-fil](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix).

> [!NOTE]
> `dataset` er et hårdt kodet navn på indtastningen `data.frame` for en R-visualisering. 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>Opret et R-drevet visuelt element og en pakke i R-kode

1. Før du begynder, skal du sørge for at [installere PBIVIZ-værktøjer](./environment-setup.md#install-pbiviz).

1. Kør følgende kommando for at oprette et nyt R-drevet visuelt element:

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   Denne kommando opretter mappen *tragtformet visualisering* med den oprindelige skabelonvisualisering (`-t` for **skabelon**). PBIVIZ findes i mappen *dist*, som er R-koden i *script.r*-filen. Prøv at importere den i Power BI, og se, hvad der sker.

1. Rediger *script.r*-filen, og erstat indholdet med dit forrige script.

1. Rediger *capabilities.json*, og erstat strengen `Values` med `dataset`. Dette erstatter navnet på "rolle" i skabelonen, så den er som i R-kode.

   ![Skærmbillede, der viser en sammenligning af ændringen i json-filen.](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. *(valgfrit)* Rediger *dependencies.json*, og tilføj et afsnit for hver R-pakke, der kræves af R-scriptet. Dette fortæller Power BI, at disse pakker skal importeres automatisk, når visualiseringen indlæses for første gang.

   ![Skærmbillede, der viser en sammenligning, hvor indhold er føjet til cranPackages-elementerne.](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. Opret en ny pakke med det visuelle element ved hjælp af kommandoen `pbiviz package`, og prøv at importere den i Power BI.

> [!NOTE]
> Se [PBIX](https://github.com/microsoft/PowerBI-visuals/blob/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) og [kildekode](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/) for at downloade.

## <a name="make-r-based-visual-improvements"></a>Foretag R-baserede visuelle forbedringer

Det visuelle element er endnu ikke brugervenligt, fordi brugeren skal kende rækkefølgen af kolonnerne i inputtabellen.

1. Opdel inputfeltet `dataset` i tre felter (roller): `Population`, `Number` og `Tooltips`

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. Rediger *capabilities.json*, og erstat `dataset`-rollen med de tre nye roller, eller hent [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json).

   Du skal opdatere sektioner: `dataRoles` og `dataViewMappings`, som definerer navne, typer, værktøjstip og maks. kolonner for hvert inputfelt.

   ![før og efter](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   Du kan finde flere oplysninger under [egenskaber](./capabilities.md).

1. Rediger *script.r* for at understøtte `Population`, `Number` og `Tooltips` som inputdatarammer i stedet for `dataset`, eller hent [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r).

   ![script](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > Hvis du vil følge ændringerne i R-script, skal du søge efter kommentarblokke: 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. Opret en ny pakke med det visuelle element ved hjælp af kommandoen `pbiviz package`, og prøv at importere den i Power BI.

> [!NOTE]
> Se [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) og [kildekode](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02) for at downloade.

## <a name="add-user-parameters"></a>Tilføj brugerparametre

1. Tilføj funktioner, som brugeren kan bruge til at styre farver og størrelser på visuelle elementer, herunder interne parametre fra brugergrænsefladen.

   ![Skærmbillede, der viser to versioner af ruden Værktøjer, hvor der er føjet indstillinger til versionen til højre.](./media/funnel-plot/diagram-two.PNG)

1. Rediger *capabilities.json*, og opdater afsnittet `objects`. Her definerer vi navne, værktøjstip og typer for hver parameter og beslutter også, hvilken partition af parametre der skal være i grupper (tre grupper i dette tilfælde).

   Download [capabilities.jsonN](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json), se [objektegenskaber](./objects-properties.md) for at få flere oplysninger

   ![egenskaber](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. Rediger *src/settings.ts* for at afspejle [denne settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts). Denne fil er skrevet i TypeScript.  

   Her finder du to blokke af koden føjet til:
   - Angiv ny grænseflade, der skal indeholde egenskabsværdien
   - Definer en medlemsegenskab og standardværdier

   ![indstillinger](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. Rediger *script.r* for at afspejle [dette script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r). Dette tilføjer understøttelse af parametrene i brugergrænsefladen ved at tilføje `if.exists` opkald pr. brugerparameter.

   > [!TIP]
   > Hvis du vil følge ændringerne i R-scriptet, skal du søge efter kommentarer:
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![script før og efter](https://raw.githubusercontent.com/microsoft/PowerBI-visuals/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   Du kan beslutte ikke at fremvise parametrene til brugergrænsefladen, som vi gjorde.  

1. Opret en ny pakke med det visuelle element ved hjælp af kommandoen `pbiviz package`, og prøv at importere den i Power BI.

> [!NOTE]
> Se [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) og [kildekode](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/) for at downloade.

> [!TIP]
> Her har vi tilføjet parametre for adskillige typer (boolesk, numerisk, streng og farve) på én gang. Hvis du vil have et simpelt eksempel, kan du se [dette eksempel](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md) om, hvordan du tilføjer en enkelt parameter. 

## <a name="convert-visual-to-rhtml-based-visual"></a>Konvertér visualisering til RHTML-baseret visualisering

Da det resulterende visuelle element i PNG-format ikke reagerer på musemarkøren, kan den bl.a. ikke zoomes ind på, så vi skal konvertere den til et HTML-baseret visuelt element. Vi opretter en tom, R-drevet, HTML-baseret visualiseringsskabelon og kopierer derefter nogle scripts fra det PNG-baserede projekt.

1. Kør kommandoen:

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. Åbn *capabilities.jsonN*, og notér `"scriptOutputType":"html"`-linjen.

1. Åbn *dependencies.json*, og notér navnene på de viste R-pakker.

1. Åbn *script.r*, og notér strukturen. Du kan åbne og køre den i RStudio, da den ikke bruger eksternt input. 

   Dermed oprettes og gemmes *out.html*. Denne fil foregår separat (uden nogen eksterne afhængigheder) og definerer grafikken inden i HTML-widgetten. 

   > [!IMPORTANT]
   > For `htmlWidgets`-brugere leveres R-programmer i [mappen r_files](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files) som en hjælp til at konvertere `plotly`- eller `widget`-objekter i separat HTML. 
   > 
   > Denne version af R-drevet visualisering understøtter også kommandoen `source` (i modsætning til tidligere typer visualiseringer) for at gøre din kode mere læselig.   
 
1. Erstat *capabilities.json* med *capabilities.json* fra det forrige trin, eller hent [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json).

   Sørg for at beholde:

   `"scriptOutputType": "html"`

1. Flet den nyeste version af *script.r* med scriptet *.r* fra skabelonen, eller hent [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r).

   Det nye script bruger `plotly`-pakken til at konvertere **ggplot**-objektet til et **afbildnings** objekt og derefter `htmlWidgets`-pakken til at gemme den i en HTML-fil. 

   De fleste funktioner i værktøjet flyttes til [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r) og funktionen `generateNiceTooltips` tilføjes for udseendet af **afbildnings** objektet.

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > Hvis du vil følge ændringerne i R-scriptet, skal du søge efter kommentarer:
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. Flet den nyeste version af *dependencies.json* med *dependencies.json* fra skabelonen for at inkludere nye R-pakkeafhængigheder, eller hent [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json).

1. Rediger *src/settings.ts* på samme måde som fra tidligere trin.

1. Opret en ny pakke med det visuelle element ved hjælp af kommandoen `pbiviz package`, og prøv at importere den i Power BI.

> [!NOTE]
> Se [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01) og kildekode for at downloade.

## <a name="build-additional-examples"></a>Opret yderligere eksempler

1. Kør følgende kommando for at oprette et tomt projekt: 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. Tag kode fra denne [fremvisning](http://www.htmlwidgets.org/showcase_networkD3.html), og foretag de fremhævede ændringer:

   ![Fremhævede ændringer](./media/funnel-plot/diagram-three.PNG)

1. Erstat skabelonens *script.r*, og kør `pbiviz package` igen. Det visuelle element er nu inkluderet i din Power BI-rapport!

## <a name="tips-and-tricks"></a>Tip og tricks

* Vi anbefaler, at udviklere redigerer *pbiviz.json* for at gemme korrekte metadata, f.eks. **version**, **mail**, **navn**, **licenstype** osv.

   > [!IMPORTANT]
   > Feltet **guid** er det entydige id for et visuelt element. Hvis du opretter et nyt projekt for hver enkelt visualisering, vil GUID også være anderledes. Det er kun det samme, når du bruger et gammelt projekt, der kopieres til et nyt visuelt element, som du ikke bør gøre.

* Rediger [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) for at oprette entydige ikoner til dit visuelle element. 

* Hvis du vil foretage fejlfinding af R-kode i RStudio ved hjælp af de samme data som i din Power BI-rapport, skal du tilføje følgende til starten af R-scriptet (rediger `fileRda`-variablen):

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   Dette gemmer miljøet fra en Power BI-rapport og indlæser det i RStudio. 

* Du behøver ikke at udvikle R-drevne visuelle elementer fra bunden med den kode, der er tilgængelig på [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R). Du kan vælge det visuelle element, der skal bruges som skabelon, og kopiere koden til et nyt projekt.

   Prøv f.eks. at bruge den [brugerdefinerede visualisering som sløjfe](https://github.com/Microsoft/PowerBI-visuals-spline).

* Hver R-visualisering anvender `unique`-operatoren på dens inputtabel. Hvis du vil undgå, at identiske rækker fjernes, kan du overveje at tilføje et ekstra inputfelt med et entydigt ID og ignorere det i R-koden.   

* Hvis du har en Power BI-konto, kan du bruge Power BI-tjenesten til at udvikle en visualisering [undervejs](./develop-circle-card.md) i stedet for at pakke dem ud med kommandoen `pbiviz package`.

### <a name="html-widgets-gallery"></a>Galleri med HTML-widgets
Udforsk visuelle elementer i [galleriet med HTML-widgets](http://gallery.htmlwidgets.org/) til brug i det næste visuelle element. For at gøre tingene nemmere har vi oprettet et [lager med visuelle projekter](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML) med mere end 20 interaktive HTML-visualiseringer, som du kan vælge imellem!

> [!TIP]
> Hvis du vil skifte mellem HTML-widgets, skal du bruge **Format** > **Indstillinger** > **Type**. Prøv det med [denne PBIX-fil](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix). 

#### <a name="to-use-a-sample-for-your-visual"></a>Sådan kan du bruge et eksempel til din visualisering

1. Hent hele mappen.
1. Rediger *script.r* og *dependencies.json* for kun at bevare én widget.
1. Rediger *capabilities.json* og *settings.ts* for at fjerne `Type`-vælgeren.
1. Rediger `const updateHTMLHead: boolean = true;` til `false` i *visual.ts*. *(for at opnå en bedre ydeevne)*
1. Skift metadata i *pbiviz.jsonN*, vigtigst af alt `guid`-feltet.
1. Opret en ny pakke, og fortsæt med at tilpasse visualiseringen efter ønske. 

![Skærmbillede, der viser seks widgets, som er beskrevet tidligere i denne artikel.](./media/funnel-plot/diagram-four.PNG)

![Skærmbillede, der viser yderligere seks widgets, som er beskrevet tidligere i denne artikel.](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> Ikke alle widgets i dette projekt understøttes af tjenesten.

## <a name="next-steps"></a>Næste trin

Hvis du vil vide mere, kan du se yderligere Power BI-selvstudier, [Udvikling af en Power BI-cirkelkortvisualisering](./develop-circle-card.md) og [R-visualiseringer](../../visuals/service-r-visuals.md).

Få mere at vide om, hvordan du [udvikler og sender visuelle elementer](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/) til [Office Store (galleri)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI), eller se flere eksempler i [R-script-fremvisning](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)