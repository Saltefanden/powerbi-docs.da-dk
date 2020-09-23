---
title: Brug af eksterne værktøjer i Power BI (prøveversion)
description: Benyt eksterne værktøjer til at udvide mulighederne i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/29/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7a7988ba9bb9efd4b2dec20fd2dc88478af439a2
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90855282"
---
# <a name="using-external-tools-in-power-bi-desktop-preview"></a>Brug af eksterne værktøjer i Power BI Desktop (prøveversion)

Fra og med udgivelsen af Power BI Desktop i juli 2020 kan du bruge eksterne værktøjer til at give Power BI Desktop yderligere funktioner og værdi. Understøttelsen af eksterne værktøjer giver dig adgang til det store udvalg af communityværktøjer til Analysis Services til BI-medarbejdere, såsom optimering af DAX-forespørgsler/-udtryk og administration af programlivscyklus.

Båndet **Eksterne værktøjer** i Power BI Desktop indeholder knapper til eksterne værktøjer, der er installeret på computeren, og som er registreret i Power BI Desktop. Eksterne værktøjer, der startes fra Power BI Desktop, forbindes automatisk med Analysis Services-programmet, der kører som en del af Power BI Desktop, så brugerne får en problemfri, sammenhængende oplevelse.

![Båndet med eksterne værktøjer i Power BI Desktop](media/desktop-external-tools/desktop-external-tools-01.png)

Disse udvalgte eksterne værktøjer omfatter følgende med links til deres installationsplacering. De enkelte eksterne værktøjer understøttes af deres respektive designere:

