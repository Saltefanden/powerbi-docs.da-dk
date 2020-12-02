---
title: Brug indsigter til at forklare stigninger eller fald i visualiseringer (eksempelvisning)
description: Du kan let få indsigt i forøgelser eller reduktioner i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 02/21/2019
LocalizationGroup: Create reports
ms.openlocfilehash: 1e8b483af507aa175e6d804bf0af70bdd0da5372
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396676"
---
# <a name="apply-insights-in-power-bi-desktop-to-explain-fluctuations-in-visuals-preview"></a>Anvend indsigt i Power BI Desktop til at forklare udsving i visualiseringer (eksempelvisning)

Ofte vil du i visualiseringer se en stor stigning og derefter et kraftigt fald i værdier og undre dig over, hvad årsagen til sådanne udsving er. Med **indsigter** i **Power BI Desktop** kan du se mere om årsagen med nogle få klik.

Se f.eks. følgende visualisering, der viser *Sales Amount* efter *Year* og *Quarter*. Der er et stort fald i salget i 2014, hvor salget falder kraftigt mellem *Qtr 1* og *Qtr 2*. I sådanne tilfælde kan du udforske dataene for at finde en forklaring på ændringen. 

![Visualisering med stigninger og fald](media/desktop-insights/insights_01a.png)

Du kan bede **Power BI Desktop** om at forklare forøgelser eller reduktioner i diagrammer, se distributionsfaktorer i diagrammer og få hurtige og automatiske indsigtsanalyser om dine data. Du skal blot højreklikke på et datapunkt og vælge **Analysér > Forklar reduktionen** (eller forøgelsen, hvis den tidligere linje var lavere) eller **Analysér > Find de steder, hvor distributionen skiller sig ud**, så leveres der indsigt til dig i et brugervenligt vindue.

![Indsigter, der vises i visualisering](media/desktop-insights/insights_01.png)

Indsigtsfunktionen er kontekstafhængig, og den er baseret på det umiddelbart forrige datapunkt – f.eks. den forrige søjle eller kolonne.

> [!NOTE]
> Denne funktion leveres som prøveversion og ændres måske. Indsigtsfunktionen er aktiveret og slået til som standard (du behøver ikke at markere et afkrydsningsfelt for eksempelvisning for at aktivere den) fra og med versionen af **Power BI Desktop** fra september 2017.


## <a name="using-insights"></a>Brug af indsigt
Hvis du vil bruge indsigt til at forklare stigninger eller fald i diagrammer, skal du bare højreklikke på et hvilket som helst datapunkt i et søjle- eller kurvediagram og vælge **Analysér > Forklar forøgelsen** (eller *Forklar reduktionen*, da al indsigt er baseret på ændringen fra det forrige datapunkt).

![Vis menuen Indsigter](media/desktop-insights/insights_02.png)

**Power BI Desktop** kører algoritmerne for maskinlæring via dataene, og derefter udfyldes et vindue med et visuelt element og en beskrivelse af, hvilke kategorier der er mest påvirket af forøgelsen eller reduktionen. Som standard leveres indsigt som en visuel gengivelse af et *vandfald* som det vises på følgende billede.

![pop op-vinduet Indsigter](media/desktop-insights/insights_03.png)

Ved at vælge små ikoner nederst i vandfaldet kan du vælge at få indsigt til at vise et punktdiagram, et stablet søjlediagram eller et bånddiagram.

![tre visualiseringer med indsigter](media/desktop-insights/insights_04.png)

Du kan bruge ikonerne med *tommel op* og *tommel ned* øverst på siden til at give feedback på det visuelle element og funktionen. Det giver feedback, men det træner ikke algoritmen til at påvirke det resultat, der returneres næste gang, du bruger funktionen.

Og læg især mærke til, at knappen **+** øverst i det visuelle element gør det muligt at tilføje det valgte visuelle element i rapporten på samme måde, som hvis du havde oprettet det visuelle element manuelt. Du kan derefter formatere eller på anden måde justere det tilføjede visuelle element på samme måde som alle andre visuelle elementer i rapporten. Du kan kun tilføje et visuelt element for den valgte indsigt, når du redigerer en rapport i **Power BI Desktop**.

Du kan bruge indsigt, når rapporten er i læse- eller redigeringstilstand, hvilket betyder, at du både kan analyse data og oprette visuelle elementer, som du nemt kan føje til dine rapporter.

## <a name="details-of-the-results-returned"></a>Oplysninger om de returnerede resultater

De oplysninger, der returneres fra indsigter, skal fremhæve forskellene mellem de to tidsperioder, så du bedre kan forstå ændringerne mellem dem.  

Hvis *Sales* f.eks. steg med 55 % i alt fra *Qtr 3* til *Qtr 4*, og det er det samme for alle produktkategorier (*Category*) (salget under Computer steg med 55 % og det samme for Audio osv.), og det samme er gældende for alle lande og alle typer kunder, er der ikke meget i dataene, der kan forklare ændringen. Det vil dog som regel ikke være tilfældet, og der vil som regel være forskelle, som kan forklare ændringerne, f.eks. blandt kategorierne *Computers* og *Home Appliances*, som steg med hele 63 % procent, mens *TV and Audio* kun steg med 23 %. Derfor har kategorierne *Computers* og *Home Appliances* bidraget med en større mængde af totalen for *Qtr 4* end de gjorde i *Qtr 3*.  I dette eksempel kan en rimelig forklaring på stigningen være: *særdeles stærkt salg i kategorierne Computers og TV and Audio*. 

