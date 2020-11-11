---
title: 'Selvstudium: Skab en model til maskinel indlæring i Power BI'
description: I dette selvstudium skal du bygge en model til maskinel indlæring i Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 08/03/2020
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 49f1b46e89fd05d05928de631b0ea42832801a05
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397225"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi"></a>Selvstudium: Skab en model til maskinel indlæring i Power BI

I denne artikel i dette selvstudium skal du bruge **automatiseret maskinel indlæring** til at oprette og anvende en binær forudsigelsesmodel i Power BI. Selvstudiet indeholder en vejledning i, hvordan du opretter et dataflow i Power BI og bruger de enheder, der er defineret i dataflowet, til at oplære og validere en model til maskinel indlæring direkte i Power BI. Derefter bruger vi denne model til at tildele scorer for nye data og generere forudsigelser.

Først skal du oprette en binær forudsigelsesmodel til maskinel indlæring for at forudsige købshensigten hos onlineshoppere på baggrund af attributterne for deres onlinesession. Vi benytter et benchmarkdatasæt til maskinel indlæring til denne øvelse. Når en model er oplært, opretter Power BI automatisk en valideringsrapport, der forklarer resultaterne af modellen. Du kan derefter gennemgå valideringsrapporten og anvende modellen på dine data for at tildele point.

Dette selvstudium består af følgende trin:
> [!div class="checklist"]

> * Opret et dataflow med inputdataene
> * Opret og oplær en model til maskinel indlæring
> * Gennemse modelvalideringsrapporten
> * Anvend modellen på en dataflowenhed
> * Brug af resultatet fra modellen i en Power BI-rapport

## <a name="create-a-dataflow-with-the-input-data"></a>Opret et dataflow med inputdataene

Den første del af dette selvstudium består i at oprette et dataflow med inputdata. Denne proces involverer nogle få trin, som vist i følgende afsnit, og begynder med hentning af data.

### <a name="get-data"></a>Hent data

Det første trin i oprettelsen af et dataflow er at gøre dine datakilder klar. I vores tilfælde bruger vi et datasæt til maskinel indlæring fra et sæt onlinesessioner, hvoraf nogle af dem resulterede i et køb. Datasættet indeholder et sæt attributter om disse sessioner, som vi bruger til oplæring af vores model.

Du kan downloade datasættet fra UC Irvine-webstedet. Til dette selvstudium har vi også adgang til denne fil fra følgende link: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Opret enhederne

Log på Power BI-tjenesten for at oprette enhederne i dit dataflow, og naviger til et arbejdsområde i den kapacitet, hvor kunstig intelligens er aktiveret.

Hvis du ikke allerede har et arbejdsområde, kan du oprette et ved at vælge **Arbejdsområder** i navigationsrudens menu i Power BI-tjenesten og vælge **Opret arbejdsområde** nederst i det viste panel. Herefter åbnes et panel til højre, hvor du kan angive oplysninger om arbejdsområdet. Skriv et navn til arbejdsområdet, og vælg derefter **Avanceret**. Bekræft, at arbejdsområdet bruger dedikeret kapacitet, ved hjælp af alternativknappen, og at det er tildelt til en forekomst af en kapacitet, hvor AI Preview er slået til. Vælg derefter **Gem**.

![Opret et arbejdsområde](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-01.png)

Når arbejdsområdet er blevet oprettet, kan du vælge **Spring over** nederst til højre på velkomstskærmen, som vist på følgende billede.

![Spring over, hvis du har et arbejdsområde](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-02.png)

 Vælg knappen **Opret** øverst til højre i arbejdsområdet, og vælg derefter **Dataflow**.

![Opret dataflow](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-03.png)

Vælg **Tilføj nye enheder**. Dette starter en **Power-forespørgselseditor** i browseren.

![Tilføj ny enhed](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-04.png)

Vælg **Tekst/CSV-fil** som en datakilde, som vist på følgende billede.

![Tekst/CSV-fil er valgt](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-05.png)

På siden **Opret forbindelse til en datakilde** , der vises herefter, skal du indsætte følgende link til _online_shoppers_intention.csv_ i feltet **Filsti eller URL-adresse** og derefter vælge  **Næste**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Filsti](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-06.png)

I Power-forespørgselseditor vises et eksempel på dataene fra CSV-filen. Du kan omdøbe forespørgslen til et mere brugervenligt navn ved at ændre værdien i feltet Navn i ruden til højre. Du kan f.eks. ændre navnet på forespørgslen til _Online Visitors_.

![Skift til et brugervenligt navn](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-07.png)

Power Query udleder automatisk kolonnetypen. Du kan ændre kolonnetypen ved at klikke på ikonet for attributtype øverst i kolonneoverskriften. I dette eksempel ændrer vi typen af kolonnen Omsætning til Sand/Falsk.

