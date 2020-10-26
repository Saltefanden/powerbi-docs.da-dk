---
title: Vis præsentationstilstand på Surface Hub og Windows 10 – Power BI
description: Se, hvordan du får vist Power BI-rapporter på Surface Hub, og hvordan du får vist Power BI-dashboards, -rapporter og -felter i fuldskærmsvisning på Windows 10-enheder.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 08/12/2020
ms.author: painbar
ms.openlocfilehash: a47af4b96e80508a6ea21de2d8d3e0b40f907d8d
ms.sourcegitcommit: 383d87841d2509131fac7cc02c5c37c6a868144f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/14/2020
ms.locfileid: "92025927"
---
# <a name="view-reports-and-dashboards-in-presentation-mode-on-surface-hub-and-windows-10-devices"></a>Få vist rapporter og dashboards i præsentationstilstand på Surface Hub og Windows 10-enheder
Du kan bruge præsentationstilstand til at vise rapporter og dashboards i fuld skærm på Windows 10-enheder og Surface Hub. Præsentationstilstand er praktisk til at vise Power BI på møder eller konferencer eller på en dedikeret projektor på kontoret. Du kan også bruge det for at se mest muligt på en lille skærm.

![Rapport i fuldskærmsvisning](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-2.png)

I præsentationstilstand:
* Alle forstyrrende elementer (f. eks. navigation og menulinjer) forsvinder, hvilket gør det lettere at fokusere på dataene i din rapport.
* En handlingsværktøjslinje bliver tilgængelig, så du kan interagere med dine data og styre præsentationen.
* Du kan afspille et slideshow, der automatisk skifter mellem sider, bogmærker eller både sider og bogmærker.

