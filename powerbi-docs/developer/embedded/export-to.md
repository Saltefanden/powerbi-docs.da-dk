---
title: Eksportér API-rapporter for integreret analyse i Power BI
description: Få mere at vide om, hvordan du eksporterer en integreret Power BI rapport.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 02/09/2021
ms.openlocfilehash: 68d4802ebb150827982a348bc67f6f46f60812be
ms.sourcegitcommit: de3b45cad5ae21c77692ce4490e21de01d21e6f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2021
ms.locfileid: "100013561"
---
# <a name="export-power-bi-report-to-file-preview"></a>Eksportér Power BI-rapport til fil (prøveversion)

`exportToFile`-API'en muliggør eksport af en Power BI-rapport ved hjælp af et REST-kald. Følgende filformater understøttes:
* **PPTX** (PowerPoint)
* **PDF**
* **PNG**
    * Når du eksporterer til en PNG, komprimeres en rapport med flere sider til en zip-fil
    * Hver fil i zip-filen repræsenterer en rapportside
    * Sidenavnene er de samme som returværdierne for API'erne [Hent sider](/rest/api/power-bi/reports/getpages) eller [Hent sider i gruppe](/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Eksempler på brug

Du kan bruge eksportfunktionen på flere forskellige måder. Her er nogle eksempler:

* **Knappen Send til udskriv** – I dit program kan du oprette en knap, der udløser et eksportjob, når der klikkes på den. Jobbet kan eksportere den viste rapport som en PDF eller en PPTX, og når den er fuldført, kan brugeren modtage filen som et download. Ved hjælp af bogmærker kan du eksportere rapporten i en bestemt tilstand, herunder konfigurerede filtre, udsnit og yderligere indstillinger. Da API'en er asynkron, kan det tage et stykke tid, før filen er tilgængelig.

* **Vedhæftet fil i mail** – send en automatiseret mail i angivne intervaller med en vedhæftet PDF-rapport. Dette scenarie kan være nyttigt, hvis du vil automatisere afsendelse af en ugentlig rapport til ledere. Du kan finde flere oplysninger under [Eksportér en Power BI-rapport, og send den som mail, med Power Automate](../../collaborate-share/service-automate-power-bi-report-export.md)

## <a name="using-the-api"></a>Brug af API'en

Før du bruger API'en, skal du bekræfte, at følgende [lejerindstillinger for administratoren](../../admin/service-admin-portal.md#tenant-settings) er aktiveret:
* **Eksportér rapporter som PowerPoint-præsentationer eller PDF-dokumenter** – Aktiveret som standard.
* **Eksportér rapporter som billedfiler** – kræves kun til *PNG* og er deaktiveret som standard.

API'en er asynkron. Når API'en [exportToFile](/rest/api/power-bi/reports/exporttofile) kaldes, udløses et eksportjob. Efter et eksportjob er udløst, kan du bruge [polling](/rest/api/power-bi/reports/getexporttofilestatus) til at spore jobbet, indtil det er fuldført.

Under polling returnerer API'en et tal, der repræsenterer den mængde arbejde, der er fuldført. Arbejdet i hvert eksportjob beregnes på baggrund af det samlede antal Eksporter i jobbet. En eksport omfatter eksport af en enkelt Visual eller en side med eller uden bogmærker. Alle Eksporter har samme vægt. Hvis dit eksport-job f. eks. omfatter eksport af en rapport med 10 sider, og polling returnerer 70, betyder det, at API'EN har behandlet syv ud af de 10 sider i eksportjobbet.

Når eksporten er fuldført, returnerer API-kaldet for polling en [URL-adresse til Power BI](/rest/api/power-bi/reports/getfileofexporttofile), så filen kan hentes. URL-adressen er tilgængelig i 24 timer.

## <a name="supported-features"></a>Understøttede funktioner

I dette afsnit beskrives, hvordan følgende understøttede funktioner udføres:

* [Valg af, hvilke sider der skal udskrives](#selecting-which-pages-to-print)
* [Eksport af en side eller en enkelt Visual](#exporting-a-page-or-a-single-visual)
* [Bogmærker](#bookmarks)
* [Filtre](#filters)
* [Godkendelse](#authentication)
* [Sikkerhed på rækkeniveau](#row-level-security-rls)
* [Databeskyttelse](#data-protection)
* [Lokalisering](#localization)

### <a name="selecting-which-pages-to-print"></a>Valg af, hvilke sider der skal udskrives

Angiv de sider, du vil udskrive i henhold til returværdierne [Hent sider](/rest/api/power-bi/reports/getpages) eller [Hent sider i gruppe](/rest/api/power-bi/reports/getpagesingroup). Du kan også angive rækkefølgen af de sider, du vil eksportere.

### <a name="exporting-a-page-or-a-single-visual"></a>Eksport af en side eller en enkelt Visual

Du kan angive en side eller en enkelt visualisering, der skal eksporteres. Sider kan eksporteres med eller uden bogmærker.

Afhængigt af typen af eksport skal du overfører forskellige attributter til objektet [ExportReportPage](/rest/api/power-bi/reports/exporttofile#exportreportpage) . I nedenstående tabel kan du se, hvilke attributter der kræves til hvert eksportjob.  

>[!NOTE]
>Eksport af en enkelt Visual har samme vægt som at eksportere en side (med eller uden bogmærker). Det betyder, at i forbindelse med system beregninger overfører begge handlinger samme værdi.

|Attribut   |Side     |Enkelt Visual  |Kommentarer|
|------------|---------|---------|---|
|`bookmark`  |Valgfrit |![Gælder ikke for.](../../media/no.png)|Brug denne til at eksportere en side i en bestemt tilstand|
|`pageName`  |![Gælder for.](../../media/yes.png)|![Gælder for.](../../media/yes.png)|Brug [GetPages](/rest/api/power-bi/reports/getpage) rest API eller klient- `getPages` API'en. Du kan finde flere oplysninger under [Hent sider og visualiseringer](/javascript/api/overview/powerbi/get-visuals).   |
|`visualName`|![Gælder ikke for.](../../media/no.png)|![Gælder for.](../../media/yes.png)|Der er to måder at få vist navnet på det visuelle element på:<li>Brug `getVisuals` klient-API'en. Du kan finde flere oplysninger under [Hent sider og visualiseringer](/javascript/api/overview/powerbi/get-visuals).</li><li>Lyt til, og log *visualClicked* -hændelsen, der udløses, når der vælges et visuelt element. Du kan finde flere oplysninger under [Sådan håndterer du hændelser](/javascript/api/overview/powerbi/handle-events)</li>. |

### <a name="bookmarks"></a>Bogmærker

[Bogmærker](../../consumer/end-user-bookmarks.md) kan bruges til at gemme en rapport i en bestemt konfiguration, herunder anvendte filtre og tilstanden for rapportens visualiseringer. Du kan bruge API'en [exportToFile](/rest/api/power-bi/reports/exporttofile) til programmeringsmæssigt at eksportere en rapports bogmærke på to måder:

* **Eksportér et eksisterende bogmærke**

    Hvis du vil eksportere et eksisterende [rapportbogmærke](../../consumer/end-user-bookmarks.md#report-bookmarks), skal du bruge egenskaben `name`, der er en entydig identifikator (forskel på store og små bogstaver), som du kan få ved at bruge [API'en med bogmærker til JavaScript](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

* **Eksportér rapportens tilstand**

    Hvis du vil eksportere rapportens aktuelle tilstand, skal du bruge egenskaben `state`. Du kan f.eks. bruge bogmærkets `bookmarksManager.capture`-metode til at hente de ændringer, som en bestemt bruger har foretaget i en rapport, og derefter eksportere den i dens nuværende tilstand ved hjælp af `capturedBookmark.state`.

>[!NOTE]
>[Personlige bogmærker](../../consumer/end-user-bookmarks.md#personal-bookmarks) og [vedvarende filtre](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) understøttes ikke.

### <a name="filters"></a>Filtre

Ved hjælp af `reportLevelFilters` i [PowerBIReportExportConfiguration](/rest/api/power-bi/reports/exporttofile#powerbireportexportconfiguration) kan du eksportere en rapport i filtreret tilstand.

Hvis du vil eksportere en filtreret rapport, skal du indsætte [parametrene for forespørgselsstrengen i URL-adressen](../../collaborate-share/service-url-filters.md), som du vil bruge som dit filter, som [ExportFilter](/rest/api/power-bi/reports/exporttofile#exportfilter). Når du angiver strengen, skal du fjerne `?filter=`-delen af parameteren for forespørgslen i URL-adressen.

Tabellen nedenfor indeholder nogle få syntakseksempler på strenge, du kan overføre til `ExportFilter`.

|Filtrer    |Syntax    |Eksempel    |
|---|----|----|----|
|En værdi i et felt    |Table/Field eq 'value'    |Store/Territory eq 'NC'    |
|Flere værdier i et felt    |Table/Field in ('value1', 'value2')     |Store/Territory in ('NC', 'TN')    |
|En specifik værdi i ét felt og en anden specifik værdi i et andet felt    |Table/Field1 eq 'value1' and Table/Field2 eq 'value2'    |Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'    |

>[!NOTE]
>`ReportLevelFilters` kan kun indeholde en enkelt [ExportFilter](/rest/api/power-bi/reports/exporttofile#exportfilter).

### <a name="authentication"></a>Godkendelse

Du kan godkende ved hjælp af en bruger (eller masterbruger) eller en [tjenesteprincipal](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Sikkerhed på rækkeniveau

Med [sikkerhed på rækkeniveau](embedded-row-level-security.md) kan du eksportere en rapport, der viser data, som kun er synlige for bestemte brugere. Hvis du f.eks. eksporterer en salgsrapport, der er defineret med områdebestemte roller, kan du filtrere rapporten programmeringsmæssigt, så det kun er et bestemt område, der vises.

Hvis du vil eksportere ved hjælp af sikkerhed på rækkeniveau, skal du have følgende tilladelser:
* Tilladelser til at skrive og dele data igen for det datasæt, som rapporten er knyttet til
* Hvis rapporten findes i et v1-arbejdsområde, skal du være administrator af arbejdsområdet
* Hvis rapporten findes i et v2-arbejdsområde, skal du være medlem eller administrator af arbejdsområdet

### <a name="data-protection"></a>Databeskyttelse

PDF- og PPTX-formaterne understøtter [følsomhedsmærkater](../../admin/service-security-sensitivity-label-overview.md). Hvis du eksporterer en rapport med et følsomhedsmærkat til en PDF eller en PPTX, vises rapporten med dens følsomhedsmærkater i den eksporterede fil.

En rapport med et følsomhedsmærkat kan ikke eksporteres til en PDF- eller PPTX-fil ved hjælp af en [tjenesteprincipal](embed-service-principal.md).

### <a name="localization"></a>Lokalisering

Når du bruger `exportToFile`-API'en, kan du overføre din foretrukne landestandard. Indstillingerne for lokalisering påvirker den måde, rapporten vises på, f.eks. ved at ændre formatering i henhold til den valgte landestandard.

## <a name="concurrent-requests"></a>Samtidige anmodninger

`exportToFile` understøtter samtidige anmodninger om eksportjob. I nedenstående tabel vises antallet af job, du kan køre samtidigt, afhængigt af hvilken SKU din rapport er placeret på. Samtidige anmodninger refererer til rapportsider. Hvis der f.eks. er 20 sider i én eksportanmodning på en A6 SKU, behandles de samtidigt. Dette tager stort set den samme tid som at sende 20 eksportanmodninger med én side hver.

Et job, der overskrider sit antal af samtidige anmodninger, afsluttes ikke. Hvis du f.eks. eksporterer tre sider i en A1 SKU, udføres det første job, og de sidste to venter på de næste to udførelsescyklusser.

>[!NOTE]
>Eksport af en Power BI-rapport til en fil ved hjælp af `exporToFile`-API'en understøttes ikke for [Premium pr. bruger](../../admin/service-premium-per-user-faq.md). 

|Azure SKU  |Office SKU  |Maksimalt antal samtidige rapportsider  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Begrænsninger

* Den rapport, du eksporterer, skal være placeret i en Premium- eller Embedded-kapacitet.
* Datasættet for den rapport, du eksporterer, skal være placeret i en Premium- eller Embedded-kapacitet.
* I forbindelse med den offentlige prøveversion er antallet af Power BI eksport pr. time begrænset til 50 pr. kapacitet. En eksport henviser til at eksportere en enkelt Visual eller en rapport side med eller uden bogmærker og omfatter ikke eksport af sideinddelte rapporter.
* Eksporterede rapporter må ikke overstige en filstørrelse på 250 MB.
* Følsomhedsmærkater understøttes ikke, når du eksporterer til PNG.
* Antallet af Eksporter (enkelte visuelle elementer eller rapportsider), der kan inkluderes i en eksporteret rapport, er 50 (Dette omfatter ikke eksport af sideinddelte rapporter). Hvis anmodningen omfatter flere Eksporter, returnerer API'EN en fejl, og eksportjobbet annulleres.
* [Personlige bogmærker](../../consumer/end-user-bookmarks.md#personal-bookmarks) og [vedvarende filtre](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) understøttes ikke.
* De Power BI-visualiseringer, der er angivet nedenfor, understøttes ikke. Når der eksporteres en rapport, som indeholder disse visualiseringer, bliver de dele af rapporten, der indeholder disse visualiseringer, ikke gengivet, og der vises et fejlsymbol.
    * Ikke-certificerede Power BI-visualiseringer
    * R-visualiseringer
    * PowerApps
    * Python-visualiseringer
    * Visio

## <a name="code-examples"></a>Kodeeksempler

Når du opretter et eksportjob, er der tre trin, du skal følge:

1. [Afsendelse af en eksportanmodning.](#step-1---sending-an-export-request)
2. [Polling](#step-2---polling).
3. [Hentning af filen](#step-3---getting-the-file).
4. [Brug af filstream](#step-4---using-the-file-stream).

Dette afsnit indeholder eksempler på hvert trin.

### <a name="step-1---sending-an-export-request"></a>Trin 1 – Afsendelse af en eksportanmodning

Det første trin er at sende en eksportanmodning. I dette eksempel sendes der en eksportanmodning for en bestemt side.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null, /* Get the page names from the GetPages REST API */
    string urlFilter = null)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names
        // To get the page names use the GetPages REST API
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
        // ReportLevelFilters collection needs to be instantiated explicitly
        ReportLevelFilters = !string.IsNullOrEmpty(urlFilter) ? new List<ExportFilter>() { new ExportFilter(urlFilter) } : null,

    };

    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Trin 2 – Polling

Når du har sendt en eksportanmodning, kan du bruge polling til at identificere, hvornår den eksportfil, du venter på, er klar.

```csharp
private async Task<HttpOperationResponse<Export>> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the PostExportRequest response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    HttpOperationResponse<Export> httpMessage = null;
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is not always populated
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return httpMessage;
}
```

### <a name="step-3---getting-the-file"></a>Trin 3 – Hentning af filen

Når polling returnerer en URL-adresse, kan du bruge dette eksempel til at få den modtagne fil.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the PollExportRequest response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="step-4---using-the-file-stream"></a>Trin 4 – Brug af filstreamen

Når du har filstreamen, kan du håndtere den på den måde, der passer bedst til dine behov. Du kan f.eks. sende en mail til den eller bruge den til at downloade de eksporterede rapporter.

### <a name="end-to-end-example"></a>Komplet eksempel

Dette er et komplet eksempel på eksport af en rapport. Dette eksempel omfatter følgende stadier:
1. [Afsendelse af eksportanmodningen](#step-1---sending-an-export-request).
2. [Polling](#step-2---polling).
3. [Hentning af filen](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null,  /* Get the page names from the GetPages REST API */
    string urlFilter = null)
{
    const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
    const int c_secToMillisec = 1000;
    try
    {
        Export export = null;
        int retryAttempt = 1;
        do
        {
            var exportId = await PostExportRequest(reportId, groupId, format, pageNames, urlFilter);
            var httpMessage = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
            export = httpMessage.Body;
            if (export == null)
            {
                // Error, failure in exporting the report
                return null;
            }
            if (export.Status == ExportState.Failed)
            {
                // Some failure cases indicate that the system is currently busy. The entire export operation can be retried after a certain delay
                // In such cases the recommended waiting time before retrying the entire export operation can be found in the RetryAfter header
                var retryAfter = httpMessage.Response.Headers.RetryAfter;
                if(retryAfter == null)
                {
                    // Failed state with no RetryAfter header indicates that the export failed permanently
                    return null;
                }

                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
            }
        }
        while (export.Status != ExportState.Succeeded && retryAttempt++ < c_maxNumberOfRetries);

        if (export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }

        var exportedFile = await GetExportedFile(reportId, groupId, export);

        // Now you have the exported file stream ready to be used according to your specific needs
        // For example, saving the file can be done as follows:
        /*
            var pathOnDisk = @"C:\temp\" + export.ReportName + exportedFile.FileSuffix;

            using (var fileStream = File.Create(pathOnDisk))
            {
                exportedFile.FileStream.CopyTo(fileStream);
            }
        */

        return exportedFile;
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Næste trin

Gennemse, hvordan du integrerer indhold for dine kunder og din organisation:

> [!div class="nextstepaction"]
>[Eksportér den sideinddelte rapport til fil](export-paginated-report.md)

> [!div class="nextstepaction"]
>[Integrer indhold for dine kunder](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Integrer til din organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Eksportér og send en Power BI-rapport via mail med Power Automate](../../collaborate-share/service-automate-power-bi-report-export.md)
