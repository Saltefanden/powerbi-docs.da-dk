---
title: Browsersupport til Power BI Report Server
description: "Få mere at vide om, hvilke browserversioner der understøtter administration og visning af Power BI Report Server og Report Viewer-kontrolelementerne."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: asaxton
ms.openlocfilehash: 3e146417c78c7c95221c37051eda08a7b8497012
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/13/2017
---
# <a name="browser-support-for-power-bi-report-server"></a>Browsersupport til Power BI Report Server
Få mere at vide om, hvilke browserversioner der understøtter administration og visning af Power BI Report Server og Report Viewer-kontrolelementerne.

## <a name="browser-requirements-for-the-web-portal"></a>Krav til browseren for webportalen
Herunder finder du den aktuelle liste over browsere, der understøtter webportalen.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9 10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iPhone og iPad med iOS 9*

* Apple Safari (+)

**Google Android**  
*Telefoner og tablets med Android 4.4 (KitKat) eller nyere*

* Google Chrome (+)
  
  **(+)**  Seneste offentligt udgivne version

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>Krav til browseren for Report Viewer-webkontrollen (2015)
Herunder finder du den aktuelle liste over browsere, der understøtter Report Viewer-webportalen. Rapportfremviseren understøtter visning af rapporter fra webportalen.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9 10.11*

* Apple Safari (+)
  
  **(+)**  Seneste offentligt udgivne version

### <a name="authentication-requirements"></a>Krav til godkendelse
Browserne understøtter specifikke godkendelsesmetoder, der skal håndteres af rapportserveren, for at klientanmodningen kan fuldføres. I følgende tabel angives de standardgodkendelsestyper, der understøttes af alle de browsere, der fungerer med et Windows-operativsystem.

| **Browsertype** | **Understøtter** | **Browserstandard** | **Serverstandard** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |Negotiate, Kerberos, NTLM, Basic |Negotiate |Ja. Standardgodkendelsesindstillingerne fungerer sammen med Microsoft Edge. |
| **Microsoft Internet Explorer** |Negotiate, Kerberos, NTLM, Basic |Negotiate |Ja. Standardgodkendelsesindstillingerne fungerer sammen med Internet Explorer. |
| **Google Chrome**(+) |Negotiate, NTLM, Basic |Negotiate |Ja. Standardgodkendelsesindstillingerne fungerer sammen med Chrome. |
| **Mozilla Firefox**(+) |NTLM, Basic |NTLM |Ja. Standardgodkendelsesindstillingerne fungerer sammen med Firefox. |
| **Apple Safari**(+) |NTLM, Basic |Basic |Ja. Standardgodkendelsesindstillingerne fungerer sammen med Safari. |

 **(+)**  Seneste offentligt udgivne version

### <a name="script-requirements-for-viewing-reports"></a>Scriptkrav for at få vist rapporter
Konfigurer webbrowseren til at køre scripts for at kunne bruge rapportfremviseren.

Hvis scripting ikke er aktiveret, vises en fejlmeddelelse svarende til følgende, når du åbner en rapport:

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 Hvis du vælger at få vist rapporten uden scriptsupport, gengives rapporten i HTML uden rapportfremviserens funktioner såsom værktøjslinjen Rapport og dokumentoversigten.

> [!NOTE]
> Værktøjslinjen Rapport er en del af HTML Viewer-komponenten. Værktøjslinjen vises som standard øverst på alle rapporter, der gengives i et browservindue. Rapportfremviseren indeholder funktioner, der giver mulighed for at søge efter rapporten for at få oplysninger, rulle til en bestemt side og justere sidestørrelsen ud fra visningsbehov. Du kan finde flere oplysninger om værktøjslinjen Rapport eller HTML Viewer under [HTML Viewer og værktøjslinjen Rapport](https://docs.microsoft.com/sql/reporting-services/html-viewer-and-the-report-toolbar).
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Browsersupport for Report Viewer-webserverobjekter i Visual Studio
Report Viewer-webserverobjektet bruges til at integrere rapportfunktionerne i et ASP.NET-webprogram. Du kan finde flere oplysninger om, hvordan du henter Report Viewer-objektet under [Integration af rapporteringstjenester ved hjælp af Report Viewer-objekter – Kom i gang](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

Brug en browser med aktivering af scriptsupport. Hvis browseren ikke kan køre scripts, kan du ikke få vist rapporten.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)**  Seneste offentligt udgivne version

## <a name="next-steps"></a>Næste trin
[Administratorhåndbog](admin-handbook-overview.md)  
[Hurtigstart: Installér Power BI Report Server](quickstart-install-report-server.md)  
[Installér Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Download SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