>[!NOTE]
>Understøttelse af Power BI-mobilapp til **telefoner, der bruger Windows 10 mobile**, ophører den 16. marts 2021. [Få mere at vide](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="use-presentation-mode"></a>Brug præsentationstilstand
Tryk på ikonet **Fuld skærm** i Power BI-mobilappen for at gå til fuldskærmsvisning.
![Ikonet Fuld skærm](././media/mobile-windows-10-app-presentation-mode/power-bi-full-screen-icon.png) Overflødige elementer i appens forsvinder, og der vises en værktøjslinje nederst på skærmen eller i højre og venstre side (afhænger af skærmstørrelsen).

[![Rapport i fuldskærmsvisning med værktøjslinjer i siden](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-toolbar.png)](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-toolbar-expanded.png#lightbox)

Fra værktøjslinjen kan du udføre følgende handlinger:

| Ikon | Handling |
|------|--------|
|![ikonet Tilbage](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-back-icon.png)|**Gå tilbage** til forrige side. Hvis du trykker på ikonet, og holder det nede, åbnes brødkrummevinduerne, hvilket giver dig mulighed for at navigere til mappen med din rapport eller til dit dashboard.|
|![Ikonet Sideinddeling](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-pages-icon.png)|**Skift sider**, og få vist en anden side af rapporten i din præsentation.|
|![Ikonet Bogmærker](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-bookmarks-icon.png)|**Anvend et bogmærke** for at præsentere den specifikke visning af dine data, som bogmærket henter. Du kan anvende både personlige bogmærker og rapportbogmærker.|
|![Ikonet Håndskrift](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-ink-icon.png)|**Vælg en farve til håndskrift**, når du bruger Surface-pennen til at tegne på og anmærke din rapportside.|
|![Ikonet Viskelæder](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-eraser-icon.png)|**Slet håndskriftsmærker**, du eventuelt har angivet med Surface-pennen for at tegne på og anmærke din rapportside.          |
|![Ikonet Nulstil](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-reset-icon.png)|**Nulstil til standardvisning** og ryd eventuelle filtre, udsnitsværktøjer eller andre ændringer af datavisning, som du eventuelt har foretaget under præsentationen.|
|![Delingsikon](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-share-icon.png)|**Del** et billede af præsentationsvisningen med dine kolleger. Billedet indeholder alle annotationer, du har angivet med Surface-pennen under præsentationen.|
|![Ikonet Opdater](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-refresh-icon.png)|**Opdater** rapporten.|
|![Ikonet Afspil](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-play-icon.png)|**Afspil slideshowet** – skjul handlingslinjen, og start slideshowet. Med en vælger kan du vælge rotere automatisk mellem sider, bogmærker eller både sider og bogmærker. Slideshowet roterer som standard mellem sider én gang hvert 30. sekund. Du kan ændre disse indstillinger i [**Indstillinger > Indstillinger**](#slideshow-settings). Se [flere detaljer](#slideshows) om slideshow|
|![Afslut fuldskærmsvisning](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-exit-full-screen-icon.png)|**Afslut** præsentationstilstand.|
|![Ikonet Søg](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-search-icon.png)|**Søg** for at søge efter andre artefakter i Power BI.|

Du kan fradocke værktøjslinjen og trække den til en hvilken som helst placering på skærmen. Dette er nyttigt i forbindelse med store skærme, når du vil fokusere på et bestemt område i din rapport og gerne vil have de tilgængelige værktøjer ved siden af det. Du skal blot placere fingeren på værktøjslinjen og stryge det ind på rapportlærredet.

[![Rapport i præsentationstilstand og fradocket værktøjslinje](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-drag-toolbar-2.png)](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-drag-toolbar-2-expanded.png#lightbox)

## <a name="slideshows"></a>Slideshow

Du kan afspille et slideshow for automatisk at gennemgå din præsentation. Du kan indstille slideshowet til at gennemgå sider, bogmærker eller både sider og bogmærker. Under slideshowet vil rapportsider med [automatisk sideopdatering](../../create-reports/desktop-automatic-page-refresh.md) fortsætte med automatisk opdatering som konfigureret, så det sikres, at de mest aktuelle data altid vises.

Når du vælger knappen **Afspil** på handlingsværktøjslinjen, begynder slideshowet. Der vises en controller, som giver dig mulighed for at afbryde slideshowet midlertidigt eller ændre det, der afspilles: sider, bogmærker eller både sider og bogmærker.

![Skærmbillede af slideshowvælger](././media/mobile-windows-10-app-presentation-mode//power-bi-windows-10-slideshow-selector.png)

 Navnet på den aktuelt viste visning (side eller bogmærke og side) vises i controlleren. På billedet ovenfor kan du se, at bogmærket **Asien og Stillehavsområdet** aktuelt vises på siden **Sales Performance** i rapporten **Sales**.

Et slideshow bevæger sig som standard kun gennem sider med et sideskift hvert 30. sekund. Du kan ændre standardfunktionsmåden under [Indstillinger for slideshow](#slideshow-settings).


### <a name="auto-play-a-slideshow-on-startup"></a>Afspil automatisk et slideshow ved start

Du kan konfigurere Power BI-mobilappen til at begynde at afspille et slideshow automatisk, hver gang appen startes. Denne indstilling er praktisk, hvis du vil skabe en kioskagtig oplevelse, der kører en rapport på offentlige skærme uden manuel indgriben. Se [Indstillinger for slideshow](#slideshow-settings) for at få oplysninger om, hvordan du konfigurerer en rapport til automatisk afspilning.

### <a name="slideshow-settings"></a>Indstillinger for slideshow

Et slideshow bevæger sig som standard kun gennem sider med et sideskift hvert 30. sekund. Du kan ændre denne standardfunktionsmåde ved at gå til **Indstillinger > Indstillinger** som vist nedenfor. Du kan også slå automatisk afspilning til og vælge en rapport, der skal afspilles.

1. Vælg ikonet Indstillinger.

1. Åbn fanen Indstillinger.

1. Du kan evt. ændre standardindstillingerne for, hvad slideshowet overføres fra (sider, bogmærker eller begge dele), og hvor ofte slidesene skal overføres.

1. Hvis du ønsker, at din rapport automatisk skal gå i gang med at blive afspillet, når appen startes, skal du slå til/fra-knappen til og vælge **Vælg rapport**. Du kan søge efter rapporter, du har adgang til.

![Skærmbillede af slideshowindstillinger](././media/mobile-windows-10-app-presentation-mode//power-bi-windows-10-slideshow-settings.png)

## <a name="next-steps"></a>Næste trin
* [Få vist dashboards og rapporter i fuldskærmsvisning fra Power BI-tjenesten](../end-user-focus.md)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)