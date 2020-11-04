---
title: Tabeller, matrixer og lister i Power BI Report Builder
description: I Power BI Report Builder er tabeller, matrixer og lister dataområder, som viser sideinddelte rapportdata i celler, der er organiseret i rækker og kolonner.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3d22696168d8ae550238fab243110db357b39c22
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297690"
---
# <a name="tables-matrixes-and-lists-in-power-bi-report-builder"></a>Tabeller, matrixer og lister i Power BI Report Builder

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

I Report Builder er tabeller, matrixer og lister *dataområder* , som viser sideinddelte rapportdata i celler, der er organiseret i rækker og kolonner. Cellerne indeholder typisk tekstdata, f.eks. tekst, datoer og tal, men de kan også indeholde målere, diagrammer eller rapportelementer, f.eks. billeder. Der refereres ofte samlet til tabeller, matrixer og lister som *tablixdataområder*.  
  
 Tabel-, matrix- og listeskabelonerne er baseret på tablixdataområdet, som er et fleksibelt gitter, der kan vises data i celler. I tabel- og matrixskabelonerne er cellerne organiseret i rækker og kolonner. Da skabeloner er variationer af det underliggende generiske tablixdataområdet, kan du få vist data i en kombination af skabelonformater og ændre tabellen, matrixen eller listen for at inkludere funktionerne fra et andet dataområde, i takt med at du udvikler din rapport. Hvis du f.eks. tilføjer en tabel og opdager, at den ikke opfylder dine behov, kan du tilføje kolonnegrupper for at lave tabellen om til en matrix.  
  
 Tabel- og matrixdataområderne kan vise komplekse datarelationer ved at inkludere indlejrede tabeller, matrixer, lister, diagrammer og målere. Tabeller og matrixer har et tabellayout, og deres data kommer fra et enkelt datasæt, som er baseret på en enkelt datakilde. Den vigtigste forskel mellem tabeller og matrixer er, at tabeller kun kan indeholde rækkegrupper, hvorimod matrixer indeholder række- og kolonnegrupper.  
  
 Lister er en smule anderledes. De understøtter et gratis layout, der kan indeholde flere peer-tabeller eller peer-matrixer, som hver især bruger data fra et andet datasæt. Lister kan også bruges til formularer, f.eks. fakturaer.  
  
 På følgende billeder kan du se simple rapporter med en tabel, en matrix eller en liste.  

![Tabel, matrix og liste i Report Builder](media/report-builder-tables-matrices-lists/report-builder-table-matrix-list.png)
  
##  <a name="tables"></a><a name="Table"></a> Tabeller  
 Brug en tabel til at vise detaljerede data, organisere dataene i rækkegrupper eller begge dele. Tabelskabelonen indeholder tre kolonner med en tabelkolonneoverskrift og en række med detaljer for data. På følgende figur kan du se den indledende tabelskabelon valgt i designområdet:  

![Tabelskabelon i designområdet i Report Builder, valgt](media/report-builder-tables-matrices-lists/report-builder-new-table.png)
  
 Du kan gruppere data efter et enkelt felt, efter flere felter eller ved at skrive dit eget udtryk. Du kan oprette indlejrede grupper eller uafhængige, tilstødende grupper og vise aggregerede værdier for grupperede data eller føje totaler til grupper. Hvis din tabel f.eks. har en rækkegruppe med navnet **Kategori** , kan du tilføje en subtotal for hver gruppe samt en samlet total for rapporten. Du kan forbedre udseendet af tabellen og fremhæve data, du vil lægge vægt på, ved at flette celler og anvende formatering på data- og tabeloverskrifter.  
  
 Du kan starte med skjule detaljer eller grupperede data og inkludere håndtag til at zoome ind på detaljeniveauet for at give brugeren mulighed for interaktivt at vælge, hvor mange data der skal vises.  
  
##  <a name="matrixes"></a><a name="Matrix"></a> Matrixer  
 Du kan bruge en matrix til at vise aggregerede dataoversigter grupperet i rækker og kolonner på samme måde som med en pivottabel eller krydstabulering. Antallet af rækker og kolonner for grupper bestemmes af antallet af entydige værdier for hver række- og kolonnegruppe. På følgende figur kan du se den indledende matrixskabelon valgt i designområdet:  

![Ny matrix tilføjet fra værktøjskassen i Report Builder, valgt](media/report-builder-tables-matrices-lists/report-builder-new-matrix.png)
 
 Du kan gruppere data efter flere felter eller udtryk i række- og kolonnegrupper. Når rapportdata og dataområder kombineres, udvides en matrix vandret og lodret på siden på kørselstidspunktet, i takt med at der tilføjes kolonner for kolonnegrupper og rækker for rækkegrupper. Der vises aggregerede værdier i matrixcellerne, som er begrænset til skæringspunktet for de række- og kolonnegrupper, som cellen hører til. Hvis din matrix f.eks. har en rækkegruppe (Kategori) og to kolonnegrupper (Område og År), der viser summen af salg, vises der to celler med summen af salg for hver værdi i gruppen Kategori i rapporten. Omfanget af cellerne for de to skæringspunkter er: Kategori og Område samt Kategori og År. Matrixen kan indeholde indlejrede og tilstødende grupper. Indlejrede grupper har en overordnet-underordnet relation og tilstødende grupper en peer-relation. Du kan tilføje subtotaler for alle niveauer af indlejrede række- og kolonnegrupper i matrixen.  
  
 For at gøre det lettere at læse matrixdataene og fremhæve de data, du vil lægge vægt på, kan du flette celler eller dele dem vandret og lodret samt anvende formatering på data- og gruppeoverskrifter.  
  
 Du kan også inkludere detaljerede håndtag til at zoome ind på detaljeniveauet og starte med skjule detaljerede data. Brugeren kan derefter klikke på håndtagene for at få vist flere eller færre detaljer efter behov.  
  
