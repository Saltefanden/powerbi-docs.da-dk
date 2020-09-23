---
title: 'Selvstudium: Kombiner data fra Excel og et OData-feed i Power BI Desktop'
description: 'Selvstudium: Kombiner data fra Excel og et OData-feed'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 0401fecc91aef03c0b9e0767bfb241cd701ff50b
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90853741"
---
# <a name="tutorial-analyze-sales-data-from-excel-and-an-odata-feed"></a>Selvstudium: Analysér salgsdata fra Excel og et OData-feed

Det er almindeligt at have data i flere datakilder. Du kan f.eks. have to databaser: én til produktoplysninger og én til salgsoplysninger. Med *Power BI Desktop* kan du kombinere data fra forskellige kilder og oprette interessante, overbevisende dataanalyser og visualiseringer.

I dette selvstudium kombinerer du data fra to datakilder:

* En Excel-projektmappe med produktoplysninger
* Et OData-feed, der indeholder ordredata

Du skal importere hvert datasæt og udføre transformations- og sammenlægningshandlinger. Derefter skal bruge du de to kilders data til at udarbejde en salgsanalyserapport med interaktive visualiseringer. Du kan senere anvende disse teknikker til SQL Server-forespørgsler, CSV-filer og andre datakilder i Power BI Desktop.

>[!NOTE]
>I Power BI Desktop kan du som regel udføre den samme opgave på flere måder. Du kan f.eks. højreklikke på eller bruge menuen **Flere indstillinger** på en kolonne eller celle for at se yderligere båndvalg. Flere alternative metoder beskrives i nedenstående trin.

## <a name="import-excel-product-data"></a>Importér Excel-produktdata

Importér først produktdata fra Excel-projektmappen *Products.xlsx* til Power BI Desktop.

