---
title: 'Hurtigstart: Opret en Power BI-rapport til Power BI-rapportserver'
description: "Få mere at vide om, hvordan du opretter en Power BI-rapport til Power BI-rapportserver med nogle få hurtige trin."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 10/28/2017
ms.author: maggies
ms.openlocfilehash: e492d31a8e1ed57a769c9a36f515d99369f6d6dc
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/13/2017
---
# <a name="quickstart-create-a-power-bi-report-for-power-bi-report-server"></a>Hurtigstart: Opret en Power BI-rapport til Power BI-rapportserver
Du kan lagre og administrere Power BI-rapporter i det lokale miljø i webportalen Power BI-rapportserver, lige som du kan lagre Power BI-rapporter i skyen i Power BI-tjenesten (https://powerbi.com). Du kan oprette og redigere rapporter i Power BI Desktop og publicere dem på webportalen. Derefter kan rapportlæsere i din organisation få dem vist i en browser eller i en Power BI-mobilapp på en mobilenhed.

![Power BI-rapport i webportalen](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Hvis du allerede har oprettet Power BI-rapporter i Power BI Desktop, er du klar til at oprette Power BI-rapporter til Power BI-rapportserver. Hvis det ikke er tilfældet, får du her fire hurtige trin til at komme i gang.

## <a name="step-1-install-power-bi-desktop-report-server"></a>Trin 1: Installér Power BI Desktop (rapportserver)
Du har muligvis allerede installeret Power BI Desktop for at oprette rapporter til Power BI-tjenesten. Vi anbefaler, at du installerer den version af Power BI Desktop, som er optimeret til Power BI-rapportserver, så du ved, at serveren og appen altid er synkroniseret. Du kan have begge versioner af Power BI Desktop på den samme computer.

1. I webportalen Power BI-rapportserver skal du vælge **Ny** > **Power BI-rapport**.
   
    ![Ny Power BI-rapport](media/quickstart-create-powerbi-report/report-server-web-portal-new-powerbi-report.png)
   
    Hvis du ikke har adgang til en Power BI-rapportserverwebportal, skal du gå til Microsoft Download Center og downloade [Microsoft Power BI Desktop](https://go.microsoft.com/fwlink/?linkid=837581) (optimeret til Power BI-rapportserver – juni 2017 GA).
2. Til sidst i installationsprocessen skal du markere **Start Power BI Desktop nu**.
   
    Programmet starter automatisk, og du er klar til at gå i gang. Du kan se, at du har den rigtige version, fordi der står "Power BI Desktop (rapportserver)" i titellinjen.
3. Hvis du ikke kender til Power BI Desktop, bør du overveje at se videoerne på velkomstskærmbilledet.
   
    ![Startskærm for Power BI Desktop](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>Trin 2: Vælg en datakilde
Du kan oprette forbindelse til en række forskellige datakilder. Læs mere om at [oprette forbindelse til datakilder](connect-data-sources.md).

1. På velkomstskærmen skal du vælge **Hent data**.
   
    Eller du kan vælge **Hent data** på fanen **Hjem**.
2. Vælg din datakilde – i dette eksempel **Analysis Services**.
   
    ![Vælg datakilde](media/quickstart-create-powerbi-report/report-server-get-data-ssas.png)
3. Udfyld **Server** og eventuelt **Database**. Sørg for, at **Opret liveforbindelse** er valgt > **OK**.
   
    ![Servernavn](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. Vælg den rapportserver, hvor du vil gemme dine rapporter.
   
    ![Valg af rapportserver](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>Trin 3: Design rapporten
Det her er den sjove del: Du får lov at oprette visuals, som illustrerer dine data.

Du kan f.eks. oprette et tragtformet diagram over kunder og gruppere værdier efter årsomsætning.

![Design en rapport](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. I **Visualiseringer** skal du vælge **Tragtformet diagram**.
2. Træk det felt, som skal tælles, til kategorien **Værdier**. Hvis det ikke er et numerisk felt, gør Power BI Desktop det automatisk til en *optælling* af værdien.
3. Træk det felt, der skal grupperes, over på kategorien **Gruppér**.

Læs meget mere om at [designe en Power BI-rapport](../desktop-report-view.md).

## <a name="step-4-save-your-report-to-the-report-server"></a>Trin 4: Gem din rapport på rapportserveren
Når rapporten er klar, kan du gemme den på den Power BI-rapportserver, du har valgt i Trin 2.

1. I menuen **Filer** skal du vælge **Gem som** > **Power BI-rapportserver**.
   
    ![Gem på rapportserveren](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. Nu kan du se den i webportalen.
   
    ![Få vist rapporten i webportalen](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger
Rapporter i Power BI-rapportserver og i Power BI-tjenesten (http://powerbi.com) fungerer stort set ens, men nogle enkelte funktioner er forskellige.

### <a name="in-a-browser"></a>I en browser
Power BI-rapportserver understøtter alle visualiseringer, herunder:

* Brugerdefinerede visuals

Rapporter i Power BI-rapportserver understøtter ikke:

* R-visuals
* ArcGIS-kort
* Brødkrummer

### <a name="in-the-power-bi-mobile-apps"></a>I Power BI-mobilappsene
Rapporter i Power BI-rapportserver understøtter al den grundlæggende funktionalitet i [Power BI-mobilappsene](../mobile-apps-for-mobile-devices.md), herunder:

* [Rapport med telefonlayout](../desktop-create-phone-report.md): Du kan optimere en rapport til Power BI-mobilapps. På din mobiltelefon har optimerede rapporter et særligt ikon, ![ikonet for rapport med telefonlayout](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-icon.png), og layout.
  
    ![Rapport optimeret til telefoner](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-report.png)

Rapporter i Power BI-rapportserver understøtter ikke disse funktioner i Power BI-mobilappsene:

* R-visuals
* ArcGIS-kort
* Brugerdefinerede visuals
* Brødkrummer
* Geofiltering eller stregkoder

## <a name="next-steps"></a>Næste trin
### <a name="power-bi-desktop"></a>Power BI Desktop
Der er så mange fantastiske ressourcer til at oprette rapporter i Power BI Desktop. Disse links er et godt sted at starte.

* [Introduktion til Power BI Desktop](../desktop-getting-started.md)
* Automatiseret læring: [Introduktion til Power BI Desktop](../guided-learning/gettingdata.yml#step-2)

### <a name="power-bi-report-server"></a>Power BI Report Server
* [Installér Power BI Desktop optimeret til Power BI-rapportserver](install-powerbi-desktop.md)  
* [Brugerhåndbog til Power BI-rapportserver](user-handbook-overview.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)