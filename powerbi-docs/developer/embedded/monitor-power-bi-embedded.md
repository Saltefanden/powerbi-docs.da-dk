---
title: Overvåg Power BI Embedded
description: Start her for at få mere at vide om, hvordan du overvåger Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: 1b8ebbd7913bc5763f9f4dd8576fbc4783e8d531
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690743"
---
# <a name="monitor-power-bi-embedded"></a>Overvåg Power BI Embedded

Når du har kritiske programmer og forretningsprocesser afhængig af Azure-ressourcer, vil du overvåge disse ressourcer for deres tilgængelighed, ydeevne og drift. I denne artikel beskrives de overvågningsdata, der genereres af Power BI Embedded, og hvordan du kan bruge funktionerne i Azure Monitor til at analysere og advare på disse data.

## <a name="monitor-overview"></a>Oversigt over overvågning

**Oversigts** siden i Azure-Portal for hver *Power bi Embedded* instans indeholder følgende oplysninger:

* **Ressourcegruppe** – den [ressourcegruppe](/azure/azure-resource-manager/management/overview#resource-groups) , som forekomsten tilhører
* **Status** -status for din Power bi Embedded forekomst
* **Placering** – placeringen af den Power bi Embedded forekomst
* **Ressourcenavn** -navnet på din Power bi Embedded forekomst
* **SKU** – den SKU, som Power bi Embedded instans bruger
* **Abonnementsnavn** -navn på dit Power bi Embedded forekomst-abonnement
* **Abonnements-id** -ABONNEMENTS-id'et for din Power bi Embedded forekomst

## <a name="what-is-azure-monitor"></a>Hvad er Azure Monitor?

*Power bi Embedded* opretter overvågningsdata ved hjælp af [Azure Monitor](/azure/azure-monitor/overview), som er en fuld stack-overvågnings tjeneste i Azure, der indeholder et komplet sæt funktioner til overvågning af dine Azure-ressourcer ud over ressourcer i andre skyer og i det lokale miljø.

Start med artiklen [overvågning af Azure-ressourcer med Azure Monitor](/azure/azure-monitor/insights/monitor-azure-resource), som beskriver følgende begreber:

- Hvad er Azure Monitor?
- Omkostninger i forbindelse med overvågning
- Overvågning af data, der er indsamlet i Azure
- Konfigurerer dataindsamling
- Standard værktøjer i Azure til analyse og besked om overvågning af data

Følgende afsnit bygger på denne artikel ved at beskrive de specifikke data, der er indsamlet for Power BI Embedded, og give eksempler på konfiguration af dataindsamling og analyse af disse data med Azure-værktøjer.

## <a name="monitoring-data"></a>Overvågning af data

Power BI Embedded indsamler de samme former for overvågning af data som andre Azure-ressourcer, der er beskrevet i [overvågning af data fra Azure-ressourcer](/azure/azure-monitor/insights/monitor-azure-resource#monitoring-data-from-Azure-resources).

Se [overvågning *Power bi Embedded* data reference](monitor-power-bi-embedded-reference.md) for at få detaljerede oplysninger om målepunkter og logfører de målepunkter, der er oprettet af Power bi Embedded.

## <a name="collection-and-routing"></a>Samling og routing

Platform Metrics og aktivitets loggen indsamles og gemmes automatisk, men de kan dirigeres til andre placeringer ved hjælp af en diagnosticerings indstilling.  

Ressource logge indsamles og gemmes ikke, før du opretter en diagnosticerings indstilling og omdirigerer dem til en eller flere placeringer.

Se [Opret diagnosticerings indstilling for at indsamle platform logs og målepunkter i Azure](/azure/azure-monitor/platform/diagnostic-settings) for at få en detaljeret proces til oprettelse af en diagnosticerings indstilling ved hjælp af Azure-Portal, CLI eller PowerShell. Når du opretter en diagnosticerings indstilling, kan du angive, hvilke kategorier logfiler der skal indsamles. Kategorierne for *Power bi Embedded* vises i [Power bi Embedded overvågningsdata reference](monitor-power-bi-embedded-reference.md#resource-logs).

### <a name="using-powershell-to-enable-diagnostics"></a>Brug af PowerShell til aktivering af diagnosticering

Hvis du vil aktivere målinger og logføring af diagnostik ved hjælp af PowerShell, skal du bruge nedenstående kommandoer. Hvis du vil vide mere om, hvordan du bruger PowerShell til at aktivere diagnosticering, skal du se [Opret og Konfigurer et log Analytics arbejdsområde i Azure Monitor ved hjælp af PowerShell](/azure/azure-monitor/platform/powershell-workspace-configuration).

* Brug denne kommando til at aktivere lagring af diagnosticeringslogge for en lagerkonto:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -StorageAccountId [your storage account id] -Enabled $true
    ```
    Id'et for lagerkontoen er ressource-id'et for den lagerkonto, du vil sende loggene til.

* Brug følgende kommando, hvis du vil aktivere streaming af diagnosticeringslogge til en hændelseshub:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -ServiceBusRuleId [your service bus rule id] -Enabled $true
    ```
* Id'et for Azure Service Bus-reglen er en streng i følgende format:

    ```powershell
    {service bus resource ID}/authorizationrules/{key name}
    ```

* Brug følgende kommando, hvis du vil aktivere afsendelse af diagnosticeringslogge til et Log Analytics-arbejdsområde:

    ```powershell
        Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -WorkspaceId [resource id of the log analytics workspace] -Enabled $true
    ```

* Du kan hente ressource-id'et for dit Log Analytics-arbejdsområde vha. følgende kommando:

    ```powershell
    (Get-AzureRmOperationalInsightsWorkspace).ResourceId
    ```

Du kan kombinere disse parametre for at aktivere flere outputindstillinger.

De målepunkter og logge, du kan indsamle, er beskrevet i følgende afsnit.

## <a name="analyzing-metrics"></a>Analyserer målepunkter

Du kan analysere målepunkter for *Power bi Embedded* med målepunkter fra andre Azure-tjenester ved hjælp af Metrics Explorer ved at åbne **målepunkter** fra menuen **Azure Monitor** . Se [kom i gang med Azure Metrics Explorer](/azure/azure-monitor/platform/metrics-getting-started) for at få mere at vide om, hvordan du bruger dette værktøj.

Du kan se en liste over de platform metrik, der indsamles for Power BI Embedded, under [overvåge *Power bi Embedded* data reference Metrics](monitor-power-bi-embedded-reference.md#metrics)  

Du kan se en liste over [alle de ressource metrikværdier, der understøttes i Azure Monitor](/azure/azure-monitor/platform/metrics-supported).

## <a name="analyzing-logs"></a>Analyserer logge

Data i Azure Monitor logge gemmes i tabeller, hvor hver tabel har sit eget sæt entydige egenskaber.  

Alle ressource logge i Azure Monitor indeholde de samme felter efterfulgt af tjenestespecifikke felter. Det fælles skema skitseres i et [Azure Monitor skema for ressource logge](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-schema#top-level-resource-logs-schema) skemaet til Power bi Embedded ressource logge findes i [Power bi Embedded data referencen](monitor-power-bi-embedded-reference.md#schemas).

[Aktivitets loggen](/azure/azure-monitor/platform/activity-log) er en platform til logon på Azure, der giver indsigt i hændelser på abonnements niveau. Du kan få det vist uafhængigt eller distribuere den til Azure Monitor logge, hvor du kan udføre mange mere komplekse forespørgsler ved hjælp af Log Analytics.  

Hvis du vil se en liste over de typer ressource logge, der er indsamlet for Power BI Embedded, skal du se [overvåge Power bi Embedded data reference](monitor-power-bi-embedded-reference.md#resource-logs)  

Du kan se en liste over de tabeller, der bruges af Azure Monitor-logge og-forespørgsel, fra Log Analytics i [overvågnings Power bi Embedded data reference](monitor-power-bi-embedded-reference.md#azure-monitor-logs-tables)  

### <a name="sample-kusto-queries"></a>Eksempler på Kusto-forespørgsler

> [!IMPORTANT]
> Når du vælger **logs** fra menuen Power bi Embedded, åbnes log Analytics, hvor forespørgselsområdet er indstillet til den aktuelle Power bi Embedded ressource. Det betyder, at forespørgsler udelukkende skal indeholde data fra ressourcen. Hvis du vil køre en forespørgsel, der indeholder data fra andre Power BI Embedded-ressourcer eller data fra andre Azure-tjenester, skal du vælge **logge** i menuen **Azure Monitor** . Du kan finde flere oplysninger [i log forespørgslens omfang og tidsinterval i Azure Monitor log Analytics](/azure/azure-monitor/log-query/scope/) .

Nedenfor finder du forespørgsels eksempler på overvågning af Power BI Embedded.

* Dette er en forespørgsel, der er fuldført på mindre end fem minutter (300.000 millisekunder).

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```
* Identificer kapacitetsnavne.

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```

## <a name="alerts"></a>Alerts

Azure Monitor beskeder proaktivt, når der findes vigtige betingelser i dine overvågningsdata. De giver dig mulighed for at identificere og løse problemer i systemet, før kunderne bemærker dem. Du kan angive beskeder om [målepunkter](/azure/azure-monitor/platform/alerts-metric-overview), [logge](/azure/azure-monitor/platform/alerts-unified-log)og [aktivitets logfil](/azure/azure-monitor/platform/activity-log-alerts).

## <a name="next-steps"></a>De næste trin

Du kan få mere at vide om logføring af Azure-ressourcediagnosticering.

>[!div class="nextstepaction"]
>[Overvågning af Power BI Embedded data reference](monitor-power-bi-embedded-reference.md)

>[!div class="nextstepaction"]
>[Overvågning af Azure-ressourcer med Azure Monitor](/azure/azure-monitor/insights/monitor-azure-resource)