---
title: Tip til rapportdesign i Power BI Report Builder
description: Brug følgende tip til at designe dine sideinddelte rapporter i Power BI Report Builder.
author: maggiesMSFT
ms.author: maggies
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
ms.openlocfilehash: fc43fd3b8cfa4aeace7ae2dd18e69958d241f83a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410039"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Tip til rapportdesign i Power BI Report Builder

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Brug følgende tip til at designe dine sideinddelte rapporter i Power BI Report Builder.  
  
##  <a name="designing-reports"></a><a name="DesigningReports"></a> Design af rapporter  
  
-   En veldesignet rapport indeholder oplysninger, der fører til handling. Identificer de spørgsmål, som rapporten skal hjælpe med at besvare. Husk på disse spørgsmål, når du designer rapporten.  
  
-   For at designe effektive datavisualiseringer skal du tænke over, hvordan du vil vise oplysninger, der er nemme at forstå for brugeren af rapporten. Vælg et dataområde, som passer godt til de data, du vil visualisere. Et diagram gengiver f.eks. effektivt resuméer og aggregerede oplysninger bedre end en tabel, der strækker sig over flere sider med detaljerede oplysninger. Du kan visualisere data fra et datasæt i et hvilket som helst dataområde, som indeholder diagrammer, kort, indikatorer, minidiagrammer, datalinjer og tabeldata i forskellige gitterlayout på baggrund af en tablix. 
  
-   Hvis du planlægger at levere rapporten i et bestemt eksportformat, skal du teste eksportformatet tidligt i dit design. Funktionsunderstøttelse varierer afhængigt af den gengivelse, du vælger.  
  
-   Når du udarbejder komplekse layout, kan du udarbejde layoutet i faser. Du kan bruge rektangler som objektbeholdere til at organisere rapportelementerne. Du kan udarbejde dataområder direkte i designområdet for at maksimere dit arbejdsområde, og derefter kan du, i takt med at du fuldfører hvert enkelt, trække det til den rektangulære objektbeholder. Ved hjælp af rektangler som objektbeholdere kan du placere alt indhold i ét trin. Rektangler hjælpe også med at styre den måde, rapportelementer gengives på, på hver side.  
  
-   Overvej at bruge betinget synlighed for bestemte rapportelementer for at reducere rodet i en rapport, og lad brugeren vælge, om elementerne skal vises. Du kan angive synligheden på baggrund af en parameter eller et håndtag til et tekstfelt. Du kan tilføje betinget skjulte tekstfelter for at vise midlertidige resultater for udtryk. Når der vises uventede data i en rapport, kan du vise disse midlertidige resultater for at hjælpe med at foretage fejlfinding af udtryk.  
  
-   Når du arbejder med indlejrede elementer i tablixceller eller rektangler, kan du angive forskellige baggrundsfarver for objektbeholderen og elementer deri. Baggrundsfarven er som standard **Ingen farve**. Elementer med en bestemt baggrundsfarve vises gennem elementer med en baggrundsfarve, der er angivet til **Ingen farve**. Denne teknik kan hjælpe dig med at vælge det rigtige element for at angive visningsegenskaber, f.eks. synlighed af kant i tablixceller.  
  
 Du kan finde flere oplysninger om ting, du skal overveje, når du designer din rapport, i [Planlægning af en rapport i Report Builder](report-builder-planning-report.md).  
  
##  <a name="naming-conventions-for-reports-data-sources-and-datasets"></a><a name="NamingConventions"></a> Navngivningskonventioner for rapporter, datasæt og datakilder  
  
-   Brug navngivningskonventioner for datakilder og datasæt, der dokumenterer datakilden.  
  
    1.  **Datakilder.** Hvis du ikke vil bruge en reel server eller database på grund af sikkerhedsårsager, kan du bruge et alias, der angiver over for brugeren, hvad datakilden er.  
  
    2.  **Datasæt.** Brug et navn, der angiver, hvilken datakilde den er baseret på.  
  
##  <a name="working-with-data"></a><a name="Data"></a> Arbejde med data  
  
-   Det første trin er at få alle de data, du vil arbejde med, vist i ruden Rapportdata. I takt med at du finjusterer de spørgsmål, som rapporten er designet til at besvare, skal du tænke på, hvordan du vil begrænse dataene i rapportens datasæt, så der kun er det, der er behov for.  
  
-   Generelt skal du kun inkludere data, som du vil vise, i en rapport. Brug variabler for forespørgslen i dine forespørgsler for datasæt for at give brugeren mulighed for at vælge, hvilke data de vil se i rapporten. Hvis du opretter delte datasæt, skal du angive filtre baseret på rapportparametre, så du kan levere den samme funktionalitet.  
  
-   Hvis du er en erfaren forfatter af forespørgsler, skal du forstå, at det kan være en god idé at gruppere data i rapporten og ikke i forespørgslen i forbindelse med mellemliggende mængder data. Hvis du foretager al gruppering i forespørgslen, er rapporten typisk en præsentation af sættet af forespørgselsresultatet. Hvis du på den anden side vil have vist aggregerede værdier for store mængder data i et diagram eller en matrix, er der ingen grund til at inkludere detaljerede data.  
  