* [Tabular Editor](https://tabulareditor.com/)
* [DAX Studio](https://daxstudio.org)
* [ALM Toolkit](http://alm-toolkit.com)


De følgende afsnit indeholder en beskrivelse af de handlinger, som de eksterne værktøjer understøtter, en liste over udvalgte værktøjer, der er inkluderet i Power BI Desktop, og en vejledning i, hvordan du registrerer yderligere værktøjer.

## <a name="supported-write-operations"></a>Understøttede skrivehandlinger

Eksterne værktøjer kan oprette forbindelse til Power BI Desktop-datasæt (Analysis Services-model) for at redigere de følgende objekter. Redigering af en Power BI Desktop-skabelonfil (PBIT) understøttes ikke.

* [Målinger](/analysis-services/tabular-models/measures-ssas-tabular) til beregninger
* [Beregningsgrupper](/analysis-services/tabular-models/calculation-groups), der giver mulighed for genanvendelse af beregninger i komplekse modeller
* [Perspektiver](/analysis-services/tabular-models/perspectives-ssas-tabular), der giver mulighed for at definere fokuserede, virksomhedsdomænespecifikke visninger af metadata for datasæt

Det kan blive muligt at administrere oversættelser af metadata ved hjælp af eksterne værktøjer, men det understøttes ikke i øjeblikket i denne prøveversion. Hvis den aktuelle brugers landestandard er en oversat landestandard, fungerer redigering af objekter på feltlisten ikke korrekt i den aktuelle version af Power BI Desktop. 

Alle datasæt-metadata for [tabelobjektmodeller](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) kan åbnes til skrivebeskyttede formål, men objekter, der ikke med på listen, som beskrives i artiklen[Model for tabelobjekt](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo), understøttes endnu ikke til redigering i Power BI Desktop Analysis Services-instansen.


## <a name="featured-external-tools"></a>Udvalgte eksterne værktøjer

Følgende open source-communityværktøjer fungerer sammen med Power BI Desktop. De understøttes af deres respektive designere. Værktøjernes respektive installationsprogrammer registrerer dem sammen med Power BI Desktop ved installationen:

* Tabular Editor
* DAX Studio
* ALM Toolkit

Lad os se på disse værktøjer hver for sig.

### <a name="tabular-editor"></a>Tabular Editor

Du kan installere [Tabular Editor](https://tabulareditor.com/) via følgende link: [Tabular Editor-websted](https://tabulareditor.com/)

Med Tabular Editor kan BI-teknikere nemt opbygge, vedligeholde og administrere tabelmodeller ved hjælp af en intuitiv og ukompliceret editor. En hierarkisk visning vider alle objekter i din tabelmodel, organiseret efter visningsmapper med understøttelse af egenskabsredigering med flere valg og fremhævning af DAX-syntaks.

![Skærmbillede af Tabular Editor](media/desktop-external-tools/desktop-external-tools-02.png)

Du kan finde kildekoden til Tabular Editor i følgende GitHub-lager: [Tabular Editor på GitHub](https://github.com/otykier/TabularEditor)

Den designer af Tabular Editor er [Daniel Otykier](https://www.linkedin.com/in/daniel-otykier-2231876).


### <a name="dax-studio"></a>DAX Studio

Du kan installere [DAX Studio](https://daxstudio.org) via følgende link: [DAX Studio-websted](https://daxstudio.org)

DAX Studio er et komplet værktøj til DAX-oprettelse, diagnosticering, justering af ydeevne og analyse. Dets funktioner omfatter objektgennemsyn, integreret sporing, udspecificering af udførelse af forespørgsler med detaljeret statistik, fremhævning og formatering af DAX-syntaks. Følgende billede er et skærmbillede fra DAX Studio. 

![Skærmbillede af DAX Studio](media/desktop-external-tools/desktop-external-tools-03.png)

Du kan finde kildekoden til DAX Studio i følgende GitHub-lager: [DAX Studio på GitHub](https://github.com/DaxStudio/DaxStudio)

Den primære designer af DAX Studio er [Darren Gosbell](https://www.linkedin.com/in/darrengosbell).

### <a name="alm-toolkit"></a>ALM Toolkit

Du kan installere [ALM Toolkit](http://alm-toolkit.com) via følgende link: [ALM Toolkit-websted](http://alm-toolkit.com)

ALM Toolkit er et værktøj til skemasammenligning til Power BI-datasæt, som anvendes i ALM-scenarier (Application Lifecycle Management). Du kan bruge det til direkte udrulning på tværs af miljøer og til at bevare historiske data med trinvis opdatering. ALM Toolkit kan sammenligne og flette metadatafiler, forgreninger og lagre. Du kan genbruge fælles definitioner på tværs af datasæt.

![Skærmbillede af ALM Toolkit](media/desktop-external-tools/desktop-external-tools-04.png)

Du kan finde kildekoden til ALM Toolkit i følgende GitHub-lager: [ALM Toolkit på GitHub](https://github.com/microsoft/analysis-services)

Den primære designer af ALM Toolkit er [Christian Wade](https://www.linkedin.com/in/christianwade1).


## <a name="how-to-register-external-tools"></a>Sådan registrerer du eksterne værktøjer

Hvis du vil registrere andre eksterne værktøjer i Power BI Desktop, skal du oprette en JSON-fil med følgende indhold:

```json
{
    "name": "<tool name>",
    "description": "<tool description>",
    "path": "<tool executable path>",
    "arguments": "<optional command line arguments>",
    "iconData": "image/png;base64,<encoded png icon data>"
}
```

Følgende liste beskriver elementerne i JSON-filen:
 
* **name:** Angiv et navn til værktøjet, som skal vises som en knaptekst på båndet Eksterne værktøjer i Power BI Desktop.
* **description:** (valgfrit) Angiv en beskrivelse, der skal vises som et værktøjstip på knappen Eksterne værktøjer på båndet i Power BI Desktop.
* **path:** Angiv den fuldt kvalificerede sti til værktøjets eksekverbare fil.
* **arguments:** (valgfrit) Angiv en streng af kommandolinjeargumenter, som værktøjets eksekverbare fil skal startes med. Du kan bruge følgende pladsholdere:
    * **%server%:** Erstattes med servernavnet og portnummeret til den lokale instans af Analysis Services-tabellen til importerede/DirectQuery-datamodeller.
    * **%database%:** Erstattes med databasenavnet på modellen, som er hosted i den lokale instans af Analysis Services-tabellen til importerede/DirectQuery-datamodeller.
* **iconData:** Angiv billeddata, som skal gengives som et knapikon på båndet Eksterne værktøjer i Power BI Desktop. Strengen skal formateres i overensstemmelse med syntaksen for data-URI'er uden præfikset "data:".
 
Navngiv filen `"<tool name>.pbitool.json"`, og placer den i følgende mappe:

* `%commonprogramfiles%\Microsoft Shared\Power BI Desktop\External Tools`

I 64-bit-miljøer skal du placere filerne i følgende mappe:

* **Program Files (x86)\Common Files\Microsoft Shared\Power BI Desktop\External Tools**

Filer på denne angivne placering med udvidelsen **.pbitool.json** indlæses af Power BI Desktop ved start.

## <a name="disabling-external-tools-using-the-registry"></a>Deaktivering af eksterne værktøjer ved hjælp af registreringsdatabasen

Eksterne værktøjer kan deaktiveres ved hjælp af **gruppepolitikker** eller ved at redigere registreringsdatabasen, hvilket ligner processen til deaktivering af **brugerdefinerede visualiseringer**.

    Registry key: *Software\Policies\Microsoft\Power BI Desktop\*

    Registry value: *EnableExternalTools*

En værdi på 1 (decimal) aktiverer brugen af eksterne værktøjer i Power BI, hvilket er standardværdien.

En værdi på 0 (decimal) deaktiverer brugen af eksterne værktøjer i Power BI.


## <a name="next-steps"></a>Næste trin

Du vil måske også være interesseret i følgende artikler:

* [Brug tværgående detaljeadgang i Power BI-rapporter](desktop-cross-report-drill-through.md)
* [Brug af udsnitsværktøjer i Power BI Desktop](../visuals/power-bi-visualization-slicers.md)