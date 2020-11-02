---
title: Design filtre i Power BI-rapporter
description: Du har god kontrol over rapportfilterets design og funktionalitet.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/23/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 358d0575c2de3297614bfed0656d953945b2ed13
ms.sourcegitcommit: 54e571a10b0fdde5cd6036017eac9ef228de5116
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/24/2020
ms.locfileid: "92502150"
---
# <a name="design-filters-in-power-bi-reports"></a>Design filtre i Power BI-rapporter

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Med den nye filteroplevelse har du god kontrol over rapportfilterets design og funktionalitet. Du kan formatere filtreringsruden, så den ser ud som resten af rapporten. Du kan låse og endda skjule filtre. Når du designer din rapport, kan du slet ikke længere se den gamle filtreringsrude i ruden Visualiseringer. Du kan udføre al redigering og formatering af dine filtre i en enkelt filtreringsrude. 

![Filteroplevelsen](media/power-bi-report-filter/power-bi-filter-new-look.png)

Her er nogle af de opgaver, som du som rapportdesigner kan udføre i den nye Filterrude:

- Tilføj og fjern felter, der kan filtreres efter. 
- Rediger filtertilstanden.
- Formatér og tilpas filtreringsruden, så den føles som en del af rapporten.
- Definer, om ruden Filtre skal være åben eller skjult som standard, når en forbruger åbner rapporten.
- Skjul hele filtreringsruden eller specifikke filtre, som forbrugerne af rapporten ikke skal se.
- Kontrollér og angiv også bogmærke for tilstanden Synlighed, Åben og Skjult for filtreringsruden.
- Lås filtre, som forbrugerne ikke må redigere.

Når forbrugerne læser en rapport, kan de pege på en hvilken som helst visualisering for at se en skrivebeskyttet liste over alle de filtre eller udsnit, der påvirker den pågældende visualisering.

![Liste over filtre for en visualisering](media/power-bi-report-filter/power-bi-filter-visual.png)

Læs om, [hvordan læsere af rapporten bruger filtre](../consumer/end-user-report-filter.md) i din rapport.

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Vis filtre for en visualisering i Læsetilstand

I Læsetilstand kan du holde markøren over filterikonet for en visualisering og se en pop op-filterliste med alle de filtre, udsnitsværktøjer m.m., der påvirker denne visualisering. Formateringen af pop op-filterlisten er den samme som formateringen af filtreringsruden.

![Filtre, der påvirker en visualisering](media/power-bi-report-filter/power-bi-filter-per-visual.png)

Her er de filtertyper, der vises i denne visning:

- Grundlæggende filtre
- Udsnit
- Tværgående fremhævning 
- Tværgående filtrering
- Avancerede filtre
- Top N-filtre
- Filtre for Relativ dato
- Udsnitsværktøjer til synkronisering
- Filtre for Inkluder/Ekskluder
- Filtre sendt via en URL-adresse

Læs mere om [interaktion med filtre i læsetilstand](../consumer/end-user-report-filter.md).

## <a name="build-the-filters-pane"></a>Opbyg filtreringsruden

Efter du har aktiveret den nye filtreringsrude, kan du se den til højre for den rapportside, der som standard er formateret på baggrund af de aktuelle rapportindstillinger. I filtreringsruden konfigurerer du, hvilke filtre du vil inkludere, og opdaterer eksisterende filtre. Filtreringsruden ser ud på samme måde for forbrugerne af din rapport, når du publicerer rapporten. 

1. Dine rapportforbrugere kan som standard se filtreringsruden. Hvis de ikke skal kunne se den, skal du vælge ikonet med øjet ud for **Filtre** .

    ![Ikon med øje for Power BI-filter](media/power-bi-report-filter/power-bi-filter-eye-icon.png)

2. Du begynder at bygge din filtreringsrude ved at trække de ønskede felter til filtreringsruden enten som en visualisering, en side eller som filtre på rapporteringsniveau.

