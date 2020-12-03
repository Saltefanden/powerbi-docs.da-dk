---
title: Fejlfinding i forbindelse med planlagt opdatering i Power BI Report Server
description: I denne artikel beskrives ressourcer, der er tilgængelige til fejlfinding i forbindelse med planlagt opdatering i Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: troubleshooting
ms.date: 11/01/2017
ms.openlocfilehash: 8cb8bf4e6d67f01f7bbdc4370d8a60691dba5a63
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418273"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Fejlfinding i forbindelse med planlagt opdatering i Power BI Report Server
I denne artikel beskrives ressourcer, der er tilgængelige til fejlfinding i forbindelse med planlagt opdatering i Power BI Report Server.

Efterhånden som problemer opstår, opdateres denne artikel med oplysninger for at hjælpe dig.

## <a name="common-issues"></a>Almindelige problemer
Følgende er de mest almindelige problemer, du kan støde på, når du forsøger at planlægge opdatering for en rapport. 

### <a name="driver-related-problems"></a>Driverrelaterede problemer
Hvis du opretter forbindelse til forskellige datakilder, kan det kræve tredjepartsdrivere, der skal installeres for at oprette forbindelse. Du vil ikke kun skulle installere dem på den computer, du bruger Power BI Desktop på, men du skal også sikre, at driveren er installeret på rapportserveren.

Driveren kan også være både 32 bit og 64 bit. Sørg for at installere 64-bit driveren, da Power BI Report Server er 64 bit.

Der henvises til producenten for at få flere oplysninger om, hvordan du installerer og konfigurerer tredjepartsdrivere.

### <a name="memory-pressure"></a>Hukommelsesbelastning
Der kan opstå belastning på hukommelsen, når rapporter kræver mere hukommelse til behandling og gengivelse. Planlagt opdatering af rapporter kan kræve en betydelig mængde hukommelse på computeren. Specielt til større rapporter. Belastning på hukommelsen kan medføre fejl i rapporter samt et potentielt nedbrud af selve rapportserveren.

Hvis du konstant oplever belastning på hukommelsen, kan det være en god ide at se på en scale-out-udrulning af rapportserveren for at fordele belastningen af ressourcer. Du kan også definere, at en given rapportserver bruges til opdatering af data med indstillingen `IsDataModelRefreshService` i rsreportserver.config. Med denne indstilling kan du definere en eller flere servere til at være frontend-server, der skal håndtere rapporter efter behov, og have et andet sæt af servere, der kun skal anvendes til planlagt opdatering.

Du kan finde oplysninger om, hvordan du overvåger en Analysis Services-forekomst, i [Overvåg en Analysis Services-forekomst](/sql/analysis-services/instances/monitor-an-analysis-services-instance).

Du kan finde oplysninger om hukommelsesindstillinger i Analysis Services under [Egenskaber for hukommelse](/sql/analysis-services/server-properties/memory-properties).

### <a name="kerberos-configuration"></a>Kerberos-konfiguration
Hvis du opretter forbindelse til en datakilde med Windows-legitimationsoplysninger, kan det kræve konfiguration af Kerberos-begrænset delegering for at kunne oprette forbindelse. Du kan finde flere oplysninger om, hvordan du konfigurerer Kerberos-begrænset delegering, under [Konfigurer Kerberos til at bruge Power BI-rapporter](configure-kerberos-powerbi-reports.md).

## <a name="known-issues"></a>Kendte problemer
Oplysninger om kendte problemer angives her, når de foreligger.

## <a name="configuration-settings"></a>Konfigurationsindstillinger
Følgende indstillinger kan bruges til at påvirke planlagt opdatering. Indstillinger, der er angivet i SQL Server Management Studio (SSMS), gælder for alle rapportservere inden for en scale-out-udrulning. Indstillinger, der er konfigureret i rsreportserver.config, gælder for den specifikke server, de er indstillet på.

**Indstillinger i SSMS:**

| Indstilling | Beskrivelse |
| --- | --- |
| MaxFileSizeMb |Maksimal filstørrelse for uploadede rapporter. Standard er 1000 MB (1 GB). Maksimal værdi er 2000 MB (2 GB). |
| ModelCleanupCycleMinutes |Definerer, hvor ofte modellen kontrolleres for at fjerne den fra hukommelsen. Standard er 15 minutter. |
| ModelExpirationMinutes |Definerer, hvor lang tid der går, før modellen udløber, baseret på tidspunkt for sidste brug, og den fjernes. Standard er 60 minutter. |
| ScheduleRefreshTimeoutMinutes |Definerer, hvor længe dataopdateringen kan vare for en tilstand. Standard er 120 minutter. Der er ingen øvre grænse. |

**Indstillinger i rsreportserver.config:**

