---
title: Form og kombiner data i Power BI Desktop
description: Form og kombiner data i Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: bb4f910f0ac6240ed2dab987a7076b3f996b86fe
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/06/2017
---
# <a name="shape-and-combine-data-in-power-bi-desktop"></a>Form og kombiner data i Power BI Desktop
I **Power BI Desktop** kan du oprette forbindelse til mange forskellige typer datakilder og derefter forme dataene til dine behov. At *forme* data betyder, at dataene skal transformeres – for eksempel omdøbning af kolonner eller tabeller, ændring af tekst til tal, fjernelse af rækker, angivelse af den første række som overskrifter osv. At *kombinere* data betyder, at der oprettes forbindelse til to eller flere datakilde, dataene formes efter behov, og de konsolideres derefter i én forespørgsel.

I dette dokument kan du se, hvordan du kan forme en forespørgsel i Power BI Desktop, og jeg vil fremhæve nogle af de mest almindelige opgaver, du skal udføre for dette. Den forespørgsel, der bruges her, er beskrevet mere detaljeret under [Introduktion til Power BI Desktop](desktop-getting-started.md), hvor du også kan se, hvordan de opretter forespørgslen fra bunden.

Det er praktisk at vide, at du kan bruge genvejsmenuer og båndet i **Forespørgselseditor** i Power BI Desktop. Det meste af det, du kan vælge på båndet **Transformér**, er også tilgængeligt, hvis du højreklikker på et element (f.eks. en kolonne) og vælger i den viste menu.

## <a name="shape-data"></a>Form data
Når du former data i Forespørgselseditor, angiver du en trinvis vejledning (som Forespørgselseditor udfører for dig) for at justere datamængden, efterhånden som Forespørgselseditor indlæser og præsenterer dem. Den oprindelige datakilde påvirkes ikke. Det er kun denne bestemte visning af dataene, der justeres eller *formes*.

De angivne trin (f.eks. omdøbning af en tabel, transformation af en datatype eller sletning af kolonner) registreres af Forespørgselseditor, og hver gang denne forespørgsel opretter forbindelse til datakilden, udføres disse trin, så dataene er altid er formet på den måde, du angiver. Denne proces foregår, når du bruger Forespørgselseditor i Power BI Desktop, eller hvis andre bruger din delte forespørgsel, for eksempel i **Power BI**-tjenesten. Disse trin er hentet, i rækkefølge, i ruden **Forespørgselsindstillinger** under **Anvendte trin**.

På følgende billede vises ruden **Forespørgselsindstillinger** for en forespørgsel, som er formet – vi gennemgår hvert enkelt trin i de næste afsnit.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished.png)

Hvis vi bruger de data fra [Introduktion til Power BI Desktop](https://powerbi.uservoice.com/knowledgebase/articles/471664), som blev hentet ved at oprette forbindelse til en Web-datakilde, kan vi forme dataene til vores behov.

For det første blev resultaterne i den ene kolonne ikke automatisk transformeret fra tekst til tal, da tabellen blev indlæst i Forespørgselseditor, og vi skal bruge dem som tal. Det er ikke noget problem. Du skal blot højreklikke på kolonneoverskriften og vælge **Rediger type \> Heltal** for at ændre dem. Hvis du vil markere mere end én kolonne, skal du først markere en kolonne og derefter holde **Skift** nede, vælge yderligere tilstødende kolonner og derefter højreklikke på en kolonneoverskrift for at ændre alle de valgte kolonner. Du kan også holde **Ctrl** nede for at vælge kolonner, der ikke støder op til hinanden.

![](media/desktop-shape-and-combine-data/shapecombine_changetype.png)

Du kan også *transformere* disse kolonner fra tekst til overskrift fra fanen **Transformér** på båndet. Her er båndet **Transformér** med en pil, der peger på knappen **Datatype**, som gør det muligt at transformere den aktuelle datatype til en anden.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Bemærk, at i ruden **Forespørgselsindstillinger** vil **Anvendte trin** afspejle de trin til formning, der er anvendt på dataene. Hvis jeg vil fjerne et trin fra formningsprocessen, skal jeg blot vælge **X** til venstre for trinnet. I det følgende billede afspejler **Anvendte trin** de trin, der er udført indtil videre: der er oprettet forbindelse til webstedet (**Kilde**), jeg har valgt tabellen (**Navigation**), og da tabellen blev indlæst, ændrede Forespørgselseditor automatisk tekstbaserede talkolonner fra *Tekst* til *Heltal* (**Ændret type**). En kolonne med rangering blev ikke automatisk ændret til en talbaseret type, og i de næste par afsnit kan du se, hvorfor.

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly.png)

