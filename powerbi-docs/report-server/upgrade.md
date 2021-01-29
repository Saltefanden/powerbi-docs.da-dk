---
title: Opgrader Power BI Report Server
description: Find ud af, hvordan du opgraderer Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.custom: ''
ms.date: 09/22/2020
ms.openlocfilehash: 68494784e3c5b21c0c3e15bd5a3a816fd07e5f8b
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2021
ms.locfileid: "99043545"
---
# <a name="upgrade-power-bi-report-server"></a>Opgrader Power BI Report Server

Find ud af, hvordan du opgraderer Power BI Report Server.

 **Download** ![ikon for download](media/upgrade/download.png "ikon for download")

Hvis du vil downloade Power BI-rapportserver og Power BI Desktop for Power BI-rapportserver, skal du gå til [rapportering i det lokale miljø med Power bi-rapportserver](https://powerbi.microsoft.com/report-server/).

## <a name="before-you-begin"></a>Inden du starter

Inden du opgraderer en rapportserver, anbefaler vi, at følgende trin udføres for at sikkerhedskopiere rapportserveren.

### <a name="backing-up-the-encryption-keys"></a>Sikkerhedskopiering af krypteringsnøgler

Sikkerhedskopiér krypteringsnøglerne, første gang du konfigurerer en rapportserverinstallation. Sikkerhedskopiér også nøglerne, hver gang du ændrer identiteten for tjenestekontiene eller omdøber computeren. Du kan finde flere oplysninger i [Sikkerhedskopiér og gendan krypteringsnøgler til rapporttjenester](/sql/reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys).

### <a name="backing-up-the-report-server-databases"></a>Sikkerhedskopiér rapportserverdatabaser

Da en rapportserver er en tilstandsløs server, gemmes alle programdata i databaserne **reportserver** og **reportservertempdb**, der kører på en forekomst af SQL Server Database Engine. Du kan sikkerhedskopiere databaserne **reportserver** og **reportservertempdb** ved hjælp af en af de understøttede metoder til sikkerhedskopiering af SQL Server-databaser. Disse anbefalinger er specifikke for rapportserverdatabaser:

* Brug modellen for fuldstændig genoprettelse til at sikkerhedskopiere databasen **reportserver**.
* Brug den enkle genoprettelsesmodel til at sikkerhedskopiere databasen **reportservertempdb**.
* Du kan bruge forskellige tidsplaner til sikkerhedskopiering af hver database. Den eneste grund til at sikkerhedskopiere **reportservertempdb** er for at undgå at skulle oprette den igen, hvis der opstår en hardwarefejl. I tilfælde af hardwarefejl behøver du ikke at genoprette dataene i **reportservertempdb**, men du har dog brug for tabelstrukturen. Hvis du mister **reportservertempdb**, er den eneste måde at få den tilbage på at genoprette rapportserverdatabasen. Hvis du opretter **reportservertempdb** igen, er det vigtigt, at den har samme navn som den primære rapportserverdatabase.

Du kan finde flere oplysninger om sikkerhedskopiering og gendannelse af SQL Server-relationsdatabaser ved at læse [Sikkerhedskopiering og gendannelse af SQL Server-databaser](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases).

### <a name="backing-up-the-configuration-files"></a>Sikkerhedskopiér konfigurationsfilerne

Power BI Report Server bruger konfigurationsfilerne til at gemme programindstillinger. Sikkerhedskopiér filerne, første gang du konfigurerer serveren, og efter du udruller brugerdefinerede udvidelser. Filer, der skal sikkerhedskopieres, omfatter:

* config.json
* RSHostingService.exe.config
* Rsreportserver.config
* Rssvrpolicy.config
* Reportingservicesservice.exe.config
* Web.config til Report Server ASP.NET-programmer
* Machine.config til ASP.NET

## <a name="upgrade-the-report-server"></a>Opgrader rapportserveren

Det er nemt at opgradere Power BI-rapportserver. Der er kun et par trin til installation af filerne.

1. Find placeringen af PowerBIReportServer.exe, og start installationen.

2. Vælg **Opgrader Power BI Report Server**.

    ![Opgrader Power BI-rapportserver](media/upgrade/reportserver-upgrade1.png "Opgrader Power BI-rapportserver")

3. Læs og acceptér licensens vilkår og betingelser, og vælg derefter **Opgrader**.

    ![Licensaftale](media/upgrade/reportserver-upgrade-eula.png "Licensaftale")

4. Når opgraderingen er udført, kan du vælge **Konfigurer Report Server** for at starte Reporting Services Configuration Manager, eller vælge **Luk** for at afslutte installationen.

    ![Opgrader konfiguration](media/upgrade/reportserver-upgrade-configure.png)

## <a name="enable-microsoft-update-security-fixes-for-power-bi-report-server"></a>Aktivér Microsoft Update-sikkerhedsrettelser til Power BI-rapportserver

Power BI-rapportserver modtager sikkerhedsrettelser via Microsoft Update. Hvis du vil gøre det muligt at hente dem, skal du manuelt tilmelde dig Microsoft Update.

1.  Åbn Windows Update i **Opdaterings- og sikkerhedsindstillinger** på den computer, du vil tilmelde.
2.  Vælg **Avancerede indstillinger**.
3.  Markér afkrydsningsfeltet for **Giv mig opdateringer til andre Microsoft-produkter, når jeg opdaterer Windows**.

## <a name="upgrade-power-bi-desktop"></a>Opgrader Power BI Desktop

Når du har opgraderet rapportserveren, skal du sørge for, at alle Power BI rapport forfattere opgraderer til den version af Power BI Desktop for Power BI-rapportserver, der svarer til serveren.

## <a name="next-steps"></a>Næste trin

* [Administratoroversigt](admin-handbook-overview.md)  
* [Installér Power BI Desktop for Power BI-rapportserver](install-powerbi-desktop.md)  
* [Bekræft installationen af Reporting Services](/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
* [Konfigurer kontoen til rapportservertjenesten](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
* [Konfigurer rapportserverens URL-adresser](/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
* [Konfigurer en rapportservers databaseforbindelse](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
* [Initialiser en rapportserver](/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
* [Konfigurer SSL-forbindelser på en rapportserver](/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
* [Konfigurer Windows-tjenestekonti og -tilladelser](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
* [Browserunderstøttelse af Power BI Report Server](browser-support.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)