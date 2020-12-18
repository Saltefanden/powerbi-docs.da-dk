---
title: 'Selvstudium: Brug af en Azure Machine Learning-model i Power BI'
titleSuffix: Azure Machine Learning
description: Få mere at vide om, hvordan du bruger en Azure Machine Learning-model i Power BI.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: tutorial
ms.author: samkemp
author: samuel100
ms.reviewer: sdgilley, maggies
ms.date: 12/10/2020
ms.openlocfilehash: 6c68fff575e4da0c9126904df2de5292747c209c
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491776"
---
# <a name="tutorial-consume-azure-machine-learning-models-in-power-bi"></a>Selvstudium: Brug af en Azure Machine Learning-model i Power BI

I dette selvstudium kommer du gennem oprettelsen af en Power BI-rapport, der er baseret på en model til maskinel indlæring. I slutningen af dette selvstudium kan du:

> [!div class="checklist"]
> * Score modeller til maskinel indlæring (installeret ved hjælp af Azure Machine Learning) i Power BI.
> * Oprette forbindelse til en Azure Machine Learning-model i Power Query-editor.
> * Oprette en rapport med en visualisering, der er baseret på den pågældende model.
> * Udgive rapporten i Power BI-tjenesten.
> * Aktivere en planlagt opdatering af rapporten.

## <a name="prerequisites"></a>Forudsætninger

Før du starter dette selvstudium, skal du gøre følgende:

- Oplær og implementer en model til maskinel indlæring i Azure Machine Learning. Brug et af disse tre selvstudier til Azure Machine Learning: 

    - [Mulighed A: Kode](/azure/machine-learning/tutorial-power-bi-custom-model)
    - [Mulighed B: Designer](/azure/machine-learning/tutorial-power-bi-designer-model)
    - [Mulighed C: Automatisk maskinel indlæring](/azure/machine-learning/tutorial-power-bi-automated-model)