Algoritmen returnerer ikke blot de værdier, der står for det største beløb i ændringen. Hvis eksempelvis størstedelen (98 %) af salget kom fra USA, vil det meste af stigningen som regel også være en stigning i salget i USA. Men, hvis USA eller andre lande ikke viser en betydelig ændring i deres relative bidrag af totalen, vil *Country* ikke blive anset for interessant i denne kontekst.  

Helt enkelt kan algoritmen betragtes som at tage alle andre kolonner i modellen og beregne opdelingen efter den kolonne for tidsperioderne *før* og *efter* for at fastslå, hvor stor en ændring der var i den opdeling, hvorefter der returneres de kolonner, hvor der er den største ændring. I eksemplet herover valgte vi *Category*, da bidraget fra *TV and Video* faldt med 7 procentpoint fra 33% til 26%, mens bidraget af *Home Appliances* steg fra ingenting til over 6 %. 

For hver kolonne, der returneres, kan der vises fire visualiseringer. Tre af disse visualiseringer er beregnet til at fremhæve ændringer af bidraget mellem de to perioder. Det kan f.eks. være en forklaring af stigningen fra *Qtr 2* til *Qtr 3*.

### <a name="the-scatter-plot"></a>Punktdiagrammet

Punktdiagrammet viser værdien af målingen i den første periode (på x-aksen) i forhold til værdien af målingen i den anden periode (på y-aksen) for hver værdi i kolonnen (i dette tilfælde *Category*). Som vist i det følgende billede vil datapunkter være i det grønne område, hvis værdien steg, og de vil være i det røde område, hvis værdien faldt. 

Den stiplede linje viser dem, der passer bedst, og det vil sige, at de datapunkter, som er placeret over denne linje, steg mere end den overordnede tendens, mens dem under linjen steg mindre.  

![Punktdiagram med stiplet linje](media/desktop-insights/insights_01b.png)

Bemærk, at de datapunkter, som var tomme i en af perioderne, ikke vises i punktdiagrammet (f.eks. *Home Appliances*)

### <a name="the-100-stacked-column-chart"></a>100 % stablet søjlediagram

Visualiseringen 100 % stablet søjlediagram viser værdien af målingen før og efter efter den valgte kolonne. Det gør det nemt at sammenligne bidraget for før og efter. Værktøjstippene viser det faktiske bidrag for den valgte værdi.

![100 % stablet søjlediagram](media/desktop-insights/insights_01c.png)

### <a name="the-ribbon-chart"></a>Bånddiagrammet

Visualiseringen Bånddiagram viser også værdien af målingen før og efter. Det er især praktisk til at vise ændringer i bidragene, når *rækkefølgen* af disse blev ændret (f.eks. hvis *Computers* tidligere udgjorde det største bidrag, men nu kun udgør det tredjestørste bidrag). 

![bånddiagram](media/desktop-insights/insights_01d.png)

### <a name="the-waterfall-chart"></a>Vandfaldsdiagram

Den fjerde visualisering er et vandfaldsdiagram, som viser de faktiske stigninger eller fald mellem perioderne. Denne visualisering viser de faktiske ændringer, men den angiver ikke kun ændringerne for bidraget, men fremhæver i stedet, hvorfor kolonnen blev udvalgt som værende interessant. 

![vandfaldsdiagram](media/desktop-insights/insights_01e.png)

Når kolonnerne rangeres efter, hvilke der har de største ændringer i de relative bidrag, tages følgende i betragtning: 

* Kardinaliteten er indregnet, da en forskel er mindre signifikant rent statistisk, og den er mindre interessant, når en kolonne har en stor kardinalitet. 

* Forskellene for de kategorier, hvor de oprindelige værdier var meget høje eller meget tæt på nul, vægtes højere end andre. Hvis en kategori f.eks. kun bidrager til 1 % af det samlede salg, og hvis den stiger til 6 %, har det større statistisk signifikans, og det vil derfor blive betragtet som mere interessant end en kategori, hvor andelen er ændret fra 50 % til 55 %. 

* Der anvendes forskellige typer heuristik for at kunne vælge de mest betydende resultater, f.eks. ved at overveje andre relationer mellem dataene.
 
Efter at have undersøgt forskellige kolonner, vises dem, der har den største ændring relativt i forhold til deres bidrag. De værdier, som havde den væsentligste ændring i bidraget, fremhæves i beskrivelsen. De værdier, der havde de største faktiske stigninger og fald, fremhæves også.


## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger
Da disse indsigter er baseret på ændringen fra det tidligere datapunkt, er de ikke tilgængelige, når du vælger det første datapunkt i en visualisering. 

Følgende liste er en samling af de scenarier, der ikke understøttes i øjeblikket til **forklaring af stigning/fald**:

* TopN-filtre
* Medtag/udelad filtre
* Målingsfiltre
* Ikke-numeriske målinger
* Brug af "Vis værdi som"
* Filtrerede målinger – Filtrerede målinger er beregninger på visuelt niveau med et bestemt filter anvendt, f.eks. *Samlet salg i Frankrig*, og de bruges på nogle af de visualiseringer, som blev oprettet af indsigtsfunktionen
* Kategoriske kolonner på x-aksen, medmindre det definerer en sortering efter kolonne, der kan skaleres. Hvis du bruger et hierarki, skal alle kolonner i det aktive hierarki opfylde denne betingelse


Desuden understøttes følgende modeltyper og datakilder ikke i øjeblikket for indsigt:

* DirectQuery
* Live Connect
* Reporting Services i det lokale miljø
* Integration

## <a name="next-steps"></a>De næste trin
Du kan finde flere oplysninger om **Power BI Desktop**, og hvordan du kommer i gang, i følgende artikler.

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Oversigt over forespørgsler i Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datakilder i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Opret forbindelse til data i Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Udform og kombiner data med Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Almindelige forespørgselsopgaver i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   
