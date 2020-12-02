---
title: Brug af skabeloner i Power BI Desktop
description: Opret og del skabeloner i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 08/16/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 71e7167be5f39868b36211fd906cccf482cada5c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412707"
---
# <a name="create-report-templates-for-power-bi-desktop"></a>Opret rapportskabeloner til Power BI Desktop

Med **Power BI Desktop** kan du oprette overbevisende rapporter til deling af indsigt på tværs af hele organisationen. Du kan bruge **skabeloner** i Power BI Desktop til at effektivisere dit arbejde ved at oprette en rapportskabelon, der er baseret på en eksisterende skabelon, som du eller andre brugere i din organisation kan bruge som udgangspunkt for en ny rapports layout, en datamodel og forespørgsler. Skabeloner i **Power BI Desktop** hjælper dig med at komme hurtigt i gang og standardisere oprettelsen af rapporter.

![Eksportér rapport som en skabelon](media/desktop-templates/desktop-templates-01.png)

## <a name="creating-templates"></a>Oprettelse af skabeloner

Power BI-rapportskabeloner indeholder følgende oplysninger fra den rapport, de blev genereret ud fra:

* **Rapportsider**, visualiseringer og andre visuelle elementer
* **Datamodeldefinitionen**, herunder skamaet, relationer, målinger og andre modeldefinitionsartefakter
* Alle **forespørgselsdefinitioner**, f. eks. forespørgsler, forespørgselsparametre og andre forespørgselselementer

Rapportens data er *ikke* inkluderet i skabelonerne. 

Rapportskabeloner bruger filtypenavnet .PBIT (mens Power BI Desktop-rapporter bruger filtypenavnet .PBIX). 

Du opretter en rapportskabelon ved at vælge **Fil > Ekportér > Power BI-skabelon** i menuen, hvilket åbner følgende vindue, hvor du bliver bedt om at give en beskrivelse af skabelonen. I dette eksempel er vores beskrivelse af skabelonen *Skabelon for månedlig salgsrapport.*

![Dialogboks til beskrivelse af skabelon](media/desktop-templates/desktop-templates-02.png)

Vælg **OK**, hvorefter du bliver bedt om at angive en filplacering, hvor du vil gemme PBIT-skabelonfilen.

![Skabelonplacering](media/desktop-templates/desktop-templates-03.png)

Herefter er din Power BI-rapportskabelon oprettet på den filplacering, du har angivet, med filtypenavnet PBIT.

> [!NOTE]
> Power BI-rapportskabelonfiler er generelt meget mindre end en Power BI Desktop-rapport, fordi skabeloner ikke indeholder data, men udelukkende rapportdefinitionerne. 

## <a name="using-templates"></a>Brug af skabeloner

Hvis du vil anvende en Power BI-rapportskabelon, skal du åbne den i Power BI Desktop og begynde at bruge den. Du kan åbne Power BI-rapportskabeloner på to måder:

* Dobbeltklik på en vilkårlig PBIT-fil for automatisk at åbne Power BI Desktop og indlæse skabelonen
* Vælg **Fil > Importér > Power BI-skabelon** i Power BI Desktop

![Importér en skabelon](media/desktop-templates/desktop-templates-04.png)

Når du åbner en rapportskabelon, åbnes en dialogboks med værdier for de parametre, der er defineret i den rapport, som skabelonen er baseret på. Hvis en rapport f.eks. analyserer kunder på baggrund af land eller område og har parameteren *Land* til at angive kundens base, vises en prompt, hvor du kan vælge en værdi for *Land* på listen over de værdier, der blev angivet, da parameteren blev defineret. 

![Angiv parametre for en skabelon](media/desktop-templates/desktop-templates-05a.png)

Når du har angivet de påkrævede parametre, bliver du bedt om at angive placeringen af de underliggende data, der er knyttet til rapporten. Den aktuelle opretter af en rapport kan derefter oprette forbindelse til data på baggrund af sine legitimationsoplysninger.

![Angiv dataplacering for en skabelon](media/desktop-templates/desktop-templates-05.png)

Når der er angivet parametre og data, oprettes en rapport med alle de sider, visualiseringer, datamodelartefakter og forespørgsler, der var en del af den rapport, som skabelonen er baseret på. 

Det er det hele. Det er nemt at oprette og bruge rapportskabeloner i Power BI Desktop, så du nemt kan genskabe overbevisende layout og andre rapportaspekter og dele dem med andre.

## <a name="next-steps"></a>De næste trin
Du er måske også interesseret i at få mere at vide om **forespørgselsparametre**:
* [Bruger du forespørgselsparametre i Power BI Desktop?](/power-query/power-query-query-parameters)

Herudover er der mange andre forskellige ting, du kan gøre med Power BI Desktop. Du kan finde flere oplysninger om funktionerne i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Oversigt over forespørgsler i Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datatyper i Power BI Desktop](../connect-data/desktop-data-types.md)
* [Udform og kombiner data med Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Almindelige forespørgselsopgaver i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)