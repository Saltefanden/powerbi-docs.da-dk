---
title: Tilføj en brugerdefineret kolonne i Power BI Desktop
description: Opret hurtigt en ny brugerdefineret kolonne i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 2074094f910efa36d449d8f54ada097d253bb2dd
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/30/2020
ms.locfileid: "91598908"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Tilføj en brugerdefineret kolonne i Power BI Desktop

I Power BI Desktop kan du nemt føje en ny brugerdefineret kolonne med data til din model ved hjælp af Query Editor. Med Forespørgselseditor kan du oprette og omdøbe din brugerdefinerede kolonne for at oprette [M-formelforespørgsler i PowerQuery](/powerquery-m/quick-tour-of-the-power-query-m-formula-language) og definere din brugerdefinerede kolonne. M-formelforespørgsler i PowerQuery indeholder et [indholdssæt med omfattende funktionsreference](/powerquery-m/power-query-m-function-reference). 

Når du opretter en brugerdefineret kolonne i Forespørgselseditor, tilføjer Power BI Desktop den som et **Anvendt trin** i **Forespørgselsindstillinger** i forespørgslen. Den kan ændres, flyttes eller redigeres når som helst.

![Skærmbillede, der viser dialogboksen Tilføj brugerdefineret kolonne.](media/desktop-add-custom-column/add-custom-column_01.png)

## <a name="use-query-editor-to-add-a-custom-column"></a>Brug Forespørgselseditor til at tilføje en brugerdefineret kolonne

Følg disse trin for at begynde at oprette en brugerdefineret kolonne:

1. Start Power BI Desktop, og indlæs nogle data.

2. Fra fanen **Start** på båndet skal du vælge **Rediger forespørgsler** og derefter vælge **Rediger forespørgsler** i menuen.

   ![Vælg Rediger forespørgsler](media/desktop-add-custom-column/add-column-from-example_02.png)

   Vinduet **Forespørgselseditor** vises. 

2. Under fanen **Tilføj kolonne** på båndet skal du vælge **Brugerdefineret kolonne**.

   ![Vælg brugerdefineret kolonne](media/desktop-add-custom-column/add-custom-column_02.png)

   Vinduet **Tilføj brugerdefineret kolonne** vises.

## <a name="the-add-custom-column-window"></a>Vinduet Tilføj brugerdefineret kolonne

Vinduet **Tilføj brugerdefineret kolonne** indeholder følgende funktioner: 
- En liste over tilgængelige kolonner på listen **Tilgængelige kolonner** til højre.

- Det indledende navn på din brugerdefinerede kolonne i feltet **Nyt kolonnenavn**. Du kan omdøbe denne kolonne.

- [M-formelforespørgsler i PowerQuery](/powerquery-m/power-query-m-function-reference) i feltet **Formel for brugerdefineret kolonne**. Du kan oprette disse forespørgsler ved at udarbejde den formel, som den nye brugerdefinerede kolonne er defineret på. 

   ![Skærmbillede, der viser dialogboksen Tilføj brugerdefineret kolonne, som indeholder tilgængelige kolonner, du kan vælge imellem.](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Opret formler til din brugerdefinerede kolonne

1. Vælg en kolonne på listen **Tilgængelige kolonner** til højre, og vælg derefter **Indsæt** under listen for at føje dem til formlen for den brugerdefinerede kolonne. Du kan også tilføje en kolonne ved at dobbeltklikke på den på listen.

2. Bemærk indikatoren nederst i vinduet **Tilføj brugerdefineret kolonne**, når du angiver formlen og opretter kolonnen. 

   Hvis der ikke er nogen fejl, får du vist en grøn markering, og meddelelsen *Der er ikke registreret nogen syntaksfejl*.

   ![Vellykket syntakskontrol på siden Tilføj brugerdefineret kolonne](media/desktop-add-custom-column/add-custom-column_04.png)

   Hvis der er en syntaksfejl, får du vist et gult advarselsikon sammen med et link til det sted, hvor fejlen opstod i din formel.

   ![Fejl på siden Tilføj brugerdefineret kolonne](media/desktop-add-custom-column/add-custom-column_05.png)

3. Vælg **OK**. 

   Power BI Desktop føjer din brugerdefinerede kolonne til modellen og føjer trinnet **Tilføjet brugerdefineret** til listen **Anvendte trin** i din forespørgsel under **Forespørgselsindstillinger**.

   ![Brugerdefineret kolonne føjet til Forespørgselsindstillinger](media/desktop-add-custom-column/add-custom-column_06.png)

4. Hvis du vil redigere din brugerdefinerede kolonne, skal du dobbeltklikke på trinnet **Tilføjet brugerdefineret** på listen **Anvendte trin**. 

   Vinduet **Tilføj brugerdefineret kolonne** vises med formlen for den brugerdefinerede kolonne, du har oprettet.

## <a name="use-the-advanced-editor-for-custom-columns"></a>Brug Avanceret editor til brugerdefinerede kolonner

Når du har oprettet din forespørgsel, kan du også bruge **Avanceret editor** til at redigere et hvilket som helst trin i din forespørgsel. Hvis du vil gøre dette, skal du følge disse trin:

1. I vinduet **Forespørgselseditor** skal du vælge fanen **Vis** på båndet. 

2. Vælg **Avanceret editor**.

   Siden **Avanceret editor** vises og giver dig fuld kontrol over din forespørgsel. 

   ![Siden Avanceret editor](media/desktop-add-custom-column/add-custom-column_07.png)

   
## <a name="next-steps"></a>De næste trin

- Du kan oprette en brugerdefineret kolonne på andre måder, f.eks. ved at oprette en kolonne baseret på eksempler, du angiver i Forespørgselseditor. Du kan finde flere oplysninger i [Tilføj en kolonne fra et eksempel i Power BI Desktop](desktop-add-column-from-example.md).

- Du kan finde oplysninger om M-reference i Power Query i [M-funktionsreference i Power Query](/powerquery-m/power-query-m-function-reference).