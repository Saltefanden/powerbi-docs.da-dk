---
title: Brug tværgående detaljeadgang i Power BI Desktop
description: Få mere at vide om, hvordan du kan få detaljeadgang fra én rapport til en anden i Power BI Desktop
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/27/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 5cf1ed76f47eba9dc989b26fbb5dcc52f92ddd18
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414271"
---
# <a name="use-cross-report-drill-through-in-power-bi"></a>Brug tværgående detaljeadgang i Power BI

Med funktionen til *detaljeadgang på tværs af rapporter* i Power BI kan du gå fra én rapport til en anden i det samme arbejdsområde for Power BI-tjenesten eller den samme app, afhængigt af konteksten. Du kan bruge detaljeadgang på tværs af rapporter til at forbinde to eller flere rapporter, der har relateret indhold, og til at overføre filterkonteksten sammen med forbindelsen på tværs af rapporter. 

Hvis du vil starte detaljeadgang på tværs af rapporter, skal du vælge et datapunkt i en *kildes visualisering* af en *kilderapport* og derefter vælge destinationen **detaljeadgang på tværs af rapporter** i genvejsmenuen. 

![Power BI-muligheden for detaljeadgang på tværs af rapporter](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Handlingen for detaljeadgang åbner *destinationssiden* i *destinationsrapporten*. 

![Power BI-destination for detaljeadgang på tværs af rapporter](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

I denne artikel kan du se, hvordan du opretter og bruger detaljeadgang på tværs af rapporter til Power BI-rapporter.

> [!NOTE]
> Du kan ikke bruge detaljeadgang på tværs af rapporter med [Delt med mig-rapporter](../collaborate-share/service-share-dashboards.md#share-a-dashboard-or-report), der er delt individuelt. Hvis du vil bruge detaljeadgang på tværs af rapporter, skal du tilgå rapporter i de arbejdsområder, som du er medlem af.

## <a name="enable-cross-report-drill-through"></a>Aktivér tværgående detaljeadgang i rapport

Det første trin i aktivering af detaljeadgang på tværs af rapporter er at validere datamodellerne for kilde- og destinationsrapporterne. Selvom skemaerne i hver rapport ikke skal være ens, skal de felter, du vil overføre, findes i begge datamodeller. Navnene på felterne og navnene på de tabeller, de tilhører, skal være identiske. Strengene skal matche, og de skal skelne mellem store og små bogstaver.

Hvis du f.eks. vil overføre et filter for feltet **State** i tabellen **US States**, skal begge modeller have tabellen **US States** og feltet **State** i den pågældende tabel. Hvis det ikke er tilfældet, skal du opdatere feltnavnet eller tabelnavnet i den underliggende model. Hvis du blot opdaterer det viste navn for felterne, fungerer det ikke korrekt for detaljeadgang på tværs af rapporter.

Når du har valideret dine modeller, kan du gør det muligt for kilderapporten at bruge detaljeadgang på tværs af rapporter. 

1. Gå til **Filer** > **Indstillinger** > **Indstillinger** i Power BI Desktop. 
1. I vinduet **Indstillinger** i venstre navigation skal du nederst i afsnittet **Aktuel fil** vælge **Rapportindstillinger**. 
1. Nederst til højre under **Detaljeadgang på tværs af rapporter** skal du vælge **Tillad, at visualiseringer i denne rapport bruger detaljeadgangsdestinationer fra andre rapporter**. 
1. Vælg **OK**. 
   
   ![Aktivér tværgående detaljeadgang i Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Du kan også aktivere detaljeadgang på tværs af rapporter fra Power BI-tjenesten.
1. I Power BI-tjenesten skal du vælge det arbejdsområde, der indeholder dine destinations- og kilderapporter.
1. Ved siden af navnet på kilderapporten på listen over arbejdsområder skal du vælge symbolet for **Flere indstillinger** og derefter vælge **Indstillinger**. 
1. Nederst i ruden **Indstillinger** under **Detaljeadgang på tværs af rapporter** skal du vælge **Tillad, at visualiseringer i denne rapport bruger detaljeadgangsmål fra andre rapporter** og derefter vælge **Gem**.
   
   ![Aktivér tværgående detaljeadgang i Power BI-tjenesten](media/desktop-cross-report-drill-through/cross-report-drill-through-02a.png)

## <a name="set-up-a-cross-report-drill-through-target"></a>Konfigurer en destination for detaljeadgang på tværs af rapporter

Konfiguration af en destinationsside for detaljeadgang på tværs af rapporter minder om konfiguration af detaljeadgang i en rapport. Aktivering af detaljeadgang på destinationssiden giver andre visualiseringer mulighed for at rette mod siden til detaljeadgang. Hvis du vil oprette detaljeadgang i en enkelt rapport, kan du se [Brug af detaljeadgang i Power BI Desktop](desktop-drillthrough.md).

Du kan konfigurere en destination for detaljeadgang på tværs af rapporter i Power BI Desktop eller Power BI-tjenesten. 
1. Rediger destinationsfilen, og vælg afsnittet **Felter** i ruden **Visualiseringer** på destinationsrapporten. 
1. Under **Detaljeadgang** skal du indstille **Krydsrapport** til **Til**. 
1. Træk de felter, du vil bruge som destinationer for detaljeadgang, til **Tilføj detaljeadgangsfelter her**. For hvert felt skal du vælge, om du vil tillade detaljeadgang, når feltet bruges som en kategori, eller når det opsummeres som en måling. 
1. Vælg, om du vil **beholde alle filtre** for visualiseringen. Hvis du ikke vil overføre anvendte filtre til kildevisualiseringen til destinationsvisualiseringen, skal du vælge **Fra**.
   
   ![Ruden Visualiseringer med indstillinger for detaljeadgang fremhævet](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)
   
1. Hvis du kun bruger siden til detaljeadgang på tværs af rapporter, skal du slette knappen **Tilbage**, der automatisk føjes til lærredet. Knappen **Tilbage** fungerer kun til navigation i en rapport. 
1. Når du har konfigureret destinationssiden, skal du gemme rapporten, hvis du bruger Power BI-tjenesten, eller gemme og publicere rapporten, hvis du bruger Power BI Desktop.

Det var det. Dine rapporter er klar til detaljeadgang på tværs af rapporter. 

## <a name="use-cross-report-drill-through"></a>Brug detaljeadgang på tværs af rapporter

Hvis du vil bruge detaljeadgang på tværs af rapporter, skal du vælge kilderapporten i Power BI-tjenesten og derefter vælge en visualisering, der bruger feltet til detaljeadgang på den måde, du angav, da du konfigurerede destinationssiden. Højreklik på et datapunkt for at åbne genvejsmenuen for visualiseringen, vælg **Detaljeadgang**, og vælg derefter destinationen for detaljeadgang. Destinationer for detaljeadgang på tværs af rapporter er formateret som **Sidenavn [Rapportnavn]** .

![Power BI-mulighed for detaljeadgang på tværs af rapporter](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Du får vist resultaterne på destinationssiden for detaljeadgang på tværs af rapporter på samme måde, som du konfigurerede dem, da du oprettede destinationen. Resultaterne filtreres i overensstemmelse med indstillingerne for detaljeadgang.

![Power BI-destination for detaljeadgang på tværs af rapporter](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

> [!IMPORTANT]
> Power BI cachelagrer destinationer for detaljeadgang på tværs af rapporter. Hvis du foretager ændringer, skal du sørge for at opdatere din browser, hvis destinationerne for detaljeadgangen ikke ser ud som forventet. 

Hvis du angiver **Bevar alle filtre** til **Til**, når du konfigurerer destinationssiden, kan filterkonteksten for kildevisualiseringen indeholde følgende: 

- Rapport, side og filtre på visualiseringens niveau, der påvirker kildevisualiseringen 
- Tværgående filtrering og tværgående fremhævning, der påvirker kildevisualiseringen 
- Udsnitsværktøj og synkroniseringsudsnit på siden
- URL-parametre

Når du lander på destinationsrapporten for detaljeadgang, anvender Power BI kun filtre for de felter, der har præcise strengmatches for feltnavn og tabelnavn. 

Power BI anvender ikke selvklæbende filtre fra destinationsrapporten, men det anvender dit personlige standardbogmærke, hvis du har et. Hvis dit personlige standardbogmærke f.eks. omfatter et filter på rapportniveau for *Country = USA*, anvender Power BI dette filter, før filterkonteksten fra kildevisualiseringen anvendes. 

I forbindelse med detaljeadgang på tværs af rapporter overfører Power BI filterkonteksten til standardsider i destinationsrapporten. Power BI overfører ikke filterkontekst for sider med værktøjstip, fordi sider med værktøjstip er filtreret på baggrund af det visuelle element for den kilde, der udløser værktøjstippet.

Hvis du vil vende tilbage til kilderapporten efter detaljeadgangen på tværs af rapporter, skal du bruge knappen **Tilbage** i browseren. 

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Detaljeadgang på tværs af rapporter fungerer ikke i Power BI-rapporter i Power BI-rapportserver.

## <a name="next-steps"></a>Næste trin

Du vil måske også være interesseret i følgende artikler:

- [Udsnitsværktøjer i Power BI](../visuals/power-bi-visualization-slicers.md)
- [Brug detaljeadgang i Power BI Desktop](desktop-drillthrough.md)