Inden vi kan arbejde med forespørgslen, skal vi foretage nogle ændringer for at kunne arbejde med dataene, som vi gerne vil:

* *Fjern den første kolonne* – den behøver vi ikke, da den kun indeholder redundante rækker, hvor der står "Se, hvordan din stat er rangeret i forhold til pensionering". Det skyldes, at det er en webbaseret tabel.
* *Ret nogle fejl* – kolonnen **Health care quality** indeholder nogle tilknytninger til staternes rangering. Dette var på webstedet angivet med teksten *(tie)* efter tallene. Det fungerer fint på webstedet, men det kræver, at vi manuelt transformerer kolonnen fra tekst til tal. Det er nemt at gøre i Power BI Desktop, og det viser samtidig en af de smarte funktioner ved **Anvendte trin**.
* *Skift tabelnavnet* – **Tabel 0** er ikke en nyttig beskrivelse, men det er let at ændre navnet.

Du kan fjerne den første kolonne ved at markere kolonnen og vælge fanen **Hjem** på båndet og derefter vælge **Fjern kolonner** som vist i følgende figur.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnsretirement.png)

Derefter skal tekstkolonnen transformeres til tal. Til at starte med virker det ret enkelt, at vi bare kan ændre kolonnen **Health care quality** fra tekst til tal (for eksempel *Heltal* eller *Decimaltal*). Men når vi ændrer typen fra **Tekst** til **Heltal** og derefter gennemser værdierne i kolonnen, viser Forespørgselseditor, at der er nogle fejl.

![](media/desktop-shape-and-combine-data/shapecombine_error.png)

Der findes et par metoder til at få vist flere oplysninger om hver enkelt fejl. Du kan markere cellen (uden at klikke på ordet **Fejl**), eller du kan klikke direkte på ordet **Fejl**. Hvis du markerer cellen *uden* at klikke direkte på ordet **Fejl**, vises fejloplysningerne nederst i vinduet Forespørgselseditor.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo.png)

Hvis du klikker direkte på ordet *Fejl*, vil Forespørgselseditor oprette et trin under **Anvendte trin** i ruden **Forespørgselsindstillinger** og vise oplysninger om fejlen.

![](media/desktop-shape-and-combine-data/shapecombine_errorselect.png)

Hvis du vil tilbage til Forespørgselseditor, skal du fjerne trinnet ved at vælge **X** ud for trinnet.

Hvis du vælger det seneste trin under **Anvendte trin**, vises fejlmeddelelsen som på følgende billede.

![](media/desktop-shape-and-combine-data/shapecombine_querystep1.png)

Da Forespørgselseditor optager trinnene sekventielt, kan vi vælge det foregående trin under **Anvendte trin** for at ændre typen for at se, hvilken værdi cellen havde før transformationen, som du kan se det i det følgende billede.

![](media/desktop-shape-and-combine-data/shapecombine_querystep2.png)

Nu kan vi rette værdierne og *derefter* ændre typen. Da Forespørgselseditor optager trinnene sekventielt, men stadig uafhængigt af hinanden, kan du flytte hvert trin under **Anvendte trin** op eller ned i sekvensen. Hvis du højreklikker på et trin, vises der en menu, hvor du kan gøre følgende: **Omdøb**, **Slet**, **Slet**  **indtil slutning** (fjern det aktuelle og alle efterfølgende trin), **Flyt op** eller **Flyt ned**.

![](media/desktop-shape-and-combine-data/shapecombine_querystepreorder.png)

