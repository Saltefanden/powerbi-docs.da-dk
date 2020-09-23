---
title: Opret forbindelse til Azure Consumption Insights-data i Power BI Desktop
description: Du kan nemt oprette forbindelse til Azure og få indsigt i forbrugs- og brugsdata ved hjælp af Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a8d2284a24bb04b175a00a69339ba9e6ac260c10
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90858619"
---
# <a name="connect-to-azure-consumption-insights-data-in-power-bi-desktop"></a>Opret forbindelse til Azure Consumption Insights-data i Power BI Desktop

Du kan bruge Power BI Desktop til at oprette forbindelse til Azure og få detaljerede data om din organisations forbrug af Azure-tjenesten. Med disse data kan du oprette brugerdefinerede rapporter og målinger, så du bedre kan forstå og analysere dit Azure-forbrug.

> [!NOTE]
> Der er begrænset understøttelse af Microsoft Azure Consumption Insights (beta). I forbindelse med ny funktionalitet skal du bruge [Azure Cost Management-connectoren til Power BI](desktop-connect-azure-cost-management.md).

## <a name="connect-with-azure-consumption-insights"></a>Opret forbindelse vha. Azure Consumption Insights

Azure Consumption Insights giver dig mulighed for at oprette forbindelse til faktureringskonti under en Azure Enterprise Aftale.

I dette afsnit får du mere at vide om, hvordan du henter de data, du skal migrere, ved hjælp af Azure Enterprise Connector. Der er også en oversigt over *kolonner med forbrugsoplysninger* tilgængelig i API'en til **ACI** (Azure Consumption Insights).

Hvis du vil bruge **Azure Consumption Insights**-connectoren, skal du have adgang til Enterprise-funktionerne på Azure Portal.

Sådan bruger du **Azure Consumption Insights**-connector i **Power BI Desktop**: 

1. På båndet **Start** skal du vælge **Hent data**.

1. Vælg **Onlinetjenester** blandt kategorierne til venstre.  

1. Vælg **Microsoft Azure Consumption Insights (beta)** . 

