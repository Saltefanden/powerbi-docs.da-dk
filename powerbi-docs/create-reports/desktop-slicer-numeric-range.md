---
title: Brug udsnitsværktøjet til numeriske områder i Power BI
description: Få mere at vide om, hvordan du kan bruge et udsnitsværktøj til at begrænse resultatet til numeriske intervaller i Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: zIZPA0UrJyA
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 59e88818adee9aaf893d9f32fe96386c3f7ac47e
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565788"
---
# <a name="use-the-numeric-range-slicer-in-power-bi"></a>Brug udsnitsværktøjet til numeriske områder i Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Med udsnitsværktøjet til numerisk område kan du anvende forskellige filtre på en numerisk kolonne i din datamodel. Der er tre muligheder for at filtrere dine numeriske data: mellem tal, mindre end eller lig med et tal samt større end eller lig med et tal. Denne enkle teknik er en effektiv måde at filtrere dine data på.

![Visual med udsnitsværktøjet til numerisk område](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="video"></a>Video

I denne video gennemgås det, hvordan du opretter et udsnitsværktøj til numeriske områder.

> [!NOTE]
> I denne video bruges en ældre version af Power BI Desktop.

<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe> 


## <a name="add-a-numeric-range-slicer"></a>Tilføj udsnitsværktøj til numeriske områder

Du kan bruge udsnitsværktøjet til numerisk område ligesom ethvert andet udsnitsværktøj. Du skal blot oprette et **udsnitsværktøj**, der er synligt for din rapport, og derefter vælge en numerisk værdi for **Felt**-værdien. På følgende billede er feltet **LineTotal** markeret.

![Opret et numerisk interval-udsnitsværktøj](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Hvis du vælger pil ned i øverste højre hjørne af udsnitsværktøjet til numerisk område, vises der en menu.

![Menu for udsnitsværktøj til numerisk område](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

I forbindelse med det numeriske område kan du vælge mellem følgende tre muligheder:

* **Mellem**
* **Mindre end eller lig med**
* **Større end eller lig med**

Når du vælger **Mellem** i menuen, vises der en skyder. Du kan bruge skyderen til at vælge numeriske værdier, der ligger mellem tallene. Nogle gange gør kornetheden af skyderen det svært, at ramme det præcise tal. Du kan også bruge skyderen og skrive den ønskede værdi i et af felterne. Denne indstilling er praktisk, når du vil se et udsnit af bestemte tal.

På følgende billede er rapportsiden filtreret for **LineTotal**-værdier i området mellem 2.500,00 og 6.000,00.

![Udsnitsværktøjet til numerisk område med Mellem](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

Når du vælger **Mindre end eller lig med**, forsvinder skyderens venstre håndtag (lavere værdi), og du kan kun justere skyderens øvre grænse. På følgende billede angiver vi skyderen til maksimalt 5928.19.

![Udsnitsværktøjet til numerisk område med Mindre end](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Sidst men ikke mindst, hvis du vælger **Større end eller lig med**, forsvinder skyderens højre håndtag (højere værdi). Du kan derefter justere den lavere værdi som vist på følgende billede. Nu vises der kun elementer, der har en **LineTotal**, som er større end eller lig med 4.902,99, i visualiseringerne på rapportsiden.

![Udsnitsværktøjet til numerisk område med Større end](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Fastgør til hele tal ved hjælp af udsnitsværktøj til numerisk område

Et udsnitsværktøj til et numerisk område fastgøres til heltal, hvis datatypen for det underliggende felt er *Heltal*. Med denne funktion kan udsnitsværktøjet nemt afstemmes til heltal. I feltet *Decimaltal* kan du angive eller vælge brøkdele af et tal. Den formatering, der anvendes i tekstfeltet, matcher den formatering, der er anvendt i feltet, selvom du kan angive eller vælge mere præcise tal.

## <a name="display-formatting-with-the-date-range-slicer"></a>Vis formatering med udsnitsværktøjet til datoområder

Når du bruger et udsnit til at få vist eller angive et område for datoer, vises datoerne i det *korte datoformat*. Landestandarden for brugerens browser eller operativsystem bestemmer datoformatet. Dette er derfor det viste format, uanset hvilke indstillinger for datatype der er for den underliggende data eller model.

Du kan f. eks. have et langt datoformat for den underliggende datatype. I dette tilfælde formaterer et datoformat såsom *dddd, d MMMM åååå* en dato i andre visualiseringer eller under andre forhold som *onsdag, 14. marts 2001*. Men i udsnitsværktøjet til datoområde vises denne dato i udsnittet som *14-03-2001.*

Visning af det korte datoformat i udsnitsværktøjet sikrer, at længden af strengen forbliver konsistent og kompakt i udsnitsværktøjet.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Følgende begrænsninger og overvejelser gælder for udsnitsværktøjet til numerisk område:

* Udsnitsværktøjet til numerisk område filtrerer alle underliggende rækker i dataene, men ingen samlede værdier. Lad os f.eks. sige, at du bruger feltet *Salgsbeløb*. Udsnitsværktøjet filtrerer derefter hver transaktion baseret på salgsbeløbet og ikke summen af salgsbeløbet for hvert enkelt datapunkt i en visualisering.
* Det fungerer i øjeblikket ikke sammen med målinger.
* Du kan skrive et vilkårligt tal i et numerisk udsnitsværktøj, selvom det er uden for området af værdier i den underliggende kolonne. Denne indstilling giver dig mulighed for at konfigurere filtre, hvis du ved, at dataene kan blive ændret i fremtiden.
* Udsnittet til datoområdet muliggør en hvilken som helst datoværdi, også selvom den ikke findes i den underliggende datokolonne.
