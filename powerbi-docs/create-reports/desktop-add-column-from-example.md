---
title: Tilføj en kolonne ud fra et eksempel i Power BI Desktop
description: Opret hurtigt en ny kolonne i Power BI Desktop ved hjælp af eksisterende kolonner som eksempler.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/16/2019
LocalizationGroup: Create reports
ms.openlocfilehash: f33a9f5656875825b70c7e51202431ba268fe86a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414501"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Tilføj en kolonne ud fra eksempler i Power BI Desktop
Med *tilføj kolonne fra eksempler* i Power-forespørgselseditor kan du føje nye kolonner til din datamodel ved at angive en eller flere eksempelværdier for de nye kolonner. Du kan oprette de nye kolonneeksempler fra et valg eller angive input baseret på alle eksisterende kolonner i tabellen.

![Skærmbillede af Power Query-editor, der viser, hvordan du tilføjer en kolonne fra eksempler i Power BI Desktop.](media/desktop-add-column-from-example/add-column-from-example_01.png)

Brug af *tilføj kolonne fra eksempel* kan du hurtigt og nemt oprette nye kolonner, og det er specielt nyttig i følgende situationer:

- Du kender de data, du gerne vil se i din nye kolonne, men du er i tvivl om, hvilken transformation eller samling af transformationer der vil give dette resultat.
- Du ved allerede, hvilke transformationer du har brug for, men du er i tvivl om, hvad du skal vælge i brugergrænsefladen for at aktivere dem.
- Du ved alt om de transformationer, du skal bruge ved hjælp af udtrykket *Brugerdefineret kolonne* i *M*-sprog, men en eller flere af disse udtryk er ikke tilgængelige i brugergrænsefladen.

Det er nemt og ligetil at tilføje en kolonne fra et eksempel. I de næste afsnit vises det, hvor nemt det er.

## <a name="add-a-new-column-from-examples"></a>Tilføj en ny kolonne fra eksempler

Hvis du vil hente eksempeldata fra Wikipedia, skal du vælge **Hent data** > **Web** fra fanen **Hjem** på båndet Power BI Desktop. 

![Hent data fra internettet](media/desktop-add-column-from-example/add-column-from-example_02.png)

Indsæt følgende URL-adresse i den dialogboks, der vises, og vælg **OK**: 

*https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States*

I dialogboksen **Navigator** skal du vælge tabellen **Stater i USA** og derefter vælge **Transformer data**. Tabellen åbnes i Power Query-editor.

Eller hvis du vil åbne data, der allerede er indlæst fra Power BI Desktop, skal du vælge **Rediger forespørgsler** på fanen **Hjem** på båndet. Dataene åbnes i Power-forespørgselseditor. 

![Vælg Rediger forespørgsler fra Power BI Desktop](media/desktop-add-column-from-example/add-column-from-example_05.png)

Når eksempeldataene åbnes i Power-forespørgselseditor, skal du vælge fanen **Tilføj kolonne** på båndet og derefter vælge **Kolonne fra eksempler**. Vælg selve ikonet **Kolonne fra eksempler** for at oprette kolonnen fra alle eksisterende kolonner, eller vælg rullepilen for at vælge mellem **Fra alle kolonner** eller **Fra markeringen**. I denne gennemgang skal du bruge **Fra alle kolonner**.