-   Afhængigt af dine krav kan du vise navne og placeringer for rapportdatakilder, kommandotekst for forespørgslen for datasættet og parameterværdier i rapporten. Det første spørgsmål, som mange nye brugere stiller, handler om, hvor dataene kommer fra. Du kan skjule tekstfelter med denne type oplysninger betinget for at reducere rodet i rapporten og lade brugerne vælge, om de vil se dem. Prøv at tilføje disse oplysninger på den sidste side i rapporten. Angiv synligheden af tekstfeltet på baggrund af en parameter, som brugeren kan ændre.  
  
##  <a name="interacting-with-the-report-design-surface"></a><a name="DesignSurface"></a> Interaktion med rapportdesignområdet  
 Rapportdesignområdet er ikke WYSIWIG. Når du placerer rapportelementer i designområdet, påvirker deres relative placering den måde, elementerne vises på, på den gengivne rapportside. Blanktegn bevares.  
  
-   Brug fastgørelseslinjer og layout til at justere og arrangere elementer i rapportdesignområdet. Du kan f.eks. justere toppen eller kanterne af de valgte elementer, udvide et element, så det passer til størrelsen på et andet element, eller justere afstanden mellem elementerne.  
  
-   Brug piletasterne til at justere placeringen og størrelsen af de markerede elementer i designområdet. Følgende kombinationer af taster er f.eks. meget nyttige:  
  
    -   **Piletaster** Flyt det markerede rapportelement.  
  
    -   **CTRL + piletaster** Skub til det markerede rapportelement.  
  
    -   **CTRL + SKIFT + piletaster** Øg eller reducer størrelsen af det valgte rapportelementet.  
  
-   Hvis du vil føje et element til en rektangel, skal du bruge den yderste venstre spids af musen til at pege på den indledende placering af elementet i rektangelobjektbeholderen. Brug tastaturgenveje til at hjælpe med at placere de valgte objekter. Rektanglet udvides automatisk for at passe til størrelsen af de indeholdte elementer.  
  
-   Hvis du vil føje flere elementer til en tablixcelle, skal du først tilføje et rektangel og derefter tilføje elementerne.  
  
     Hver tablixcelle indeholder som standard et tekstfelt. Når du føjer et rektangel til en celle, erstatter rektanglet tekstfeltet. Placer f.eks. indlejrede indikatorer i et rektangel i en tablixcelle for at styre den måde, som størrelsen af et diagram eller en indikator udvides på, i takt med at du ændrer højden på den række, cellen befinder sig i.  
  
-   Brug kontrolelementet **Zoom** til at justere visningen af designområdet. Du kan arbejde med hele siden eller mindre dele af siden.  
  
-   Hvis du vil trække felter fra ruden Rapportdata til ruden Gruppering, skal du undgå at trække feltet på tværs af andre rapportelementer i designområdet, da dette markerer de andre elementer og fjerner tablixdataområdet. Træk feltet ned i ruden Rapportdata og derefter på tværs af ruden Gruppering.  
  
###  <a name="selecting-items"></a><a name="Selecting"></a> Valg af elementer  
 Du markerer det ønskede objekt i rapportdesignområdet ved hjælp af ESC-tasten ved at højreklikke i kontekstmenuen, ved hjælp af ruden Egenskaber eller ruden Gruppering.  
  
-   -   Tryk på ESC for at gennemse stakken af rapportelementer, der optager den samme plads i designområdet.  
  
    -   Prøv at bruge kontekstsmenuen ved hjælp af højreklik på nogle rapportelementer for at vælge rapportelementet eller den del af rapportelementet, du vil have.  
  
    -   I ruden Egenskaber kan du se egenskaberne for det aktuelle valg.  
  
    -   Hvis du vil arbejde med rækkegrupper og kolonnegrupper i et tablixdataområde, skal du vælge gruppen i ruden Gruppering.  

  
##  <a name="working-with-specific-types-of-report-items"></a><a name="ReportItems"></a> Arbejde med bestemte typer rapportelementer  
  
###  <a name="working-with-parameters"></a><a name="Parameters"></a> Arbejde med parametre  
  
-   Det primære formål med rapportparametre er at filtrere data på datakilden og kun hente det, der er nødvendigt til rapportens formål.  
  
-   Find en balance mellem at aktivere interaktivitet og hjælpe en bruger med at få de resultater, der vil have, for rapportparametre. Du kan f.eks. angive standardværdier for en parameter til værdier, som du ved er populære.  
  
###  <a name="working-with-text"></a><a name="Text"></a> Arbejde med tekst  
  
-   Når du indsætter flere linjer i et tekstfelt, tilføjes teksten som én tekstkørsel. Hver tekstkørsel kan kun formateres som en enhed. Hvis du vil formatere hver linje uafhængigt af hinanden, skal du indsætte en ny linje ved at trykke på RETURN i tekstkørslen efter behov. Du kan derefter anvende formatering og typografier på hver linje uafhængigt af teksten i tekstfeltet.  
  