![Skift datatype](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-08.png)

Vælg knappen **Gem og luk** for at lukke Power Query-editor. Angiv et navn på dataflowet, og vælg derefter **Gem** i dialogboksen, som vist på følgende billede.

![Gem dataflowet](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-09.png)

## <a name="create-and-train-a-machine-learning-model"></a>Opret og oplær en model til maskinel indlæring

Hvis du vil tilføje en model til maskinel indlæring, skal du bruge knappen **Anvend ML-model** på listen **Handlinger** for den basisenhed, der indeholder dine oplæringsdata og mærkatoplysninger, og derefter vælge **Tilføj en model til maskinel indlæring**.

![Tilføj en model til maskinel indlæring](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-10.png)

Det første trin til oprettelse af vores model til maskinel indlæring er at identificere de historiske data, herunder det resultatfelt, som du vil forudsige. Modellen vil blive oprettet ved at lære fra disse data.

I forbindelse med det datasæt, som vi benytter, er dette felt **Revenue**. Vælg **Omsætning** som værdien for "Resultatfelt", og vælg derefter **Næste**.

![Vælg historiske data](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-11.png)

Derefter skal du vælge den type model til maskinel indlæring, der skal oprettes. Power BI analyserer værdierne i resultatfeltet, som du har identificeret, og foreslår de typer af modeller til maskinel indlæring, der kan oprettes for at forudsige dette felt.

Da vi i dette tilfælde forudsiger et binært resultat af, om en bruger vil foretage et køb eller ej, anbefales det, at du vælger Binær forudsigelse. Da vi er interesseret i at forudsige de brugere, der vil foretage et køb, skal du vælge Sand som det resultat for Omsætning, du er mest interesseret i. Du kan desuden angive brugervenlige mærkater for de resultater, der skal bruges i den rapport, der genereres automatisk, og som opsummerer resultaterne af modelvalideringen. Vælg derefter Næste.

![Binær forudsigelse er valgt](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-12.png)

Derefter udfører Power BI en foreløbig scanning af en prøve af dine data og foreslår de input, der kan resultere i mere nøjagtige forudsigelser. Hvis der ikke anbefales et felt i Power BI, bliver der angivet en forklaring ved siden af det. Du har mulighed for at ændre markeringerne til kun at omfatte de felter, du vil have, at modellen skal undersøge, eller du kan vælge alle felter ved at markere afkrydsningsfeltet ud for navnet på enheden. Vælg **Næste** for at acceptere inputtene.

![Vælg Næste](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-13.png)

I det sidste trin skal vi angive navnet på vores model. Navngiv modellen _Purchase Intent Prediction_. Du kan vælge at reducere oplæringstiden for at få vist resultater hurtigt eller øge den tid, der bruges på oplæringen, så du får den bedste model. Vælg derefter **Gem og oplær** for at begynde at oplære modellen.

![Gem modellen](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-14.png)

Oplæringsprocessen starter med at indsamle og normalisere dine historiske data og opdele dit datasæt i to nye enheder _Purchase Intent Prediction Training Data_ og _Purchase Intent Prediction Testing Data_.

Afhængigt af datasættets størrelse kan oplæringsprocessen tage alt fra nogle få minutter til den oplæringstid, der er valgt på forrige skærm. På dette tidspunkt kan du se modellen på fanen **Modeller til maskinel indlæring** i dataflowet. Statussen Klar angiver, at modellen er sat i kø til oplæring eller er under oplæring.

Du kan få bekræftet, at modellen oplæres og valideres, gennem dataflowets status. Dette vises som en igangværende dataopdatering på fanen **Dataflows** i arbejdsområdet.

![Klar til oplæring](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-15.png)

Når oplæringen af modellen er fuldført, viser dataflowet et opdateret opdateringstidspunkt. Du kan få bekræftet, at modellen er oplært, ved at gå til fanen **Modeller til maskinel indlæring** i dataflowet. Den model, du har oprettet, bør have status som **Oplært** og tidspunktet for **Senest oplært** bør nu være opdateret.

![Senest oplært den](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-16.png)

## <a name="review-the-model-validation-report"></a>Gennemse modelvalideringsrapporten
Hvis du vil gennemse modelvalideringsrapporten, skal du under fanen Modeller til maskinel indlæring vælge knappen Vis oplæringsrapport i kolonnen Handlinger for modellen. I denne rapport beskrives det, hvordan ydeevnen for din model til maskinel indlæring sandsynligvis vil være.

På siden **Ydeevne af modellen** i rapporten skal du vælge **de bedste forudsigelser** for at få vist de bedste forudsigelser for din model. Du kan vælge en af forudsigelserne for at få vist fordelingen af det resultat, der er knyttet til den pågældende forudsigelse.