##  <a name="lists"></a><a name="List"></a> Lister  
 Brug en liste til at oprette et formaliafrit layout. Du er ikke begrænset til et gitterlayout, men kan placere felterne, hvor du vil, på listen. Du kan bruge en liste til at designe en formular for at vise mange felter eller som en objektbeholder for at vise flere dataområder for grupperede data side om side. Du kan f.eks. definere en gruppe for en liste, tilføje en tabel, et diagram og et billede og vise værdier i tabellarisk og grafisk form for hver gruppeværdi, som du måske ville gøre for en medarbejder- eller patientpost.  

![Ny liste tilføjet fra værktøjskassen i Report Builder, valgt](media/report-builder-tables-matrices-lists/report-builder-new-list.png)
  
##  <a name="preparing-data"></a><a name="PreparingData"></a> Forberedelse af data  
 Der vises data fra et datasæt i dataområder med en tabel, en matrix og en liste. Du kan forberede data i den forespørgsel, der henter data til datasættet, eller ved at angive egenskaberne i tabellen, matrixen eller listen.  
  
 Forespørgselssprog såsom Transact-SQL, som du bruger til at hente data til datasættene, kan forberede dataene ved at anvende filtre, så der kun inkluderes et undersæt af dataene, og null-værdier eller tomme værdier erstattes med konstanter, hvilket gør det lettere at læse rapporten samt sortere og gruppere data.  
  
 Hvis du vælger at forberede data i dataområdet med en tabel, matrix eller liste for en rapport, kan du angive egenskaber for dataområdet eller celler i dataområdet. Hvis du vil filtrere eller sortere dataene, skal du angive egenskaber for dataområdet. Hvis du f.eks. vil sortere dataene, skal du angive, hvilke kolonner der skal sorteres efter, og hvilken retninger der skal sorteres i. Hvis du vil angive en alternativ værdi for et felt, skal du angive værdierne for celleteksten, der viser feltet. Hvis du f.eks. vil have en tom værdi vist, når et felt er tomt eller null, skal du bruge et udtryk til at angive værdien.  
  
##  <a name="building-and-configuring-a-table-matrix-or-list"></a><a name="BuildingConfiguringTableMatrixList"></a> Oprettelse og konfiguration af en tabel, en matrix eller en liste  
 Når du føjer tabeller og matrixer til din rapport, kan du bruge guiden Tabel og Matrix eller oprette dem manuelt ud fra de skabeloner, som Report Builder indeholder. Lister oprettes manuelt ud fra listeskabelonen.  
  
 Guiden hjælper dig gennem trinnene, så du hurtigt kan udarbejde og konfigurere en tabel eller matrix. Når du har fuldført guiden, eller hvis du udarbejder tablixdataområder fra bunden, kan du konfigurere og tilpasse dem yderligere. Med dialogboksene, som er tilgængelige via genvejsmenuerne i dataområderne, er det let at konfigurere de mest anvendte egenskaberne for sideskift, gentagelsesnøjagtighed og synlighed af sidehoveder og sidefødder, visningsindstillinger, filtre og sortering. Men tablixdataområdet byder på et væld af yderligere egenskaber, som du kun kan angive i ruden Egenskaber i Report Builder. Hvis du f.eks. vil vise en meddelelse, når datasættet for en tabel, matrix eller liste er tom, skal du angive meddelelsesteksten i tablixegenskaben NoRowsMessage i ruden Egenskaber.  
  
##  <a name="changing-between-tablix-templates"></a><a name="ChangingBetweenTablixTemplates"></a> Skift mellem tablixskabeloner  
 Du er ikke begrænset af dit indledende valg af tablixskabelon. I takt med at du tilføjer grupper, totaler og mærkater, vil du måske redigere dit tablixdesign. Du vil måske f.eks. starte med en tabel og derefter slette detaljerækken og tilføje kolonnegrupper.  
  
 Du kan fortsætte med at udvikle en tabel, matrix eller liste ved at tilføje en hvilken som helst tablixfunktion. Tablixfunktionerne omfatter visning af detaljerede data eller aggregater for grupperede data i rækker og kolonner. Du kan oprette indlejrede grupper, uafhængige tilstødende grupper eller rekursive grupper. Du kan filtrere og sortere grupperede data og nemt kombinere grupper ved at inkludere flere gruppeudtryk i en gruppedefinition  
  
 Du kan også tilføje totaler for en gruppe eller samlet totaler for dataområdet. Du kan skjule rækker eller kolonner for at forenkle en rapport og give brugeren mulighed for at skifte mellem visninger af skjulte data ligesom i en detaljeret rapport. 

## <a name="next-steps"></a>Næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