-   Du kan angive formategenskaber og handlinger for et tekstfelt eller pladsholdertekst i tekstfeltet. Hvis der kun er én linje med tekst, er det mere effektivt at angive egenskaberne for tekstfelt end for teksten.  
  
###  <a name="working-with-expressions"></a><a name="Expressions"></a> Arbejde med udtryk  
  
-   Forstå formaterne af simple og komplekse udtryk. Du kan skrive formatet af simple udtryk direkte i tekstfelter, egenskaber i ruden Egenskab eller på steder i dialogbokse, der accepterer et udtryk.
  
-   Når du opretter et udtryk, hjælper det at oprette hver del uafhængigt af hinanden og kontrollere dens værdi. Du kan derefter kombinere alle dele i et færdigt udtryk. En nyttig teknik er at tilføje et tekstfelt i en matrixcelle, vise hver del af udtrykket og angive betinget synlighed for tekstfeltet. For at styre kanttype og farven, når tekstfeltet er skjult, skal du først placere tekstfeltet i et rektangel og derefter angive kanttypen og farven på rektanglet, så de passer til matrixen.  
  
###  <a name="working-with-indicators"></a><a name="Indicators"></a> Arbejde med indikatorer  
  
-   En indikator viser som standard mindst tre tilstande. Når du har føjet en indikator til en rapport, kan du konfigurere den ved at tilføje eller fjerne tilstande. Vælg en indikator, der varierer både i farve og form, for at gøre den lettere at se for brugerne.  
  
##  <a name="controlling-the-rendering-of-report-items-on-the-report-page"></a><a name="Rendering"></a> Styring af gengivelse af rapportelementer på rapportsiden  
  
-   Rapportelementer udvides i rapportdesignområdet for at passe til indholdet fra det tilknyttede datasæt eller udtryk eller den tilknyttede underrapport eller tekst.  
  
    -   Når du placerer et element på rapportsiden, bliver afstanden mellem elementet og alle elementer, der starter til højre for det, den minimumafstand, der skal bevares, i takt med at et rapportelement udvides vandret. På samme måde bliver afstanden mellem et element og elementet over det minimumafstanden, der skal bevares, i takt med at det øverste element udvides lodret.  
  
    -   Et element i en rapport udvides for at passe til dataene og skubber peer-elementer (elementer i samme overordnet objektbeholder) af vejen ved hjælp af følgende regler:  
  
    -   Hvert element flyttes ned for at bevare minimumafstanden mellem selve elementet og de elementer, der slutter over det.  
  
    -   Hvert element flyttes til højre for at bevare minimumafstanden mellem selve elementet og de elementer, der slutter til venstre for det. I systemer med et layout fra højre mod venstre flyttes hvert element til venstre for at bevare minimumafstanden mellem selve elementet og de elementer, der slutter til højre for det.  
  
    -   Objektbeholdere udvides for at passe til udvidelsen af underordnede elementer. For et markeret element identificerer egenskaben Parent objektbeholderen for elementet i ruden Egenskaber. Du kan også bruge ruden Dokumentdisposition for at se opbevaringshierarkiet for rapportelementer.  
  
    -   Værktøjslinjen **Layout** indeholder flere knapper, der hjælper med at justere kanter, centre og afstand for rapportelementer. Du aktiverer værktøjslinjen **Layout** ved i menuen **Visning** at pege på **Værktøjslinjer** og derefter klikke på **Layout**.  
  
-   Hvis du har planer om at gemme rapporten som en .pdf-fil, skal bredden af rapporten være eksplicit angivet til en værdi, der giver dig de resultater, du vil have, i eksportfilformatet. Angiv f.eks. bredden af rapportsiden til præcis 7,9375 tommer og venstre og højre margen til 0,5 tommer.  
  
-   Brug **Udskriftslayout** og **Sideopsætning** på værktøjslinjen i rapportfremviser til at gengive en rapport i visning, der kan udskrives. Gør følgende for at fjerne uønskede tomme sider:  
  
    1.  Fjern alle ekstra mellemrum mellem dataområder og kanterne af rapporten.  
  
    2.  Reducer sidemargenerne i dialogboksen **Rapportegenskaber**.  
  
    3.  Brug **Rektangler** som objektbeholdere for at styre den måde, rapportelementer gengives på.  
  
    4.  I kolonneoverskrifterne skal du ændre egenskaben WritingMode for tekstfeltet til at bruge lodret tekst.  

 Du kan få vejledning i [Undgå tomme sider ved udskrivning af sideinddelte rapporter](../guidance/report-paginated-blank-page.md).

 Kombinationen af denne funktionsmåde, egenskaberne for bredde og højde af rapportelementer, størrelsen af rapportens brødtekst, definitionen af højde og bredde for siden, margenindstillingerne for den overordnede rapport og understøttelse af specifik gengivelse for sider bestemmer alt sammen, hvilke rapportelementer der passer sammen på en gengivet side.
 
## <a name="next-steps"></a>Næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
