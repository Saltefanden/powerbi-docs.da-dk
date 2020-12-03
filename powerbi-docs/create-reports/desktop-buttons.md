---
title: Brug knapper i Power BI
description: Du kan tilføje knapper i Power BI-rapporter, der får dine rapporter til at fungere som apps, og sørge for, at brugerne bliver mere involveret.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/21/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 77f16bedb45b0730a7007da19a427b1832bc9969
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414455"
---
# <a name="use-buttons-in-power-bi"></a>Brug knapper i Power BI
Ved hjælp af **knapper** i Power BI kan du oprette rapporter, der fungerer på samme måde som apps, og dermed skabe et indtagende miljø, så brugerne kan holde over, klikke og yderligere interagere med Power BI-indhold. Du kan føje knapper til rapporter i **Power BI Desktop** og i **Power BI-tjenesten**. Når du deler dine rapporter i Power BI-tjeneste, får brugerne en applignende visning.

![Knapper i Power BI](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>Opret knapper i rapporter

### <a name="create-a-button-in-power-bi-desktop"></a>Opret en knap i Power BI Desktop

Du opretter knapper i **Power BI Desktop** på følgende måde: Vælg **Knapper** på båndet **Indsæt**, hvorefter der vises en rullemenu, hvor du kan vælge den ønskede knap, som vist på følgende billede. 

![Tilføj kontrolelementet knap i Power BI Desktop](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Opret en knap i Power BI-tjenesten

Hvis du vil oprette en knap, skal du åbne rapporten i redigeringsvisning i **Power BI-tjenesten**. Vælg **Knapper** i den øverste menulinje, hvorefter der vises en rullemenu, hvor du kan vælge den ønskede knap, som vist på følgende billede. 

![Tilføj et knapkontrolelement i Power BI-tjenesten](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>Tilpas en knap

Uanset om du opretter knappen i Power BI Desktop eller i Power BI-tjenesten, er resten af processen den samme. Når du vælger knappen på rapportcanvasset, kan du i ruden **Visualiseringer** se mange måder, som du kan tilpasse knappen på, så den passer til dine behov. Du kan f.eks. slå **Knaptekst** til eller fra ved at skifte skyderen på det pågældende kort i ruden **Visualiseringer**. Du kan bl.a. også ændre ikonet for knappen, udfyldningen af knappen, titlen eller den handling, som udføres, når brugerne vælger knappen i en rapport.

![Formatér en knap i en Power BI-rapport](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Angiv egenskaber for knappen, når den er inaktiv, når der holdes over den, eller når den vælges

Der er tre tilstande for knapper i Power BI: standard (den måde de vises på, når der ikke holdes over dem, eller når de ikke vælges), når der holdes over dem, eller når de vælges (hvilket ofte omtales som "når der *klikkes* på dem"). Mange af kortene i ruden **Visualiseringer** kan ændres enkeltvist på baggrund af de tre tilstande, hvilket medfører masser af fleksibilitet til at tilpasse knapperne.

På følgende kort i ruden **Visualiseringer** kan du justere formateringen eller funktionsmåden af en knap på baggrund af de tre tilstande:

* Knaptekst
* Ikon
* Kontur
* Udfyldning

For hver tilstand kan du vælge, hvordan knappes skal fremstå. Udvid ét af disse kort, og vælg den rullemenu, der vises øverst på kortet. På følgende billede kan du se, at kortet **Ikon** er udvidet med rullemenuen valgt for at vise de tre tilstande.

![Tre tilstande for en knap i en Power BI-rapport](media/desktop-buttons/power-bi-button-format.png)

## <a name="select-the-action-for-a-button"></a>Vælg handlingen for knappen

Du kan vælge, hvilken handling der udføres, når en bruger vælger en knap i Power BI. Du får adgang til indstillingerne for knappens handlinger via kortet **Handling** i ruden **Visualiseringer**.

![Handlinger for en knap i Power BI](media/desktop-buttons/power-bi-button-action.png)

Her er indstillingerne for knaphandlinger:

- **Tilbage** sender brugeren tilbage til den forrige side i rapporten. Dette er nyttigt til sider med detaljeadgang.
- **Bogmærke** viser den rapportside, der er knyttet til et bogmærke, som er defineret for den aktuelle rapport. Få mere at vide om [bogmærker i Power BI](desktop-bookmarks.md). 
- **Detaljeadgang** sender brugeren til en side med detaljeadgang, der er filtreret efter deres valg, uden at der bruges bogmærker. Få mere at vide om, [detaljeaniveauknapper i rapporter](desktop-drill-through-buttons.md).
- **Sidenavigation** sender brugeren til en anden side i rapporten, også uden at der bruges bogmærker. Se [Opret sidenavigation](#create-page-navigation) i denne artikel for at få flere oplysninger.
- **Spørgsmål og svar** åbner et vindue med **stifinder til Spørgsmål og svar**. 

For nogle knapper er der automatisk valgt en standardhandling. For knappen **Spørgsmål og svar** er **Spørgsmål og svar** f.eks. valgt automatisk som standardhandling. Du kan få mere at vide om **Stifinder med spørgsmål og svar** i [dette blogindlæg](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

Du kan prøve eller teste de knapper, du opretter for din rapport, ved hjælp af *Ctrl + klik* på den knap, du vil bruge. 

## <a name="create-page-navigation"></a>Opret sidenavigation

Med **handlingstypen** **Sidenavigation** kan du hurtigt oprette en hel navigationsoplevelse uden at skulle gemme eller administrere bogmærker.

Hvis du vil konfigurere en sidenavigationsknap, skal du oprette en knap med **Sidenavigation** som handlingstype og vælge **destination** ssiden.

![Handlingen Sidenavigation](media/desktop-buttons/power-bi-page-navigation.png)

Du kan oprette en brugerdefineret navigationsrude og føje navigationsknapperne til den. Du undgår at skulle redigere og administrere bogmærker, hvis du vil ændre, hvilke sider der skal vises i navigationsruden.

![Opret en navigationsside](media/desktop-buttons/power-bi-build-navigation-pane.png)

Derudover kan du oprette en betinget formatering af værktøjstippet, som du kan gøre med andre knaptyper.

## <a name="set-the-navigation-destination-conditionally"></a>Indstil betingelserne for navigationsdestinationen

Du kan bruge betinget formatering til at angive navigationsdestinationen baseret på resultatet af en måling. Det kan f.eks. være, at du vil spare plads på dit rapportlærred ved at have en enkelt knap til at navigere til forskellige sider, der er baseret på brugerens valg.

:::image type="content" source="media/desktop-buttons/button-navigate-go.png" alt-text="Naviger med en Start-knap":::
 
Hvis du vil oprette det eksempel, der er vist ovenfor, skal du starte med at oprette en tabel med en enkelt kolonne med navnene på navigationsdestinationerne:

:::image type="content" source="media/desktop-buttons/button-create-table.png" alt-text="Opret en tabel":::

Power BI bruger den nøjagtige strengforekomst til at angive destinationen for detaljeadgang. Du skal derfor dobbelttjekke, at de angivne værdier justeres præcist i forhold til navnene på detaljeadgangssiderne.

Når du har oprettet tabellen, kan du føje den til siden som et enkelt udsnit:

:::image type="content" source="media/desktop-buttons/button-navigate-slicer.png" alt-text="Naviger til udsnit":::

Opret derefter en sidenavigationsknap, og vælg indstillingen for betinget formatering for destinationen:

:::image type="content" source="media/desktop-buttons/button-set-page-nav-destination.png" alt-text="Sidenavigationsknap":::
 
Vælg navnet på den kolonne, du har oprettet, i dette tilfælde **Vælg en destination**:

:::image type="content" source="media/desktop-buttons/button-select-destination.png" alt-text="Vælg en destination":::

Nu kan knappen navigere til forskellige sider afhængigt af brugerens valg.

:::image type="content" source="media/desktop-buttons/button-navigate-go.png" alt-text="Naviger med en Start-knap":::
 
### <a name="shapes-and-images-for-navigation"></a>Figurer og billeder til navigation

Handlingen sidenavigation understøttes for former og billeder, ikke kun knapper. Her er et eksempel på brug af en af de indbyggede former:

:::image type="content" source="media/desktop-buttons/button-navigation-arrow.png" alt-text="Brug en pil til navigation":::
 
Her er et eksempel på brug af et billede:

:::image type="content" source="media/desktop-buttons/button-navigation-image.png" alt-text="Brug et billede til navigation":::
 
## <a name="buttons-support-fill-images"></a>Knapper understøtter udfyldningbilleder

Knapper understøtter udfyldningbilleder. Du kan tilpasse knappens udseende og funktionsmåde med udfyldningsbilleder kombineret med de indbyggede knaptilstande: standard, peg, på tryk og deaktiveret (til detaljeadgang).

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-fill-images.png" alt-text="Udfyldningsbilleder af detaljeniveauknap":::

Indstil **udfyldning** på **Til**, og opret derefter billeder for de forskellige tilstande.

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-fill-state-settings.png" alt-text="Indstillinger for udfyldningsbilleder":::


## <a name="next-steps"></a>Næste trin
Du kan finde flere oplysninger om de funktioner, der er ens eller interagerer med knapper, i følgende artikler:

* [Brug detaljeadgang i Power BI-rapporter](desktop-drillthrough.md)
* [Brug bogmærker til at dele indsigt og oprette historier i Power BI](desktop-bookmarks.md)
* [Opret en detaljeniveauknap](desktop-drill-through-buttons.md)