Du kan desuden vælge et vilkårligt trin på listen **Anvendte trin** og fortsætte med at forme dataene på det trin i sekvensen. Forespørgselseditor vil automatisk indsætte et nyt trin direkte efter det aktuelt valgte trin under **Anvendte trin**. Lad os prøve.

Start med at vælge det trin på listen **Anvendte trin**, der står før ændringen af typen for kolonnen **Health care quality**. Derefter erstatter vi værdierne med teksten "(tie)" i cellen, så der kun er tallet tilbage. Højreklik på den celle, der indeholder "35 (tie)", og vælg *Erstat værdier* i menuen. Læg mærke til det trin på listen **Anvendte trin**, der er valgt (trinnet før ændringen af typen).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues.png)

Da vi indsætter et trin, vises der en advarsel om dette, da efterfølgende trin kan medføre, at forespørgslen ikke fungerer som ventet. Det gælder om at være påpasselig og tænke sig om. Da dette er et selvstudium, vil jeg gerne fremhæve en virkelig sej funktion i Forespørgselseditor, så du kan se, hvordan du kan oprette, slette, indsætte og ændre rækkefølgen af trin. Her vil jeg beskrive funktionen **Indsæt**.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Der er tre værdier, der indeholder "ties", så jeg erstatter værdierne i disse. Når der oprettes et nyt trin under Anvendte trin i Forespørgselseditor, navngives det baseret på handlingen, som i dette tilfælde er **Erstattet værdi**. Når du har mere end ét trin med samme navn i din forespørgsel, vil Forespørgselseditor tilføje et tal (i stigende rækkefølge) til hvert efterfølgende trin under **Anvendte trin** for at skelne mellem dem.

På følgende skærm vises tre trin med **Erstattet værdi** under **Forespørgselsindstillinger**, men det viser også noget andet, som er endnu mere interessant: da vi har fjernet hver forekomst af teksten "(tie)" fra kolonnen **Health care quality** vil trinnet **Ændret type** nu blive fuldført *uden fejl*.

![](media/desktop-shape-and-combine-data/shapecombine_replacedvaluesok.png)

> [!NOTE]
> Du kan også bruge **Fjern fejl** (på båndet eller i genvejsmenuen), som fjerner alle de rækker, som indeholder fejl. I dette tilfælde ville det have fjernet alle de stater, som indeholdt teksten "*(tie)*", fra dataene, og de rækker skulle gerne bevares, da alle staterne skal med i tabellen.

Det er blot et eksempel på, hvor effektiv og alsidig Forespørgselseditor kan være.

Til sidst vil jeg ændre navnet på tabellen til noget mere beskrivende. Når der skal oprettes rapporter, er det især praktisk at have beskrivende tabelnavne, hvis der oprettes forbindelse til flere datakilder, og de vises alle i ruden **Felter** i visningen **Rapport**.

Det er nemt at ændre tabelnavnet. Du skal blot skrive det nye navn under **Egenskaber** i ruden **Forespørgselsindstillinger** og trykke på **Enter**. Jeg kalder tabellen *RetirementStats*.

![](media/desktop-shape-and-combine-data/shapecombine_renametable.png)

Nu er dataene blevet formet til det, vi skal bruge. Lad os derefter oprette forbindelse til en anden datakilde og kombinere dataene.

## <a name="combine-data"></a>Kombiner data
Dataene omkring de forskellige stater er interessante og kan bruges til at skabe yderligere analyser og forespørgsler. Men der er et problem: De fleste data anvender forkortelser på to bogstaver for statskoder og ikke statens fulde navn. Vi skal bruge en måde at knytte forkortelserne for staterne til deres navne på.

Vi er heldige. Der er en anden offentlig datakilde, som gør lige præcis dette, men den skal formes en del, før vi kan knytte den til vores pensioneringstabel. Her er webressourcen med forkortelser for stater:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

Jeg vælger **Ny kilde \> Web** under fanen **Hjem** i Forespørgselseditor, skriver adressen og vælger OK, hvorefter resultaterne fra websiden vises i Navigator.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator.png)

Jeg vælger **Tabel[rediger]**, da det omfatter de ønskede data, men det kræver lidt mere formning af dataene.

