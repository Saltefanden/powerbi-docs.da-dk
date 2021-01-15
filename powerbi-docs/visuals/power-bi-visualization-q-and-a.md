---
title: Opret en visualisering til Spørgsmål og svar i Power BI
description: Sådan opretter og formaterer du en visualisering til Spørgsmål og svar i Power BI Desktop eller Power BI-tjenesten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: rien
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 01/05/2021
ms.openlocfilehash: 1cf80593458c12a1bee07ed40202e3613fdcb5e9
ms.sourcegitcommit: c700e78dfedc34f5a74b23bbefdaef77e2a87f8a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/07/2021
ms.locfileid: "97961356"
---
# <a name="create-a-qa-visual-in-power-bi"></a>Opret en visualisering til Spørgsmål og svar i Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

Visualiseringen til Spørgsmål og svar giver brugerne mulighed for at stille spørgsmål på et naturligt sprog og få svar i form af en visualisering. *Forbrugere* kan bruge den til hurtigt at få svar på deres data. *Designere* kan også bruge den til hurtigt at oprette visualiseringer. Hvis du er rapportdesigner, er denne artikel til dig. Du kan dobbeltklikke et vilkårligt sted i en rapport og bruge et naturligt sprog for at komme i gang. I denne artikel beskrives det, hvordan du opretter, formaterer og tilpasser en visualisering til Spørgsmål og svar. Den understøtter temaer og andre standardformateringsindstillinger, der er tilgængelige i Power BI. Når du har oprettet den, fungerer den som alle andre visualiseringer, der understøtter tværgående filtrering, tværgående fremhævning og bogmærker. 

Er du på udkig efter mere baggrund om Spørgsmål og svar i Power BI? Se [Introduktion til Spørgsmål og svar](../natural-language/q-and-a-intro.md). 

![Gennemgang af visualiseringen til Spørgsmål og svar](../natural-language/media/qna-visual-walkthrough.gif)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Visualiseringen til Spørgsmål og svar består af fire kernekomponenter:

- Spørgsmålsfeltet. Det er her, brugerne skriver deres spørgsmål og får vist forslag, der kan hjælpe dem med at fuldføre deres spørgsmål.
- En foruddefineret liste over foreslåede spørgsmål.
- Ikonet for at konvertere visualiseringen til Spørgsmål og svar til en standardvisualisering. 
- Ikon til åbning af værktøjer til Spørgsmål og svar, der giver designere mulighed for at konfigurere det underliggende program til naturligt sprog.

## <a name="prerequisites"></a>Forudsætninger

1. Download [PBIX-eksempelfilen Sales & Marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix) for at følge med.

1. Vælg **Fil** > **Åbn** øverst til venstre i Power BI Desktop.
   
2. Find din kopi af **PBIX-eksempelfilen Sales & Marketing**.

