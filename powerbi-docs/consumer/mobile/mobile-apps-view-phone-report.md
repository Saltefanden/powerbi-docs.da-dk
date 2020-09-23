---
title: Få vist Power BI-rapporter, der er optimeret til din telefon
description: Læs om, hvordan du kan interagere med rapportsider, der er optimeret til visning i Power BI-telefonapps.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 05/05/2020
ms.author: painbar
ms.openlocfilehash: 9030d7ebacad92780a7dcafe33ae5bdded842b01
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90856132"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Få vist Power BI-rapporter, der er optimeret til din telefon

Gælder for:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Android-telefon](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone-telefoner |Android-telefoner |

Når du får vist en Power BI-rapport på din telefon, kontrollerer Power BI, om rapporten er optimeret til telefoner. Hvis den er, åbner Power BI automatisk den optimerede rapport i stående visning.

![Rapport i stående format](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Hvis der ikke findes en rapport, der er optimeret til telefoner, bliver rapporten stadig åbnet, men den åbnes i liggende format uden optimering til telefoner. Hvis du vender telefonen sidelæns, når du har åbnet en rapport, der er optimeret til telefoner, åbnes rapporten med det oprindelige rapportlayout uden optimering. Hvis det kun er nogle af siderne, der er optimeret, vises der en meddelelse i stående format om, at rapporten er tilgængelig i liggende format.

![Rapportside, der ikke er optimeret](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Alle andre funktioner i Power BI-rapporterne kan stadig bruges i de rapporter, der er optimeret til telefoner. Få mere at vide om, hvad du kan gøre i:

* [Rapporter på iPhone-telefoner](mobile-reports-in-the-mobile-apps.md). 
* [Rapporter på Android-telefoner](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrer rapportsiden på en telefon
Hvis der er defineret filtre i en rapport, der er optimeret til telefoner, kan du bruge filtrene, når du får vist rapporten på en telefon. Rapporten åbnes på din telefon filtreret efter de værdier, der filtreres efter i rapporten på internettet. Du får vist en meddelelse om, at der er aktive filtre på siden. Du kan ændre filtrene på telefonen.

1. Tryk på filterikonet ![Telefonfilterikon](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) nederst på siden.

2. Brug grundlæggende eller avanceret filtrering for at få vist de resultater, du er interesseret i.
   
    ![Avanceret filter i Power BI-telefonrapport](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.png)

## <a name="cross-highlight-visuals"></a>Tværgående fremhævning i visualiseringer
Tværgående fremhævning af visualiseringer i stående visning fungerer på samme måde som i Power BI-tjenesten og i telefoner i liggende visning: Når du vælger data i en visualisering, fremhæves relaterede data i de andre visualiseringer på siden.

Læs mere om [filtre og fremhævning i Power BI](../../create-reports/power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Vælg visualiseringer
Når du vælger en visualisering i en rapport på en telefon, fremhæves visualiseringen, og der fokuseres på den, så du ikke kan bruge fingerbevægelser på dit canvas.

Når du har valgt en visualisering kan du bladre i visualiseringen. Hvis du vil fravælge en visualisering, skal du trykke et sted uden for visualiseringen.

## <a name="open-visuals-in-focus-mode"></a>Åbn visualisering i Fokustilstand
Telefonrapporter tilbyder også en fokustilstand: Du får en større visning af en enkelt visual, og det er nemmere at udforske den.

* Tryk på de tre prikker ( **...** ) i øverste højre hjørne af en visualisering i en rapport på telefonen, og vælg **Udvid til fokustilstand**.
  
    ![Udvid til fokustilstand](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

Det, du foretager dig i fokustilstand, påvirker dit rapportlærred og omvendt. Hvis du for eksempel fremhæver en værdi i en visualisering og derefter går tilbage til hele rapporten, filtreres rapporten efter den værdi, du fremhævede i visualiseringen.

Nogle handlinger kan kun udføres i Fokustilstand på grund af den begrænsede skærmstørrelse:

* **Brug detailudledning** for at få vist flere oplysninger i en visualisering. Læs mere om [at få vist oplysninger på forskellige niveauer](mobile-apps-view-phone-report.md#drill-down-in-a-visual) i en rapport på en telefon herunder.
* **Sortér** værdierne i visualiseringen.
* **Tilbagefør**: Ryd de trin, du har udført i visualiseringen, og gå tilbage til den definition, der var angivet ved oprettelse af rapporten.
  
    Hvis du vil rydde alle ændringerne fra en visualisering, skal du trykke på de tre prikker ( **...** ) > **Tilbagefør**.
  
    ![Vend tilbage](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Hvis du bruger Tilbagefør på rapportniveau, ryddes dine ændringer fra alle visualiseringer. Hvis du bruger Tilbagefør på visualiseringsniveau, ryddes ændringer i den valgte visualisering.   

## <a name="drill-down-in-a-visual"></a>Detailudledning i en visualisering
Hvis der er defineret hierarkiniveauer i en visualisering, kan du dykke ned i de mere detaljerede oplysninger, som vises i en visualisering, og derefter gå opad i hierarkiet igen. Du kan [tilføje detailudledning i en visualisering](../end-user-drill.md) i enten Power BI-tjenesten eller i Power BI Desktop.

Der findes få typer detailudledning:

### <a name="drill-down-on-a-value"></a>Detailudledning for en værdi
1. Tryk længe (tryk og hold nede) på et datapunkt i en visual.
2. Der vises værktøjstip, og hvis der er defineret et hierarki, vises der en pil for detailudledning og færre detaljer i sidefoden for værktøjstippet.
3. Tryk på pil ned for detailudledning

    ![Tryk på detailudledning](media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Tryk på pil op for færre detaljer.

### <a name="drill-to-next-level"></a>Udvid til næste niveau
1. Tryk på de tre prikker ( **...** ) i øverste højre hjørne i en rapport på telefonen, og vælg **Udvid til fokustilstand**.
   
    ![Udvid til fokustilstand](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    I dette eksempel viser søjlerne de aktuelle værdier for stater.
2. Tryk på udforskningsikonet ![Ikonet Udforsk](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) nederst til venstre.
   
    ![Tilstanden Udforsk](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Tryk på **Vis næste niveau** eller **Udvid til næste niveau**.
   
    ![Udvid til næste niveau](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Nu viser søjlerne værdierne for byer.
   
    ![Udvidede niveauer](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Hvis du trykker på pilen i øverste venstre hjørne, kommer du tilbage til telefonrapporten med værdierne udvidet til det nederste niveau.
   
    ![Stadig udvidet til nederste niveau](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Hvis du vil tilbage til det oprindelige niveau, skal du trykke på de tre prikker ( **...** ) igen og vælge **Tilbagefør**.
   
    ![Vend tilbage](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Detaljeadgang fra en værdi
Detaljeadgang knytter værdier på én rapportside til andre rapportsider. Når du får detaljeadgang fra et datapunkt til en anden rapportside, bruges datapunktets værdier til at filtrere siden med detaljeadgang, eller den vil være i konteksten for de valgte data.
Rapportforfattere kan [definere detaljeadgang](../../create-reports/desktop-drillthrough.md), når de opretter rapporten.

1. Tryk længe (tryk og hold nede) på et datapunkt i en visual.
2. Der vises værktøjstip, og hvis der er defineret detaljeadgang, vises der en pil for detaljeadgang i sidefoden for værktøjstippet.
3. Tryk på pilen for detaljeadgang

    ![Tryk på detaljeadgang](media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Vælg den rapportside, du vil have detaljeadgang til

    ![Vælg en rapportside](media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Brug knappen Tilbage i appoverskriften for at gå tilbage til den side, du startede fra.


## <a name="next-steps"></a>Næste trin
* [Opret rapporter, der optimeret til Power BI-mobilapps](../../create-reports/desktop-create-phone-report.md)
* [Opret en telefonvisning af et dashboard i Power BI](../../create-reports/service-create-dashboard-mobile-phone-view.md)
* [Opret dynamiske visualiseringer, der er optimeret til alle størrelser](../../visuals/power-bi-report-visualizations.md)
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)