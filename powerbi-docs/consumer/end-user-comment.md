---
title: Føj kommentarer til dashboards og rapporter
description: I dette dokument kan du se, hvordan du føjer kommentarer til et dashboard, en rapport eller en visualisering, og hvordan du bruger kommentarer til at føre samtaler med samarbejdspartnere.
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Consumer
ms.openlocfilehash: ee053fe000ad85b768ce3d451984f987e3c79e6f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96400747"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>Føj kommentarer til et dashboard eller en rapport

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Tilføj en personlig kommentar, eller start en samtale om et dashboard eller en rapport med dine kolleger. **Kommentar** funktionen er bare én af de måder, en *erhvervsbruger* kan samarbejde med sine kolleger på. 

![video om kommentarer](media/end-user-comment/comment.gif)

> [!NOTE]
> Hvis du samarbejder med andre og bl.a. føjer kommentarer til delte rapporter, kræver det en Power BI Pro-licens, eller at indholdet hostes i Power BI Premium-kapacitet. [Hvilken licenstype har jeg?](end-user-license.md)

## <a name="how-to-use-the-comments-feature"></a>Sådan bruges kommentarfunktionen
Kommentarer kan føjes til et helt dashboard, til individuelle visualiseringer på et dashboard, til en rapportside, til en sideinddelt rapport og til individuelle visualiseringer på en rapportside. Tilføj en generel kommentar eller en kommentar, der er målrettet bestemte kolleger.  

Når du tilføjer en kommentar i en rapport, henter Power BI de aktuelle værdier for filter og udsnit og opretter et [bogmærke](end-user-bookmarks.md). Det betyder, at når du vælger eller reagerer på en kommentar, så kan en rapportside eller en visualisering i rapporten blive ændret for at vise dig den filtrerede værdi eller det udsnit, der var aktivt, da kommentaren blev tilføjet.  

![video om rapport med filtre](media/end-user-comment/power-bi-comment.gif)

Hvorfor er det vigtigt? Forestil dig, at en kollega har anvendt et filter, der viste en interessant indsigt, som vedkommende vil dele med teamet. Hvis filteret ikke er valgt, giver kommentaren måske ikke mening.

Hvis du bruger en sideinddelt rapport, kan du kun angive en generel kommentar om din rapport.  Det er ikke muligt at angive kommentarer på de enkelte visualiseringer i sideinddelte rapporter.

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>Føj en generel kommentar til et dashboard eller en rapport
Processen til tilføjelse af kommentarer til et dashboard eller en rapport er den samme.  I dette eksempel bruger vi et dashboard. 

1. Åbn et Power BI-dashboard eller en rapport, og vælg ikonet **Kommentarer**. Herefter åbnes dialogboksen Kommentarer.

    ![ikonet kommentarer på menulinjen](media/end-user-comment/power-bi-comment-icon.png)

    Her kan vi se, at opretteren af dashboardet allerede har tilføjet en generel kommentar.  Alle, der har adgang til dette dashboard, kan se denne kommentar.

    ![Skærmbillede af dashboardet, hvor afsnittet Kommentarer er valgt](media/end-user-comment/power-bi-first-comments.png)

2. Hvis du vil besvare kommentaren, skal du vælge **Besvar**, skrive dit svar og vælge **Send**.  

    ![Skærmbilledet Vælg svar](media/end-user-comment/power-bi-comments-reply.png)

    Power BI sender som standard dit svar til den kollega, der begyndte kommentartråden, i dette tilfælde Aaron. 

    ![Kommentar med svar](media/end-user-comment/power-bi-respond.png)

 3. Hvis du vil tilføje en kommentar, der ikke er en del af en eksisterende tråd, skal du angive din kommentar i det øverste tekstfelt.

    ![Skærmbillede, der viser ny tråd](media/end-user-comment/power-bi-new-commenting.png)

    Kommentarerne til dette dashboard ser nu sådan ud.

    ![Samtale med kommentarer](media/end-user-comment/power-bi-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>Føj en kommentar til en specifik visualisering på et dashboard eller i en rapport
Ud over at du kan føje kommentarer til et helt dashboard eller en hel rapport, kan du også føje kommentarer til et enkelt dashboardfelt eller en enkelt visualisering i en rapport. Processerne er ens, og i dette eksempel bruger vi en rapport.

1. Peg på visualiseringen, og vælg **Flere handlinger** (...).    
2. Vælg **Tilføj en kommentar** på rullelisten.

    ![Tilføj en kommentar er førstevalg](media/end-user-comment/power-bi-comment-reports.png)  

3.  Dialogboksen **Kommentarer** åbnes, og de andre visualiseringer på siden nedtones. Dette visuelle element har endnu ikke nogen kommentarer. 

    ![Skærmbillede, hvor visualiseringen er valgt, og dialogboksen Kommentarer er åben](media/end-user-comment/power-bi-comments-column.png)  

4. Skriv din kommentar, og vælg derefter **Post**.

    ![Dialogboksen Kommentarer med en ny meddelelse](media/end-user-comment/power-bi-comment-spikes.png)  

    - Hvis du vælger en kommentar på en rapportside, som oprindeligt var skrevet til en visualisering, så fremhæves denne visualisering (se nedenfor).

    - På et dashboard viser diagramikonet ![kommentar med diagramikon](media/end-user-comment/power-bi-comment-chart-icon.png) os, at der er knyttet en kommentar til en specifik visualisering. Kommentarer, der gælder for hele dashboardet, har ikke et særligt ikon. Når du vælger diagramikonet, fremhæves den relaterede visualisering på dashboardet.
    

    ![relateret visuelt element, der er fremhævet](media/end-user-comment/power-bi-highlights.png)

5. Vælg **Luk** for at vende tilbage til dashboardet eller rapporten.

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>Få dine kollegers opmærksomhed ved hjælp af @-tegnet
Uanset om du opretter en kommentar til et dashboard, en rapport, et felt eller en visualisering, kan du få dine kollegers opmærksomhed ved at bruge "\@"-symbolet.  Når du skriver "\@"-symbolet, åbnes der en rulleliste i Power BI, hvor du kan søge efter og vælge personer i din organisation. Bekræftede navne med "\@"-symbolet foran vises med blå skrift. @mentioned-personerne modtager straks en mail i deres indbakke, og hvis de bruger en Power BI-mobilapp, modtager de en pushmeddelelse på deres enhed. De kan åbne kommentaren direkte fra meddelelsen, få vist dataene og svare i overensstemmelse hermed.

Her er en samtale, jeg har med visualiserings *designeren*. De bruger @-symbolet til at sikre, at jeg ser kommentaren. Jeg modtager en meddelelse og vælger linket for at åbne dette dashboard og den relevante samtale.  

![Tilføj en kommentaromtale](media/end-user-comment/power-bi-comment-conversation.png)  

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

- Bogmærker optages ikke, når du besvarer en samtale. Kun den første kommentar i en samtale opretter et bogmærke.
- Hvis du bruger en sideinddelt rapport, kan du kun angive en generel kommentar om din rapport.  Det er ikke muligt at angive kommentarer på de enkelte visualiseringer i sideinddelte rapporter.

## <a name="next-steps"></a>Næste trin
Tilbage til [visualiseringer til erhvervsbrugere](end-user-visualizations.md)    
[Vælg en visualisering for at åbne en rapport](end-user-report-open.md)
