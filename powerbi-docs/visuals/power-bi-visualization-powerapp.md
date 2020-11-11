---
title: Integrer en ny Power App i en Power BI-rapport
description: Integrer en app, der bruger den samme datakilde, og som kan filtreres som andre rapportelementer
author: mihart
manager: kvivek
ms.reviewer: tapan maniar
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/01/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c46410caff373eb8474a4b687e834b822f2da8ac
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397524"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>Selvstudium: Integrer en Power Apps-visualisering i en Power BI-rapport

I dette selvstudie bruger du Power Apps-visualiseringen til at oprette en ny app, der er integreret i et eksempel på en Power BI-rapport. Denne app interagerer med andre visualiseringer i rapporten.

Hvis du ikke har et Power Apps-abonnement, skal du [oprette en gratis konto](https://make.powerapps.com/signup?redirect=marketing&email=), før du begynder.

I dette selvstudium lærer du, hvordan du kan:
> [!div class="checklist"]
> * Føj en Power Apps-visualisering til en Power BI-rapport
> * Arbejde i Power Apps for at oprette en ny app, der bruger data fra Power BI-rapporten.
> * Få vist og interagere med Power Apps-visualiseringen i rapporten.

## <a name="prerequisites"></a>Forudsætninger

* En af browserne [Google Chrome](https://www.google.com/chrome/browser/) eller [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge).
* Et [Power BI-abonnement](../fundamentals/service-self-service-signup-for-power-bi.md) med [Eksempel på analyse af salgsmuligheder](../create-reports/sample-opportunity-analysis.md#get-the-content-pack-for-this-sample) installeret.
* En forståelse af, hvordan du [opretter apps i Power Apps](/powerapps/maker/canvas-apps/data-platform-create-app-scratch) og [redigerer Power BI-rapporter](../create-reports/service-the-report-editor-take-a-tour.md).



## <a name="create-a-new-app"></a>Opret en ny app
Når du føjer Power Apps-visualiseringen til din rapport, starter den Power Apps Studio med en dynamisk dataforbindelse mellem Power Apps og Power BI.

1. Åbn rapporten Eksempel på analyse af salgsmuligheder, og vælg siden *Kommende salgsmuligheder*. 


2. Flyt og tilpas størrelsen på nogle af rapportfelterne for at gøre plads til en ny visualisering.

    ![Flyt og tilpas størrelsen på rapportfelter](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. I ruden Visualiseringer skal du vælge ikonet for Power Apps og derefter tilpasse størrelsen på visualiseringen, så den passer til den plads, du har lavet.

    ![Ruden Visualisering med ikonet for Power Apps valgt](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. I ruden **Felter** skal du vælge **Name** , **Product Code** og **Sales Stage**. 

    ![vælg felter](media/power-bi-visualization-powerapp/power-bi-fields.png)

4. I Power Apps-visualiseringen skal du vælge det Power Apps-miljø, hvor du vil oprette appen og derefter klikke eller trykke på **Opret ny**.

    ![Opret ny app](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    I Power Apps Studio kan du se, at der oprettes en grundlæggende app med et *galleri* , hvor der vises et af de felter, du valgte i Power BI.

    ![Power Apps åbnes](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  Tilpas størrelsen på galleriet, så det kun fylder halvdelen af skærmen. 

6. I venstre rude skal du vælge **Screen1** og derefter angive egenskaben **Fill** for skærmen til "LightBlue" (så det ser pænere ud i rapporten).

    ![farvepalet](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. Gør plads til et mærkatkontrolelement. 

    ![rediger galleridimensioner](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. Indsæt et kontrolelement af typen tekstmærkat under **galleri**.

   ![mærkatkontrolelement](media/power-bi-visualization-powerapp/power-bi-label.png)

7. Træk mærkatet til bunden af visualiseringen. Angiv egenskaben **Text** til `"Opportunity Count: " & CountRows(Gallery1.AllItems)`. Nu vises det samlede antal salgsmuligheder i datasættet.

    ![App med galleri, hvor størrelsen er tilpasset](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![App med et opdateret mærkat](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. Gem appen med navnet "Salgsmuligheder". 

    ![gem appen](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>Se appen i rapporten.
Appen er nu tilgængelig i Power BI-rapporten, og den interagerer med de øvrige visualiseringer, da den bruger den samme datakilde.

![App i Power BI-rapport](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

I Power BI-rapporten skal du vælge udsnittet **Jan** , som filtrerer hele rapporten inklusive dataene i appen.

![filtreret rapport](media/power-bi-visualization-powerapp/power-bi-last.png)

Bemærk, at det viste antal salgsmuligheder i appen stemmer overens med tallet øverst til venstre i rapporten. Du kan vælge andre elementer i rapporten, hvorefter dataene i appen opdateres.


## <a name="clean-up-resources"></a>Fjern ressourcer
Hvis du ikke længere vil bruge Eksempel på analyse af salgsmuligheder, kan du slette dashboardet, rapporten og dataarket.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser
Du kan finde oplysninger om fejlfinding i [Visualisering af Power Apps til Power BI](/powerapps/maker/canvas-apps/powerapps-custom-visual#limitations-of-the-power-apps-visual)

## <a name="next-steps"></a>Næste trin
[Visual til Spørgsmål og svar](power-bi-visualization-types-for-reports-and-q-and-a.md)    
[Selvstudium: Integrer et Power Apps-visual i en Power BI-rapport](/powerapps/maker/canvas-apps/powerapps-custom-visual)