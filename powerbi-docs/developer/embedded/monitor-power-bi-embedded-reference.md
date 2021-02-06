---
title: Overvågning af Power BI Embedded data reference
description: Vigtig referencemateriale, der skal bruges, når du overvåger Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: subject-monitoring
ms.date: 01/14/2021
ms.openlocfilehash: 9c07e75736b3ccdb33bf76f79656a8982cddb6d8
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617013"
---
# <a name="monitoring-power-bi-embedded-data-reference"></a>Overvågning af Power BI Embedded data reference

Se [Monitor Power bi Embedded](monitor-power-bi-embedded.md) for at få oplysninger om, hvordan du indsamler og analyserer overvågningsdata for Power bi Embedded.

## <a name="metrics"></a>Metrikværdier

Dette afsnit indeholder en liste over alle de automatisk indsamlede platforms metrikværdier, der indsamles for Power BI Embedded.  

|Metrik type | Navneområde for ressource udbyder/type<br/> og link til individuelle målepunkter |
|-------|-----|
| Kapaciteter | [Microsoft. PowerBIDedicated/kapaciteter](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities) |

### <a name="capacities"></a>Kapaciteter

Ressource udbyder, og skriv: [Microsoft. PowerBIDedicated/kapaciteter](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities)

| Name | Metrikværdi | Enhed | Beskrivelse |
|:---|:-------|:-----|:------------|
|Hukommelse (Gen1) |memory_metric               |Byte        |Hukommelsesresidente. Område 0-3 GB for a1, 0-5 GB for a2, 0-10 GB for a3, 0-25 GB for A4, 0-50 GB for A5 og 0-100 GB for A6. Understøttes kun for Power BI Embedded generation 1-ressourcer. |
|Hukommelse udskiftning (datasæt) (Gen1) |memory_thrashing_metric     |Procent      |Gennemsnitlig hukommelse udskiftning. Understøttes kun for Power BI Embedded generation 1-ressourcer. |
|QPU-stor udnyttelse (Gen1) |qpu_high_utilization_metric |Antal        |QPU høj udnyttelse i løbet af det seneste minut, 1 for stor QPU udnyttelse, ellers til 0. Understøttes kun for Power BI Embedded generation 1-ressourcer. |
|Forespørgsels varighed (datasæt) (Gen1) |QueryDuration               |Millisekunder |Varighed af DAX-forespørgsel i sidste interval. Understøttes kun for Power BI Embedded generation 1-ressourcer. |
|Kølængde for forespørgsels pulje (datasæt) (Gen1) |QueryPoolJobQueueLength     |Antal        |Antal job i køen i forespørgsels trådgruppen. Understøttes kun for Power BI Embedded generation 1-ressourcer. |

## <a name="metric-dimensions"></a>Metriske dimensioner