Når du føjer en visualisering til et rapportlærred, tilføjer Power BI automatisk et filter i filtreringsruden for hvert felt i visualiseringen. 

## <a name="hide-the-filters-pane-while-editing"></a>Skjul ruden Filtre, mens du redigerer

Power BI Desktop har fået et nyt bånd, der er tilgængeligt som prøveversion. Med til/fra-knappen **Filtre** under fanen **Vis** kan du få vist eller skjule ruden Filtre. Denne funktion er nyttig, når du ikke bruger ruden Filtre og har brug for ekstra plads på skærmen. Denne tilføjelse justerer ruden Filtre med de andre ruder, som du kan åbne og lukke, f. eks. ruderne Bogmærker og Valg. 

![Vis eller skjul ruden Filtre under redigering](media/power-bi-report-filter/power-bi-filter-hide.png)

Denne indstilling skjuler kun ruden filtre i Power BI Desktop. Hvis du vil skjule ruden Filtre for dine slutbrugere, skal du i stedet vælge **øje** -ikonet ud for **Filtre** .

![Ikonet med øjet](media/power-bi-report-filter/power-bi-filter-eye.png) 

## <a name="lock-or-hide-filters"></a>Lås eller skjul filtre

Du kan låse eller skjule de enkelte filterkort. Hvis du låser et filter, kan forbrugerne af rapporten se, men ikke ændre det. Hvis du skjuler det, kan de slet ikke se det. Det er typisk nyttigt at skjule filterkort, hvis du har brug for at skjule filtre til dataoprydning, der udelukker Null-værdier eller uventede værdier. 

- I filtreringsruden skal du markere eller fjerne markeringen i ikonerne **Lås filter** eller **Skjul filter** på et filterkort.

   ![Skjul eller lås filtre](media/power-bi-report-filter/power-bi-filter-lock-hide.png)

I takt med at du slår disse indstillinger til og fra i filtreringsruden, kan du se ændringerne blive afspejlet i rapporten. Skjulte filtre vises ikke på pop op-filterlisten for en visualisering.

Du kan også konfigurere tilstanden for filtreringsruden, så den følger dine bogmærker i rapporten. Der kan angives bogmærke for tilstandene Åben, Lukket og Synlighed for ruden.
 
## <a name="format-the-filters-pane"></a>Formatér filtreringsruden

En stor del af filteroplevelsen er, at du kan formatere filtreringsruden, så den matcher udseendet af din rapport. Du kan også formatere filtreringsruden forskelligt for hver side i rapporten. Her er de elementer, du kan formatere: 

- Baggrundsfarve
- Baggrundsgennemsigtighed
- Kant slået til eller fra
- Kantfarve
- Skrifttype, farve og tekststørrelse for titel og overskrift

Du kan også formatere disse elementer for filterkort, afhængigt af om de er anvendt (indstillet til noget) eller tilgængelige (ryddet): 

- Baggrundsfarve
- Baggrundsgennemsigtighed
- Kant: til eller fra
- Kantfarve
- Skrifttype, farve og tekststørrelse
- Farve på inputfelt

### <a name="format-the-filters-pane-and-cards"></a>Formatér filtreringsruden og kortene

1. I rapporten skal du klikke på selve rapporten eller baggrunden ( *tapetet* ), og derefter skal du i ruden **Visualiseringer** vælge **Formatér** . 
    Du kan se formateringsindstillinger for rapportsiden, tapetet samt filtreringsruden og filterkort.

1. Udvid **ruden Filtre** for at angive farven på baggrunden, ikonet og den venstre kant, som skal komplementere rapportsiden.

    ![Udvid ruden Filtre](media/power-bi-report-filter/power-bi-format-filter-pane.png)