1. Vælg **Opret forbindelse**.

   ![Skærmbillede af dialogboksen Microsoft Azure Consumption Insights. Vælg Opret forbindelse.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

   I den viste dialogboks skal du angive dit **Azure-tilmeldingsnummer**.

   ![Skærmbillede af dialogboks til at angive Azure-tilmeldingsnummer.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

   * Du kan hente dit tilmeldingsnummer på [Azure Enterprise Portal](https://ea.azure.com) på den placering, der er vist på følgende billede:

  ![Skærmbillede af Azure Enterprise Portal til at hente tilmeldingsnummeret.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)

   Denne version af connectoren understøtter kun virksomhedstilmeldinger fra https://ea.azure.com. Tilmeldinger i Kina understøttes ikke i øjeblikket.

   Derefter skal du angive din *adgangsnøgle* for at oprette forbindelse.

   ![Skærmbillede af dialogboks til at angive adgangsnøgle til at oprette forbindelse til Microsoft Azure Consumption Insights.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

   * Din adgangsnøgle for tilmelding findes på [Azure Enterprise Portal](https://ea.azure.com).

  ![Skærmbillede af Azure Enterprise Portal, der viser adgangsnøgler til tilmelding.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

Når du har angivet din *adgangsnøgle* og valgt **Opret forbindelse**, åbnes vinduet **Navigator**, hvor du kan se ni tilgængelige tabeller:

| Tabel        | Beskrivelse |
|------------- | -------------------------------------------------------------|
| **Budgetter** | Budgetoplysninger, hvor du kan se de faktiske omkostninger eller det faktiske forbrug sammenlignet med eksisterende budgetmål. |
| **MarketPlace** | Forbrugsbaserede gebyrer for Azure Marketplace. |
| **Prisark** | Gældende priser pr. måler for en tilmelding. |
| **RICharges** | Gebyrer knyttet til dine reserverede instanser i løbet af de sidste 24 måneder. |
| **RIRecommendations_Single** | Anbefalinger til køb af reserverede instanser på baggrund af dine forbrugstendenser for et enkelt abonnement i løbet af de sidste 7, 30 eller 60 dage. |
| **RIRecommendations_Shared** | Anbefalinger til køb af reserverede instanser på baggrund af dine forbrugstendenser på tværs af alle dine abonnementer i løbet af de sidste 7, 30 eller 60 dage. |
| **RIUsage** | Oplysninger om forbrug for dine eksisterende reserverede instanser i løbet af den sidste måned. |
| **Oversigter** | En månedlig oversigt over saldi, nye køb, Azure Marketplace-gebyrer, justeringer og gebyrer for overforbrug. |
| **UsageDetails** | En oversigt over forbrugte mængder og anslåede abonnementsgebyrer. |

Du kan markere et afkrydsningsfelt ud for en af tabellerne for at få den vist. Du kan vælge en eller flere tabeller ved at markere afkrydsningsfeltet ud for deres navn og derefter vælge **Indlæs**.

![Skærmbillede af dialogboksen Navigator, der viser alle tilgængelige tabeller.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04b.png)

> [!NOTE]
> Tabellerne *Summary* og *PriceSheet* er kun tilgængelige for API-nøglen på tilmeldingsniveau. Derudover har dataene i disse tabeller som standard den aktuelle måneds data for *Usage* og *PriceSheet*. Tabellerne *Summary* og *MarketPlace* er ikke begrænset til den aktuelle måned.
>
>

Når du vælger **Indlæs**, indlæses dataene i **Power BI Desktop**.

![Skærmbillede af dialogboks, der vises, når data indlæses.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

Når de markerede data er indlæst, kan de tabeller og felter, som du har valgt, ses i ruden **Felter**.

![Skærmbillede af ruden Felter efter indlæsning af en tabel fra vinduet Navigator.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Brug Azure Consumption Insights
Hvis du vil bruge **Azure Consumption Insights**-connectoren, skal du have adgang til Enterprise-funktionerne på Azure Portal.

Når du har indlæst data ved hjælp af **Azure Consumption Insights**-connectoren, kan du oprette dine egne brugerdefinerede målinger og kolonner ved hjælp af **Forespørgselseditoren**. Du kan også oprette visualiseringer, rapporter og dashboards med henblik på deling i **Power BI-tjenesten**.

Hvis du har en tom forespørgsel, kan du hente et eksempel på en Azure-samling med brugerdefinerede forespørgsler. Der er to måder, du kan gøre dette på: 

I **Power BI Desktop**: 

1. Vælg båndet **Start** 
2. Vælg **Hent data** > **Tom forespørgsel** 

Eller i **Forespørgselseditor**: 

1. Højreklik i ruden **Forespørgsler** til venstre 
2. Vælg **Ny forespørgsel > Tom forespørgsel** i den viste menu

Skriv følgende i **formellinjen**:

    = MicrosoftAzureConsumptionInsights.Contents

Følgende billede viser en eksemelsamling, der kommer frem.

![Skærmbillede af samling af eksempler.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

Når du arbejder med rapporter og opretter forespørgsler, kan du gøre følgende:

* Hvis du vil definere antallet af måneder fra og med dags dato, skal du bruge *numberOfMonth*
  * Brug en værdi mellem 1 og 36. Repræsenter antallet af måneder – fra dags dato – du vil importere. Det anbefales, at du ikke får data for mere end 12 måneder. Med denne grænse undgår du begrænsninger for import af Power BI-forespørgsler og tærskler for datamængde.
* Hvis du vil definere en månedsperiode i et historisk tidsvindue, skal du bruge *startBillingDataWindow* og *endBillingDataWindow*
* Brug ikke *numberOfMonth* sammen med *startBillingDataWindow* eller *endBillingDataWindow*

## <a name="migrate-from-the-azure-enterprise-connector"></a>Migrer fra Azure Enterprise Connector

Nogle kunder har oprettet visualiseringer ved hjælp af *Azure Enterprise Connector (beta)* . Den bliver på et tidspunkt erstattet med **Azure Consumption Insights**-connectoren. Den nye connector indeholder funktioner og forbedringer, der omfatter:

* Flere tilgængelige datakilder for *Saldooversigt* og *Køb fra Marketplace*
* Nye og avancerede parametre, f.eks. *startBillingDataWindow* og *endBillingDataWindow*
* Bedre ydeevne og svartid

I de næste trin kan du se, hvordan du overgår til **Azure consumption Insights**-connectoren. Med disse trin bevares det arbejde, du allerede har udført med at oprette brugerdefinerede dashboards eller rapporter.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>Trin 1: Opret forbindelse til Azure ved hjælp af den nye connector
Det første trin er at bruge den **Azure Consumption Insights**-connector, som blev detaljeret beskrevet tidligere i denne artikel. I dette trin skal du vælge **Hent data > Tom forespørgsel** på båndet **Hjem** i **Power BI Desktop**.

### <a name="step-2-create-a-query-in-advanced-editor"></a>Trin 2: Opret en forespørgsel i Avanceret editor
I **Forespørgselseditor** skal du vælge **Avanceret editor** i sektionen **Forespørgsel** på båndet **Start**. Angiv følgende forespørgsel i vinduet **Avanceret editor**, der vises:

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![Skærmbillede af en dialogboks til at oprette en forespørgsel i den avancerede editor.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

Du skal udskifte værdien *enrollmentNumber* med dit tilmeldingsnummer. Du kan se dit nummer på [Azure Enterprise Portal](https://ea.azure.com). Parameteren *numberOfMonth* angiver, hvor mange måneder med data du vil gå tilbage i forhold til den aktuelle dato. Brug (0) for den aktuelle måned.

Når du har valgt **Udført** i vinduet **Avanceret editor**, opdateres eksempelvisningen, og der vises data fra det angivne månedsinterval i tabellen. Vælg **Luk og anvend**, og vend tilbage.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>Trin 3: Flyt målinger og brugerdefinerede kolonner til den nye rapport
Derefter skal du flytte de brugerdefinerede kolonner eller målinger, du har oprettet, til den nye detaljetabel. Her er trinnene.

1. Åbn Notesblok (eller en anden teksteditor).
2. Vælg den måling, der skal flyttes, kopiér teksten fra feltet *Formel*, og indsæt den i Notesblok.

   ![Skærmbillede, der viser formelfeltet for kolonner og målinger.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Omdøb *Query1* til navnet på den oprindelige detaljetabel.
4. Hvis du vil oprette nye tabelmålinger og brugerdefinerede kolonner, skal du højreklikke på tabellen og vælge **Ny måling**. Klip og indsæt derefter dine gemte målinger og kolonner, indtil du er færdig.

### <a name="step-4-relink-tables-that-had-relationships"></a>Trin 4: Sammenkæd igen tabeller, der havde relationer
Mange dashboards indeholder flere tabeller, der bruges til opslag eller filtrering, f.eks. datotabeller eller tabeller til brugerdefinerede projekter. De kan løse de fleste andre problemer ved at genoprette disse relationer. Her kan du se, hvordan du gør.

- Under fanen **Udformning** i **Power BI Desktop** skal du vælge **Administrer relationer** for at åbne et vindue, hvor du kan oprette relationer i modellen. Sammenkæd igen tabellerne efter behov.

    ![Skærmbillede af dialogboksen Opret relation. Vælg Administrer relationer.](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>Trin 5: Kontrollér dine visualiseringer, og juster feltformatering efter behov
På nuværende tidspunk burde de fleste af dine oprindelige visualiseringer, tabeller og detailudledninger fungere som forventet. Nogle små finjusteringer kan være nødvendige, før du kan formatere udseende og funktionalitet præcist. Brug lidt tid på at gennemse dine dashboards og visualiseringer for at sikre, at de ser ud som ønsket.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Brug ACI-API'en (Azure Consumption and Insights) til at hente forbrugsdata
Azure leverer også [**ACI-API'en (Azure Consumption and Insights)** ](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/). Du kan oprette dine egne brugerdefinerede løsninger til indsamling, rapportering og visualisering af oplysninger om Azure-forbrug ved hjælp af ACI-API'en.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Tilknyt navne og brugsoplysninger mellem portalen, connectoren og API'en
Kolonnerne og navnene på oplysninger på Azure Portal svarer til dem i API'en og connectoren, selvom de ikke altid er identiske. Som en hjælp til at afklare dette indeholder følgende tabel en oversigt. Det angives også, om kolonnen er forældet. Du kan finde flere oplysninger om og definitioner på disse vilkår i [ordbog over Azure-faktureringsdata](/azure/billing/billing-enterprise-api-usage-detail).

| ACI-connector/ContentPack ColumnName | Kolonnenavn for ACI-API | Kolonnenavn for EA | Forældet/vises for bagudkompatibilitet |
| --- | --- | --- | --- |
| AccountName |accountName |Kontonavn |Nej |
| AccountId |accountId | |Ja |
| AccountOwnerId |accountOwnerEmail |AccountOwnerId |Nej |
| AdditionalInfo |additionalInfo |AdditionalInfo |Nej |
| AdditionalInfold | | |Ja |
| Forbrugt antal |consumedQuantity |Forbrugt antal |Nej |
| Forbrugt tjeneste |consumedService |Forbrugt tjeneste |Nej |
| ConsumedServiceId |consumedServiceId | |Ja |
| Cost |cost |ExtendedCost |Nej |
| Omkostningssted |costCenter |Omkostningssted |Nej |
| Dato |dato |Dato |Nej |
| Dag | |Dag |Nej |
| DepartmentName |departmentName |Navn på afdeling |Nej |
| DepartmentID |departmentId | |Ja |
| Forekomst-id | | |Ja |
| InstanceId |instanceId |Forekomst-id |Nej |
| Placering | | |Ja |
| Målerkategori |meterCategory |Målerkategori |Nej |
| Måler-id | | |Ja |
| Målernavn |meterName |Målernavn |Nej |
| Målerområde |meterRegion |Målerområde |Nej |
| Målerunderkategori |meterSubCategory |Målerunderkategori |Nej |
| MeterId |meterId |Måler-id |Nej |
| Måned | |Måned |Nej |
| Produkt |product |Produkt |Nej |
| ProductId |productId | |Ja |
| Ressourcegruppe |resourceGroup |Ressourcegruppe |Nej |
| Placering af ressource |resourceLocation |Placering af ressource |Nej |
| ResourceGroupId | | |Ja |
| ResourceLocationId |resourceLocationId | |Ja |
| ResourceRate |resourceRate |ResourceRate |Nej |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |Nej |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |Nej |
| ServiceInfo1Id | | |Ja |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |Nej |
| ServiceInfo2Id | | |Ja |
| Store Service-id |storeServiceIdentifier |Store Service-id |Nej |
| StoreServiceIdentifierId | | |Ja |
| Navn på abonnement |subscriptionName |Navn på abonnement |Nej |
| Tags |tags |Tags |Nej |
| TagsId | | |Ja |
| Måleenhed |unitOfMeasure |Måleenhed |Nej |
| År | |År |Nej |
| SubscriptionId |subscriptionId |SubscriptionId |Ja |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |Nej |


## <a name="next-steps"></a>Næste trin

Du kan oprette forbindelse til mange forskellige datakilder ved hjælp af Power BI Desktop. Du kan få flere oplysninger i følgende artikler:

* [Opret forbindelse til Azure Cost Management-data i Power BI Desktop](desktop-connect-azure-cost-management.md)
* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Opret forbindelse til Excel-projektmapper i Power BI Desktop](desktop-connect-excel.md)   
* [Angiv data direkte i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)