---
title: Mobiludvikling
description: Sådan opretter du mobilvenlige Power BI-visualiseringer
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 99df7a301a1025d50c82c5cc7f5966325a6a6a6f
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747522"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Sådan opretter du mobilvenlige Power BI-visualiseringer
Mobilforbruget spiller en afgørende rolle i Power BI. En af fordelene er, at du kan oprette forbindelse til dine data uanset tid og sted.

Du skal som udvikler, der opretter Power BI-visualiseringer, være opmærksom på de entydige begrænsninger for de enkelte mobilenheder for at nå ud til så mange brugere som muligt og levere den bedste mobiloplevelse.

Brug [Power BI-appen til Windows, iOS og Android](../../consumer/mobile/mobile-apps-for-mobile-devices.md) for at give dine virksomhedsbrugere en omfattende visning af deres data, når de er på farten – lige ved hånden.

## <a name="requirements"></a>Krav

Følgende krav er vigtige i forbindelse med udviklingen af visualiseringer til mobilenheder:

- Gengiv

  Dine Power BI-visualiseringer skal kunne gengives på alle understøttede mobilenheder, herunder understøttede browsere og programmer, uden fejl i rapporter, dashboards, eller når de kører i **fokusstilstand**. 

- Interaktiv

  Interaktiv funktionalitet skal være angivet på samme måde, som den angives på stationære computere. Alle hændelser, der håndteres i browsere på stationære computere, skal understøttes eller have sammenlignelige hændelseshandlere til mobilenheder.
  
  Grundlæggende navigation og valg af datapunkter bør f.eks. have samme funktionalitet som browsere på stationære computere. Hvis en visualisering understøtter valg af flere elementer med **Ctrl**, skal udvikleren overveje at tilføje en tilsvarende hændelseshandler til mobilenheder.

  Følgende tabel indeholder en liste over tilsvarende hændelser på mobilenheder.

  | Navn på musehændelse | Navn på berøringshændelse |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | brug eksternt bibliotek |
  | `contextmenu` | brug eksternt bibliotek |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (eller eksternt bibliotek) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Ikke alle mobilenheder eller enheder med berøringsskærm understøtter musehændelser (eller hændelser med *musepræfikset*). Hvis det er tilfældet, skal *muse-* og *berøringshændelser* håndteres samtidig.

## <a name="optional"></a>Valgfri
Følgende betragtes som valgfri og bruges til at oprette en bedre oplevelse for slutbrugerne.

- Gengiv

  Hvis du vil understøtte mindre visualiseringer, kan du tilføje formateringsindstillinger, som brugeren kan ændre for at justere størrelsen på hvert element. Du kan f.eks. føje formateringsindstillinger til etiketter til brug i rapporter og dashboards. Det gør det muligt for brugerne at tilpasse en visualisering, så den passer til lige præcis deres mobilenhed.
  
  De samme indstillinger kan også anvendes for visualiseringer i browsere på stationære computere, og hvis der er behov for det, tilsidesættes for at tilpasse visualiseringen til mindre skærme.

  > [!NOTE]
  > Hvis du vil optimere en visualisering i **fokustilstand**, skal du være opmærksom på både stående og liggende retning på skærmen. Se [Vis indhold i fokustilstand](../../consumer/end-user-focus.md).

- Interaktiv

  Overvej at tilføje mobilspecifikke hændelseshandlere, f.eks. træk og rulning.

- Failover

  En visualisering skal vise en beskrivende fejl, hvis den ikke kan gengives på mobilenheden.

## <a name="supported-browsers-and-devices"></a>Understøttede browsere og enheder
Power BI-visualiseringen skal kunne gengives på alle enheder, der understøtter Power BI Apps. Du kan få flere oplysninger i [Understøttede browsere til Power BI](../../fundamentals/power-bi-browsers.md) og [Power BI-mobilapps](../../consumer/mobile/mobile-apps-for-mobile-devices.md).

Når du tester i forhold til de seneste modeller af Windows-, iOS- og Android-enheder, skal du overveje de fleste af disse kvalitetsaspekter.

## <a name="next-steps"></a>Næste trin
Kom i gang ved at se [Selvstudium: Udvikling af en Power BI-visualisering](./custom-visual-develop-tutorial.md).