1. Åbn filen i rapportvisning ![Skærmbillede af ikonet for rapportvisning.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Vælg plustegnet ![Skærmbillede af den gule fane.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) for at tilføje en ny side.

Hvis du får vist en fejl, når du opretter visualiseringen til Spørgsmål og svar, skal du se artiklen [Begrænsninger i Spørgsmål og svar](../natural-language/q-and-a-limitations.md) for at få oplysninger om, hvorvidt konfigurationen af datakilden understøttes.    

> [!NOTE]
> Når du deler din rapport med en Power BI-kollega, kræves det, at I begge har individuelle Power BI Pro-licenser, eller at rapporten er gemt i et arbejdsområde i en Premium-kapacitet. Se [deling af rapporter](../collaborate-share/service-share-dashboards.md).

## <a name="create-a-qa-visual-using-a-suggested-question"></a>Opret visualiseringen til Spørgsmål og svar ved hjælp af et foreslået spørgsmål
I denne øvelse vælger vi et af de foreslåede spørgsmål til at oprette vores visualisering til Spørgsmål og svar. 

1. Start på en tom rapportside, og vælg ikonet for visualiseringen til Spørgsmål og svar i ruden Visualiseringer.

    ![Ruden Visualiseringer med ikonet for visualiseringen til Spørgsmål og svar fremhævet](media/power-bi-visualization-q-and-a/power-bi-icon.png)

2. Træk kanten for at tilpasse størrelsen af visualiseringen.

    ![Visualiseringen til Spørgsmål og svar på rapportlærredet](media/power-bi-visualization-q-and-a/power-bi-qna.png)

3. Hvis du vil oprette visualiseringen, skal du vælge et af de foreslåede spørgsmål eller begynde at skrive i spørgsmålsfeltet. I dette eksempel har vi valgt **de mest populære geo-stater efter omsætningssum**. Power BI gør sit bedste for at vælge den visualiseringstype, der skal bruges. I dette tilfælde er det et kort.

    ![Kort som visualisering til Spørgsmål og svar](media/power-bi-visualization-q-and-a/power-bi-map.png)

    Men du kan fortælle Power BI, hvilken visualiseringstype du vil bruge, ved at føje den til din forespørgsel på et naturligt sprog. Vær opmærksom på, at det ikke er alle visualiseringstyper, der vil fungere eller give mening for dine data. Disse data ville f.eks. ikke resultere i et meningsfyldt punktdiagram. Men de fungerer som et kartogram.

    ![Visualiseringen til Spørgsmål og svar som et kartogram](media/power-bi-visualization-q-and-a/power-bi-specify-map.png)

## <a name="create-a-qa-visual-using-a-natural-language-query"></a>Opret en visualisering til Spørgsmål og svar ved hjælp af en forespørgsel på et naturligt sprog
I ovenstående eksempel valgte vi et af de foreslåede spørgsmål til at oprette vores visualisering til Spørgsmål og svar.  I denne øvelse skriver vi vores spørgsmål. I takt med at vi skriver vores spørgsmål, hjælper Power BI os med autofuldførelse, forslag og feedback.

Hvis du er usikker på, hvilken type spørgsmål du skal stille, eller hvilken terminologi du skal bruge, skal du udvide **Vis alle forslag** eller gennemse ruden Felter i højre side af lærredet. I ruden Felter kan du blive fortrolig med begreberne og indholdet i datasættet Salg og marketing.

![lærred med Vis alle forslag og ruden Felter fremhævet](media/power-bi-visualization-q-and-a/power-bi-terminology.png)


1. Skriv et spørgsmål i feltet Spørgsmål og svar. Power BI føjer en rød understregning til ord, der ikke genkendes. Når det er muligt, hjælper Power BI med at definere ord, der ikke genkendes.  I det første eksempel nedenfor vil valg af begge forslag fungere.  

    ![Skriv et spørgsmål i spørgsmålsfeltet i Spørgsmål og svar](media/power-bi-visualization-q-and-a/power-bi-red-suggest.png)

2. I takt med at vi skriver mere af spørgsmålet, giver Power BI os besked om, at spørgsmålet ikke er forstået, og forsøger at hjælpe. I eksemplet nedenfor spørger Power BI os "Mente du..." og foreslår en anden måde at formulere spørgsmålet på ved hjælp af terminologi fra vores datasæt. 

    ![Visualiseringen til Spørgsmål og svar med forslag](media/power-bi-visualization-q-and-a/power-bi-define.png)

5. Ved hjælp af Power BI kunne vi stille et spørgsmål kun med genkendelige begreber. Power BI viser resultaterne som et kurvediagram. 

    ![Resultater af visualisering til Spørgsmål og svar](media/power-bi-visualization-q-and-a/power-bi-type.png)


6. Lad os ændre visualiseringen til et søjlediagram. 

    ![Visualisering til Spørgsmål og svar med "som et søjlediagram" føjet til spørgsmålet](media/power-bi-visualization-q-and-a/power-bi-specify-visual.png)

7.  Føj flere visualiseringer til rapportsiden, og se, hvordan Spørgsmål og svar-visual'et interagerer med de andre visuals på siden. I dette eksempel har Spørgsmål og svar-visual'et krydsfilteret kurvediagrammet og krydsfremhævet det liggende søjlediagram.

    ![Spørgsmål og svar-visual, hvor der er valgt én søjle, og virkningen på de andre tre visuals på rapportsiden](media/power-bi-visualization-q-and-a/power-bi-filters.png)

## <a name="format-and-customize-the-qa-visual"></a>Formatér og tilpas visualiseringen til Spørgsmål og svar
Visualiseringen til Spørgsmål og svar kan tilpasses ved hjælp af formateringsruden og anvendelse af et tema. 

### <a name="apply-a-theme"></a>Anvend et tema
Når du vælger et tema, anvendes temaet på hele rapportsiden. Der er mange temaer at vælge imellem, så prøv dem, indtil du får det ønskede udseende. 

1. På menulinjen skal du vælge fanen **Start** og vælge **Skift tema**. 

    ![Skrivebord med Skift tema valgt](media/power-bi-visualization-q-and-a/power-bi-themes.png)

    
    
2. I dette eksempel har vi valgt **Flere temaer** > **Kan bruges af farveblinde**.

    ![Visualisering til Spørgsmål og svar med tema for farveblinde anvendt](media/power-bi-visualization-q-and-a/power-bi-color-blind.png)

### <a name="format-the-qa-visual"></a>Formatér visualiseringen til Spørgsmål og svar
Formatér visualiseringen til Spørgsmål og svar, spørgsmålsfeltet og den måde, som forslagene vises på. Du kan ændre alt lige fra en titels baggrund til den pegefølsomme farve for ord, der ikke genkendes. Her har vi føjet en grå baggrund til spørgsmålsfeltet og ændret understregningerne til gul og grøn. Titlen er centreret og har en gul baggrund. 

![Visualiseringen til Spørgsmål og svar med resultaterne af vores formatering](media/power-bi-visualization-q-and-a/power-bi-q-and-a-format.png)

## <a name="convert-your-qa-visual-into-a-standard-visual"></a>Konvertér din visualisering til Spørgsmål og svar til en standardvisualisering
Vi har formateret vores visualisering som et søjlediagram, der kan bruges af farveblinde: Vi har tilføjet en titel og en kant. Nu er vi klar til at konvertere den til en standardvisualisering i vores rapport samt fastgøre den til et dashboard.

Vælg ikonet ![tandhjulsikonet](media/power-bi-visualization-q-and-a/power-bi-convert-icon.png) for at **omdanne dette resultat fra Spørgsmål og svar til en standardvisualisering**.

![Visualisering til Spørgsmål og svar med en pil, der peger på ikonet for standardvisualisering](media/power-bi-visualization-q-and-a/power-bi-visual-convert.png)

Denne visualisering er ikke længere en visualisering til Spørgsmål og svar, men et standardsøjlediagram. Den kan fastgøres til et dashboard. I rapporten fungerer denne visualisering ligesom andre standardvisualiseringer. Bemærk, at der vises et ikon for et søjlediagram i ruden Visualiseringer i stedet for et ikon for visualiseringen til Spørgsmål og svar.

Hvis du bruger **_Power BI-tjenesten_* _, kan du nu fastgøre visualiseringen til et dashboard ved at vælge tegnestiftikonet. 


![Power BI-tjenesten med fastgøringsikonet fremhævet](media/power-bi-visualization-q-and-a/power-bi-pin.png)


## <a name="advanced-features-of-the-qa-visual"></a>Avancerede funktioner i visualiseringen til Spørgsmål og svar
Når du vælger tandhjulsikonet, åbnes ruden med værktøjer til visualiseringen til Spørgsmål og svar. 

![Visualiseringen til Spørgsmål og svar med ikonet Værktøjer valgt](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling.png)

Brug ruden Værktøjer til at lære Spørgsmål og svar begreber, det ikke genkender, til at administrere disse begreber og administrere de foreslåede spørgsmål til dette datasæt og denne rapport. I ruden Værktøjer kan du også gennemse spørgsmål, brugere har stillet i denne visualisering til Spørgsmål og svar, og se spørgsmål, som brugerne har markeret med et flag. Hvis du vil vide mere, kan du se [Introduktion til værktøjer til Spørgsmål og svar for at træne Spørgsmål og svar i Power BI](../natural-language/q-and-a-tooling-intro.md).

![Ruden Værktøjer til Spørgsmål og svar](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling-pane.png)

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding
Visualiseringen til Spørgsmål og svar kan integreres med Office og Bing for at forsøge at matche almindelige ord, der ikke genkendes, med felter i dit datasæt.  

## <a name="next-steps"></a>Næste trin

Du kan integrere et naturligt sprog på flere forskellige måder. Du kan få flere oplysninger i følgende artikler:

_ [Værktøjer til Spørgsmål og svar](../natural-language/q-and-a-tooling-intro.md)
* [Bedste praksis for Spørgsmål og svar](../natural-language/q-and-a-best-practices.md)