1. [Download Excel-projektmappen Products.xlsx](https://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx), og gem den som *Products.xlsx*.

1. Vælg pilen ud for **Hent data** under fanen **Hjem** på båndet i Power BI Desktop, og vælg derefter **Excel** i menuen **Mest almindelige**.

   ![Hent data](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)

   >[!NOTE]
   >Du kan også vælge selve menupunktet **Hent data** eller vælge **Hent data** fra Power BI-dialogboksen **Introduktion**, vælge **Excel** eller **Filer** > **Excel** i dialogboksen **Hent data** og derefter vælge **Opret forbindelse**.

1. I dialogboksen **Åbn** skal du gå til og vælge filen **Products.xlsx** og derefter vælge **Åbn**.

1. I **Navigator** skal du vælge tabellen **Products** og derefter vælge **Transformer data**.

   ![Ruden Navigator til Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

Der åbnes en forhåndsvisning af tabellen i Power-forespørgselseditor, hvor du kan anvende transformationer til at rydde op i dataene.

![Power Query-editor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)

>[!NOTE]
>Du kan også åbne Power-forespørgselseditor ved at vælge **Rediger forespørgsler** > **Rediger forespørgsler** på båndet **Hjem** i Power BI Desktop eller ved at højreklikke eller vælge **Flere indstillinger** ud for en hvilket som helst forespørgsel i **rapportvisning** og vælge **Rediger forespørgsel**.

## <a name="clean-up-the-products-columns"></a>Ryd op i produktkolonnerne

Din kombinerede rapport skal bruge kolonnerne **ProductID**, **ProductName**, **QuantityPerUnit** og **UnitsInStock** fra Excel-projektmappen. Du kan fjerne de andre kolonner.

1. I Power-forespørgselseditor skal du vælge kolonnerne **ProductID**, **ProductName**, **QuantityPerUnit** og **UnitsInStock**. Du kan bruge Ctrl til at vælge mere end én kolonne eller Skift til at vælge kolonner ved siden af hinanden.

1. Højreklik på en hvilken som helst af de valgte overskrifter. Vælg **Fjern andre kolonner** i rullemenuen.
   Du kan også vælge **Fjern kolonner** > **Fjern andre kolonner** i gruppen **Administrer kolonner** under fanen **Hjem** på båndet.

   ![Fjern andre kolonner](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-odata-feeds-order-data"></a>Importér ordredata fra OData-feed

Importér derefter ordredataene fra OData-feedet for eksempelsalgssystemet Northwind.

1. I Power-forespørgselseditor skal du vælge **Ny kilde** og derefter i rullemenuen **Mest almindelige** vælge **OData-feed**.

   ![Hent OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)

1. I dialogboksen **OData-feed** skal du indsætte URL-adressen til OData-feedet for Northwind, `https://services.odata.org/V3/Northwind/Northwind.svc/`. Vælg **OK**.

   ![Dialogboksen OData-feed](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)

1. I **Navigator** skal du vælge tabellen **Orders** og derefter vælge **Transformer data** for at indlæse data i Power-forespørgselseditor.

   ![Navigator til OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)

   >[!NOTE]
   >I **Navigator** kan du vælge et tabelnavn uden at markere afkrydsningsfeltet, hvis du vil have vist et eksempel.

## <a name="expand-the-order-data"></a>Udvid ordredataene

Du kan bruge tabelreferencer til at udarbejde forespørgsler, når du opretter forbindelse til datakilder med flere tabeller, f.eks. relationsdatabaser eller OData-feedet for Northwind. Tabellen **Orders** indeholder referencer til flere relaterede tabeller. Du kan bruge handlingen Udvid til at føje kolonnerne **ProductID**, **UnitPrice** og **Quantity** fra den relaterede tabel **Order_Details** til emnetabellen (**Orders**).

1. Rul til højre i tabellen **Orders**, indtil du ser kolonnen **Order_Details**. Den indeholder referencer til en anden tabel og ikke til data.

   ![Kolonnen Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/order-details-column.png)

1. Vælg ikonet **Udvid** (![ikonet Udvid](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) i kolonneoverskriften **Order_Details**.

1. I rullemenuen:

   1. Vælg **(Markér alle kolonner)** for at rydde alle kolonner.

   1. Vælg **ProductID**, **UnitPrice** og **Quantity**, og vælg derefter **OK**.

      ![Udvid rullemenuen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand-drop-down-menu.png)

Når du har udvidet tabellen **Order_Details**, erstatter tre nye indlejrede tabelkolonner kolonnen **Order_Details**. Der er nye rækker i tabellen for hver ordres tilføjede data.

![Udvidede kolonner](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expanded-columns.png)

## <a name="create-a-custom-calculated-column"></a>Opret en brugerdefineret beregnet kolonne

I Power-forespørgselseditor kan du oprette beregninger og brugerdefinerede felter for at forbedre dine data. Du opretter en brugerdefineret kolonne, der ganger enhedsprisen med antallet af varer for at beregne den samlede pris for hver ordres linjeelement.

1. På båndet under fanen **Tilføj kolonne** i Power-forespørgselseditor skal du vælge **Brugerdefineret kolonne**.

   ![Tilføjelse af en brugerdefineret kolonne](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/adding-a-custom-column.png)

1. I dialogboksen **Brugerdefineret kolonne** skal du skrive **LineTotal** i feltet **Nyt kolonnenavn**.

1. I feltet **Formel for brugerdefineret kolonne** efter **=** skal du angive **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** . Du kan også vælge feltnavnene fra rulleboksen **Tilgængelige kolonner** og vælge **<< Indsæt** i stedet for at skrive dem.

1. Vælg **OK**.

   ![Dialogboksen Brugerdefineret kolonne](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/custom-column-dialog-box.png)

   Det nye felt **LineTotal** vises som den sidste kolonne i tabellen **Orders**.

## <a name="set-the-new-fields-data-type"></a>Angiv datatypen for det nye felt

Når Power-forespørgselseditor opretter forbindelse til data, udfører det et bedste gæt om hvert felts datatype med henblik på visning. Et overskriftsikon angiver den tildelte datatype for hvert felt. Du kan også se **Datatype** på båndet under fanen **Hjem** og gruppen **Transformér**.

Din nye kolonne **LineTotal** har datatypen **Hvilken som helst**, men den har valutaværdier. Hvis du vil tildele en datatype, skal du højreklikke på kolonneoverskriften **LineTotal**, vælge **Skift type** i rullemenuen og derefter vælge **Fast decimaltal**.

![Skift datatypen til en fast decimal](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/change-data-type-to-fixed-decimal.png)

>[!NOTE]
>Du kan også vælge kolonnen **LineTotal**, vælge pilen ud for **Datatype** i området **Transformer** under fanen **Hjem** på båndet og derefter vælge **Fast decimaltal**.

## <a name="clean-up-the-orders-columns"></a>Ryd op i ordrekolonner

Du kan gøre det nemmere at arbejde med modellen ved at slette, omdøbe og omarrangere nogle kolonner.

Følgende kolonner skal bruges i rapporten:

* **OrderDate**
* **ShipCity**
* **ShipCountry**
* **Order_Details.ProductID**
* **Order_Details.UnitPrice**
* **Order_Details.Quantity**
* **LineTotal**

Markér disse kolonner, og brug **Fjern andre kolonner**, som du gjorde med Excel-dataene. Du kan også markere de kolonner, der ikke er angivet, højreklikke på en af dem og vælge **Fjern kolonner**.

Du kan omdøbe kolonnerne med præfikset "**Order_Details.** " for at gøre dem nemmere at læse:

1. Dobbeltklik, eller tryk og hold nede, på de enkelte kolonneoverskrifter, eller højreklik på kolonneoverskriften, og vælg **Omdøb** i rullemenuen.

1. Slet præfikset **Order_Details.** præfiks fra hvert navn.

Endelig kan du nemmere få adgang til kolonnen **LineTotal** ved at trække og slippe den til venstre umiddelbart til højre for kolonnen **ShipCountry**.

![Tabel, der er ryddet op](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/cleaned-up-table.png)

## <a name="review-the-query-steps"></a>Gennemse forespørgselstrinnene

De handlinger, du bruger til at forme og transformere data med Power-forespørgselseditor, registreres. Hver handling vises til højre i ruden **Forespørgselsindstillinger** under **Anvendte trin**. Du kan gå tilbage gennem **Anvendte trin** for at gennemse trinnene og redigere, slette eller omarrangere dem, hvis det er nødvendigt. Ændring af foregående trin er dog risikofyldt, da det kan afbryde senere trin.

Vælg alle dine forespørgsler på listen **Forespørgsler** i venstre side af Power-forespørgselseditor, og gennemse de **Anvendte trin** i **Forespørgselsindstillinger**. Når du har anvendt de tidligere datatransformationer, bør **Anvendte trin** for dine to forespørgsler se sådan ud:

![Anvendte trin for produktforespørgsel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/products-query-applied-steps.png) &nbsp;&nbsp; ![Anvendte trin for ordreforespørgsel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orders-query-applied-steps.png)

>[!TIP]
>Bagved Anvendte trin ligger der formler, som er skrevet på *Power-forespørgselssproget*, hvilket også er kendt som [M-sproget](/powerquery-m/power-query-m-reference). Hvis du vil se og redigere formlerne, skal du vælge **Avanceret editor** i gruppen **Forespørgsel** under fanen **Hjem** på båndet.

## <a name="import-the-transformed-queries"></a>Importér de transformerede forespørgsler

Når du er tilfreds med dine transformerede data og er klar til at importere dem til **rapportvisning** i Power BI Desktop, skal du vælge **Luk og anvend** > **Luk og anvend** under fanen **Hjem** på båndet under gruppen **Luk**.

![Luk og anvend](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Når dataene er indlæst, vises forespørgslerne på listen **Felter** i **rapportvisning** i Power BI Desktop.

![Forespørgsler på listen Felter](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/queries-in-fields-list.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Administrer relationen mellem datasæt

I Power BI Desktop er det ikke et krav, at du kombinerer forespørgsler for at oprette rapporter ud fra dem. Men du kan bruge relationerne mellem datasæt på baggrund af almindelige felter til at udvide og forbedre dine rapporter. Power BI Desktop kan registrere relationer automatisk, eller du kan oprette dem i Power BI Desktop-dialogboksen **Administrer relationer**. Det kan du finde flere oplysninger under [Opret og administrer relationer i Power BI Desktop](../transform-model/desktop-create-and-manage-relationships.md).

Med det delte felt `ProductID` oprettes der en relation mellem datasættene `Orders` og `Products` i dette selvstudium.

1. I **rapportvisning** i Power BI Desktop skal du vælge **Administrer relationer** under fanen **Hjem** på båndet under området **Relationer**.

   ![Båndet Administrer relationer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)

1. I dialogboksen **Administrer relationer** kan du se, at Power BI Desktop allerede har registreret og angivet en aktiv relation mellem tabellerne **Products** og **Orders**. Vælg **Rediger** for at få vist relationen.

   ![Dialogboksen Administrer relationer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)

   **Rediger relationer** åbnes og viser oplysninger om relationen.  

   ![Dialogboksen Rediger relation](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)

1. Power BI Desktop har automatisk registreret relationen korrekt, så du kan vælge **Annuller** og derefter **Luk**.

I venstre side i Power BI Desktop skal du vælge **Model** for at få vist og administrere forespørgselsrelationer. Dobbeltklik på pilen på den linje, der forbinder de to forespørgsler, for at åbne dialogboksen **Rediger relation** og få vist eller ændre relationen.

![Relationsvisning](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Hvis du vil vende tilbage til **rapportvisningen** fra **modelvisningen**, skal du vælge ikonet **Rapport**.

![Ikonet Rapportvisning](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Opret visualiseringer ved hjælp af dine data

Du kan oprette forskellige visualiseringer i Gennemse visning i Power BI Desktop for at få indsigt i data. Der kan være flere sider i rapporter, og der kan være flere visualiseringer på hver side. Du og andre kan interagere med visualiseringerne for at analysere og forstå dataene. Du kan finde flere oplysninger i [Interager med en rapport i Redigeringsvisning i Power BI-tjenesten](../create-reports/service-interact-with-a-report-in-editing-view.md).

Du kan både bruge dine datasæt og relationen mellem dem, når du vil visualisere og analysere dine salgsdata.

Først skal du oprette et stablet søjlediagram, der bruger felter fra begge forespørgsler, for at vise antallet af hvert produkt, der er bestilt.

1. Vælg feltet **Quantity** fra **Orders** i ruden **Felter** til højre, eller træk det til et tomt område på lærredet. Der oprettes et stablet søjlediagram, hvor du kan se det samlede antal bestilte produkter.

1. Hvis du vil se, hvor mange der er bestilt af hvert produkt, skal du vælge **ProductName** under **Products** i ruden **Felter** eller trække det til diagrammet.

1. Hvis du vil sortere produkterne efter mest til mindst bestilt, skal du vælge ellipsen **Flere indstillinger** ( **...** ) øverst til højre i visualiseringen og derefter vælge **Sortér efter antal**.

1. Brug håndtagene i hjørnerne af diagrammet til at udvide det, så flere produktnavne bliver synlige.

   ![Liggende søjlediagram med antal efter ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/quantity-by-productname-bar-chart.png)

Opret derefter et diagram, der viser ordrebeløbet i dollar (**LineTotal**) over tid (**OrderDate**).

1. Mens ingenting er markeret på lærredet, skal du vælge **LineTotal** fra **Orders** i ruden **Felter** eller trække det til en tom plads på lærredet. Det stablede søjlediagram viser det samlede ordrebeløb i dollar.

1. Markér det stablede diagram, og vælg derefter **OrderDate** fra **Orders**, eller træk det til diagrammet. I diagrammet vises nu linjetotaler for hver ordredato.

1. Træk i hjørnerne for at tilpasse størrelsen af visualiseringen og se flere data.

   ![Kurvediagrammet LineTotals efter OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-orderdate-line-chart.png)

   >[!TIP]
   >Hvis du kun får vist **Years** i diagrammet og kun tre datapunkter, skal du klikke på pilen ud for **OrderDate** i feltet **Akse** i ruden **Visualiseringer** og vælge **OrderDate** i stedet for **Datohierarki**.

Endelig skal du oprette en kortvisualisering, der viser ordrebeløb for de enkelte lande.

1. Mens ingenting er markeret på lærredet, skal du vælge **ShipCountry** fra **Orders** i ruden **Felter** eller trække det til en tom plads på lærredet. Power BI Desktop registrerer, at dataene er landenavne. Der oprettes derefter automatisk en kortvisualisering med et datapunkt for hvert land med ordrer.

1. Hvis datapunkterne skal afspejle mængden af ordrer for hvert land, skal du trække feltet **LineTotal** til kortet. Du kan også trække det til **Træk datafelter hertil** under **Størrelse** i ruden **Visualiseringer**. Størrelserne på cirklerne på kortet afspejler nu ordrebeløbene i dollar for de enkelte lande.

   ![Kortvisualiseringen LineTotals efter ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-shipcountry-map-visualization.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Arbejd med visualiseringerne i rapporten for at analysere yderligere

I Power BI Desktop kan du interagere med visualiseringer, som krydsfremhæver og filtrerer på tværs af hinanden for at vise yderligere tendenser. Du kan finde flere oplysninger i [Filtre og fremhævning i Power BI-rapporter](../create-reports/power-bi-reports-filters-and-highlighting.md).

På grund af relationen mellem dine forespørgsler påvirker interaktioner med én visualisering alle andre visualiseringer på siden.

Vælg cirklen for **Canada** på kortvisualiseringen. De to andre visualiseringer filtreres for at fremhæve linjetotalerne og ordremængderne for Canada.

![Salgsdata filtreret for Canada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/sales-data-filtered-for-canada.png)

Vælg et diagramprodukt af typen **Quantity by ProductName** for at se kortet og datodiagrammet filtreret til at afspejle produktets data. Vælg en diagramdato af typen **LineTotal by OrderDate** for at se kortet filtreret til at vise dataene for datoen.

>[!TIP]
>Hvis du vil fjerne en markering, skal du vælge den igen eller vælge en af de andre visualiseringer.

## <a name="complete-the-sales-analysis-report"></a>Færdiggør salgsanalyserapporten

I den færdige rapport kombineres data fra Excel-filen *Products.xlsx* og OData-feedet for Northwind i visualiseringer, der hjælper med at analysere forskellige landes ordreoplysninger, tidsrammer og produkter. Når din rapport er færdig, kan du [uploade den til Power BI-tjenesten](../create-reports/desktop-upload-desktop-files.md) og dele den med andre Power BI-brugere.

## <a name="next-steps"></a>Næste trin

* [Microsoft Learn til Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
* [Se videoer om Power BI Desktop](../fundamentals/desktop-videos.md)
* [Besøg Power BI-forummet](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Læs Power BI-bloggen](https://go.microsoft.com/fwlink/?LinkID=519327)