- Tilmeld dig en [gratis Power BI-prøveversion](https://app.powerbi.com/signupredirect?pbi_source=web).
- [Installér Power BI Desktop](https://powerbi.microsoft.com/desktop/) på en lokal computer.

## <a name="create-the-data-model"></a>Opret datamodellen

Åbn Power BI Desktop, og vælg **Hent data**. Søg efter **web** i dialogboksen **Hent data**. Vælg kilden **Web** > **Opret forbindelse**.

:::image type="content" source="media/service-aml-integrate/pbi-get-data.png" alt-text="Skærmbillede, der viser webdata.":::

I dialogboksen **Fra web** skal du kopiere og indsætte følgende URL-adresse i feltet:

```txt 
https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt
```

:::image type="content" source="media/service-aml-integrate/pbi-data.png" alt-text="Skærmbillede, der viser URL-adresse til websted.":::

Vælg **OK**.

Vælg **Transformer data** for at åbne vinduet **Power Query-editor**.

Vælg knappen **Azure Machine Learning** på båndet Hjem i Power Query-editor.

:::image type="content" source="media/service-aml-integrate/aml-button.png" alt-text="Skærmbillede, der viser Power Query-editor.":::

Når du har logget på din Azure-konto ved hjælp af enkeltlogon, får du vist en liste over tilgængelige tjenester. Vælg den **my-sklearn-service**, som du har oprettet under oplæringen, og installer et selvstudium til modellen til maskinel indlæring. 

Power Query udfylder automatisk kolonnerne for dig. Du husker, at vi i vores skema til tjenesten havde en Python-decorator, der angav inputtet. Vælg **OK**.

:::image type="content" source="media/service-aml-integrate/aml-pbi-run.png" alt-text="Skærmbillede, der viser Azure Machine Learning-modeller.":::

Hvis du vælger **OK**, kaldes Azure-Machine Learning-tjenesten. Det udløser en advarsel om beskyttelse af personlige data for både data og slutpunkt.

:::image type="content" source="media/service-aml-integrate/data_privacy_warning.png" alt-text="Skærmbillede, der viser advarsel om beskyttelse af personlige oplysninger.":::

Vælg **Fortsæt**. På det næste skærmbillede skal du vælge **Ignorer kontrol af niveauerne for beskyttelse af personlige oplysninger for denne fil** > **Gem**.

Når der er foretaget en vurdering af dataene, opretter Power Query en ekstra kolonne med navnet **AzureML.my-diabetes-model**.

:::image type="content" source="media/service-aml-integrate/scored-data.png" alt-text="Skærmbillede, der viser kolonnen for den tilføjede vurdering.":::

De data, som tjenesten returnerer, er en **liste**. 

> [!NOTE]
> Hvis du har installeret en designermodel, kan du se en **post**.

Hvis du vil hente forudsigelser, skal du på båndet **Transformer** vælge knappen **Udvid kolonne** > **Udvid til nye rækker**.

Efter udvidelsen kan du se forudsigelserne i kolonnen AzureML.my-diabetes-model.

:::image type="content" source="media/service-aml-integrate/after-expand.png" alt-text="Skærmbillede, der viser udvidelsen.":::

Følg de næste trin for at fuldføre oprydningen af din datamodel.

1. Omdøb kolonnen **AzureML.my-diabetes-model** til **forudsagt**.
1. Omdøb kolonnen **Y** til **faktisk**.
1. Rediger typen af kolonnen **faktisk**: Markér kolonnen, og på båndet **Transformér** skal du vælge **Datatype** > **Decimaltal**.
1. Rediger typen af kolonnen **forudsagt**: Markér kolonnen, og på båndet **Transformér** skal du vælge **Datatype** > **Decimaltal**.
1. Vælg **Luk og anvend** på båndet **Hjem**.

## <a name="create-a-report-with-visualizations"></a>Opret en rapport med visualiseringer

Nu kan du oprette nogle visualiseringer for at vise dine data.

1. Vælg et **Kurvediagram** i ruden **Visualiseringer**. 
1. Når visualiseringen Kurvediagram er valgt:
1. Træk feltet **ALDER** til **aksen**.
1. Træk feltet **faktisk** til **Værdier**.
1. Træk feltet **forudsagt** til **Værdier**.

Tilpas størrelsen på kurvediagrammet, så det udfylder siden. Rapporten indeholder nu et enkelt kurvediagram med to linjer, én for de forudsagte værdier og én for de faktiske værdier fordelt efter alder.

:::image type="content" source="media/service-aml-integrate/report-viz.png" alt-text="Skærmbillede, der viser ruden Visualiseringer.":::

## <a name="publish-the-report"></a>Publicer rapporten

Du kan tilføje flere visualiseringer, hvis du vil det. Vi vil gøre det kort i dette selvstudium og publicerer derfor rapporten.

1. Gem rapporten.
1. Vælg **Fil** > **Udgiv** > **Publicer i Power BI**.
1. Log på Power BI-tjenesten.
1. Vælg **Mit arbejdsområde**.
1. Når rapporten er publiceret, skal du vælge linket **Åbn < MY_PBIX_FILE. PBIX > i Power BI**. Rapporten åbner rapporten i Power BI i din browser.

     :::image type="content" source="media/service-aml-integrate/publish-success.png" alt-text="Skærmbillede, der viser, at publiceringen lykkedes.":::

## <a name="enable-datasets-to-refresh"></a>Gør det muligt at opdatere datasæt

I et scenarie, hvor datakilden opdateres med nye data, der skal vurderes, skal du opdatere dine legitimationsoplysninger, så dataene kan blive vurderet. 

Vælg **Flere indstillinger (...)**  > **Indstillinger** > **Indstillinger** på den sorte overskriftslinje i Mit arbejdsområde i Power BI-tjenesten.

:::image type="content" source="media/service-aml-integrate/settings-pbi.png" alt-text="Skærmbillede, der viser indstillinger.":::

Vælg **Datasæt**, udvid **Legitimationsoplysninger for datakilde**, og vælg derefter **Rediger legitimationsoplysninger**.

:::image type="content" source="media/service-aml-integrate/data-refresh.png" alt-text="Skærmbillede, der viser opdatering af legitimationsoplysninger.":::

Følg vejledningen for både **azureMLFunctions** og **Web**. Sørg for, at du vælger et niveau for beskyttelse af personlige oplysninger. Du kan nu angive en **planlagt opdatering** af dataene. Vælg en **Opdateringshyppighed** og **Tidszone**. Du kan også vælge en mailadresse, hvor Power BI kan sende meddelelser om opdateringsfejl.

:::image type="content" source="media/service-aml-integrate/schedule-refresh.png" alt-text="Skærmbillede, der viser opdatering af datasæt og vurdering.":::

Vælg **Anvend**.

>[!NOTE]
> Når dataene opdateres, sendes dataene også til dit Azure Machine Learning-slutpunkt til vurdering.

## <a name="clean-up-resources"></a>Fjern ressourcer

>[!IMPORTANT]
>Du kan bruge de ressourcer, du har oprettet, som forudsætninger for andre Azure Machine Learning-selvstudier og artikler med vejledning.

Hvis du ikke vil bruge de ressourcer, du har oprettet, skal du slette dem, så du ikke pådrager dig nogen gebyrer.

1. Vælg **Ressourcegrupper** længst til venstre i Azure Portal.
 
1. Vælg den ressourcegruppe, du har oprettet, på listen.

1. Vælg **Slet ressourcegruppe**.

   ![Skærmbillede af valgene til at slette en ressourcegruppe i Azure Portal.](./media/service-aml-integrate/delete-resources.png)

1. Indtast navnet på ressourcegruppen. Vælg derefter **Slet**.
1. Slet rapporten og det relaterede datasæt i Mit arbejdsområde i Power BI-tjenesten. Du behøver ikke at slette Power BI Desktop eller rapporten på din computer. Power BI Desktop er gratis.

## <a name="next-steps"></a>Næste trin

I denne serie af selvstudier lærer du, hvordan du konfigurerer en tidsplan i Power BI, så nye data kan blive vurderet i forhold til vurderingsslutpunktet i Azure Machine Learning.
