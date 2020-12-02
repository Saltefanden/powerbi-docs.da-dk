---
title: Brug SAP HANA i Power BI
description: Brug SAP HANA i Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 708a4439262111954012c944a464dd8e59db8068
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404450"
---
# <a name="connect-to-sap-hana-databases-in-power-bi"></a>Opret forbindelse til SAP HANA-databaser i Power BI

Med Power BI Desktop har du nu adgang til *SAP HANA*-databaser. Hvis du vil bruge SAP HANA, skal SAP HANA ODBC-driveren være installeret på den lokale klientcomputer, for at Power BI Desktop SAP HANA-dataforbindelsen kan fungere korrekt. Du kan downloade SAP HANA-klientværktøjer fra [SAP-udviklingsværktøjer](https://tools.hana.ondemand.com/#hanatools), som indeholder den nødvendige ODBC-driver. Du kan også få dem fra [SAP software Download Center](https://support.sap.com/en/my-support/software-downloads.html). I softwareportalen kan du søge efter *SAP HANA CLIENT* til Windows-computere. Da strukturen i SAP Software Download Center ofte ændres, kan vi ikke give en mere specifik vejledning til, hvordan du henter programmet.

Hvis du vil oprette forbindelse til en SAP HANA-database, skal du vælge **Hent data**, vælge **Database** > **SAP HANA-database** og derefter vælge **Opret forbindelse**:

![SAP HANA-database, dialogboksen Hent data, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

Når du opretter forbindelse til en SAP HANA-database, skal du angive servernavnet. Derefter skal du angive porten via rullelisten og inputfeltet.

I denne version understøttes SAP HANA i [DirectQuery](desktop-directquery-sap-hana.md) tilstand i Power BI Desktop og Power BI-tjenesten. Du kan også publicere og overføre rapporter til Power BI-tjenesten, når du ikke bruger SAP HANA i DirectQuery-tilstand. Du kan også publicere og overføre rapporter til Power BI-tjenesten, når du ikke bruger SAP HANA i DirectQuery-tilstand.

## <a name="supported-features-for-sap-hana"></a>Understøttede funktioner til SAP HANA

Denne version indeholder mange funktioner til SAP HANA som vist på listen nedenfor:

* Power BI-forbindelseskomponenten til SAP HANA bruger SAP ODBC-driveren for at give den bedste brugeroplevelse.

* SAP HANA understøtter både DirectQuery og Import.

* Power BI understøtter HANA-oplysningsmodeller, f.eks visningerne Analytic og Calculation, og har optimeret navigation.

* Med SAP HANA kan du også bruge funktionen Direct SQL til at oprette forbindelse til række- og kolonnetabeller.

* Power BI indeholder optimeret navigation for HANA-modeller.

* Power BI understøtter SAP HANA-variabler og -inputparametre.

* Power BI understøtter HDI-objektbeholderbaserede beregningsvisninger.

  * Understøttelse af HDI-objektbeholderbaserede beregningsvisninger findes i den offentlige prøveversion i august 2019-udgivelsen af Power BI Desktop. Hvis du vil have adgang til HDI-objektbeholderbaserede beregningsvisninger i Power BI, skal du sørge for, at de HANA-databasebrugere, du bruger sammen med Power BI, har tilladelse til at få adgang til HDI-kørselsobjektbeholderen, der gemmer de visninger, du vil have adgang til. Hvis du vil tildele denne adgang, skal du oprette en rolle, der giver adgang til din HDI-objektbeholder. Tildel derefter rollen til den HANA-databasebruger, du vil bruge sammen med Power BI. Denne bruger skal også have tilladelse til at læse fra systemtabellerne i \_SYS\_BI-skemaet som normalt. Se den officielle SAP-dokumentation for at få mere at vide om, hvordan du opretter og tildeler databaseroller. [Dette SAP-blogindlæg](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) kan være et godt sted at starte.

  * Der er i øjeblikket nogle begrænsninger for HANA-variabler, der er knyttet til HDI-baserede beregningsvisninger. Disse begrænsninger skyldes fejl på HANA-siden.
  
    For det første er det ikke muligt at anvende en HANA-variabel i en delt kolonne i en HDI-objektbeholderbaseret beregningsvisning. Du kan løse problemet med denne begrænsning ved at opgradere til HANA 2 version 37.02 og nyere eller HANA 2 version 42 og nyere. For det andet vises standardværdierne for variabler og parametre ikke i brugergrænsefladen i Power BI. En fejl i SAP HANA forårsager denne begrænsning, men SAP har ikke annonceret en rettelse endnu.

## <a name="limitations-of-sap-hana"></a>Begrænsninger i SAP HANA

Der er også nogle begrænsninger for brugen af SAP HANA som vist nedenfor:

* NVARCHAR-strenge afkortes til en maksimumlængde på 4000 Unicode-tegn.
* SMALLDECIMAL understøttes ikke.
* VARBINARY understøttes ikke.
* Kun datoer mellem 30.12.1899 og 31.12.9999 er gyldige.
* SAP HANA-opdatering med enkeltlogon understøttes ikke for opdateringer af Excel-projektmapper i øjeblikket. Hvis du vil opdatere dataene i Power BI, kan du bruge en Power BI-rapport med SAP HANA-enkeltlogon.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om DirectQuery og SAP HANA i følgende ressourcer:

* [DirectQuery og SAP HANA](desktop-directquery-sap-hana.md)
* [Brug DirectQuery i Power BI](desktop-directquery-about.md)
* [Power BI-datakilder](power-bi-data-sources.md)
* [Aktivér kryptering for SAP HANA](desktop-sap-hana-encryption.md)
