---
title: Grundlæggende DAX i Power BI Desktop
description: Grundlæggende DAX i Power BI Desktop
author: Minewiskan
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 10/21/2019
LocalizationGroup: Model your data
ms.openlocfilehash: 522dccb6f4e6e3cf3422bc85ba9727c9160d9d80
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413834"
---
# <a name="apply-dax-basics-in-power-bi-desktop"></a>Anvend Grundlæggende DAX i Power BI Desktop
Denne artikel henvender sig til nye brugere af Power BI Desktop. Den giver dig en hurtig og nem introduktion til, hvordan du kan bruge DAX (Data Analysis Expressions) til at løse en række grundlæggende problemer med beregning og dataanalyse. Vi gennemgår nogle konceptbaserede oplysninger, en række opgaver, du kan udføre, og et videnstjek for at teste, hvad du har lært. Når du har gennemgået denne artikel, bør du have en god forståelse af de vigtigste grundlæggende begreber i DAX.

## <a name="what-is-dax"></a>Hvad er DAX?
DAX er en samling funktioner, operatorer og konstanter, der kan bruges i en formel eller et udtryk til at beregne og returnere en eller flere værdier. Mere forenklet sagt hjælper DAX dig med at oprette nye oplysninger ud fra data, der allerede findes i modellen.

## <a name="why-is-dax-so-important"></a>Hvorfor er DAX så vigtigt?
Det er nemt at oprette en ny Power BI Desktop-fil og importere data til den. Du kan endda oprette rapporter, der viser værdifuld indsigt, uden at bruge nogen DAX-formler overhovedet. Men hvad nu, hvis du har brug for at analysere vækstprocentdelen hen over produktkategorier og for forskellige dataområder? Eller du har brug for at beregne vækst år for år sammenlignet med tendenser på markedet? DAX-formler leverer denne funktionalitet sammen med mange andre vigtige funktioner. Du kan få det maksimale ud af dine data ved at lære, hvordan du opretter effektive DAX-formler. Når du får vist de oplysninger, du skal bruge, kan du begynde at løse reelle forretningsproblemer, der påvirker bundlinjen. Dette er styrken ved Power BI, og DAX hjælper dig med at finde frem til den.

## <a name="prerequisites"></a>Forudsætninger
Du ved muligvis allerede, hvordan du opretter formler i Microsoft Excel. Denne viden kan være nyttig til at forstå DAX, men selvom du ikke har nogen erfaring med Excel-formler, vil de begreber, der er beskrevet her, hjælpe dig med at komme i gang med at oprette DAX-formler og løse virkelige BI-problemer med det samme.

Vi fokuserer på forståelsen af DAX-formler, der bruges i beregninger, specielt i målinger og beregnede kolonner. Du bør allerede have kendskab til at bruge Power BI Desktop til at importere data og føje felter til en rapport, og du bør også have kendskab til grundlæggende begreber såsom [Målinger](desktop-measures.md) og [Beregnede kolonner](desktop-calculated-columns.md).

### <a name="example-workbook"></a>Eksempelprojektmappe

Den bedste måde at lære DAX at kende på er ved at oprette nogle grundlæggende formler, bruge dem med faktiske data og selv se resultaterne. Eksemplerne og opgaverne her bruger [Contoso-salgseksemplet som Power BI Desktop-fil](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip). Denne eksempelfil er den samme, som bruges i [Selvstudiet: Opret dine egne målinger i Power BI Desktop](desktop-tutorial-create-measures.md). 

## <a name="lets-begin"></a>Lad os komme i gang!
Vi baserer vores forståelse af DAX på tre grundlæggende begreber: *Syntaks*, *Funktioner* og *Kontekst*. Der er andre vigtige begreber i DAX, men forståelse af disse tre begreber er det bedste grundlag til at opbygge dine DAX-færdigheder.

### <a name="syntax"></a>Syntaks
Før du opretter dine egne formler, skal vi se nærmere på syntaksen i DAX-formler. Syntaksen omfatter de forskellige elementer, der udgør en formel, eller mere enkelt udtrykt, den måde en formel er skrevet på. Her er f.eks. en enkel DAX-formel til en måling:

![DAX-formelsyntaks](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Formlen inkluderer følgende syntakselementer:

**A.** Målingsnavnet **Samlet salg**.

**B.** Operatoren lighedstegn ( **=** ), som angiver starten af formlen. Når den er beregnet, returneres et resultat.

**C.** DAX-funktionen **SUM**, som adderer alle tallene i kolonnen **Sales[SalesAmount]** . Du får mere at vide om funktioner senere.

**D.** Parenteser **()** , som omslutter et udtryk, der indeholder et eller flere argumenter. Alle funktioner kræver mindst ét argument. Et argument overfører en værdi til en funktion.

**E.** Den refererede tabel **Salg**.

**F.** Den refererede kolonne **[SalesAmount]** i tabellen Salg. Med dette argument ved funktionen SUM, hvilken kolonne en SUM skal aggregeres på.

Når du prøver at forstå en DAX-formel, er det ofte nyttigt at opdele hvert enkelt element i et sprog, som du tænker og taler på hver dag. Du kan f.eks. læse denne formel som:

> *Beregn (=) SUM af værdierne i kolonnen [SalesAmount] i tabellen Sales for den måling, der er navngivet Samlet salg.*
> 
> 

Når den føjes til en rapport, beregner og returnerer denne måling værdier ved at sammenlægge salgsbeløb for hver af de andre felter, som er medtaget. f.eks. Cell Phones in the USA (Mobiltelefoner i USA).

Du tænker måske "Udfører denne måling ikke præcist det samme, som hvis jeg bare føjede feltet SalesAmount til min rapport?" Jo, det gør den. Men der er en god grund til at oprette vores egne måling, der sammenlægger værdier fra feltet SalesAmount: Vi kan bruge det som et argument i andre formler. Det virker muligvis en smule forvirrende lige nu, men i takt med at du får flere færdigheder i forbindelse med DAX-formler, vil viden om denne måling gøre dine formler og din model mere effektiv. Senere vil du faktisk kunne se målingen Total Sales blive vist som et argument i andre formler.

Lad os gennemgå et par andre ting om denne formel. Vi har specielt introduceret en funktion, [SUM](/dax/sum-function-dax). Funktioner er formler, der er skrevet på forhånd, og som gør det nemmere at udføre komplekse beregninger og manipulationer med tal, datoer, tid, tekst og meget mere. Du får mere at vide om funktioner senere.

Du kan også se, at kolonnenavnet [SalesAmount] kom efter den Salgs-tabel, som kolonnen tilhører. Dette navn kaldes et fuldt kvalificeret kolonnenavn, fordi det indeholder kolonnenavnet med det foranstillede tabelnavn. Kolonner, der refereres til i den samme tabel, kræver ikke, at tabelnavnet inkluderes i formlen, hvilket kan gøre lange formler, der refererer til mange kolonner, kortere og nemmere at læse. Det er dog god praksis at inkludere tabelnavnet i dine målingsformler, selv når de er i den samme tabel.

> [!NOTE]
> Hvis et tabelnavn indeholder mellemrum, reserverede nøgleord eller tegn, der ikke er tilladt, skal tabelnavnet være omsluttet af enkelte anførselstegn. Du skal også sætte tabelnavne i anførselstegn, hvis navnet indeholder tegn uden for det alfanumeriske ANSI-tegnområde, uanset om din landestandard understøtter tegnsættet eller ej.
> 
> 

Det er vigtigt, at formlerne har den korrekte syntaks. Hvis syntaksen ikke er korrekt, returneres der i de fleste tilfælde en syntaksfejl. I andre tilfælde kan syntaksen være korrekt, men de returnerede værdier er muligvis ikke, hvad du forventer. DAX-editoren i Power BI Desktop indeholder en funktion med forslag, der bruges til at oprette syntaktisk korrekte formler ved at hjælpe dig med at vælge de korrekte elementer.

Lad os oprette en simpel formel. Denne opgave vil være med til at give dig en bedre forståelse af formelsyntaks, og hvordan forslagsfunktionen i formellinjen kan hjælpe dig.

### <a name="task-create-a-measure-formula"></a>Opgave: Opret en målingsformel

1. [Download](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip), og åbn Power BI Desktop-filen Contoso-salgseksempel. 
    
2. Højreklik på tabellen **Salg** på feltlisten i rapportvisning, og klik derefter på **Ny måling**.
    
3. På formellinjen skal du erstatte **Måling** ved at angive det nye målingsnavn *Salg i forrige kvartal*.
    
4. Efter lighedstegnet skal du skrive de første par bogstaver *CAL* og derefter dobbeltklikke på den funktion, du vil bruge. I denne formel skal du bruge funktionen **CALCULATE**.

   Du skal bruge CALCULATE-funktionen til at filtrere de beløb, som vi vil optælle efter et argument, som vi sender til funktionen CALCULATE. Der refereres til dette som indlejrede funktioner. Funktionen CALCULATE har mindst to argumenter. Det første er udtrykket, der skal evalueres, og det andet er et filter.
   
5. Efter venstreparentesen *(* for funktionen **CALCULATE** skal du skrive *SUM* efterfulgt af endnu en venstreparentes *(* . 

   Derefter overfører vi et argument til funktionen SUM.

6. Begynd at skrive *Sal*, og vælg derefter **Sales [SalesAmount]** efterfulgt af en højreparentes *)* . 

   Dette er det første udtryksargument til vores CALCULATE-funktion.
    
7. Skriv et komma ( *,* ) efterfulgt af et mellemrum for at angive det første filter, og skriv derefter *PREVIOUSQUARTER*. 
    
   Du skal bruge tidsintelligensfunktionen PREVIOUSQUARTER til at filtrere SUM-resultater efter det forrige kvartal.
    
8. Efter venstreparentesen *(* for funktionen PREVIOUSQUARTER skal du skrive *Calendar[DateKey]* .
    
   Funktionen PREVIOUSQUARTER har ét argument, som er en kolonne, der indeholder et sammenhængende datoområde. I vores tilfælde er det kolonnen DateKey i tabellen Calendar.
    
9. Luk begge argumenter, der overføres til funktionen PREVIOUSQUARTER og funktionen CALCULATE, ved at skrive to højreparenteser *))* .
    
   Din formel skal se sådan ud:
    
   **Salg i forrige kvartal = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
10. Vælg fluebenet ![fluebensikon](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) på formellinjen, eller tryk på Enter for at validere formlen og føje den til modellen.

Du gjorde det! Du har lige oprettet en kompleks måling ved hjælp af DAX og endda én, der ikke er nem. Det, denne formel gør, er at beregne det samlede salg for det foregående kvartal, afhængigt af de filtre der anvendes i en rapport. Hvis vi f.eks. sætter SalesAmount og vores nye måling for salg i forrige kvartal ind i et diagram og derefter tilføjer Year og QuarterOfYear som Udsnit, får vi noget i stil med dette:

![Diagram over salg i forrige kvartal og SalesAmount](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Du er lige blevet introduceret til flere vigtige aspekter af DAX-formler: 

- Denne formel indeholdt to funktioner. [PREVIOUSQUARTER](/dax/previousquarter-function-dax), der er en intelligensfunktion for tid, indlejres som et argument, der overføres til filtreringsfunktionen [CALCULATE](/dax/calculate-function-dax). 

   DAX-formler kan indeholde op til 64 indlejrede funktioner. Det er usandsynligt, at en formel nogen sinde vil indeholde så mange indlejrede funktioner. En sådan formel ville faktisk være vanskelig at oprette og foretage fejlfinding af, og den ville sandsynligvis heller ikke være ret hurtig.

- I denne formel har du også brugt filtre. Filtre begrænser det, der beregnes. I dette tilfælde valgte du ét filter som et argument, hvilket faktisk er resultatet af en anden funktion. Du får mere at vide om filtre senere.

- Du brugte funktionen CALCULATE. Denne funktion er en af de mest effektive funktioner i DAX. Når du udarbejder modeller og opretter mere komplekse formler, vil du sandsynligvis bruge denne funktion mange gange. Selvom yderligere drøftelse af funktionen CALCULATE ligger uden for denne artikels omfang, skal du være særligt opmærksom på den, i takt med at din viden om DAX vokser.

### <a name="syntax-quickquiz"></a>Hurtig syntakstest
1. Hvad bruges denne knap på formellinjen til?
   
   > ![Valg af knap](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. Hvad er et kolonnenavn i en DAX-formel altid omsluttet af?

Svarene er angivet i slutningen af denne artikel.

### <a name="functions"></a>Funktioner
Funktioner er foruddefinerede formler, der udfører beregninger ved hjælp af bestemte værdier, kaldet argumenter, i en bestemt rækkefølge eller struktur. Argumenter kan være andre funktioner, en anden formel, et udtryk, kolonnereferencer, tal, tekst, logiske værdier som f.eks. TRUE eller FALSE eller konstanter.

DAX indeholder følgende kategorier af funktioner: [Dato og klokkeslæt](/dax/date-and-time-functions-dax), [Tidsintelligens](/dax/time-intelligence-functions-dax),[Oplysninger](/dax/information-functions-dax), [Logisk](/dax/logical-functions-dax),[Matematisk](/dax/math-and-trig-functions-dax), [Statistisk](/dax/statistical-functions-dax), [Tekst](/dax/text-functions-dax), [Overordnet/underordnet](/dax/parent-and-child-functions-dax) og [Andet](/dax/other-functions-dax). Hvis du kender funktioner i formler i Excel, vil mange af funktionerne i DAX virke bekendte for dig. Men DAX-funktioner er imidlertid helt specielle på følgende måder:

* En DAX-funktion refererer altid til en hel kolonne eller tabel. Hvis du kun vil bruge bestemte værdier fra en tabel eller kolonne, kan du føje filtre til formlen.
* Har du behov for at tilpasse beregningerne række for række, har DAX funktioner, der giver dig mulighed for at bruge den aktuelle rækkeværdi eller en relateret værdi som en form for argument, så du kan foretage beregninger, der varierer alt efter indhold. Du får mere at vide om kontekst senere.
* DAX indeholder mange funktioner, der returnerer en tabel i stedet for en værdi. Tabellen vises ikke, men den bruges til at levere input til andre funktioner. Du kan f.eks. hente en tabel, og derefter tælle de særskilte værdier i den eller beregne dynamiske beløb på tværs af filtrerede tabeller eller kolonner.
* DAX indeholder en lang række funktioner til tidsintelligens. Med disse funktioner kan du definere eller vælge datoområder og udføre dynamiske beregninger baseret på dem. Du kan f.eks. sammenligne beløb på tværs af parallelle perioder.
* Excel har en meget populær funktion, LOPSLAG. DAX-funktioner bruger ikke en celle eller et celleområde som reference, på samme måde som LOPSLAG gør i Excel. DAX-funktioner bruger en kolonne eller en tabel som reference. I Power BI Desktop skal du huske på, at du arbejder med en relationsdatamodel. Det er let at slå værdier op i en anden tabel, og i de fleste tilfælde behøver du slet ikke at oprette formler.
  
  Som du kan se, kan funktionerne i DAX hjælpe dig med at oprette effektive formler. Reelt har vi kun lige berørt de grundlæggende elementer i funktioner. I takt med at du får flere DAX-færdigheder, vil du oprette formler ved hjælp af mange forskellige funktioner. Et af de bedste steder at finde detaljer om hver enkelt DAX-funktion er i [referencen til DAX-funktioner](/dax/).

### <a name="functions-quickquiz"></a>Hurtig funktionstest
1. Hvad refererer en funktion altid til?
2. Kan e formel indeholde mere end én funktion?
3. Hvilken kategori af funktioner ville du bruge til at sammenkæde to tekststrenge til én streng?

Svarene er angivet i slutningen af denne artikel.

### <a name="context"></a>Kontekst
Kontekst er et af de vigtigste DAX-begreber at forstå. Der er to typer kontekst i DAX: rækkekontekst og filterkontekst. Vi skal først se på rækkekontekst.

**Rækkekontekst**

Det er nemmest at tænke på rækkekontekst som den aktuelle række. Den er relevant, når en formel har en funktion, som anvender filtre til at identificere en enkelt række i en tabel. Funktionen vil altid anvende en rækkekontekst til hver række i tabellen, hvor der foretages filtrering. Denne type rækkekontekst anvendes oftest til målinger.

**Filterkontekst**

Filterkontekst er lidt sværere at forstå end rækkekontekst. Det er nemmest at betragte filterkontekst som: Et eller flere filtre i en beregning, der angiver et resultat eller en enkelt værdi.

Filterkontekst bruges ikke i stedet for rækkekontekst, men bruges i stedet som supplement til rækkekontekst. Hvis du f.eks. vil foretage yderligere begrænsning af de værdier, der skal inkluderes i en beregning, kan du anvende en filterkontekst, som ikke kun angiver rækkekonteksten, men også angiver en bestemt værdi (filter) i denne rækkekontekst.

Filterkontekst kan nemt ses i dine rapporter. Når du f.eks. føjer SamletPris til en visualisering og derefter tilføjer År og Område, definerer du en filterkontekst, der vælger en delmængde af data baseret på et givet år og område.

Hvorfor er filterkontekst så vigtig i DAX? Grunden til det er, at selvom filterkontekst nemmest kan anvendes ved at føje felter til en visualisering, så kan filterkontekst også anvendes i en DAX-formel ved at definere et filter, der bruger funktioner som f.eks. ALL, RELATED, FILTER, CALCULATE efter relation og efter andre målinger og kolonner. Lad os f.eks. se på følgende formel i en måling, der har fået navnet Butikssalg:

![Målingen Butikssalg](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

For bedre at forstå denne formel kan vi opdele den på lignende måde, som vi gør med andre formler.

Formlen inkluderer følgende syntakselementer:

**A.** Målingsnavnet **Butikssalg**.

**B.** Operatoren lighedstegn ( **=** ), som angiver starten af formlen.

**C.** Funktionen **CALCULATE**, der evaluerer et udtryk som et argument i en kontekst, som er ændret af de angivne filtre.

**D.** Parenteser **()** , som omslutter et udtryk, der indeholder et eller flere argumenter.

**E.** En måling **[Samlet salg]** i samme tabel som et udtryk. Målingen Samlet salg har formlen: =SUM(Sales[SalesAmount]).

**F.** Et komma ( **,** ), som adskiller det første udtryksargument fra filterargumentet.

**G.** Den fuldt kvalificerede kolonne **Channel[ChannelName]** . Dette er vores rækkekontekst. Hver række i denne kolonne angiver en kanal, f.eks. Butik eller Online.

**H.** Den særskilte værdi **Butik** som et filter. Dette er vores filterkontekst.

Denne formel sikrer, at det kun er værdier for salg, som er defineret af målingen Samlet salg, der udelukkende beregnes for rækkerne i kolonnen Channel[ChannelName] med værdien *Butik* anvendt som et filter.

Som du kan forestille dig, giver det utrolige og effektive muligheder at kunne definere filterkontekst i en formel. Evnen til kun at referere til en bestemt værdi i en relateret tabel er blot et enkelt eksempel. Du skal ikke være bekymret, hvis du ikke forstår konteksten fuldt ud lige med det samme. Efterhånden som du opretter dine egne formler, vil du få en bedre forståelse af kontekst, og hvorfor det er så vigtigt i DAX.

### <a name="context-quickquiz"></a>Hurtig konteksttest
1. Hvad er de to typer kontekst?
2. Hvad er filterkontekst?
3. Hvad er rækkekontekst?

Svarene er angivet i slutningen af denne artikel.

## <a name="summary"></a>Oversigt
Nu hvor du har en grundlæggende forståelse af de vigtigste begreber i DAX, kan du begynder at oprette DAX-formler til målinger på egen hånd. Det kan være lidt svært at blive fortrolig med DAX, men der er mange ressourcer, du kan bruge. Når du har læst denne artikel og forsøgt dig med nogle af dine egne formler, kan du få mere at vide om andre DAX-begreber og -formler, der kan hjælpe dig med at løse dine forretningsproblemer. Der er mange DAX-ressourcer tilgængelig for dig, hvoraf den vigtigste er [referencen Data Analysis Expressions (DAX)](/dax/).

Da DAX har eksisteret i flere år i andre Microsoft BI-værktøjer, f.eks. Power Pivot og Analysis Services-tabelmodeller, findes der en stor mængde nyttige oplysninger. Du kan finde flere oplysninger i bøger, hvidbøger og blogs både fra Microsoft og andre, der arbejder professionelt med BI. [DAX Resource Center Wiki on TechNet](https://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) er også et godt sted at starte.

### <a name="quickquiz-answers"></a>Svar på hurtigtest
Syntaks:

1. Validerer og indsætter målingen i modellen.
2. Parenteser [].

Funktioner:

1. En tabel og en kolonne.
2. Ja. En formel kan indeholde op til 64 indlejrede funktioner.
3. [Tekstfunktioner](/dax/text-functions-dax).

Kontekst:

1. Rækkekontekst og filterkontekst.
2. En eller flere filtre i en beregning, der angiver en enkelt værdi.
3. Den aktuelle række.