![Modellens ydeevne](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-17.png)

Du kan bruge udsnitsværktøjet **Tærskel for sandsynlighed** på siden Ydeevne af modellen til at undersøge dens indflydelse på præcision og genkaldelse for modellen.

![Tærskel for sandsynlighed](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-18.png)

De øvrige sider i rapporten beskriver de statistiske ydeevnemålepunkter for modellen.

Rapporten indeholder også siden Oplæringsoplysninger, der beskriver de forskellige gentagelser, der er blevet kørt, hvordan funktionerne blev trukket ud fra inputtet, samt hyperparametrene for den endelige model, der blev anvendt.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Anvend modellen på en dataflowenhed

Vælg knappen **Anvend model** øverst i rapporten for at aktivere denne model. I dialogboksen **Anvend** skal du angive den destinationsenhed, der har de kildedata, som modellen skal anvendes for.

![Anvend modellen](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-19.png)

Du skal **opdatere** dataflowet for at få vist et eksempel på resultatet af din model, når du bliver bedt om det.

Anvendelse af modellen vil oprette to nye enheder med suffikset **enriched <model_name>** og **enriched <model_name> explanations**. Anvendelse af modellen i enheden **Online Visitors** vil i vores tilfælde oprette **Online Visitors enriched Purchase Intent Prediction** , som omfatter det forudsagte output fra modellen, og **Online Visitors enriched Purchase Intent Prediction explanations** , som indeholder de vigtigste postspecifikke influencere for forudsigelsen. 

Hvis du anvender en model til binær forudsigelse, tilføjes der fire kolonner med et forudsagt resultat, en sandsynlighedsscore, de vigtigste postspecifikke influencere for forudsigelsen og et forklaringsindeks, der hver især har det angivne kolonnenavn som præfiks.  

![Tre kolonner med resultater](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-20.png)

Når dataflowet er blevet opdateret, kan du vælge enheden **Online Visitors enriched Purchase Intent Prediction** for at få vist resultaterne.

![Se resultaterne](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-21.png)

Du kan også aktivere en hvilken som helst AutoML-model i arbejdsområdet direkte fra Power Query-editor i dit dataflow. For at få adgang til AutoML-modeller, skal du vælge knappen Rediger for den enhed, du vil forbedre med indsigt fra din Azure ML-model, som vist på følgende billede.

![Opret objektet](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-22.png)

Når knappen Rediger vælges, åbnes Power-forespørgselseditoren for enhederne i dit dataflow. Vælg knappen Brug kunstig intelligens på båndet.

![Brug kunstig intelligens](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-23.png)

 Vælg mappen Power BI-modeller til maskinel indlæring i menuen i navigationsruden. Alle de AutoML-modeller, du har adgang til, er angivet her som funktioner i Power Query. Inputparametrene for AutoML-modellen er også automatisk tilknyttet som parametre for den tilsvarende funktion i Power Query. Bemærk, at automatisk tilknytning af parametre kun sker, hvis parameterens navn og datatype er den samme.
 
For at aktivere en AutoML-model kan du angive en af den valgte enheds kolonner som input på rullelisten. Du kan også angive en konstant værdi, der skal bruges som input, ved at slå kolonneikonet til venstre for inputdialogboksen til og fra.

![PQO-funktionsbrowser](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-24.png)

Vælg Anvend for at få vist AutoML-modellens output som en ny kolonne i enhedstabellen. Du får også modelaktiveringen som et anvendt trin for forespørgslen.

![Vis resultater](media/service-tutorial-build-machine-learning-model/tutorial-machine-learning-model-25.png)

Når du gemmer dit dataflow, aktiveres modellen automatisk, når dataflowet opfriskes, for alle nye eller opdaterede rækker i enhedstabellen.

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Brug af resultatet fra modellen i en Power BI-rapport

Hvis du vil bruge outputtet med tildelt score fra din model til maskinel indlæring, kan du oprette forbindelse til dataflowet fra Power BI Desktop ved hjælp af Dataflow-connectoren. Enheden **Online Visitors enriched Purchase Intent Prediction** kan nu bruges til at inkorporere forudsigelserne fra din model i Power BI-rapporter.

## <a name="next-steps"></a>Næste trin

I dette selvstudium har du oprettet og anvendt en binær forudsigelsesmodel i Power BI ved hjælp af disse trin:

* Opret et dataflow med inputdataene
* Opret og oplær en model til maskinel indlæring
* Gennemse modelvalideringsrapporten
* Anvend modellen på en dataflowenhed
* Brug af resultatet fra modellen i en Power BI-rapport

Du kan finde flere oplysninger om automatiseret maskinel indlæring i Power BI i [Automatiseret maskinel indlæring i Power BI](../transform-model/dataflows/dataflows-machine-learning-integration.md).