![Vælg Tilføj kolonne fra eksempler](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>Ruden Tilføj kolonne fra eksempler
Når du vælger **Tilføj kolonne** > **fra eksempler**, åbnes ruden **Tilføj kolonne fra eksempler** øverst i tabellen. Den nye **Kolonne 1** vises til højre for de eksisterende kolonner (det kan være nødvendigt at rulle for at se dem alle). Når du angiver dine eksempelværdier i tomme celler i **Kolonne 1**, opretter Power BI regler og transformationer, der matcher dine eksempler, og de bruges til at udfylde resten af kolonnen.

Læg mærke til, at **Kolonne fra eksempler** også vises som et **Anvendt trin** i ruden **Forespørgselsindstillinger**. Som det altid er tilfældet, vil Forespørgselseditor registrere dine transformationstrin og anvende dem til forespørgslen i rækkefølge.

![Ruden Tilføj kolonne fra eksempler](media/desktop-add-column-from-example/add-column-from-example_04.png)

Mens du skriver dit eksempel i den nye kolonne, får du i Power BI vist et eksempel på, hvordan resten af kolonnen vil se ud baseret på de transformationer, der oprettes. Hvis du for eksempel skriver *Alabama* i den første række, svarer det til værdien **Alabama** i den første kolonne i tabellen. Når du trykker på ENTER, udfylder Power BI resten af den nye kolonne baseret på den første kolonneværdi, og navngiver kolonnen **navn & forkortelse af postnummer[12] – Kopiér**.

Gå nu til rækken **Massachusetts [E]** i den nye kolonne, og slet **[E]** i strengen. Power BI registrerer ændringen og bruger eksemplet til at oprette en transformation. Power BI beskriver transformationerne i ruden **Tilføj kolonne fra eksempler** og omdøber kolonnen til **Tekst før afgrænser.** 

![Transformeret kolonne fra eksempler](media/desktop-add-column-from-example/add-column-from-example_06.png)

Mens du fortsætter med at angive eksempler, føjer Power-forespørgselseditor til transformationerne. Når du er tilfreds, skal du vælge **OK** for at bekræfte dine ændringer. 

Du kan omdøbe den nye kolonne, som du vil, ved at dobbeltklikke på kolonneoverskriften eller ved at højreklikke på den og vælge **Omdøb**. 

Se denne video for at se **Tilføj kolonne fra eksempler** i aktion ved hjælp af datakildeeksemplet: 

[Power BI Desktop: Tilføj kolonne fra eksempler](https://www.youtube.com/watch?v=-ykbVW9wQfw). 

## <a name="list-of-supported-transformations"></a>Liste over understøttede transformationer
Mange men ikke alle transformationer er tilgængelige, når du bruger **Tilføj kolonne fra eksempler**. På følgende liste vises alle understøttede transformationer:

**Generelt**

- Betinget kolonne

**Reference**
  
- Reference til en bestemt kolonne, herunder transformationer i form af trim, rydning og store/små bogstaver

**Transformationer**

- Kombiner (understøtter kombination af konstantstrenge og hele kolonneværdier)
- Erstat
- Længde
- Udtræk   
  - Første tegn
  - Sidste tegn
  - Område
  - Tekst før afgrænser
  - Tekst efter afgrænser
  - Tekst mellem afgrænsere
  - Længde
  - Fjern tegn
  - Behold tegn

> [!NOTE]
> Alle transformationer af *tekst* tager højde for et muligt behov for at anvende transformation til kolonneværdien i form af trim, rydning eller store/små bogstaver.

**Datotransformationer**

- Dag
- Dag i uge
- Navn på dag i uge
- Dag i år
- Måned
- Navn på måned
- Kvartal i år
- Uge i måned
- Uge i år
- År
- Alder
- Årets start
- Årets slutning
- Månedens start
- Månedens slutning
- Kvartalets start
- Dage i måned
- Kvartalets slutning
- Ugens start
- Ugens slutning
- Dag i måned
- Dagens start
- Dagens slutning

**Tidstransformationer**

- Hour
- Minute
- Second  
- Til lokal tid

> [!NOTE]
> I alle *dato*- og *tid*-transformationer tages der højde for et muligt behov for at konvertere kolonneværdien til *Dato* eller *Klokkeslæt* eller *DateTime*.

**Taltransformationer** 

- Absolut værdi
- Arcus cosinus
- Arcus sinus
- Arcus tangens
- Konverter til et tal
- Cosinus
- Kube
- Division
- Eksponent
- Fakultet
- Divider (heltal)
- Er lige
- Er ulige
- Ln
- Logaritme med grundtallet 10
- Modulus
- Multiplicer
- Rund ned
- Rund op
- Fortegn
- Sin.
- Kvadratrod
- Kvadrat
- Subtraher
- Sum
- Tangent
- Inddeling/intervaller
