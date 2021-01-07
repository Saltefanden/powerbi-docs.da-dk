---
title: Eksportér sideinddelte API-rapporter for integreret analyse i Power BI
description: Få mere at vide om, hvordan du eksporterer en integreret og sideinddelt Power BI-rapport
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: 9c547bd99513470e67bb9717546d9814a9a57c3c
ms.sourcegitcommit: a92a3570eb14793a758a32e8fa1a756ec5d83f8c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/21/2020
ms.locfileid: "97708013"
---
# <a name="export-paginated-report-to-file-preview"></a>Eksportér sideinddelt rapport til fil (prøveversion)

`exportToFile`-API'en muliggør eksport af en sideinddelt Power BI-rapport ved hjælp af et REST-kald. Følgende filformater understøttes:
* **PPTX** (PowerPoint)
* **PDF**
* **XLSX** (Excel)
* **DOX** (Word)
* **CSV**
* **XML**
* **MHTML**
* **Billede**
    * Når du eksporterer til et billede, skal du angive billedformatet via formateringsindstillingen `OutputFormat`
    * De understøttede OutputFormat-værdier er: BMP, EMF, GIF, JPEG, PNG eller TIFF (standard)

## <a name="usage-examples"></a>Eksempler på brug

Du kan bruge eksportfunktionen på flere forskellige måder. Her er nogle eksempler:

* **Knappen Send til udskriv** – I dit program kan du oprette en knap, der udløser et eksportjob, når der klikkes på den. Jobbet kan eksportere den viste rapport som en PDF eller en PPTX, og når den er fuldført, kan brugeren modtage filen som et download. Du kan ved hjælp af rapportparametre og formatindstillinger eksportere rapporten i en bestemt tilstand, herunder filtrerede data, brugerdefinerede sidestørrelser og andre formatspecifikke indstillinger. Da API'en er asynkron, kan det tage et stykke tid, før filen er tilgængelig.

* **Vedhæftet fil i mail** – send en automatiseret mail i angivne intervaller med en vedhæftet PDF-rapport. Dette scenarie kan være nyttigt, hvis du vil automatisere afsendelse af en ugentlig rapport til ledere.

## <a name="using-the-api"></a>Brug af API'en

API'en er asynkron. Når API'en [exportToFile](/rest/api/power-bi/reports/exporttofile) kaldes, udløses et eksportjob. Efter et eksportjob er udløst, kan du bruge [polling](/rest/api/power-bi/reports/getexporttofilestatus) til at spore jobbet, indtil det er fuldført.

Når eksporten er fuldført, returnerer API-kaldet for polling en [URL-adresse til Power BI](/rest/api/power-bi/reports/getfileofexporttofile), så filen kan hentes. URL-adressen er tilgængelig i 24 timer.

## <a name="supported-features"></a>Understøttede funktioner

### <a name="format-settings"></a>Formatindstillinger

Angiv forskellige formatindstillinger for hvert filformat. De understøttede egenskaber og værdier svarer til [parametre for enhedsoplysninger](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) for URL-parametre i sideinddelte rapporter.

Her er to eksempler: ét til eksport af de første fire sider i en rapport ved hjælp af rapportsidestørrelsen til en PPTX-fil og et andet til eksport af den tredje side i en rapport til en JPEG-fil.

**Eksporterer de første fire sider til en PPTX-fil**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**Eksporterer den tredje side til en JPEG-fil**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Rapportparametre

Du kan bruge `exportToFile`-API'en til at eksportere en rapport til et program med et sæt rapportparametre. Dette gøres ved hjælp egenskaberne for [rapportparameter](../../paginated-reports/paginated-reports-parameters.md).

Her er et eksempel på angivelse af rapportparameterværdier.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Godkendelse

Du kan godkende ved hjælp af en bruger (eller masterbruger) eller en [tjenesteprincipal](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Sikkerhed på rækkeniveau

Når du bruger et Power BI-datasæt, der har sikkerhed på rækkeniveau (RLS) defineret som en datakilde, kan du eksportere en rapport, der viser data, som kun er synlige for bestemte brugere. Hvis du f.eks. eksporterer en salgsrapport, der er defineret med områdebestemte roller, kan du filtrere rapporten programmeringsmæssigt, så det kun er et bestemt område, der vises.

Hvis du vil eksportere ved hjælp af RLS, skal du have læserettigheder til det Power BI-datasæt, som rapporten bruger som en datakilde.

Her er et eksempel på, hvordan du kan angive et effektivt brugernavn til RLS.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}
            ]
      }
}
```
## <a name="ppu-concurrent-requests"></a>Samtidige anmodninger for Premium pr. bruger
`exportToFile`-API'en tillader én anmodning i et 5-minutters-vindue, når du bruger [Premium pr. bruger](../../admin/service-premium-per-user-faq.md). Flere (mere end én) anmodninger inden for et 5-minutters-vindue resulterer i fejlen *For mange anmodninger* (429).

## <a name="code-examples"></a>Kodeeksempler

Det Power BI API-SDK, der bruges i kodeeksemplerne, kan hentes [her](https://www.nuget.org/packages/Microsoft.PowerBI.Api).

Når du opretter et eksportjob, er der tre trin, du skal følge:

1. Afsendelse af en eksportanmodning.
2. Polling.
3. Hentning af filen.

Dette afsnit indeholder eksempler på hvert trin.

### <a name="step-1---sending-an-export-request"></a>Trin 1 – Afsendelse af en eksportanmodning

Det første trin er at sende en eksportanmodning. I dette eksempel sendes der en eksportanmodning for et bestemt sideområde, en bestemt sidestørrelse og bestemte rapportparameterværdier.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"},
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} },
        },
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Trin 2 – Polling

Når du har sendt en eksportanmodning, kan du bruge polling til at identificere, hvornår den eksportfil, du venter på, er klar.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>Trin 3 – Hentning af filen

Når polling returnerer en URL-adresse, kan du bruge dette eksempel til at få den modtagne fil.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Komplet eksempel

Dette er et komplet eksempel på eksport af en rapport. Dette eksempel omfatter følgende stadier:
1. [Afsendelse af eksportanmodningen](#step-1---sending-an-export-request).
2. [Polling](#step-2---polling).
3. [Hentning af filen](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="limitations"></a>Begrænsninger

Eksport af en sideinddelt rapport, der har et Power BI-datasæt som datakilde, understøttes ikke for tjenesteprincipaler.

## <a name="next-steps"></a>Næste trin

Gennemse, hvordan du integrerer indhold for dine kunder og din organisation:

> [!div class="nextstepaction"]
>[Eksportér rapport til fil](export-to.md)

> [!div class="nextstepaction"]
>[Integrer indhold for dine kunder](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Integrer til din organisation](embed-sample-for-your-organization.md)
