---
title: Oversigt over udviklerhåndbog, Power BI-rapportserver
description: Velkommen til udviklerhåndbogen til Power BI-rapportserver, der er en placering i det lokale miljø til lagring og administration af dine Power BI- og mobilrapporter samt dine sideinddelte rapporter.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.openlocfilehash: d485c7ab7583d2604cd9da9e4c122c6cceeeb4fe
ms.sourcegitcommit: 8afdd3601209636c9ab92d75f967d4ee0a2cab26
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/21/2020
ms.locfileid: "95011996"
---
# <a name="developer-handbook-overview-power-bi-report-server"></a>Oversigt over udviklerhåndbog, Power BI-rapportserver

Velkommen til udviklerhåndbogen til Power BI-rapportserver, der er en placering i det lokale miljø til lagring og administration af dine Power BI- og mobilrapporter samt dine sideinddelte rapporter.

![Håndbog til administratorer](media/developer-handbook-overview/admin-handbook.png)

I denne håndbog fremhæves de muligheder, du har som udvikler, for at arbejde med Power BI-rapportserver.

## <a name="embedding"></a>Integration

Du kan integrere en hvilken som helst rapport på Power BI-rapportserver i en iFrame ved at føje parameteren `?rs:Embed=true` for forespørgselsstrengen til URL-adressen. Denne teknik fungerer til Power BI-rapporter samt til andre rapporttyper.

### <a name="report-viewer-control"></a>Kontrolelementet Rapportfremviser

Du kan gøre brug af kontrolelementet Rapportfremviser i forbindelse med sideinddelte rapporter. Den giver dig mulighed for at placere kontrolelementet i et .NET-vindue eller -webprogram. Du kan finde flere oplysninger under [Introduktion til kontrolelementet Rapportfremviser](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

## <a name="apis"></a>API'er

Du har flere API-indstillinger, som du kan bruge til at interagere med Power BI-rapportserver. Denne teknik omfatter følgende.

* [REST API'er](rest-api.md)
* [Adgang til URL-adresse](/sql/reporting-services/url-access-ssrs)
* [WMI-provider](/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Du kan også bruge [PowerShell-hjælpeprogrammerne](https://github.com/Microsoft/ReportingServicesTools) i åben kildekode til at administrere din rapportserver.

> [!NOTE]
> PowerShell-hjælpeprogrammerne understøtter Power BI Desktop-filer (.pbix) via kommandoerne -RsRest*.

Kør følgende kommando for at finde ud af, hvilke kommandoer i ReportingServicesTools PowerShell-modulet der understøtter Power BI Desktop filer (.pbix).

```powershell
Get-Command -Module ReportingServicesTools -Noun RsRest*
```

## <a name="custom-extensions"></a>Brugerdefinerede udvidelser

Udvidelsesbiblioteket er et sæt klasser, grænseflader og værdityper, der er inkluderet i Power BI-rapportserver. Dette bibliotek giver adgang til systemets funktionalitet, og det er designet til at være det fundament, som Microsoft .NET Framework-programmer kan bruge til at udvide komponenter til Power BI-rapportserver.

Der findes flere typer udvidelser, som du kan oprette.

* Udvidelser til databehandling
* Udvidelser til levering
* Udvidelser til gengivelse i forbindelse med sideinddelte rapporter
* Udvidelser til sikkerhed

Du kan finde flere oplysninger under [Udvidelsesbibliotek](/sql/reporting-services/extensions/reporting-services-extension-library).

## <a name="next-steps"></a>Næste trin

[Introduktion til kontrolelementet Rapportfremviser](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)  
[Oprettelse af programmer ved hjælp af webtjenesten og .NET Framework](/sql/reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework)  
[Adgang til URL-adresse](/sql/reporting-services/url-access-ssrs)  
[Udvidelsesbibliotek](/sql/reporting-services/extensions/reporting-services-extension-library)  
[WMI-provider](/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