1. Udvid **Filterkort** for at angive farve og kant for **Tilgængelig** og **Anvendt** . Hvis du angiver forskellige farver for kortene Tilgængelig og Anvendt, er det oplagt, hvilke filtre der anvendes. 
  
    ![Udvid filterkort](media/power-bi-report-filter/power-bi-format-filter-cards.png)

## <a name="theming-for-filters-pane"></a>Temaer for ruden Filtre
Du kan nu ændre standardindstillingerne for ruden Filtre med temafilen. Her er et eksempel på kodestykke for et tema, der kan hjælpe dig i gang:

 
```
"outspacePane": [{ 

"backgroundColor": {"solid": {"color": "#0000ff"}}, 

"foregroundColor": {"solid": {"color": "#00ff00"}}, 

"transparency": 50, 

"titleSize": 35, 

"headerSize": 8, 

"fontFamily": "Georgia", 

"border": true, 

"borderColor": {"solid": {"color": "#ff0000"}} 

}], 

"filterCard": [ 

{ 

"$id": "Applied", 

"transparency": 0, 

"backgroundColor": {"solid": {"color": "#ff0000"}}, 

"foregroundColor": {"solid": {"color": "#45f442"}}, 

"textSize": 30, 

"fontFamily": "Arial", 

"border": true, 

"borderColor": {"solid": {"color": "#ffffff"}}, 

"inputBoxColor": {"solid": {"color": "#C8C8C8"}} 

}, 

{ 

"$id": "Available", 

"transparency": 40, 

"backgroundColor": {"solid": {"color": "#00ff00"}}, 

"foregroundColor": {"solid": {"color": "#ffffff"}}, 

"textSize": 10, 

"fontFamily": "Times New Roman", 

"border": true, 

"borderColor": {"solid": {"color": "#123456"}}, 

"inputBoxColor": {"solid": {"color": "#777777"}} 

}] 
```

## <a name="sort-the-filters-pane"></a>Sortér ruden Filtre

Brugerdefinerede sorteringsfunktioner er tilgængelige i filtreringsruden. Når du opretter rapporter, kan du trække og slippe filtre for at omarrangere dem i en hvilken som helst rækkefølge.

![Omarranger sorteringsrækkefølge for filtre](media/power-bi-report-filter/power-bi-filter-sort.gif)

Standardsorteringsrækkefølgen er alfabetisk for filtre. Hvis du vil starte en brugerdefineret sorteringstilstand, skal du bare trække et filter til en ny placering. Du kan kun sortere filtre inden for det niveau, som de gælder for – f.eks. et filter på visualiseringsniveau, sideniveau eller rapportniveau.

## <a name="improved-filters-pane-accessibility"></a>Forbedret tilgængelighed i filtreringsruden

Vi har forbedret navigation via tastaturet for filtreringsruden. Du kan bruge tabulator til at bevæge dig gennem alle dele af filtreringsruden og bruge genvejstasten på tastaturet eller Skift + F10 til at åbne genvejsmenuen.

