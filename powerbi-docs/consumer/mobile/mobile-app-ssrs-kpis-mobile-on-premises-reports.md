---
title: Vis rapporter og KPI'er i det lokale miljø i Power BI-mobilapps
description: Power BI-mobilappsene tilbyder live, touchaktiveret mobiladgang til dine virksomhedsoplysninger i det lokale miljø via SQL Server Reporting Services og Power BI-rapportserver.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/05/2019
ms.openlocfilehash: 18ad1be61202ddf189da064a833fddf6d793a2ba
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413397"
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>Vis rapporter og KPI'er fra rapportserveren i det lokale miljø i Power BI-mobilapps

Power BI-mobilapps leverer live, touchaktiveret mobiladgang til dine firmaoplysninger i det lokale miljø via Power BI-rapportserver og SQL Server 2016 Reporting Services (SSRS).

Gælder for:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android-telefon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android-tablet](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPad-tablets |Android-telefoner |Android-tablets |


![Startside for rapportserver i mobilappsene](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>Det vigtigste først
**Mobilappsene er der, hvor du ser Power BI-indhold, ikke hvor du opretter det.**

* Du og andre personer, der opretter rapporter i din organisation, [opretter Power BI-rapporter med Power BI Desktop, og publicerer dem derefter på webportalen Power BI-rapportserver](../../report-server/quickstart-create-powerbi-report.md). 
* Du opretter [KPI'er direkte i webportalen](/sql/reporting-services/working-with-kpis-in-reporting-services), organiserer dem i mapper og markerer dine favoritter, så du nemt kan finde dem. 
* Du [opretter Reporting Services-mobilrapporter](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) med SQL Server 2016 Enterprise Edition Mobile Report Publisher, og publicerer dem på [Reporting Services-webportalen](/sql/reporting-services/web-portal-ssrs-native-mode).  

Derefter opretter du forbindelse til op til fem rapportservere i Power BI-mobilappsene for at se Power BI-rapporter og -KPI'er, organiseret i mapper eller samlet som favoritter. 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>Se nærmere på eksemplerne i mobilappsene uden serverforbindelse
Selvom du ikke har adgang til en Reporting Services-webportal, kan du stadig udforske funktionerne i Reporting Services-mobilrapporter og -KPI'er. 

1. Tryk på dit profilbillede i øverste venstre hjørne, og tryk derefter på **Indstillinger** på det kontopanel, der glider ud.

2. Tryk på **Reporting Services-eksempler** på siden Indstillinger, og gennemse for at interagere med eksemplerne på KPI'er og mobilrapporter.
   
   ![Reporting Services-eksempler](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-report-server"></a>Opret forbindelse til en rapportserver i det lokale miljø
Du kan se Power BI-rapporter, Reporting Services-mobilrapporter og KPI'er i Power BI-mobilapps. 

1. Åbn Power BI-appen på din mobilenhed.
2. Hvis du ikke er logget på Power BI endnu, skal du trykke på **Rapportserver**.
   
   ![Log på en rapportserver](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   Hvis du allerede er logget på Power BI-appen, skal du trykke på dit profilbillede i øverste venstre hjørne og derefter trykke på **Indstillinger** på det kontopanel, der glider ud.
3. Tryk på **Opret forbindelse til server** på siden Indstillinger, der åbnes.
   
    ![Opret forbindelse til server](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

    Mobilappen skal have adgang til serveren på en eller anden måde. Der er et par måder at gøre det på:
     * Den nemmeste måde er at være på samme netværk/anvende en VPN-forbindelse.
     * Det er muligt at bruge en Web Application Proxy til at oprette forbindelse, hvis du er uden for organisationen. Du kan få flere oplysninger under [Brug af OAuth til at oprette forbindelse til Reporting Services](mobile-oauth-ssrs.md).
     * Åbn en forbindelse (port) i firewallen.

4. Udfyld serveradressen, og giv serveren et brugervenligt navn, hvis du vil. Brug dette format til serveradressen:
   
     `https://<servername>/reports`
   
     OR
   
     `https://<servername>/reports`
   
   Inkluder **http** eller **https** foran forbindelsesstrengen.
   
    ![Dialogboksen Opret forbindelse til server](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. Når du har skrevet serveradressen og et valgfrit brugervenligt navn, skal du trykke på **Opret forbindelse** og derefter udfylde dit brugernavn og din adgangskode, når du bliver bedt om det.
6. Nu kan du se serveren i ruden Konti – i dette eksempel hedder den "Arbejdsserver".
   
   ![Rapportserver i navigationsruden](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="connect-to-an-on-premises-report-server-in-ios-or-android"></a>Opret forbindelse til en rapportserver i det lokale miljø i iOS eller Android

Hvis du får vist Power BI i iOS- eller Android-mobilappen, kan din it-administrator have defineret en appkonfigurationspolitik. Hvis det er tilfældet, skal du ikke angive lige så mange oplysninger, når du skal oprette forbindelse til en rapportserver. 

1. Du får vist en meddelelse om, at din mobilapp er konfigureret med en rapportserver. Tryk på **Log på**.

    ![Log på rapportserveren](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-sign-in.png)

2.  Detaljerne om rapportserveren er allerede udfyldt på siden **Opret forbindelse til server**. Tryk på **Opret forbindelse**.

    ![Rapportserveroplysningerne er udfyldt](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-remote-configure-connect-server.png)

3. Skriv en adgangskode, og tryk derefter på **Log på**. 

    ![Skærmbillede, der viser indtastning af adgangskode med knappen Log på.](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-address.png)

Nu kan du få vist og interagere med KPI'er og Power BI-rapporter på rapportserveren.

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>Se Power BI-rapporter og -KPI'er i Power BI-appen
Power BI-rapporter, Reporting Services-mobilrapporter og KPI'er vises i de samme mapper, som de er placeret i på Reporting Services-webportalen. 

* Tryk på en Power BI-rapport ![Ikon for Power BI-rapport](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png). Den åbnes i vandret tilstand, og du kan interagere med den i Power BI-appen.

    > [!NOTE]
  > Analysér ned og op er i øjeblikket ikke aktiveret i Power BI-rapporter på en Power BI-rapportserver.
  
    ![Power BI-rapport](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* I Power BI Desktop kan ejere [optimere en rapport](../../create-reports/desktop-create-phone-report.md) til Power BI-mobilapps. På din mobiltelefon har optimerede rapporter et særligt ikon, ![ikonet for Optimeret Power BI-rapport](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png), og layout.
  
    ![Power BI-rapport optimeret til mobil visning](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* Tryk på en KPI for at få den vist i fokuseret tilstand.
  
    ![KPI i fokuseringstilstand](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Se dine foretrukne KPI'er og rapporter
Du kan markere KPI'er og rapporter som favoritter på webportalen og derefter se dem i en enkelt praktisk mappe på din mobilenhed sammen med din foretrukne Power BI-dashboards.

* Tryk på **Favoritter** på navigationslinjen.
  
   ![Favoritter i navigationsruden](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   Dine foretrukne KPI'er og rapporter fra webportalen findes alle på denne side sammen med Power BI-dashboards i Power BI-tjenesten:
  
   ![Power BI-rapporter og -dashboards på siden Favoritter](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>Fjern en forbindelse til en rapportserver
1. Åbn ruden Konti, og tryk på **Indstillinger**.
2. Tryk på navnet på den server, som du ikke vil oprette forbindelse til.
3. Tryk på **Fjern server**.

## <a name="next-steps"></a>De næste trin
* [Hvad er Power BI?](../../fundamentals/power-bi-overview.md)  
* Har du nogen spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)