> [!TIP]
> Er der en hurtigere eller nemmere måde at udføre disse trin på? Ja, vi kunne oprette en *relation* mellem de to tabeller og forme dataene baseret på relationen. Det er stadig en god idé at følge trinnene herunder, da det er en god måde at lære at arbejde med tabeller på. Du skal bare også vide, at du kan bruge relationer til hurtigt at bruge data fra flere tabeller.
> 
> 

Du skal udføre følgende trin for at forme dataene:

* Fjern de to øverste rækker – de er resultatet af den måde, websidens tabel blev oprettet på, og dem behøver vi ikke. Vælg **Formindsk rækker \> Fjern rækker \> Fjern de øverste rækker** under fanen **Home** .

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

Vinduet **Fjern de øverste rækker** åbnes, og du kan angive, hvor mange rækker du vil fjerne.

* Fjern de nederste 26 rækker – de indeholder alle territorierne, som vi ikke behøver at inkludere. Vælg **Formindsk rækker \> Fjern rækker \> Fjern de nederste rækker** under fanen **Hjem** .

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Da tabellen RetirementStats ikke indeholder oplysninger for Washington DC, skal vi filtrere dem fra listen. Vælg rullepilen ud for kolonnen Region Status, og fjern markeringen i afkrydsningsfeltet ud for **Federal district**.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Fjern nogle unødvendige kolonner –– vi skal kun bruge bogstavforkortelsen for staterne, så vi kan fjerne følgende kolonner: **Column2**, **Column3** og derefter **Column5** til og **Column10**. Start med at markere Column2, hold **Ctrl** trykket ned, og markér de øvrige kolonner, der skal fjernes (når du holder Ctrl nede, kan du markere flere rækker, der ikke støder op til hinanden). Vælg **Fjern kolonner \> Fjern kolonner** under fanen Hjem.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

* Brug den første række som overskrifter – da vi har fjernet de tre øverste rækker, er den aktuelle øverste række den overskrift, vi vil have. Du kan vælge **Brug den første række som overskrifter** under fanen **Hjem** eller fra fanen **Transformér** på båndet.

![](media/desktop-shape-and-combine-data/shapecombine_usefirstrowasheaders.png)

>[!NOTE]
>Dette er et godt tidspunkt at påpege, at *rækkefølgen* af de anvendte trin i Forespørgselseditor er vigtig, og den kan påvirke, hvordan datatypen formes. Det er også vigtigt at overveje, hvordan ét trin kan påvirke efterfølgende trin. Hvis du fjerner et trin fra Anvendte trin, fungerer de efterfølgende trin muligvis ikke som oprindeligt tiltænkt, på grund af effekten af rækkefølgen af trin i forespørgslen.

>[!NOTE]
>Hvis du gør vinduet med Forespørgselseditor smallere, vil nogle af elementerne på båndet bliver gjort mindre, så den synlige plads kan udnyttes bedre. Hvis du gør vinduet med Forespørgselseditor bredere, udvides elementerne på båndet, så det større område udnyttes bedst muligt.

* Omdøb kolonnerne og selve tabellen – som sædvanligt kan du omdøbe en kolonne på flere måder. Start med at markere kolonnen, og vælg enten **Omdøb** under **Transformér** på båndet, eller højreklik, og vælg **Omdøb** i menuen. I det følgende billede vises pile til begge muligheder. Du skal kun vælge den ene mulighed.

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

Jeg vælger at omdøbe dem til *State Name* og *State Code*. Hvis du vil omdøbe tabellen, skal du blot skrive et nyt navn i feltet **Navn** i ruden **Forespørgselsindstillinger**. Lad os kalde tabellen *StateCodes*.

Nu da tabellen StateCodes er formet til formålet, kan vi kombinere disse to tabeller eller forespørgsler i én. Da de tabeller, vi har nu, er et resultat af de forespørgsler, vi anvendte på dataene, refereres der ofte til dem som *forespørgsler*.

Der er to primære måder at kombinere forespørgsler på – *fletning* og *tilføjelse*.

