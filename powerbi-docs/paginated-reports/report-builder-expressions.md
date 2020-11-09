---
title: Udtryk i Power BI Report Builder
description: Udtryk bruges i stor udstrækning overalt i sideinddelte rapporter i Power BI Report Builder til at hente, beregne, vise, gruppere, sortere, filtrere, parameterisere og formatere data.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7dbda608fcab3457a45c4ad93abf7143a19abcd1
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298168"
---
# <a name="expressions-in-power-bi-report-builder"></a>Udtryk i Power BI Report Builder

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Udtryk bruges i stor udstrækning overalt i sideinddelte rapporter i Power BI Report Builder til at hente, beregne, vise, gruppere, sortere, filtrere, parameterisere og formatere data. 
  
Mange egenskaber for rapportelementer kan angives til et udtryk. Udtryk kan hjælpe dig med at styre indhold, design og interaktivitet i din rapport. Udtryk skrives i Microsoft Visual Basic, gemmes i rapportdefinitionen og evalueres af rapportbehandleren, når du kører rapporten.  
  
 I modsætning til programmer såsom Microsoft Office Excel, hvor du arbejder med data direkte i et regneark, arbejder du i en rapport med udtryk, der er pladsholdere for data. Hvis du vil se de faktiske data fra de evaluerede udtryk, skal du få forhåndsvist rapporten. Når du kører rapporten, evaluerer rapportbehandleren hvert udtryk, da den kombinerer rapportdata og elementer i rapportlayoutet såsom tabeller og diagrammer.  
  
 I takt med at du designer en rapport, angives mange udtryk for rapportelementerne for dig. Når du f.eks. trækker et felt fra dataruden til en celle i tabellen i rapportdesignområdet, angives værdien for tekstfeltet til et simpelt udtryk for feltet. På følgende figur vises felterne Id, Navn, Salgsområde, Kode og Salg for datasættet i ruden Rapportdata. Der er føjet tre felter til tabellen: [Navn], [Kode] og [Salg]. Notationen [Navn] i designområdet repræsenterer det underliggende udtryk `=Fields!Name.Value`.  
  
