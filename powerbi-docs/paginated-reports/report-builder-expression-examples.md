---
title: Eksempler på udtryk i Power BI Report Builder
description: Udtryk bruges ofte i sideinddelte rapporter i Power BI Report Builder til at styre indhold og rapportens udseende.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3a24724e67a931860296983fe3a116137d3b5361
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859515"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Eksempler på udtryk i Power BI Report Builder
Udtryk bruges ofte i sideinddelte rapporter i Power BI Report Builder til at styre indhold og rapportens udseende. Udtryk er skrevet i Microsoft Visual Basic, og du kan bruge indbyggede funktioner, brugerdefinerede kode, rapport- og gruppevariabler samt brugerdefinerede variabler. Udtryk begynder med et lighedstegn (=).   

Dette emne indeholder eksempler på udtryk, der kan bruges til almindelige opgaver i en rapport.  
  
-   [Funktioner i Visual Basic](#VisualBasicFunctions) Eksempler på dato, streng, konvertering og betingede Visual Basic-funktioner.  
  
-   [Rapportfunktioner](#ReportFunctions) Eksempler på aggregater og andre indbyggede rapportfunktioner.  
  
-   [Udseendet af rapportdata](#AppearanceofReportData) Eksempler på ændring af udseendet af en rapport.  
  
-   [Egenskaber](#Properties) Eksempler på angivelse af egenskaber for rapportelementer for at styre formatet eller synligheden.  
  
-   [Parametre](#Parameters) Eksempler på brug af parametre i et udtryk.  
  
-   [Brugerdefineret kode](#CustomCode) Eksempler på integreret brugerdefineret kode.  
  
Du kan finde flere oplysninger om simple og komplekse udtryk, hvor du kan bruge udtryk, og de referencetyper, du kan inkludere i et udtryk, i emnerne under [Udtryk i Power BI Report Builder](report-builder-expressions.md). 
  
## <a name="functions"></a>Funktioner  
 Mange udtryk i en rapport indeholder funktioner. Du kan formatere data, anvende logik og få adgang til rapportmetadata ved hjælp af disse funktioner. Du kan skrive udtryk, der bruger funktioner, via kørselsbiblioteket i Microsoft Visual Basic samt via navneområderne `xref:System.Convert` og `xref:System.Math`. Du kan føje referencer til funktioner i brugerdefineret kode. Du kan også bruge klasser fra Microsoft .NET Framework, herunder `xref:System.Text.RegularExpressions`.  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Funktioner i Visual Basic  
 Du kan bruge funktioner i Visual Basic til at håndtere de data, der vises i tekstfelter, eller der bruges til parametre, egenskaber eller andre områder af rapporten. Dette afsnit indeholder eksempler, der demonstrerer nogle af disse funktioner. Du kan finde flere oplysninger i [Medlemmer af kørselsbiblioteket i Visual Basic](/dotnet/visual-basic/language-reference/runtime-library-members) på MSDN.  
  
 .NET Framework indeholder mange muligheder for brugerdefinerede formater, f.eks. specifikke datoformater. Du kan finde flere oplysninger i [Formateringstyper](/dotnet/standard/base-types/formatting-types).  
  
### <a name="math-functions"></a>Matematikfunktioner  
  
-   Funktionen **Round** er nyttig til at afrunde tal til det nærmeste heltal. Følgende udtryk afrunder 1.3 til 1:  
  
    ```  
    = Round(1.3)  
    ```  
  
     Du kan også skrive et udtryk for at afrunde en værdi til et multiplum, som du angiver, ligesom med funktionen **MAFRUND** i Excel. Multiplicer værdien med en faktor, der opretter et heltal, afrund tallet, og divider derefter med den samme faktor. Hvis du f.eks. vil afrunde 1.3 til det nærmeste multiplum af .2 (1.4), skal du bruge følgende udtryk:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> Datofunktioner  
  
-   Funktionen **Today** leverer den aktuelle dato. Dette udtryk kan bruges i et tekstfelt til at vise datoen i rapporten eller i en parameter til at filtrere data baseret på den aktuelle dato.  
  
    ```  
    =Today()  
    ```  
  
-   Brug funktionen **DateInterval** til at udtrække en specifik del af en dato. Her er nogle gyldige parametre af typen **DateInterval**:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Med dette udtryk vises f.eks. ugenummeret i det aktuelle år for dags dato:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   Funktionen **DateAdd** er nyttigt til at levere en række datoer baseret på en enkelt parameter. Følgende udtryk indeholder en dato, der er seks måneder efter datoen fra parameteren med navnet *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   Funktionen **Year** viser året for en bestemt dato. Du kan bruge denne til at gruppere datoer sammen eller til at vise året som en mærkat for en række datoer. Dette udtryk leverer året for en bestemt gruppe af datoer for salgsordrer. Funktionen **Month** og andre funktioner kan også bruges til at håndtere datoer. Du kan finde flere oplysninger i dokumentationen til Visual Basic.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Du kan kombinere funktioner i et udtryk for at tilpasse formatet. Følgende udtryk ændrer formatet af en dato i formen måned-dag-år til måned-uge-ugenummer. Eksempelvis 12/23/2009 til december, uge 3:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Når funktionen bruges som et beregnet felt i et datasæt, kan du bruge dette udtryk i et diagram til at aggregere værdier efter uge i hver måned.  
  
-   Følgende udtryk formaterer værdien SellStartDate som MMM-ÅÅ. Feltet SellStartDate er data af typen datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   Følgende udtryk formaterer værdien SellStartDate som dd/MM/åååå. Feltet SellStartDate er data af typen datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   Funktionen **CDate** konverterer værdien til en dato. Funktionen **Now** returnerer en datoværdi, der indeholder den aktuelle dato og det aktuelle klokkeslæt i henhold til systemet. **DateDiff** returnerer en lang værdi, der angiver antallet af tidsintervaller mellem to datoværdier.  
  
     I følgende eksempel kan du se startdatoen for det aktuelle år  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   I følgende eksempel kan du se startdatoen for den forrige måned baseret på den aktuelle måned.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   Følgende udtryk genererer intervalårene mellem SellStartDate og LastReceiptDate. Disse felter befinder sig i to forskellige datasæt, DataSet1 og DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   Funktionen **DatePart** returnerer en heltalsværdi med den angivne komponent i en given datoværdi. Følgende udtryk returnerer året for den første værdi for SellStartDate i DataSet1. Datasætområdet er angivet, fordi der er flere datasæt i rapporten.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   Funktionen **DateSerial** returnerer en datoværdi, der repræsenterer et angivet år, en angiven måned og en angiven dag med oplysningerne om tid angivet til midnat. I følgende eksempel kan du se slutdatoen for den forrige måned baseret på den aktuelle måned.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   Følgende udtryk viser forskellige datoer baseret på en datoparameterværdi, som vælges af brugeren.  
  
|Beskrivelse af eksempel|Eksempel|  
|-------------------------|-------------|  
|I går|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|For to dage siden|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|For en måned siden|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|For to måneder siden|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|For et år siden|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|For to år siden|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> Strengfunktioner  
  
-   Kombiner mere end et felt ved hjælp af sammenkædningsoperatorer og konstanter i Visual Basic. Følgende udtryk returnerer to felter på hvert sin separate linje i det samme tekstfelt:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Formatér datoer og tal i en streng med funktionen **Format**. Følgende udtryk viser værdier for parametrene *StartDate* og *EndDate* i langt datoformat:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Hvis tekstfeltet kun indeholder en dato eller et tal, skal du bruge egenskaben Formatér for tekstfeltet til at anvende formatering i stedet for funktionen **Format** i tekstfeltet.  
  
-   Funktionerne **Right**, **Len** og **InStr** er nyttige til at returnere en understreng, f.eks. trimning af *DOMÆNE*\\*brugernavn* til kun brugernavnet. Følgende udtryk returnerer en del af en streng til højre for en omvendt skråstreg (\\) fra en parameter med navnet *Bruger*:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     Følgende udtryk resulterer i den samme værdi som den forrige, hvor medlemmer af `xref:System.String`-klassen for .NET Framework bruges i stedet for funktioner i Visual Basic:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Vis de valgte værdier fra en parameter med flere værdier. I følgende eksempel bruges funktionen **Join** til at sammenkæde de valgte værdier for parameteren *MySelection* i en enkelt streng, der kan angives som et udtryk for værdien af et tekstfelt i et rapportelement:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     Følgende eksempel gør det samme som ovenstående eksempel samt viser en tekststreng forud for listen over valgte værdier.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   Funktionerne **Regex** fra .NET Framework `xref:System.Text.RegularExpressions` er nyttige til at ændre formatet af eksisterende strenge, f.eks. formatering af et telefonnummer. I følgende udtryk bruges funktionen **Replace** til at ændre formatet af et ticifret telefonnummer i et felt fra "*nnn*-*nnn*-*nnnn*" til "(*nnn*) *nnn*-*nnnn*":  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Bekræft, at der ikke er nogen ekstra mellemrum i værdien af Fields!Phone.Value, og at den er af typen `xref:System.String`.  
  
### <a name="lookup"></a>Opslag  
  
-   Ved at angive et nøglefelt kan du bruge funktionen **Lookup** til at hente en værdi fra et datasæt for en en-til-en-relation, f.eks. et nøgleværdipar. Følgende udtryk viser produktnavnet fra et datasæt ("Produkt"), så produkt-id'et matcher:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Ved at angive et nøglefelt kan du bruge funktionen **LookupSet** til at hente et sæt af værdier fra et datasæt for en en-til-mange-relation. En person kan f.eks. have flere telefonnumre. I følgende eksempel antager vi, at datasættet PhoneList indeholder en identifikator for en person og et telefonnummer i hver række. **LookupSet** returnerer en matrix af værdier. Følgende udtryk kombinerer de returnerede værdier i en enkelt streng og viser listen over telefonnumre for den person, der angives af ContactID:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> Konverteringsfunktioner  
 Du kan bruge funktionerne i Visual Basic til at konvertere et felt fra én datatype til en anden datatype. Konverteringsfunktioner kan bruges til at konvertere standarddatatypen for et felt til den datatype, der er nødvendig til at foretage beregninger eller til at kombinere tekst.  
  
-   Med følgende udtryk konverteres konstanten 500 til typen Decimal, så den kan sammenlignes med datatypen penge i Transact-SQL i feltet Værdi for et filterudtryk.  
  
    ```  
    =CDec(500)  
    ```  
  
-   Med følgende udtryk vises antallet af værdier, der er valgt for parameteren *MySelection* med flere værdier.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> Beslutningsfunktioner  
  
-   Med funktionen **Iif** returneres én af to værdier, afhængigt af om udtrykket er sandt eller ej. I følgende udtryk bruges funktionen **Iif** til at returnere den booleske værdi **Sand**, hvis værdien af `LineTotal` overstiger 100. Ellers returneres **Falsk**:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Brug flere **IIF**-funktioner (også kendt som "indlejrede IIF'er") til at returnere én af tre værdier afhængigt af værdien af `PctComplete`. Følgende udtryk kan placeres i fyldfarven for et tekstfelt for at ændre baggrundsfarven afhængigt af værdien i tekstfeltet.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Værdier, der er større end eller lig med 10, vises med en grøn baggrund, mellem 1 og 9 vises med en blå baggrund og mindre end 1 vises med en rød baggrund.  
  
-   Du kan også bruge funktionen **Switch** til at få den samme funktionalitet. Funktionen **Switch** er nyttig, når du skal teste tre eller flere betingelser. Funktionen **Switch** returnerer den værdi, der er knyttet til det første udtryk i en serie, der evalueres som Sand:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Værdier, der er større end eller lig med 10, vises med en grøn baggrund, mellem 1 og 9 vises med en blå baggrund, lig med 1 vises med en gul baggrund, og 0 eller mindre vises med en rød baggrund.  
  
-   Test værdien af feltet `ImportantDate`, og returner "Rød", hvis den er mere end en uge gammel, og ellers "Blå". Dette udtryk kan bruges til at styre egenskaben Color for et tekstfelt i et rapportelement:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Test værdien af feltet `PhoneNumber`, og returner "Ingen værdi", hvis den er **null** (**Intet** i Visual Basic), og returner ellers værdien for telefonnummeret. Dette udtryk kan bruges til at styre værdien af et tekstfelt i et rapportelement.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Test værdien af feltet `Department`, og returner enten navnet på en underrapport eller **null** (**Intet** i Visual Basic). Dette udtryk kan bruges til betingede underrapporter for detaljeadgang.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Test, om en feltværdi er null. Dette udtryk kan bruges til at styre egenskaben **Hidden** for et billede i et rapportelement. I eksemplet nedenfor vises det billede, der er angivet af feltet [LargePhoto], kun, hvis værdien af feltet ikke er null.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   Funktionen **MonthName** returnerer en enkelt strengværdi med navnet på den angivne måned. I følgende eksempel vises NA i feltet Måned, når feltet indeholder værdien 0.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> Rapportfunktioner  
 Du kan tilføje en reference til andre rapportfunktioner, der håndterer data i en rapport, i et udtryk. Dette afsnit indeholder eksempler på to af disse funktioner. 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   Funktionen **Sum** kan sammenlægge værdierne i en gruppe eller et dataområde. Denne funktion kan være nyttig i en gruppes sidehoved eller sidefod. Med følgende udtryk vises summen af data i gruppen Ordre eller dataområdet:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   Du kan også bruge funktionen **Sum** til betingede aggregeringsberegninger. Hvis et datasæt f.eks. indeholder et felt med navnet Tilstand med de mulige værdier, Ikke startet, Startet, Fuldført, beregnes den aggregerede sum kun for værdien Fuldført med følgende udtryk, når det placeres i et gruppehoved:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   Når funktionen **RowNumber** bruges i et tekstfelt i et dataområde, vises rækkenummeret for hver forekomst af tekstfeltet, hvori udtrykket forekommer. Denne funktion kan være nyttig til at nummerere rækker i en tabel. Den kan også være nyttig i forbindelse med mere komplekse opgaver, f.eks. at levere sideskift baseret på antallet af rækker. Du kan finde flere oplysninger under [Sideskift](#PageBreaks) i dette emne.  
  
     Det omfang, du angiver for **RowNumber** styrer, hvornår gennummerering begynder. Nøgleordet **Intet** angiver, at funktionen begynder at tælle fra den første række i det yderste dataområde. Hvis du vil begynde at tælle i indlejrede dataområder, skal du bruge navnet på dataområdet. Hvis du vil begynde at tælle i en gruppe, skal du bruge navnet på gruppen.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> Udseendet af rapportdata  
 Du kan bruge udtryk til at ændre den måde, data vises på i en rapport. Du kan f.eks. vise værdierne af to felter i et enkelt tekstfelt, vise oplysninger om rapporten eller påvirke den måde, sideskift indsættes på i rapporten.  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> Sidehoveder og sidefødder  
 Når du designer en rapport, vil du måske vise navnet på rapporten og sidenummeret i rapportens sidefod. Brug følgende udtryk til at gøre det:  
  
-   Følgende udtryk indeholder navnet på rapporten og det klokkeslæt, den blev kørt på. Det kan placeres i et tekstfelt i rapportens sidefod eller i brødteksten i rapporten. Klokkeslættet er formateret med formateringsstrengen fra .NET Framework til det korte datoformat:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   Når følgende udtryk placeres i et tekstfelt i rapportens sidefod, vises sidenummeret og det samlede antal sider i rapporten:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 I følgende eksempler beskrives det, hvordan du viser den første og den sidste værdi fra en side i sidehovedet på samme måde, som du ville med en mappeliste. I eksemplet antages det, at der er et dataområde med et tekstfelt med navnet `LastName`.  
  
-   Når følgende udtryk placeres i et tekstfelt i venstre side af sidehovedet, vises den første værdi af tekstfeltet `LastName` på siden:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   Når følgende udtryk placeres i et tekstfelt i højre side af sidehovedet, vises den sidste værdi af tekstfeltet `LastName` på siden:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 I følgende eksempel beskrives det, hvordan du få vist det samlede antal sider. I eksemplet antages det, at der er et dataområde med et tekstfelt med navnet `Cost`.  
  
-   Når følgende udtryk placeres i sidehovedet eller sidefoden, vises summen af værdierne i tekstfeltet `Cost` for siden:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Du kan kun referere til ét rapportelement pr. udtryk i et sidehoved eller en sidefod. Du kan også referere til navnet på tekstfeltet i udtryk i sidehovedet og sidefoden, men ikke til det faktiske dataudtryk i tekstfeltet.  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> Sideskift  
 I nogle rapporter vil du måske placere et sideskift efter et angivet antal rækker i stedet for eller måske ud over på grupper eller rapportelementer. Det gør du ved at oprette en gruppe, der indeholder de grupper eller detaljerede poster, du vil have. Føj et sideskift til gruppen, og tilføj derefter et gruppeudtryk for at gruppere efter et angivet antal rækker.  
  
-   Når følgende udtryk placeres i gruppeudtrykket, tildeles et nummer til hvert sæt af 25 rækker. Når et sideskift er defineret for gruppen, resulterer dette udtryk i et sideskift for 25. række.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Giv brugerne tilladelse til at angive en værdi for antallet af rækker pr. side, opret en parameter med navnet `RowsPerPage`, og basér gruppeudtrykket på parameteren, som vist i følgende udtryk:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> Egenskaber  
 Udtryk bruges ikke kun til at vise data i tekstfelter. De kan også bruges til at ændre den måde, egenskaber anvendes på i forhold til rapportelementer. Du kan ændre typografioplysningerne for et rapportelement eller ændre dets synlighed.  
  
###  <a name="formatting"></a><a name="Formatting"></a> Formatering  
  
-   Når følgende udtryk bruges i egenskaben Color for et tekstfelt, ændres farven på teksten afhængigt af værdien af feltet `Profit`:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     Du kan også bruge objektvariablen `Me` i Visual Basic. Denne variabel er en anden måde at referere til værdien af et tekstfelt på.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   Når følgende udtryk bruges i egenskaben BackgroundColor for et rapportelement i et dataområde, skifter baggrundsfarven for hver række mellem bleg grøn og hvid:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Hvis du bruger et udtryk for et angivet område, skal du muligvis angive datasættet for aggregeringsfunktionen:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  Tilgængelige farver kommer fra KnownColor-optællingen i .NET Framework.  
  
### <a name="chart-colors"></a>Diagramfarver  
 Du kan bruge brugerdefineret kode til at styre den rækkefølge, som farver knyttes til datapunktværdier, for at angive farver for et diagram af typen Figur. Dette hjælper dig med at bruge ensartede farver for flere diagrammer, der har de samme kategorigrupper. 
  
###  <a name="visibility"></a><a name="Visibility"></a> Synlighed  
 Du kan vise og skjule elementer i en rapport ved hjælp af egenskaber for synlighed for rapportelementet. I et dataområde, f.eks. en tabel, kan du starte med skjule detaljerækker på baggrund af værdien i et udtryk.  
  
-   Når følgende udtryk bruges til indledende synlighed for detaljerækker i en gruppe, vises detaljerækkerne for al salg, der overstiger 90 % i feltet `PctQuota`:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   Når følgende udtryk angives i egenskaben Hidden for en tabel, vises tabellen kun, hvis den indeholder mere end 12 rækker:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   Når følgende udtryk angives i egenskaben **Hidden** for en kolonne, vises kolonnen kun, hvis feltet findes i rapportens datasæt, efter dataene hentes fra datakilden:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URL-adresser  
 Du kan tilpasse URL-adresser ved hjælp af rapportdata samt betinget styre, om URL-adresser tilføjes som en handling for et tekstfelt.  
  
-   Når følgende udtryk bruges som en handling for et tekstfelt, genereres der en brugerdefineret URL-adresse, som angiver feltet `EmployeeID` i datasættet som en URL-parameter.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   Følgende udtryk styrer betinget, om en URL-adresse føjes til et tekstfelt. Dette udtryk afhænger af en parameter med navnet `IncludeURLs`, som giver en bruger tilladelse til at beslutte, om vedkommende vil inkludere aktive URL-adresser i en rapport. Dette udtryk er angivet som en handling for et tekstfelt. Ved at angive parameteren til Falsk og derefter vise rapporten kan du eksportere rapporten Microsoft Excel uden links.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="report-data"></a><a name="ReportData"></a> Rapportdata  
 Udtryk kan bruges til at håndtere data, der bruges i rapporten. Du kan referere til parametre og andre rapportoplysninger. Du kan tilmed ændre den forespørgsel, der bruges til at hente dataene til rapporten.  
  
###  <a name="parameters"></a><a name="Parameters"></a> Parametre  
 Du kan bruge udtryk i en parameter til at variere standardværdien for parameteren. Du kan f.eks. bruge en parameter til at filtrere data for en bestemt bruger på baggrund af det bruger-id, der bruges til at køre rapporten.  
  
-   Når følgende udtryk bruges som standardværdien for en parameter, indsamles bruger-id'et for den person, der kører rapporten:  
  
    ```  
    =User!UserID  
    ```  
  
-   Brug den globale samling af **parametre** for at referere til en parameter i en forespørgselsparameter, et filterudtryk, et tekstfelt eller andre områder af rapporten. I dette eksempel antages det, at parameteren hedder *Afdeling*:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Parametre kan oprettes i en rapport, men angives til at være skjulte. Når rapporten køres på rapportserveren, vises parameteren ikke på værktøjslinjen, og læseren af rapporten kan ikke ændre standardværdien. Du kan bruge en skjult parameter, der er angivet til en standardværdi, som en brugerdefinerede konstant. Du kan bruge denne værdi i et hvilket som helst udtryk, herunder et feltudtryk. Med følgende udtryk identificeres det felt, der er angivet af standardværdien for parameteren med navnet *ParameterField*:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> Brugerdefineret kode  
 Du kan bruge brugerdefineret kode integreret i en rapport. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Brug af gruppevariabler til brugerdefineret aggregering  
 Du kan initialisere værdien for en gruppevariabel, der er lokal for et bestemt gruppeområde, og derefter inkludere en reference til denne variabel i udtryk. En af de måder, du kan bruge gruppevariabler med brugerdefineret kode på, er ved at implementere en brugerdefineret aggregat. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Udeladelse af null- eller nulværdier på kørselstidspunktet  
 Nogle værdier i et udtryk kan evalueres til null eller ikke-defineret på tidspunktet for behandlingen af rapporten. Dette kan resulterer i kørselsfejl, der medfører, at **#Error** vises i tekstfeltet i stedet for det evaluerede udtryk. Funktionen **IIF** er særligt følsom over for denne funktionsmåde, fordi hver del af **IIF**-sætningen evalueres (herunder funktionskald) i modsætning til en If-Then-Else-sætning, før de sendes til den rutine, som undersøger for **sand** eller **falsk**. Sætningen `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` genererer **#Error** i den gengivne rapport, hvis `Fields!Sales.Value` er INTET.  
  
 Brug en af følgende strategier for at undgå denne tilstand:  
  
-   Angiv tælleren til 0 og nævneren til 1, hvis værdien for feltet B er 0 eller ikke-defineret. Ellers skal du angive tælleren til værdien for feltet A og nævneren til værdien for feltet B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Brug en brugerdefineret kodefunktion til at returnere værdien for udtrykket. Følgende eksempel returnerer den procentvise forskel mellem en aktuel værdi og en tidligere værdi. Dette kan bruges til at beregne forskellen mellem de to på hinanden følgende værdier, og det håndterer kanttilfældet for den første sammenligning (når der ikke er nogen tidligere værdi) og sager, hvor enten den forrige værdi eller den aktuelle værdi er **null** (**Intet** i Visual Basic).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     Med følgende udtryk vises det, hvordan du kalder denne brugerdefinerede kode fra et tekstfelt for objektbeholderen "ColumnGroupByYear" (gruppe eller et dataområde).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Dette hjælper med at undgå kørselsundtagelser. Du kan nu bruge et udtryk som `=IIF(Me.Value < 0, "red", "black")` i egenskaben **Color** for tekstfeltet til at vise tekst betinget baseret på, om værdierne er større eller mindre end 0.  
  
## <a name="next-steps"></a>De næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
