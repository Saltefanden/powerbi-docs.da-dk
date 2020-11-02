---
title: Dynamisk sikkerhed på rækkeniveau med Analysis Services-tabelmodel
description: Dynamisk sikkerhed på rækkeniveau med Analysis Services-tabelmodel i det lokale miljø
author: davidiseminger
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 047c4e7d71cbbae95f4b1f8067548d807421385d
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349592"
---
# <a name="implement-row-level-security-in-an-on-premises-analysis-services-tabular-model"></a>Implementer sikkerhed på rækkeniveau i en Analysis Services-tabelmodel i det lokale miljø

Ved hjælp af et eksempeldatasæt til gennemgang af nedenstående trin kan du i dette selvstudium se, hvordan du implementerer [**sikkerhed på rækkeniveau**](../admin/service-admin-rls.md) i en *Analysis Services-tabelmodel* i det lokale miljø og bruger den i en Power BI-rapport.

* Opret en ny sikkerhedstabel i [databasen AdventureworksDW2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Opret tabelmodellen med de nødvendige fakta- og dimensionstabeller
* Definer roller og tilladelser
* Modellen skal udrulles i en forekomst af en *Analysis Services-tabel*
* Opret en Power BI Desktop-rapport, der viser de data, som er tilpasset til den bruger, der har adgang til rapporten
* Udrul rapporten for *Power BI-tjenesten*
* Opret et nyt dashboard, der er baseret på rapporten
* Del dashboardet med dine kolleger

Dette selvstudium kræver [databasen AdventureworksDW2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Opgave 1: Opret brugersikkerhedstabellen, og definer datarelationen

Du finder mange artikler, som beskriver, hvordan du definerer dynamisk sikkerhed på rækkeniveau med *SSAS-tabelmodellen (SQL Server Analysis Services)* . I dette eksempel bruger vi [Implementér dynamisk sikkerhed ved hjælp af rækkefiltre](/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters).

Disse trin kræver brug af relationsdatabasen AdventureworksDW2012.

1. Opret tabellen `DimUserSecurity` i AdventureworksDW2012 som vist nedenfor. Du kan bruge [SSMS (SQL Server Management Studio)](/sql/ssms/download-sql-server-management-studio-ssms) til at oprette tabellen.

   ![Opret tabellen DimUserSecurity](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

1. Når du har oprettet og gemt tabellen, skal du oprette relationen mellem `DimUserSecurity`-tabellens `SalesTerritoryID`-kolonne og `DimSalesTerritory`-tabellens `SalesTerritoryKey`-kolonne som vist nedenfor.

   Højreklik på **DimUserSecurity** i SQL Server Management Studio, og vælg **Design** . Vælg derefter **Tabeldesigner** > **Relationer...** . Gem tabellen, når du er færdig.

   ![Relationer for fremmede nøgler](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

1. Føj brugere til tabellen. Højreklik på **DimUserSecurity** , og vælg **Rediger de første 200 rækker** . Når du har tilføjet brugere, skal tabellen `DimUserSecurity` se ud som i det følgende eksempel:

   ![Tabellen DimUserSecurity med eksempelbrugere](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)

   Du ser disse brugere i senere opgaver.

1. Derefter skal du oprette en *indre joinforbindelse* til tabellen `DimSalesTerritory`, der viser de områdeoplysninger, som er knyttet til brugeren. SQL-koden her opretter den indre joinforbindelse, og billedet viser, hvordan tabellen derefter ser ud.

    ```sql
    select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
    ```

   Den joinforbundne tabel viser, hvem der er ansvarlig for hvert salgsområde, takket være den relation, der blev oprettet i trin 2. Eksempelvis kan du se, at *Rita Santos* er ansvarlig for *Australien* .

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Opgave 2: Opret tabelmodellen med fakta- og dimensionstabeller

Når dit relations-data warehouse er på plads, skal du definere tabelmodellen. Du kan oprette modellen ved hjælp af [SQL Server Data Tools](/sql/ssdt/sql-server-data-tools) (SSDT). Du kan finde flere oplysninger i [Opret et nyt tabelmodelprojekt](/analysis-services/tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project).

1. Importér alle nødvendige tabeller i modellen som vist nedenfor.

    ![Importeret SQL Server til brug sammen med dataværktøjer](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

1. Når du har importeret de nødvendige tabeller, skal du definere rollen *SalesTerritoryUsers* med læsetilladelse. Vælg menuen **Model** i SQL Server Data Tools, og vælg derefter **Roller** . I **Rolleadministrator** skal du vælge **Ny** .

1. Under **Medlemmer** i **Rolleadministrator** skal du tilføje de brugere, som du definerede i tabellen `DimUserSecurity` i [Opgave 1](#task-1-create-the-user-security-table-and-define-data-relationship).

    ![Tilføj brugere i Rolleadministrator](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

1. Tilføj derefter de rette funktioner for tabellerne `DimSalesTerritory` og `DimUserSecurity` som vist nedenfor under fanen **Rækkefiltre** .

    ![Føj funktioner til Rækkefiltre](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

1. Funktionen `LOOKUPVALUE` returnerer værdier for en kolonne, hvor Windows-brugernavnet stemmer overens med det brugernavn, der returneres af funktionen `USERNAME`. Du kan derefter begrænse forespørgsler til de steder, hvor funktionen `LOOKUPVALUE` returnerede værdier, der stemmer overens med værdierne i den samme eller en relateret tabel. I kolonnen **DAX Filter** skal du skrive følgende formel:

    ```dax
        =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    ```

    I denne formel returnerer funktionen `LOOKUPVALUE` alle værdier for kolonnen `DimUserSecurity[SalesTerritoryID]`, hvor `DimUserSecurity[UserName]` er den samme som det brugernavn, der aktuelt er logget på Windows, og `DimUserSecurity[SalesTerritoryID]` er den samme som `DimSalesTerritory[SalesTerritoryKey]`.

    > [!IMPORTANT]
    > Når du bruger sikkerhed på rækkeniveau, understøttes DAX-funktionen [USERELATIONSHIP](/dax/userelationship-function-dax) ikke.

   Det sæt salgs `SalesTerritoryKey`er, `LOOKUPVALUE` returnerer, bruges derefter til at begrænse de rækker, der vises i `DimSalesTerritory`. Det er kun rækker, hvor værdien for `SalesTerritoryKey` findes i de id'er, som returneres af funktionen `LOOKUPVALUE`, der vises.

1. Tilføj følgende formular for tabellen `DimUserSecurity` i kolonnen **DAX Filter** :

    ```dax
        =FALSE()
    ```

    Denne formel angiver, at alle kolonner skal fortolkes som `false`, hvilket betyder, at kolonner i tabellen `DimUserSecurity` ikke kan forespørges.

Nu skal du behandle og udrulle modellen. Du kan finde flere oplysninger under [Udrul](/analysis-services/tutorial-tabular-1200/lesson-13-deploy).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Opgave 3: Tilføj datakilder i din datagateway i det lokale miljø

Når din tabelmodel er udrullet og klar til forbrug, skal du føje en datakildeforbindelse til din Analysis Services-tabelserver i det lokale miljø.

1. Hvis du vil give Power BI-tjenesten adgang til din analysetjeneste i det lokale miljø, skal du i dit miljø have installeret og konfigureret en [datagateway i det lokale miljø](service-gateway-onprem.md).

1. Når gatewayen er konfigureret korrekt, skal du oprette en datakildeforbindelse til din forekomst af *Analysis Services* -tabellen. Du kan finde flere oplysninger i [Administrer din datakilde – Analysis Services](service-gateway-enterprise-manage-ssas.md).

   ![Opret forbindelse til datakilde](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

Når denne procedure er fuldført, er gatewayen konfigureret og klar til at interagere med din Analysis Services-datakilde i det lokale miljø.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Opgave 4: Opret en rapport, der er baseret på Analysis Services-tabelmodellen, ved hjælp af Power BI Desktop

1. Start Power BI Desktop, og vælg **Hent data** > **Database** .

1. På listen over datakilder skal du vælge **SQL Server Analysis Services-databasen** og vælge **Opret forbindelse** .

   ![Opret forbindelse til SQL Server Analysis Services-databasen](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

1. Udfyld dine oplysninger i din forekomst af Analysis Services-tabellen, og vælg **Opret liveforbindelse** . Vælg derefter **OK** .
  
   ![Detaljer om Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   I Power BI fungerer dynamisk sikkerhed kun sammen med en direkte forbindelse.

1. Du kan se, at den udrullede model er i Analysis Services-forekomsten. Vælg den pågældende model, og vælg derefter **OK** .

   I Power BI Desktop vises nu alle tilgængelige felter til højre for lærredet i ruden **Felter** .

1. I ruden **Felter** skal du vælge målingen **SalesAmount** i tabellen **FactInternetSales** og dimensionen **SalesTerritoryRegion** i tabellen **SalesTerritory** .

1. For at holde rapporten simpel tilføjer vi ikke flere kolonner lige nu. Hvis du vil have en mere meningsfuld datavisning, kan du ændre visualiseringen til et **kransdiagram** .

   ![Visualiseringen Kransediagram](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

1. Når rapporten er klar, kan du udgive den direkte på Power BI-portalen. På båndet **Hjem** i Power BI Desktop skal du vælge **Publicer** .

## <a name="task-5-create-and-share-a-dashboard"></a>Opgave 5: Opret og del et dashboard

Du har oprettet rapporten og publiceret den i **Power BI** -tjenesten. Nu kan du bruge det eksempel, der blev oprettet i forrige trin til at demonstrere modelsikkerhedsscenariet.

I sin rolle som *salgschef* kan brugeren Grace se data fra alle de forskellige salgsområder. Grace opretter denne rapport og publicerer den i Power BI-tjenesten. Denne rapport blev oprettet i de foregående opgaver.

Når Grace udgiver rapporten, er det næste trin at oprette et dashboard i Power BI-tjenesten med navnet *TabularDynamicSec* på baggrund af denne rapport. På det følgende billede skal du lægge mærke til, at Grace kan se de data, der svarer til hele salgsområdet.

   ![Dashboard for Power BI-tjeneste](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

Nu deler Grace dashboardet med sin kollega, Rita, der er ansvarlig for salg i området Australien.

   ![Del et Power BI-dashboard](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

Når Rita logger på Power BI-tjenesten og ser det delte dashboard, som Grace har oprettet, er det kun salg fra området Australien, der er synligt.

Tillykke! Power BI-tjenesten viser den dynamiske sikkerhed på rækkeniveau, der er defineret i Analysis Services-tabelmodellen i det lokale miljø. Power BI bruger egenskaben `EffectiveUserName` til at sende de aktuelle Power BI-brugeroplysninger til datakilden i det lokale miljø for at køre forespørgslerne.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Opgave 6: Forstå, hvad der sker i baggrunden

Denne opgave forudsætter, at du kender [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler), da du skal registrere en SQL Server Profiler-sporing på din lokale forekomst af SSAS-tabellen.

Sessionen initialiseres, så snart brugeren Rita får adgang til dashboardet i Power BI-tjenesten. Du kan se, at rollen **salesterritoryusers** træder i kraft med det samme og bruger det gældende brugernavn **<EffectiveUserName>rita@contoso.com</EffectiveUserName>**
```
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>rita@contoso.com</EffectiveUserName></PropertyList>
```
Baseret på anmodningen om gældende brugernavn konverterer Analysis Services anmodningen til de faktiske `contoso\rita`-legitimationsoplysninger, efter at der er sendt en forespørgsel til det lokale Active Directory. Når Analysis Services får legitimationsoplysningerne, returnerer Analysis Services de data, brugeren har tilladelse til at få vist og adgang til.

Hvis der forekommer mere aktivitet på dashboardet, kan du med SQL Profiler se en bestemt forespørgsel, der vender tilbage til Analysis Services-tabelmodellen som en DAX-forespørgsel. Hvis Rita f. eks. går fra dashboardet til den underliggende rapport, udføres følgende forespørgsel.

   ![DAX-forespørgsel vender tilbage til Analysis Services-model](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

Nedenfor kan du også se den DAX-forespørgsel, der udføres for at udfylde rapportdataene.
   
   ```dax
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>rita@contoso.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Overvejelser

* I det lokale miljø er sikkerhed på rækkeniveau med Power BI kun tilgængelig med en direkte forbindelse.

* Eventuelle ændringer af dataene efter behandling af modellen er øjeblikkeligt tilgængelige for brugere, der har adgang til rapporten via en direkte forbindelse, fra Power BI-tjenesten.