```xml
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Værktøjer til fejlfinding
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Logfiler, der er relevante for planlagt opdatering af Power BI-rapporter
De logfiler, der indeholder oplysninger om planlagt opdatering, er RSPowerBI_logfiler. De er placeret i mappen LogFiles på placeringen for installation af rapportserveren. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Fejltilstand**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

**_Vellykket opdatering_* _

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

_ *Forkerte legitimationsoplysninger**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Aktivering af detaljeret logføring
Aktivering af detaljeret logføring i Power BI Report Server er den samme som for SQL Server Reporting Services.

1. Åbn `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. Skift **DefaultTraceSwitch** til **4** under `<system.diagnostics>`.
3. Skift **Komponenter** til **alle: 4** under `<RStrace>`. 

### <a name="executionlog"></a>ExecutionLog
Når en Power BI-rapport gengives, eller en plan til planlagt opdatering er udført, føjes nye poster til kørselsloggen i databasen. Disse poster er tilgængelige i visningen **ExecutionLog3** i rapportserverens katalogdatabase.

Afviklingslogposter for Power BI-rapporter adskiller sig fra poster til andre rapporttyper.

* TimeRendering-kolonner er altid 0. Gengivelse af Power BI-rapporter finder sted i browseren, ikke på serveren.
* Der er 2 anmodningstyper og efterfølgende elementhandlinger:
  * **Interaktiv**: Når en rapport vises.
    * **ASModelStream**: Når datamodellen streames til Analysis Services fra kataloget.
    * **ConceptualSchema**: Når brugeren klikker på visning af rapporten.
    * **QueryData**: Hver gang der anmodes om data fra klienten.
  * **Opdater cache**: Når en plan til planlagt opdatering er blevet udført.
    * **ASModelStream**: Når datamodellen streames til Analysis Services fra kataloget.
    * **DataRefresh**: Når data opdateres fra en eller flere datakilder.
    * **SaveToCatalog**: Når datamodellen gemmes i kataloget igen.

## <a name="analysis-services"></a>Analysis Services
Det kan ske, at du vil ændre Analysis Services for at foretage fejlfinding af problemer eller tilpasse hukommelsesgrænser.

> [!IMPORTANT]
> Disse indstillinger nulstilles, hver gang du opgraderer rapportserveren. Sørg for at gemme en kopi af dine ændringer og anvende dem igen, hvis det er nødvendigt.
> 
> 

### <a name="install-location"></a>Placering af installation
Der er følgende standardplacering til Power BI Report Server og Analysis Services.

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Konfiguration af indstillinger for Analysis Services (msmdsrv.ini)
I mappen `<install directory>\PBIRS\ASEngine` finder du filen *msmdsrv.ini*, som du kan bruge til at styre forskellige indstillinger for Analysis Services. Når du åbner denne fil, vil du med det samme se, at denne fil ikke har alle de indstillinger, du ville forvente i filen msmdsrv.ini. 

Dette skyldes, at den faktiske Analysis Services-proces, der køres af Power BI Report Server, startes i `<install directory>\PBIRS\ASEngine\workspaces`. I denne mappe vil se hele den *msmdsrv.ini*-fil, du er vant til. Det er vigtigt ikke at ændre filen i arbejdsområdemappen, eftersom den omskrives, når Analysis Services-processen startes. Hvis du vil styre en indstilling, skal du gøre dette ved at ændre msmdsrv.ini i mappen `<install directory>\PBIRS\ASEngine`.

Følgende indstillinger nulstilles, når Analysis Services-processen startes. Eventuelle ændringer, du har foretaget af disse, ignoreres.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Profiler den lokale Analysis Services-proces
En SQL Profiler-sporing kan køres på den lokale Analysis Services-proces til diagnoseformål. Gør følgende for at oprette forbindelse til den lokale forekomst af Analysis Services.

SQL Server Profiler Trace er inkluderet i download af [SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms).

1. Start **SQL Server Profiler** som administrator.
2. Vælg knappen **Ny sporing**.
3. Vælg **Analysis Services** i dialogboksen **Opret forbindelse til server**, og angiv **localhost:5132** som servernavn.
4. Vælg de hændelser, du vil hente, og vælg **Kør** i dialogboksen **Egenskaber for sporing**.

## <a name="lock-pages-in-memory-windows-privilege"></a>Windows-rettigheden Lås sider i hukommelsen
Hvis du finder ud af, at du ikke kan gengive en Power BI-rapport, kan det hjælpe at tildele rettigheden **Lås sider i hukommelsen** til den tjenestekonto, der kører Power BI-rapportserveren. Du kan finde flere oplysninger om, hvordan du konfigurerer **Lås sider i hukommelsen**, i [Windows-rettigheder, der er tildelt Analysis Services-tjenestekontoen](/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv).

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)