Når du har en eller flere kolonner, som du vil føje til en anden forespørgsel, skal du **flette** forespørgslerne. Når du har flere rækker med data, som du vil føje til en eksisterende forespørgsel, skal du **tilføje** forespørgslen.

I dette tilfælde vil vi flette forespørgsler. Start med at vælge den forespørgsel i Forespørgselseditor, som den anden forespørgsel skal flettes *ind i*, hvilket i dette tilfælde er *RetirementStats*. Vælg derefter **Kombiner \> Flet forespørgsler** under fanen **Hjem** på båndet.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

Du kan blive bedt om at angive beskyttelsesniveauer for at sikre, at dataene kombineres uden at medtage eller overføre data, du ikke ville overføre.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeriesb.png)

Vinduet **Flet** åbnes, og vi bliver bedt om at vælge, hvilken tabel vi vil flette med den valgte tabel, og derefter de tilsvarende kolonner, der skal bruges til fletningen. Vælg State i tabellen *RetirementStats* (forespørgsel), og vælg derefter forespørgslen *StateCodes* (let i dette tilfælde, da der kun er én anden forespørgsel – når du opretter forbindelse til mange forskellige datakilder, er der mange forespørgsler at vælge imellem). Når vi vælger de korrekte matchende kolonner – **State** fra *RetirementStats* og **State Name** fra *StateCodes* – ser vinduet **Flet** ud som følger, og knappen **OK** er aktiveret.

![](media/desktop-shape-and-combine-data/shapecombine_merge.png)

Den nye kolonne **NewColumn** oprettes i slutningen af forespørgslen, som er indholdet af tabellen (forespørgsel), der blev flettet med den eksisterende forespørgsel. Alle kolonner fra den flettede forespørgsel samles i **NewColumn**, men du kan vælge at **udvide** tabellen og inkludere de ønskede kolonner.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Hvis du vil udvide den flettede tabel og vælge, hvilke kolonner der skal inkluderes, skal du vælge udvidelsesikonet (![Udvid](media/desktop-shape-and-combine-data/icon.png)). Vinduet **Udvid** vises.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

I dette tilfælde vil vi kun have kolonnen **State Code**, så vi vælger kun den pågældende kolonne og vælger derefter **OK**. Jeg fjerner markeringen i afkrydsningsfeltet fra Brug det oprindelige kolonnenavn som præfiks, da vi ikke skal bruge det. Hvis vi bevarer markeringen, vil den flettede kolonne blive navngivet **NewColumn.State Code** (det oprindelige kolonnenavn, eller **NewColumn** efterfulgt af et punktum, hvorefter kolonnenavnet føres ind i forespørgslen).

>[!NOTE]
>Vil du prøve at importere tabellen **NewColumn**? Du kan eksperimentere lidt, og hvis du ikke kan lide resultatet, skal du bare slette dette trin på listen **Anvendte trin** i ruden **Forespørgselsindstillinger**. Din forespørgsel vender tilbage til tilstanden før trinnet **Udvid** blev anvendt. Du har mulighed for at prøve det af, så mange gange du har lyst, indtil udvidelsesprocessen ser ud, som den skal.

Vi har nu en enkelt forespørgsel (tabel), der kombinerer to datakilder, som er blevet formet efter vores behov. Denne forespørgsel kan fungere som udgangspunkt for mange ekstra, interessante dataforbindelser – f.eks. boligomkostningsstatistikker, demografi eller jobmuligheder i en vilkårlig stat.

Vælg Luk og anvend under fanen **Hjem** for at anvende ændringerne og lukke Forespørgselseditor. Det transformerede datasæt vises i Power BI Desktop, hvor du nu kan bruge det til at oprette rapporter.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Næste trin
Du kan gøre mange forskellige ting med Power BI Desktop. Du kan finde flere oplysninger om funktionerne i følgende ressourcer:

* [Introduktion til Power BI Desktop](desktop-getting-started.md)
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Opret forbindelse til data i Power BI Desktop](desktop-connect-to-data.md)
* [Almindelige forespørgselsopgaver i Power BI Desktop](desktop-common-query-tasks.md)   
