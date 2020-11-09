---
title: 'Selvstudium: Aktivér en model af typen Machine Learning Studio (klassisk) i Power BI (prøveversion)'
description: I dette selvstudium skal du aktivere en model af typen Machine Learning Studio (klassisk) i Power BI.
author: davidiseminger
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/12/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 7e2019d3b554bc4e033c7aee36c41216ba910a9f
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916837"
---
# <a name="tutorial-invoke-a-machine-learning-studio-classic-model-in-power-bi-preview"></a>Selvstudium: Aktivér en model af typen Machine Learning Studio (klassisk) i Power BI (prøveversion)

I dette selvstudium gennemgår vi, hvordan du inkorporerer indsigt fra en model af typen **Azure Machine Learning Studio (klassisk)** i Power BI. Dette selvstudium indeholder en vejledning i tildeling af Power BI-brugeradgang til en Azure ML-model, oprettelse af et dataflow og anvendelsen af indsigt fra Azure ML-modellen i dit dataflow. Det indeholder også en henvisning til startvejledningen til oprettelse af en Azure ML-model, hvis du ikke allerede har en model.

I selvstudiet kommer du gennem følgende trin:

> [!div class="checklist"]
> * Opret og publicer en Azure Machine Learning-model
> * Giv en Power BI-bruger adgang til at bruge modellen
> * Opret et dataflow
> * Anvend indsigt fra Azure ML-modellen i dataflowet

## <a name="create-and-publish-an-azure-ml-model"></a>Opret og publicer en Azure ML-model

Følg instruktionerne i [trin 1 i gennemgangen: Opret et arbejdsområde af typen Machine Learning Studio (klassisk)](/azure/machine-learning/studio/walkthrough-1-create-ml-workspace) for at oprette et **Machine Learning** -arbejdsområde.

Du kan bruge disse trin, hvis du allerede har en Azure ML-model eller et datasæt. Hvis du ikke har en publiceret model, kan du oprette en model på få minutter ved at referere til [Opret dit første datavidenskabseksperiment i Azure Machine Learning Studio (klassisk)](/azure/machine-learning/studio/create-experiment), hvorved en Azure Machine Learning-model konfigureres til forudsigelse af bilpriser.

Følg trinnene under [Udrul en webtjeneste af typen Azure Machine Learning Studio (klassisk)](/azure/machine-learning/studio/tutorial-part3-credit-risk-deploy) for at publicere Azure Machine Learning-modellen som en webtjeneste.

## <a name="grant-a-power-bi-user-access"></a>Tildel adgang til en Power BI-bruger

Hvis du vil have adgang til en Azure Machine Learning-model fra Power BI, skal du have adgangen **Læs** til Azure-abonnementet og ressourcegruppen og adgangen **Læs** til webtjenesten Azure Machine Learning Studio (klassisk) for modeller af typen Machine Learning Studio (klassisk).  Du skal have adgangen **Læs** til Machine Learning-arbejdsområdet for Azure Machine Learning-modellen.

Følgende trin forudsætter, at du er medadministrator af Azure-abonnementet og den ressourcegruppe, som modellen blev publiceret i.