Du kan finde flere oplysninger om, hvilke metrik dimensioner der er, under [flerdimensionelle målepunkter](/azure/azure-monitor/platform/data-platform-metrics#multi-dimensional-metrics).

Power BI Embedded har ingen målepunkter, der indeholder dimensioner.

## <a name="resource-logs"></a>Ressource logge

Dette afsnit indeholder en liste over de typer ressource logge, du kan indsamle til Power BI Embedded.

Du kan finde oplysninger på en liste over [alle kategorityper for ressource logfiler, der understøttes i Azure Monitor](/azure/azure-monitor/platform/resource-logs-schema).

Dette afsnit indeholder en liste over alle de kategorityper for ressource logge, der er indsamlet for Power BI Embedded.  

|Ressource logtype | Navneområde for ressource udbyder/type<br/> og link til individuelle målepunkter |
|-------|-----|
| Kapaciteter | [Microsoft. PowerBIDedicated/kapaciteter](/azure/azure-monitor/platform/resource-logs-categories#microsoftpowerbidedicatedcapacities) |

## <a name="azure-monitor-logs-tables"></a>Azure Monitor logs tabeller

Dette afsnit refererer til alle de Azure Monitor logs Kusto-tabeller, der er relevante for Power BI Embedded og tilgængelige for en forespørgsel efter Log Analytics.

|Ressourcetype | Noter |
|-------|-----|
| [Power BI Embedded](/azure/azure-monitor/reference/tables/tables-resourcetype#power-bi-embedded) |Se en liste over tabeller nedenfor |

### <a name="power-bi-embedded"></a>Power BI Embedded

| Tabel |  Beskrivelse |
|:---------|:-------------|------------------|
| [AzureActivity](/azure/azure-monitor/reference/tables/azureactivity) | Poster fra Azure-aktivitets loggen, der giver indsigt i alle hændelser på abonnements niveau eller administrationsgruppe niveau, som er opstået i Azure.    |                             |                                                   | 
| [AzureDiagnostics](/azure/azure-monitor/reference/tables/azurediagnostics)   | Lagrer ressource logge til Azure-tjenester, der bruger Azure Diagnostic mode. Ressource logge beskriver den interne funktion af Azure-ressourcer. |
| [AzureMetrics](/azure/azure-monitor/reference/tables/azuremetrics)   | Metrik data, der udsendes af Azure-tjenester, og som måler deres tilstand og ydeevne. |

Hvis du vil have en reference til alle Azure Monitor logs/Log Analytics-tabeller, skal du se [referencen til referencen til Azure monitors tabellen](/azure/azure-monitor/reference/tables/tables-resourcetype).

## <a name="activity-log"></a>Aktivitetslog

Du kan vælge **Program** og/eller **Alle målepunkter**-kategorierne.

### <a name="engine"></a>Program

Motor kategorien giver ressourcen besked om at logføre de hændelser, der er angivet nedenfor. For hver hændelse er der egenskaber.

|     Hændelsesnavn     |     Hændelsesbeskrivelse     |
|----------------------------|----------------------------------------------------------------------------------|
|    Overvågningslogon    |    Registrerer alle nye forbindelse til programhændelserne, siden sporingen startede.    |
|    Sessionsinitialisering    |    Registrerer alle sessionsinitialiseringshændelser, siden sporingen startede.    |
|    Start af VertiPaq-forespørgsel    |    Registrerer alle VertiPaq SE-forespørgsler, siden sporingen startede.    |
|    Forespørgselsstart    |    Registrerer alle starthændelser for forespørgsler, siden sporingen startede.    |
|    Forespørgselsophør    |    Registrerer alle ophørshændelser for forespørgsler, siden sporingen startede.    |
|    Ophør af VertiPaq-forespørgsel    |    Registrerer alle ophørshændelser for VertiPaq SE-forespørgsler, siden sporingen startede.    |
|    Overvågningslogout    |    Registrerer alle afbrydelser af forbindelse til programhændelserne, siden sporingen startede.    |
|    Error    |    Registrerer alle programfejlhændleser, siden sporingen startede.    |

#### <a name="event-example"></a>Eksempel på hændelse

I nedenstående tabel vises et eksempel på en hændelse.

| Navn på egenskab | Eksempel på ophør af VertiPaq-forespørgsel | Beskrivelse af egenskab |
|---|---|---|
| EventClass | XM_SEQUERY_END | Hændelsesklasse bruges til at kategorisere hændelser. |
| Hændelsesunderklasse | 0 | Hændelsesunderklasse giver yderligere oplysninger om hver enkelt hændelsesklasse. (Eksempel: 0: VertiPaq-scanning) |
| RootActivityId | ff217fd2-611d-43c0-9c12-19e202a94f70 | Id for rodaktivitet. |
| CurrentTime | 2018-04-06T18:30:11.9137358Z | Tidspunkt, hvor hændelsen startede, når det er tilgængeligt. |
| StartTime | 2018-04-06T18:30:11.9137358Z | Tidspunkt, hvor hændelsen startede, når det er tilgængeligt. |
| JobID | 0 | Job-id for status. |
| ObjectID | 464 | Objekt-id |
| ObjectType | 802012 | ObjectType |
| EndTime | 2018-04-06T18:30:11.9137358Z | Tidspunkt, hvor hændelsen ophørte. |
| Varighed | 0 | Tid (i millisekunder), der optages af hændelsen. |
| SessionType | Bruger | Sessionstype (hvilken enhed udløste handlingen). |
| ProgressTotal | 0 | Total status. |
| IntegerData | 0 | Heltalsdata. |
| Severity | 0 | Niveau for alvorsgrad for en undtagelse. |
| Vellykket | 1 | 1 = succes. 0 = fejl (1 betyder f.eks., at tilladelseskontrol er udført uden fejl, og 0 betyder, at der er fejl i denne kontrol). |
| Error | 0 | Fejlnummer for en given hændelse. |
| ConnectionID | 3 | Entydigt forbindelses-id. |
| DatasetID | 5eaa550e-06ac-4adf-aba9-dbf0e8fd1527 | Id'et for det datasæt, som brugerens erklæring kører på. |
| SessionID | 3D063F66-A111-48EE-B960-141DEBDA8951 | Sessions-GUID. |
| SPID | 180 | Serverproces-id. Dette identificerer entydigt en brugersession. Dette svarer direkte til det sessions-GUID, der anvendes af XML/A. |
| ClientProcessID | null | Proces-id for klientprogrammet. |
| ApplicationName | null | Navnet på det klientprogram, der oprettede forbindelse til serveren. |
| CapacityName | pbi641fb41260f84aa2b778a85891ae2d97 | Navnet på Power BI Embedded-kapacitetsressourcen. |

### <a name="allmetrics"></a>Alle målepunkter

Når indstillingen **Alle målepunkter** er markeret, logføres data for alle de målepunkter, du kan bruge med en Power BI Embedded-ressource.

I følgende tabel vises de handlinger, der er relateret til Power BI Embedded, som kan oprettes i aktivitets loggen.

## <a name="schemas"></a>Skemaer

Power BI Embedded bruger det **Power bi dedikerede** skema.

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Overvåg Azure-Power BI Embedded](monitor-power-bi-embedded.md)

>[!div class="nextstepaction"]
>[Logføring af Azure-ressourcediagnosticering](/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

>[!div class="nextstepaction"]
>[Set-AzureRmDiagnosticSetting](/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting)
