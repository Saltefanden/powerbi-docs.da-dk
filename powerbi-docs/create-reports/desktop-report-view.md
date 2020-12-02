---
title: Rapportvisning i Power BI Desktop
description: Rapportvisning i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 10/12/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 3b168eb0e6a475651f4f8fb6337c518812d8ffcf
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412868"
---
# <a name="work-with-report-view-in-power-bi-desktop"></a>Arbejde med Rapportvisning i Power BI Desktop

Hvis du har arbejdet med Power BI, ved du, hvor let det er at oprette rapporter med dynamiske perspektiver, som giver indsigt i dine data. Power BI har også mere avancerede funktioner i Power BI Desktop. Med Power BI Desktop kan du oprette avancerede forespørgsler, mikse data fra flere kilder, oprette relationer mellem tabeller med mere.

Power BI Desktop indeholder *Rapportvisning*, hvor du kan oprette et vilkårligt antal rapportsider med visualiseringer. Rapportvisning i Power BI Desktop giver dig stort set samme designoplevelse som Redigeringsvisning i en rapport i *Power BI-tjenesten*. Du kan f.eks. flytte visualiseringer rundt og kopiere, indsætte og flette dem.

Forskellen mellem dem er, at når du bruger Power BI Desktop, kan du arbejde med dine forespørgsler og modellere dine data for at sikre, at dataene giver den bedste indsigt i dine rapporter. Du kan derefter gemme din Power BI Desktop-fil et sted efter eget valg, uanset om det er på dit lokale drev eller i cloudmiljøet.

## <a name="lets-take-a-look"></a>Lad os se!

Når du indlæser data i Power BI Desktop, får du vist Rapportvisning med et tomt lærred, med links, der kan hjælpe dig med at føje data til din rapport.

![Power BI Desktop](media/desktop-report-view/report-view-blank-canvas.png)

Du kan skifte mellem **Rapportvisning**, **Datavisning** og **Relationsvisning** ved at vælge ikonerne på navigationsruden til venstre:

![Ikonet Rapportvisning](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

Når du har tilføjet nogle data, kan du føje felter til en ny visualisering på lærredet.

![Tilføj en visualisering ved at trække fra ruden Felter](media/desktop-report-view/pbid_reportview_addvis.gif)

Hvis du vil ændre visualiseringstypen, kan du vælge den på lærredet og derefter vælge en ny type i **Visualiseringer**.

![Skift en visualisering ved at vælge en ny](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Sørg for at eksperimentere med forskellige visualiseringstyper. Det er vigtigt, at din visualisering formidler oplysningerne i dine data klart.

En rapport har mindst én tom side til at starte med. Sider vises i navigationsruden lige til venstre for canvasset. Du kan føje alle mulige visualiseringer til en side, men det er vigtigt ikke at overdrive. Hvis du har for mange visualiseringer på en side, ser det rodet ud, og det kan være svært at finde de relevante oplysninger. Du kan tilføje nye sider i din rapport. Du skal blot klikke på **Ny side** på båndet.

![Ikonet Ny side](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Hvis du vil slette en side, skal du klikke på **X** på sidens fane nederst i rapportvisningen.

![Tilføj en side i en rapport](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Rapporter og visualiseringer kan ikke fastgøres til et dashboard i Power BI Desktop. Hvis du vil gøre dette, skal du publicere på dit Power BI-websted. Du kan få flere oplysninger i [Publicer datasæt og rapporter fra Power BI Desktop](desktop-upload-desktop-files.md).

## <a name="copy-and-paste-between-reports"></a>Kopiér og indsæt mellem rapporter

Du kan nemt tage en visualisering fra én Power BI Desktop-rapport og indsætte den i en anden rapport. Du skal blot bruge tastaturgenvejen Ctrl + C til at kopiere din rapportvisualisering. I den anden Power BI Desktop-rapport skal du bruge Ctrl + V til at indsætte visualiseringen i den anden rapport. Du kan vælge én visualisering ad gangen eller kopiere alle visualiseringer på en side og derefter indsætte dem i Power BI Desktop-destinationsrapporten.

Muligheden for at kopiere og indsætte visualiseringer er nyttig for personer, der ofte opretter og opdaterer flere rapporter. Når du kopierer mellem filer, vil indstillinger og formatering, der udtrykkeligt er angivet i formateringsruden, være gældende, og visualiseringer, der afhænger af et tema eller af standardindstillinger, opdateres automatisk, så de matcher temaet i destinationsrapporten. Så når du formaterer en visualisering, og den ser ud præcist, som du ønsker det, kan du kopiere og indsætte den i nye rapporter og bevare alt det gode formateringsarbejde.

Hvis felterne i din model er forskellige, får du vist en fejl i visualiseringen og en advarsel om, hvilke felter der ikke findes. Fejlen ligner det, du ser, når du sletter et felt i den model, som en visualisering bruger.

![Fejl i kopiering/indsættelse i en visualisering – intet datafelt](media/desktop-report-view/report-view_07.png)

Du løser fejlen ved blot at erstatte de brudte felter med de felter, du vil bruge fra modellen i den rapport, som du indsatte visualiseringen i. Hvis du bruger en brugerdefineret visualisering, skal du også importere den brugerdefinerede visualisering til destinationsrapporten.

## <a name="hide-report-pages"></a>Skjul rapportsider

Når du opretter en rapport, kan du også skjule sider i rapporten. Denne tilgang kan være nyttig, hvis du har brug for at oprette underliggende data eller visualiseringer i rapporten, men ikke ønsker, at disse sider skal være synlige for andre, f.eks. når du opretter tabeller eller understøttende visualiseringer, som bruges på andre rapportsider. Der kan være mange andre kreative årsager til, at du vil oprette en rapportside og derefter skjule den i en rapport, du vil publicere.

Det er nemt at skjule en rapportside. Du skal blot højreklikke på rapportsidens fane og vælge **Skjul** i den menu, der vises.

![Indstillingen Skjul side](media/desktop-report-view/report-view_05.png)

Du skal dog gøre nogle få overvejelser, når du skjuler en rapportside:

* Du kan stadig se en skjult rapportvisning i Power BI Desktop, selvom sidens titel er nedtonet. På følgende billede er side 4 skjult.

    ![nedtonet side, der er skjult](media/desktop-report-view/report-view_06.png)

* Du *kan ikke* se en skjult rapportside, når du får vist rapporten i Power BI-tjenesten.

* Det er *ikke* en sikkerhedsforanstaltning at skjule en rapportside. Brugerne kan stadig tilgå siden, og sidens indhold er stadig tilgængelig vha. detaljeadgang og andre metoder.

* Når en side er skjult, vises der ingen navigationspile i Visningstilstand.