Log på [Azure Portal](https://portal.azure.com), og naviger til siden **Abonnementer** , som du finder ved hjælp af listen **Alle tjenester** i menuen i navigationsruden.

![Skærmbillede, der viser Azure Portal, hvor Abonnementer er valgt.](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_01.png)

Vælg det Azure-abonnement, som du brugte til publicering af modellen, og vælg **Access Control (IAM)** . Vælg derefter **Tilføj rolletildeling** , rollen **Læser** , og vælg Power BI-brugeren. Vælg **Gem** , når du er færdig. På følgende billede vises disse valg.

![Access Control i Azure Portal](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_02.png)

Gentag derefter trinnene ovenfor for at tildele rolleadgangen **Bidragyder** til Power BI-brugeren for den specifikke Machine Learning-webtjeneste, som Azure ML-modellen er blevet udrullet i.

## <a name="create-a-dataflow"></a>Opret et dataflow

### <a name="get-data-for-creating-the-dataflow"></a>Hent data til oprettelse af dataflowet

Log på Power BI-tjenesten med legitimationsoplysningerne for den bruger, som du har givet adgang til Azure ML-modellen i det forrige trin.

I dette trin forudsættes det, at du har de data, du vil tildele point med din Azure ML-model i CSV-format.  Hvis du har brugt **eksperimentet med bilpriser** til at oprette modellen i Machine Learning Studio (klassisk), deles datasættet via følgende link:

* [Eksempelmodel til Azure Learning Studio (klassisk)](https://github.com/santoshc1/PowerBI-AI-samples/blob/master/Tutorial_MLStudio_model_integration/Automobile%20price%20data%20_Raw_.csv)

### <a name="create-a-dataflow"></a>Opret et dataflow

Log på Power BI-tjenesten for at oprette enhederne i dit dataflow, og gå til et arbejdsområde i kapaciteten, som AI-prøveversionen er aktiveret for.

Hvis du ikke allerede har et arbejdsområde, kan du oprette et ved at vælge **Arbejdsområder** i menuen til venstre og derefter vælge **Opret arbejdsområde** i det nederste panel.  Dette åbner et panel, hvor du kan angive oplysninger om arbejdsområdet. Skriv et navn til arbejdsområdet, og vælg derefter **Gem**.

![Opret arbejdsområde](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_03.png)

Når arbejdsområdet er blevet oprettet, kan du vælge **Spring over** nederst til højre på velkomstskærmen.

![Spring over](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_04.png)

Vælg fanen **Dataflow (prøveversion)** , vælg knappen **Opret** øverst til højre i arbejdsområdet, og vælg derefter **Dataflow**.

![Dataflow (prøveversion)](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_05.png)

Vælg **Tilføj nye enheder** , hvilket starter **Power-forespørgselseditor** i browseren.

![Tilføj ny enhed](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_06.png)

Vælg **Tekst/CSV-fil** som en datakilde.

![Vælg datakilde](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_07.png)

Du bliver bedt om at oprette forbindelse til en datakilde på det næste skærmbillede. Indsæt linket til de data, du brugte til at oprette din Azure ML-model. Hvis du har brugt dataene om _bilpriser_ , kan du indsætte følgende link i feltet **Filsti eller URL-adresse** og derefter vælge **Næste**.

`https://raw.githubusercontent.com/MicrosoftLearning/Principles-of-Machine-Learning-Python/master/Module7/Automobile%20price%20data%20_Raw_.csv`

![Opret forbindelse til datakilde](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_08.png)

I Power-Forespørgselseditor vises et eksempel på dataene fra CSV-filen. Vælg **Transformér tabel** på kommandobåndet, og vælg derefter **Brug den første række som overskrifter**.  Herefter føjes forespørgselstrinnet _Hævede overskrifter_ til ruden **Anvendte trin** til højre. Du kan også omdøbe forespørgslen til et mere brugervenligt navn, f.eks _Bilpriser_ , ved hjælp af ruden til højre.

![Skærmbillede af Power Query-editor, der viser et eksempel på dataene.](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_09.png)

Vores kildedatasæt har ukendte værdier, der er angivet til "?".  Hvis du vil rydde disse værdier, kan du for nemheds skyld erstatte "?" med "0" for at undgå fejl på et senere tidspunkt.  Det gør du ved at vælge kolonnerne *normalized-losses* , *bore* , *stroke* , *compression-ratio* , *horsepower* , *peak-rpm* og *price* ved at klikke på kolonnernes navn i kolonneoverskrifterne, og derefter klikke på "Transformér kolonner" og vælge "Erstat værdier".  Erstat "?" med "0".

![Erstat værdier](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_10.png)

Alle kolonnerne i tabellen fra en tekst-/CSV-kilde behandles som tekstkolonner.  Vi skal nu ændre de numeriske kolonner til deres korrekte datatyper.  Du kan gøre dette i Power-forespørgslen ved at klikke på datatypesymbolet i kolonneoverskriften.  Sørg for, at kolonnerne får typerne nedenfor:

- **Heltal** : symboling, normalized-losses, curb-weight, engine-size, horsepower, peak-rpm, city-mpg, highway-mpg, price
- **Decimaltal** :  wheel-base, length, width, height, bore, stroke, compression-ratio

![Rediger kolonner](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_11.png)

Vælg **Udført** for at lukke Power-forespørgselseditor. Du får nu vist listen over enheder med de _bilprisdata_ , som vi har tilføjet. Vælg **Gem** i øverste højre hjørne, angiv et navn til dataflowet, og vælg derefter **Gem**.

![Gem dataflow](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_12.png)

### <a name="refresh-the-dataflow"></a>Opdater dataflowet

Når du gemmer dataflowet, vises en meddelelse om, at dataflowet er blevet gemt. Vælg **Opdater nu** for at overføre data fra kilden til dataflowet.

![Opdater dataflow](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_13.png)

Vælg **Luk** i øverste højre hjørne, og vent, indtil opdateringen af dataflowet er blevet fuldført.

Du kan også opdatere dataflowet ved hjælp af kommandoen **Handlinger**. I dataflowet vises et tidsstempel for, hvornår opdateringen blev fuldført.

![Manuel opdatering](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_14.png)

## <a name="apply-insights-from-your-azure-ml-model"></a>Anvend indsigt fra din Azure ML-model

Hvis du vil have adgang til Azure ML-modellen for _Forudsigelse af bilpriser_ , kan du redigere enheden _Bilpriser_ , som den estimerede pris skal føjes til.

![Rediger enhed](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_15.png)

Når du vælger ikonet **Rediger** , åbnes Power-forespørgselseditoren for enhederne i dit dataflow.

![Rediger](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_16.png)

Vælg knappen **AI-indsigt** på båndet, og vælg derefter mappen _Azure Machine Learning-modeller_ i navigationsruden.

De Azure ML-modeller, som du har fået adgang til, er angivet som Power-forespørgselsfunktioner med præfikset *AzureML*.  Når du klikker på den funktion, der svarer til modellen _AutomobilePricePrediction_ , vises parametrene for modellens webtjeneste som funktionsparametre.

Du aktiverer en Azure ML-model ved at angive en af den valgte enheds kolonner som input på rullelisten. Du kan også angive en konstant værdi, der skal bruges som input, ved at slå kolonneikonet til venstre for inputdialogboksen til og fra. Når et kolonnenavn svarer til et af navnene på funktionsparametrene, foreslås den pågældende kolonne automatisk som input.  Hvis navnet på en kolonne ikke har noget match, kan du vælge det på rullelisten.

I forbindelse med modellen _Forudsigelse af bilpriser_ er inputparametrene som følger:

- make
- body-style
- wheel-base
- engine-size
- horsepower
- peak-rpm
- highway-mpg

Da vores tabel stemmer overens med det oprindelige datasæt, der blev brugt til at oplære modellen, er de korrekte kolonner allerede blevet valgt for alle parametrene i dette tilfælde.

![Oplær modellen](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_17.png)

Vælg **Aktivér** for at få vist Azure ML-modellens output som en ny kolonne i enhedstabellen. Du får også vist modelaktiveringen som et anvendt trin for forespørgslen.

Outputtet fra modellen vises som en post i outputkolonnen. Du kan udvide kolonnen for at oprette individuelle outputparametre i separate kolonner. I dette tilfælde er vi kun interesseret i _Scored Labels_ , der indeholder den estimerede pris på bilen.  Så vi fjerner markeringen af resten og vælger **OK**.

![Modeloutput](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_18.png)

Den resulterende kolonne *Scored Labels* har prisforudsigelsen fra Azure ML-modellen.

![Scored labels](media/service-tutorial-invoke-machine-learning-model/tutorial-invoke-machine-learning-model_19.png)


Når du gemmer dit dataflow, aktiveres Azure ML-modellen automatisk, når dataflowet opdateres for alle nye eller opdaterede rækker i enhedstabellen.

## <a name="clean-up-resources"></a>Fjern ressourcer

Hvis du ikke længere har brug for de Azure-ressourcer, du har oprettet ved hjælp af denne artikel, kan du slette dem for at undgå eventuelle gebyrer.  Du kan også slette de dataflow, du har oprettet, hvis du ikke længere har brug for dem.

## <a name="next-steps"></a>Næste trin

I dette selvstudium har du oprettet et simpelt eksperiment ved hjælp af Azure Machine Learning Studio (klassisk) og et simpelt datasæt ved hjælp af disse trin:

- Opret og publicer en Azure Machine Learning-model
- Giv en Power BI-bruger adgang til at bruge modellen
- Opret et dataflow
- Anvend indsigt fra Azure ML-modellen i dataflowet

Du kan finde flere oplysninger om Azure Machine Learning-integration i Power BI i [Azure Machine Learning-integration i Power BI (prøveversion)](../transform-model/service-machine-learning-integration.md).