![Designvisning i Report Builder](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 Når du får forhåndsvist rapporten, kombinerer rapportbehandleren tabeldataområdet med de faktiske data fra dataforbindelsen og viser en række i tabellen for hver række i resultatsættet.  
  
 Hvis du vil angive udtryk manuelt, skal du vælge et element i designområdet og bruge genvejsmenuer og dialogbokse til at angive egenskaberne for elementet. Når du ser knappen * **(fx)** eller værdien `<Expression>` på en rulleliste, ved du, at du kan angive egenskaben til et udtryk. 
  
##  <a name="understanding-simple-and-complex-expressions"></a><a name="Types"></a> Forståelse af simple og komplekse udtryk  
 Udtryk begynder med et lighedstegn (=) og skrives i Microsoft Visual Basic. Udtryk kan indeholde en kombination af konstanter, operatorer og referencer til indbyggede værdier (felter, samlinger og funktioner) samt til ekstern eller brugerdefineret kode.  
  
 Du kan bruge udtryk til at angive værdien for mange egenskaber for rapportelementer. De mest almindelige egenskaber er værdier for tekstfelter og pladsholdertekst. Hvis et tekstfelt kun indeholder ét udtryk, er udtrykket typisk værdien af egenskaben for tekstfeltet. Hvis et tekstfelt indeholder flere udtryk, er hvert udtryk værdien af pladsholdertekst i tekstfeltet.  
  
 Udtryk vises som standard i rapportdesignområdet som _simple* eller *komplekse udtryk*.  
  
-   **Simpel** Et simpelt udtryk indeholder en reference til et enkelt element i en indbygget samling, f.eks. et felt i datasættet, en parameter eller et indbygget felt. I designområdet vises et simpelt udtryk i parenteser. `[FieldName]` svarer f.eks. til det underliggende udtryk `=Fields!FieldName.Value`. Simple udtryk oprettes automatisk for dig, når du opretter rapportlayoutet, og trækker elementer fra ruden Rapportdata til designområdet. Du kan finde flere oplysninger om symboler, der repræsenterer forskellige indbyggede samlinger, i [Forståelse af præfikssymboler til simple udtryk](#DisplayText).  
  
-   **Kompleks** Et komplekst udtryk indeholder referencer til flere indbyggede referencer, operatorer og funktionskald. Et komplekst udtryk vises som <\<Expr>>, når udtryksværdien indeholder mere end en enkelt reference. Hvis du vil se udtrykket, skal du holde markøren over det og bruge værktøjstippet. Hvis du vil redigere udtrykket, skal du åbne det i dialogboksen **Udtryk**.  
  
 På følgende figur kan du se typiske eksempler på simple og komplekse udtryk for både tekstfelter og pladsholdertekst.  
  
![Standardformat af udtryk i Report Builder](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 Hvis du vil have vist eksempelværdier i stedet for tekst til udtryk, skal du formatere tekstfeltet eller pladsholderteksten. På følgende figur kan du se rapportdesignområdet, som er ændret til at vise eksempelværdier:  
  
![Format af eksempel på udtryk i Report Builder](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="understanding-prefix-symbols-in-simple-expressions"></a><a name="DisplayText"></a> Forståelse af præfikssymboler i simple udtryk  

Der bruges symboler i simple udtryk til at indikere, om referencen er til et felt, en parameter, en indbygget samling eller samlingen ReportItems. I følgende tabel kan du se eksempler på vist tekst og udtryk i tekst:  
  
|Element|Eksempel på vist tekst|Eksempel på udtryk i tekst|  
|----------|--------------------------|-----------------------------|  
|Felter i datasæt|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Rapportparametre|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Indbyggede felter|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Bogstavelig værdi af tegn, der bruges til vist tekst|`\[Sales\]`|`[Sales]`|  
  
##  <a name="writing-complex-expressions"></a><a name="References"></a> Skrivning af komplekse udtryk  
 Udtryk kan indeholde referencer til funktioner, operatorer, konstanter, felter, parametre, elementer fra indbyggede samlinger og integreret brugerdefineret kode eller brugerdefinerede assemblies.  
  
 I følgende tabel kan du se de referencetyper, du kan inkludere i et udtryk:  
  
|Referencer|Beskrivelse|Eksempel|  
|----------------|-----------------|-------------|  
|Konstanter|Beskriver de konstanter, du kan få adgang til på en interaktiv måde for egenskaber, der kræver værdier såsom skriftfarver.|`="Blue"`|  
|Operatorer|Beskriver de operatorer, du kan bruge til at kombinere referencer i et udtryk. Operatoren **&** bruges f.eks. til at sammenkæde strenge.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|Indbyggede samlinger|Beskriver de indbyggede samlinger, du kan inkludere i et udtryk, f.eks. `Fields`, `Parameters` og `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|Indbyggede rapport- og aggregeringsfunktioner|Beskriver de indbyggede funktioner, f.eks. `Sum` eller `Previous`, du kan få adgang til fra et udtryk.|`=Previous(Sum(Fields!Sales.Value))`|  
|Referencer til brugerdefineret kode og assembly i udtryk i Report Builder |Beskriver, hvordan du kan få adgang til de indbyggede CLR-klasser `xref:System.Math` og `xref:System.Convert`, andre CLR-klasser, biblioteksfunktioner for kørselstid i Visual Basic eller metoder fra en ekstern assembly.<br /><br /> Beskriver, hvordan du kan få adgang til brugerdefineret kode, der er integreret i din rapport, eller som du kompilerer og installerer som en brugerdefineret assembly på både rapportklienten og rapportserveren.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="validating-expressions"></a><a name="Valid"></a> Validering af udtryk  
 Når du opretter et udtryk for en bestemt egenskab for et rapportelement, afhænger de referencer, du kan inkludere i et udtryk, af de værdier, som egenskaben for rapportelementet kan acceptere, og af det omfang, som egenskaben evalueres i. Eksempel:  
  
-   Udtrykket [Sum] beregner som standard summen af data, der er inden for omfanget, på det tidspunkt, hvor udtrykket evalueres. For en celle i en tabel afhænger omfanget af medlemskaber af række- og kolonnegrupper. 
  
-   Værdien af egenskaben Font skal evalueres i forhold til navnet på en skrifttype.  
  
-   Syntaksen af udtrykket valideres på designtidspunktet. Validering af omfanget af et udtryk forekommer, når du publicerer rapporten. I forbindelse med validering, der afhænger af de faktiske data, kan der kun registreres fejl på kørselstidspunktet. Nogle af disse udtryk producerer #Fejl som en fejlmeddelelse i den gengivne rapport. 

## <a name="next-steps"></a>Næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
