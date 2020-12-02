---
title: Administratoroversigt, Power BI-rapportserver
description: Denne artikel indeholder en administrationsoversigt over Power BI-rapportserveren, der er en placering i det lokale miljø til lagring og administration af dine Power BI- og mobilrapporter samt dine sideinddelte rapporter.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: a1c8e11fbf3b157a0d9fc1a897347875b82226fa
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387252"
---
# <a name="admin-overview-power-bi-report-server"></a>Administratoroversigt, Power BI-rapportserver
Denne artikel indeholder en administrationsoversigt over Power BI-rapportserveren, der er en placering i det lokale miljø til lagring og administration af dine Power BI- og mobilrapporter samt dine sideinddelte rapporter. I denne artikel introduceres begreber i forbindelse med planlægning, udrulning og administration af din Power BI-rapportserver, og den indeholder links til flere oplysninger.

![Skærmbillede af Power BI-rapportserver, der viser logonindstillinger.](media/admin-handbook-overview/admin-handbook.png)
 
## <a name="installing-and-migration"></a>Installation og overførsel
Du skal installere Power BI-rapportserveren for at begynde at bruge den. Vi har artikler, der beskriver, hvordan du håndterer denne opgave.

Før du begynder at installere, opgradere eller overføre til Power BI-rapportserver, skal du tage et kig på [systemkravene](system-requirements.md) for rapportserveren.

### <a name="installing"></a>Installation
Hvis du anvender en ny Power BI-rapportserver, kan du hente hjælp i følgende dokument. 

[Installer Power BI-rapportserver](install-report-server.md)

### <a name="migration"></a>Overførsel
Der findes ingen opgradering til SQL Server Reporting Services. Hvis du har en eksisterende SQL Server Reporting Services-udgave, som du vil gøre til Power BI-rapportserver, skal du overføre den. Der kan også være andre årsager til at foretage en overførsel. Gennemse overførselsdokumentet for at få flere oplysninger.

[Overfør en rapportserverinstallation](migrate-report-server.md)

## <a name="configuring-your-report-server"></a>Konfiguration af rapportserveren
Du har mange muligheder under konfigurationen af rapportserveren. Vil du bruge SSL? Vil du konfigurere en mailserver? Vil du integrere med Power BI-tjenesten for at kunne fastgøre visualiseringer?

Størstedelen af konfigurationen sker i Report Server Configuration Manager. Tjek [konfigurationsstyrings](/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode)dokumentationen for at få flere oplysninger.

## <a name="security"></a>Sikkerhed
Sikkerhed og beskyttelse er vigtigt for alle organisationer. Du kan få mere at vide om godkendelse, roller og rettigheder i [sikkerheds](/sql/reporting-services/security/reporting-services-security-and-protection)dokumentationen.

## <a name="next-steps"></a>Næste trin
[Installer Power BI-rapportserver](install-report-server.md)  
[Find produktnøglen til din rapportserver](find-product-key.md)  
[Installer Power BI Desktop optimeret til Power BI-rapportserver](install-powerbi-desktop.md)  
[Download Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Download SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)