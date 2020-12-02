---
title: Rapportdata i Power BI Report Builder
description: Dit første trin til at designe en rapport i Power BI Report Builder er at oprette datakilder og datasæt, der repræsenterer de underliggende rapportdata.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 08/04/2020
ms.openlocfilehash: 97b93f23c8070af1b514032cea122b257097d664
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2020
ms.locfileid: "96120642"
---
# <a name="report-data-in-power-bi-report-builder"></a>Rapportdata i Power BI Report Builder

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Rapportdata kan stamme fra flere kilder af data i din organisation. Dit første trin til at designe en rapport i Power BI Report Builder er at oprette datakilder og datasæt, som repræsenterer de underliggende rapportdata. Hver datakilde indeholder oplysninger om dataforbindelse. Hvert datasæt indeholder en forespørgselskommando, der definerer det sæt af felter, der skal bruges som data fra en datakilde. Hvis du vil visualisere data fra hvert datasæt, skal du tilføje et dataområde, f.eks. en tabel, en matrix, et diagram eller et kort. Når rapporten behandles, kører forespørgslerne på datakilden, og hvert dataområde udvides efter behov for at vise forespørgselsresultaterne for datasættet.  

Få mere at vide om, hvordan [opretter en integreret datakilde til sideinddelte rapporter i Power BI Report Builder](paginated-reports-embedded-data-source.md).


##  <a name="terms"></a><a name="BkMk_ReportDataTerms"></a> Vilkår  
  
- **Dataforbindelse.** Også kendt som en *datakilde*. En dataforbindelse omfatter et navn og forbindelsesegenskaber, der er afhængige af forbindelsestypen. En dataforbindelse indeholder med vilje ikke legitimationsoplysninger. En dataforbindelse angiver ikke, hvilke data der skal hentes fra den eksterne datakilde. For at gøre det skal du angive en forespørgsel, når du opretter et datasæt.  
  
- **Forbindelsesstreng.** En forbindelsesstreng er en strengversion af de forbindelsesegenskaber, der er nødvendige for at oprette forbindelse til en datakilde. Forbindelsesegenskaber varierer afhængigt af dataforbindelsestypen. 

    > [!NOTE]
    > Forbindelsesstrenge for datakilder kan ikke være baseret på udtryk.
  
- **Integreret datakilde.** Også kendt som *rapportspecifikke datakilder*. En datakilde, der er defineret i en rapport og kun bruges af den pågældende rapport.  
  
- **Legitimationsoplysninger.** Legitimationsoplysningerne er de godkendelsesoplysninger, der skal angives for at give dig adgang til eksterne data.  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> Tip til at angive rapportdata

 Brug følgende oplysninger til at designe din strategi for data i rapporten.  
  
- **Filtrer data** Rapportdata kan filtreres i forespørgslen eller i rapporten. Du kan bruge datasæt og forespørgselsvariabler til at oprette overlappende parametre og give en bruger mulighed for at begrænse valgmulighederne fra tusindvis af valg til et mere håndterbart antal. Du kan filtrere data i en tabel eller et diagram på baggrund af parameterværdier eller andre værdier, som du angiver.  
  
- **Parametre** Forespørgselskommandoer for datasæt, der omfatter forespørgselsvariabler, opretter automatisk matchende rapportparametre. Du kan også oprette parametre manuelt. Når du får vist en rapport, vises parametrene i værktøjslinjen i rapporten. Brugerne kan vælge værdier til at styre rapportdata eller udseendet af rapporten. Hvis du vil tilpasse rapportdata til en bestemt målgruppe, kan du oprette sæt med rapportparametre med forskellige værdier, der er linket til den samme rapportdefinition, eller bruge det indbyggede felt **UserID**. 
  
- **Gruppér og aggreger data** Rapportdata kan grupperes og aggregeres i forespørgslen eller i rapporten. Hvis du aggregerer værdier i forespørgslen, kan du fortsat kombinere værdier i rapporten inden for rammerne af, hvad der giver mening.  
  
- **Sortér data** Rapportdata kan sorteres i forespørgslen eller i rapporten. Du kan også tilføje en interaktiv sorteringsknap i tabeller for at lade brugeren styre sorteringsrækkefølgen.  
  
- **Data baseret på udtryk** Da de fleste rapportegenskaber kan baseres på udtryk, og udtryk kan indeholde referencer til felter i datasæt og rapportparametre, kan du skrive effektive udtryk for at styre rapportdata og udseendet. Du kan give en bruger mulighed for at styre de data, vedkommende kan se, ved at definere parametre.  
  
- **Få vist data fra et datasæt** Data fra et datasæt vises typisk i et eller flere dataområder, f.eks. en tabel og et diagram.  
  
- **Få vist data fra flere datasæt** Du kan skrive udtryk i et dataområde på baggrund af ét datasæt, der slår værdier eller aggregater op i andre datasæt. Du kan inkludere underrapporter i en tabel på baggrund af ét datasæt for at vise data fra en anden datakilde.  
  
 Brug følgende liste til at definere datakilder for en rapport.  
  
- Forstå arkitekturen af bag softwaredatalag for din organisation og de potentielle problemer, der kan opstå fra datatyper. Forstå, hvordan dataudvidelser og databehandlingsudvidelser kan påvirke forespørgselsresultaterne. Datatyper varierer mellem kilden for data, dataprovidere og de datatyper, der er gemt i rapportdefinitionsfilen (.rdl).  
  
- Datakilder og datasæt forfattes i en rapport og publiceres til Power BI-tjenesten. Når de er publiceret, kan du konfigurere legitimationsoplysninger direkte i Power BI-tjenesten eller i din Enterprise Gateway. 

## <a name="next-steps"></a>Næste trin

- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Vejledning til datahentning for sideinddelte rapporter](../guidance/report-paginated-data-retrieval.md)
