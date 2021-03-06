---
title: 'Selvstudium: Brug Cognitive Services i Power BI (prøveversion)'
description: I dette selvstudium bruger du Cognitive Services og dataflow i Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 02/20/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: 22548c092e1407d1744a019c15cb0d29a94913eb
ms.sourcegitcommit: 772c65b7b440ab082510bf3f64b871d19139d451
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/12/2020
ms.locfileid: "97353352"
---
# <a name="tutorial-use-cognitive-services-in-power-bi"></a>Selvstudium: Brug Cognitive Services i Power BI

Power BI giver adgang til et sæt funktioner fra Azure Cognitive Services, så du kan forbedre dine data via selvbetjent dataforberedelse til dataflow. De tjenester, der understøttes i dag, er [Synspunktsanalyse](/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-sentiment-analysis), [Udtrækning af nøglesætninger](/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-keyword-extraction), [Registrering af sprog](/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-language-detection) og [Billedmarkering](/azure/cognitive-services/computer-vision/concept-tagging-images). Transformationerne udføres i Power BI-tjenesten og kræver ikke et Azure Cognitive Services-abonnement. Denne funktion kræver Power BI Premium.

Cognitive Services-transformationer understøttes i [Selvbetjent dataforberedelse til dataflow](https://powerbi.microsoft.com/blog/introducing-power-bi-data-prep-wtih-dataflows/). Brug de trinvise eksempler til tekstanalyse og billedmarkering nedenfor for at komme i gang.

I dette selvstudium lærer du, hvordan du kan:

> [!div class="checklist"]
> * Importere data til et dataflow
> * Tildele synspunkter point og udtrække nøglesætninger fra en tekstkolonne i et dataflow
> * Oprette forbindelse til resultaterne fra Power BI Desktop


## <a name="prerequisites"></a>Forudsætninger

Følgende elementer er nødvendige for at fuldføre dette selvstudium: 

- En Power BI-konto. Hvis du ikke er tilmeldt Power BI, kan du [tilmelde dig en gratis prøveversion](https://app.powerbi.com/signupredirect?pbi_source=web), før du begynder.
- Adgang til en Power BI Premium-kapacitet med AI-arbejdsbelastningen aktiveret. Denne arbejdsbelastning er som standard deaktiveret i prøveperioden. Hvis du er i en Premium-kapacitet, og AI Insights ikke vises, skal du kontakte administratoren af Premium-kapaciteten for at aktivere AI-arbejdsbelastningen i administrationsportalen.

## <a name="text-analytics"></a>Tekstanalyse

Følg trinnene i dette afsnit for at færdiggøre tekstanalysedelen af selvstudiet.

### <a name="step-1-apply-sentiment-scoring-in-power-bi-service"></a>Trin 1: Anvend pointtildeling i Power BI-tjenesten

Kom i gang ved at gå til et Power BI-arbejdsområde med Premium-kapacitet, og opret et nyt dataflow ved hjælp af knappen **Opret** i øverste højre hjørne af skærmen.

![Skærmbillede, der viser Power BI-arbejdsområdet med Opret og derefter Dashboard valgt.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_01.png)

Dialogboksen Dataflow viser indstillingerne til oprettelse af et nyt dataflow. Vælg **Tilføj nye enheder**. Vælg derefter **Tekst/CSV** i menuen med datakilder.

![Skærmbillede, der viser Vælg en datakilde, der indeholder Tekst/CSV.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_02.png)

Indsæt denne URL-adresse i feltet URL-adresse: [https://pbiaitutorials.blob.core.windows.net/textanalytics/FabrikamComments.csv](https://pbiaitutorials.blob.core.windows.net/textanalytics/FabrikamComments.csv), og klik på **Næste**.

![Skærmbillede, der viser Opret forbindelse til datakilde, hvor du kan angive URL-adressen.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_03.png)

Dataene er nu klar til at blive brugt til tekstanalyse, og vi kan give synspunkter point og udtrække nøglesætninger fra kundens kolonne med kommentarer.

Vælg **AI Insights** i Power-forespørgselseditor

![Skærmbillede, der viser Rediger forespørgsler med Alle indsigter valgt.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_04.png)

Udvid mappen **Cognitive Services**, og vælg den funktion, du vil bruge. I dette eksempel får synspunkterne i kolonnen med kommentarer point, men du kan følge de samme trin for at prøve registrering af sprog og udtrækning af nøglesætninger.

![Skærmbillede, der viser Kald funktion med en funktion valgt.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_05.png)

Når en funktion er markeret, vises de obligatoriske og valgfri felter. Vælg kolonnen med anmeldelser som tekstinput for at give eksemplerne på synspunkter i anmeldelserne point. Kulturoplysninger er valgfrit input og kræver et ISO-format. Du kan f.eks. angive "en", hvis teksten skal behandles som engelsk. Når feltet er tomt, registrerer Power BI først sproget for inputværdien, før synspunkterne får tildelt point.

![Skærmbillede, der viser dialogboksen Kald funktion med tekstrullemenuen.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_06.png)

Nu skal du vælge **Kald** for at køre funktionen. En ny kolonne med synspunktsscoren for hver række føjes til tabellen. Du kan gå tilbage til **AI Insights** for at udtrække nøglesætninger i anmeldelsesteksten på samme måde.

Når du er færdig med transformationerne, kan du ændre forespørgselsnavnet til "Kundernes kommentarer" og vælge **Udført**.

![Skærmbillede, der viser Rediger forespørgsler med Navn fremhævet.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_07.png)

**Gem** derefter dataflowet, og giv det navnet Fabrikam. Vælg knappen **Opdater nu**, der vises som pop op, når du har gemt dataflowet.

![Skærmbillede, der viser knappen Gem.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_08.png)

Når dataflowet er blevet gemt og opdateret, kan du bruge det i en Power BI-rapport.

### <a name="step-2-connect-from-power-bi-desktop"></a>Trin 2: Opret forbindelse fra Power BI Desktop

Åbn Power BI Desktop. Vælg **Hent data** på båndet Hjem.

Gå til **Power BI-dataflow (Beta**) i Power BI-afsnittet, og vælg **Opret forbindelse**.

![Skærmbillede, der viser ruden Hent data med Power BI-dataflow valgt.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_09.png)

Eftersom der er tale om en prøveversion, bliver du bedt om at acceptere betingelserne for prøveversionen. Når du har accepteret disse betingelser, kan du logge på med din organisationskonto.

![Skærmbillede, der viser en logonmeddelelse for din organisationskonto.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_10.png)

Vælg det dataflow, du lige har oprettet. Gå til tabellen med kundekommentarer, og klik på **Indlæs**.

![Skærmbillede, der viser Navigator med hvor tabellen med kundekommentarer er valgt.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_11.png)

Nu, hvor dataene er indlæst, kan du begynde at oprette en rapport.

## <a name="image-tagging"></a>Billedmarkering

Gå til et Power BI-arbejdsområde med Premium-kapacitet. Opret et nyt dataflow ved hjælp af knappen **Opret** i øverste højre hjørne af skærmen.

![Skærmbillede, der viser Power BI-arbejdsområdet med Opret og derefter Dataflow valgt.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_12.png)

Vælg **Tilføj nye enheder**.

![Skærmbillede, der viser en mulighed for at tilføje nye enheder, så du kan begynde at oprette en arbejdsproces.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_13.png)

Når du bliver bedt om at vælge en datakilde, skal du vælge **Tom forespørgsel**.

![Skærmbillede, der viser Vælg en datakilde, der indeholder Tom forespørgsel.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_14.png)

Kopiér forespørgslen nedenfor i forespørgselseditoren, og klik på Næste. Du kan erstatte URL-stierne nedenfor med andre billeder eller tilføje flere rækker. Funktionen *Web.Contents* importerer billedets URL-adresse som binær. Hvis du har en datakilde med billeder, der er gemt som binære, kan du også bruge dem direkte.


```python
let
  Source = Table.FromRows({
  { Web.Contents("https://images.pexels.com/photos/87452/flowers-background-butterflies-beautiful-87452.jpeg") },
  { Web.Contents("https://upload.wikimedia.org/wikipedia/commons/5/53/Colosseum_in_Rome%2C_Italy_-_April_2007.jpg") }}, { "Image" })
in
  Source
```

![Skærmbillede, der viser Opret forbindelse til datakilde, som viser din forespørgsel og knappen Næste.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_15.png)

Når du bliver spurgt om legitimationsoplysninger, skal du vælge *Anonym*.

![Skærmbillede, der viser Rediger forespørgsler, hvor du kan angive legitimationsoplysninger.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_16.png)

Du får vist følgende billede.

![Skærmbillede, der viser dialogboksen Angiv legitimationsoplysninger, hvor du kan angive godkendelsestypen.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_17.png)

Du bliver bedt om legitimationsoplysninger for hver enkelt webside.

Vælg **AI Insights** i forespørgselseditoren.

![Skærmbillede, der viser Rediger forespørgsler med Alle indsigter valgt og én advarsel vist.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_18.png)

Log på med din **organisationskonto**.

![Skærmbillede viser dialogboksen Angiv legitimationsoplysninger, hvor du kan angive organisationskontoen.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_19.png)

Vælg funktionen Markér billeder, indtast _[Binary]_ i kolonnefeltet og _en_ i feltet med kulturoplysninger. 

> [!NOTE]
> I øjeblikket kan du ikke vælge en kolonne ved hjælp af en rulleliste, hvilket vil blive løst hurtigst muligt under den private prøveperiode.

![Skærmbillede, der viser Kald funktion med funktionen TagImages valgt.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_20.png)

Fjern anførselstegnene rundt om kolonnenavnet i funktionseditoren. 

> [!NOTE]
> At fjerne anførselstegnene er en midlertidig løsning, og problemet vil blive løst så hurtigt som muligt under prøveperioden.

![Skærmbillede, der viser funktionseditoren med Billede fremhævet uden anførselstegn.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_21.png)

Funktionen returnerer en post med koderne i CSV-format og som en json-post. Vælg udvidelsesknappen for at tilføje den ene eller begge to som kolonner i tabellen.

![Skærmbillede, der viser knappen Udvid, som har to modsatrettede pile.](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_22.png)

Vælg **Udført**, og gem dataflowet. Når du har opdateret dataflowet én gang, kan du oprette forbindelse til det fra Power BI Desktop ved hjælp af dataflowforbindelserne. (Se trinnene på side 5 i dette dokument).

## <a name="clean-up-resources"></a>Fjern ressourcer

Når forespørgslen ikke længere er nødvendig, kan du slette den ved at højreklikke på navnet på forespørgslen i Power-forespørgselseditor og vælge **Slet**.

## <a name="next-steps"></a>Næste trin

I dette selvstudium anvendte du tildeling af point til synspunkter og funktioner til markering af billeder i et Power BI-dataflow. Du kan få mere at vide om Cognitive Services i Power BI ved at læse følgende artikler.

* [Cognitive Services i Azure](/azure/cognitive-services/)
* Kom i gang [med selvbetjent dataforberedelse i dataflow](../transform-model/dataflows/dataflows-introduction-self-service.md)
* Få mere at vide om [Power BI Premium](https://powerbi.microsoft.com/power-bi-premium/)

Du vil måske også være interesseret i følgende artikler.

* [Selvstudium: Brug Azure Machine Learning-modeller i Power BI](service-aml-integrate.md)
* [Azure Machine Learning-integration i Power BI (prøveversion)](../transform-model/dataflows/dataflows-machine-learning-integration.md)
* [Cognitive Services i Power BI (prøveversion)](../transform-model/dataflows/dataflows-machine-learning-integration.md)