![Tilgængelighed i filtreringsruden](media/power-bi-report-filter/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Omdøb filtre
Når du redigerer filtreringsruden, kan du dobbeltklikke på titlen for at redigere den. Det er nyttigt at kunne omdøbe filtre, hvis du vil opdatere filterkortet, så det giver mere mening for dine slutbrugere. Husk, at når du omdøber filterkortet, omdøbes det viste navn på feltet på feltlisten *ikke* . Det ændrer blot det viste navn, der bruges i filterkortet.

![Omdøb et filter](media/power-bi-report-filter/power-bi-filter-rename.png)

## <a name="filters-pane-search"></a>Søgning i ruden Filtre

Du kan bruge søgefunktionen i ruden Filtre rude til at søge efter titel på tværs af dine filterkort. Denne funktion er praktisk, hvis du har flere forskellige filterkort i ruden Filtre og har brug for hjælp til at finde de relevante.

![Søg efter et filter](media/power-bi-report-filter/power-bi-filter-search.png)

Du kan også formatere søgefeltet på samme måde, som du kan formatere de andre elementer i ruden Filtre.

![Formater søgefeltet](media/power-bi-report-filter/power-bi-filter-format-search.png)

Denne søgefunktion i ruden Filtre er som standard er slået til, men du kan også vælge at slå den til eller fra ved at vælge **Aktivér søgning for ruden Filtre** under indstillingerne for **rapporten** i dialogboksen **Indstillinger** .

![Slå søgning til eller fra](media/power-bi-report-filter/power-bi-enable-search-filter.png)

## <a name="restrict-changes-to-filter-type"></a>Begræns ændringer af filtertype

I afsnittet **Filtreringsoplevelse** under indstillinger for **rapporten** kan du styre, om brugere kan ændre filtertypen.

![Begræns ændring af filtertype](media/power-bi-report-filter/power-bi-enable-change-filter-type.png)

## <a name="allow-saving-filters"></a>Tillad lagring af filtre

Læserne af din rapport kan som standard gemme filtre for din rapport. Du kan vælge, at de ikke skal have tilladelse til at gemme filtre.

- Under indstillingerne for **rapporten** i dialogboksen **Indstillinger** under **Faste filtre** skal du vælge **Giv ikke slutbrugere tilladelse til at gemme filtre i denne rapport** .

    :::image type="content" source="media/power-bi-report-filter/power-bi-persistent-filters.png" alt-text="Skærmbillede af Giv ikke slutbrugere tilladelse til at gemme filtre i denne rapport.":::

## <a name="apply-filters-apply-button-preview"></a>Knappen Anvend filtre (prøveversion)

Du kan tilføje en enkelt **Anvend** -knap i filtreringsruden, så du og dine slutbrugere kan anvende alle filterændringer på én gang. Denne knap kan være en fordel, hvis du vil udsætte anvendelse af filterændringer. Du behøver kun at vente én gang, når du er klar til at anvende alle filter ændringerne i rapporten eller visualiseringerne.

:::image type="content" source="media/power-bi-report-filter/apply-filter-button.png" alt-text="Skærmbillede af Giv ikke slutbrugere tilladelse til at gemme filtre i denne rapport.":::

### <a name="turn-on-apply"></a>Slå Anvend til

Du kan vælge denne funktion på rapportniveau. Funktionen er dog som standard slået fra.

1. Gå til **Filer** > **Indstillinger** > **Indstillinger** > **Reduktion af forespørgsler** .

1. Vælg **Føj en enkelt Anvend-knap til filterruden for at anvende ændringer på én gang** .

    :::image type="content" source="media/power-bi-report-filter/turn-on-apply-filter-button.png" alt-text="Skærmbillede af Giv ikke slutbrugere tilladelse til at gemme filtre i denne rapport.":::

### <a name="format-the-apply-button"></a>Formatér knappen Anvend

Du kan i øjeblikket styre en del af formateringen af teksten **Anvend** til knappen. Angiv følgende indstillinger i afsnittet **Filterrude** i ruden **Formatér** :

- **Farve på skrifttype og ikon** styrer tekstfarven.
- **Tekststørrelse i sidehoved** styrer tekststørrelsen.
- **Skrifttypefamilie** styrer skrifttypen.

    :::image type="content" source="media/power-bi-report-filter/format-apply-filter.gif" alt-text="Skærmbillede af Giv ikke slutbrugere tilladelse til at gemme filtre i denne rapport.":::

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Ruden Filtre vises ikke i Publicer på internettet. Hvis du planlægger at udgive en rapport på internettet, skal du overveje at tilføje udsnit til filtrering.

## <a name="next-steps"></a>Næste trin

- [Sådan bruger du rapportfiltre](../consumer/end-user-report-filter.md)
- [Filtre og fremhævning i rapporter](power-bi-reports-filters-and-highlighting.md)
- [Forskellige typer af filtre i Power BI](power-bi-report-filter-types.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
