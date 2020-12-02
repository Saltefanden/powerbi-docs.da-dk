---
title: Modelvisning i Power BI Desktop
description: Modelvisning i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/17/2020
LocalizationGroup: Model your data
ms.openlocfilehash: b257fc5af97cb16798cc27bdbdb92c1b63a65181
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413765"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Arbejde med modelvisning i Power BI Desktop

I *Modelvisning* vises alle tabellerne, kolonnerne og relationerne i din model. Denne visning kan være særligt nyttig, når din model indeholder komplekse relationer mellem mange tabeller.

Vælg ikonet **Model** i siden af vinduet for at få vist en visning af den eksisterende model. Hold markøren over en relationslinje for at få vist de kolonner, der bruges.

![Modelvisning, Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

I figuren har tabellen *Stores* en *StoreKey*-kolonne, der er relateret til tabellen *Salg*, som også har en *StoreKey*-kolonne. De to tabeller har en relation af typen *mange til én* (\*: 1). En pil midt på linjen viser retningen af kontekstflowet for filteret. De dobbelte pile betyder, at den tværgående filterretning er angivet til *Begge*.

Du kan dobbeltklikke på en relation for at åbne den i dialogboksen **Rediger relationer**. Du kan finde flere oplysninger om relationer under [Opret og administrer relationer i Power BI Desktop](desktop-create-and-manage-relationships.md).
