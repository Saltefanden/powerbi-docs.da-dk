---
title: Genstart en Power BI Premium-kapacitet
description: Få mere at vide om, hvordan du genstarter en Power BI Premium-kapacitet for at løse problemer med ydeevnen.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: ac0935dd6f2239ab96b9e7689a4f8e5bc013efa1
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512510"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Genstart en Power BI Premium-kapacitet

Som Power BI-administrator skal du muligvis genstarte en Premium-kapacitet. I denne artikel forklarer vi, hvordan du genstarter en kapacitet og besvarer flere spørgsmål om genstart og ydeevne.

## <a name="why-does-power-bi-provide-this-option"></a>Hvorfor rummer Power BI denne mulighed?

Power BI giver brugerne mulighed for at udføre komplekse analyser af enorme mængder data. Desværre kan brugerne forårsage problemer med ydeevnen ved at overlæsse Power BI-tjenesten med job, skrive alt for avancerede forespørgsler, oprette cirkulære referencer osv.

Delt kapacitet i Power BI tilbyder beskyttelse mod sådanne situationer ved at angive grænser for filstørrelser, opdatere tidsplaner og andre aspekter af tjenesten. I en Power BI Premium-kapacitet er de fleste af disse begrænsninger dog fjernet. En enkelt rapport med et forkert DAX-udtryk eller en meget kompleks model kan derfor medføre betydelige problemer med ydeevnen. Når en rapport behandles, kan den forbruge alle de tilgængelige ressourcer i kapaciteten. 

Power BI forbedrer konstant, hvordan brugere af Premium-kapacitet beskyttes mod sådanne problemer. Vi giver også administratorer værktøjer til at analysere, hvornår kapaciteter er overbelastede og hvorfor. Du kan finde flere oplysninger i vores [korte træningssession](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) og [lange træningssession](https://powerbi.tips/2018/07/). Du skal også være i stand til at afhjælpe betydelige problemer, når de opstår. Den hurtigste måde at afhjælpe disse problemer på er ved at genstarte kapaciteten.

> [!NOTE]
> Power BI Premium har for nylig udgivet en ny version af Premium med navnet **Premium Gen2**, der i øjeblikket er tilgængelig som prøveversion. Prøveversion af Gen2-kapaciteter kræver ikke genstart, så denne funktion er ikke tilgængelig i Premium Gen2.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>Er det sikkert at genstarte? Mister jeg nogen data?

Alle de gemte data, definitioner, rapporter og dashboards på din kapacitet forbliver intakte efter genstart. Når du genstarter en kapacitet, stoppes igangværende planlagte opdateringer og ad hoc-opdateringer midlertidigt af opdateringsprogrammet i de fleste tilfælde, og derefter genstarter de for at opdatere den logik for nye forsøg, der er indbygget i Power BI. Tjenesten forsøger igen at udføre eventuelle berørte opdateringer, når kapaciteten bliver tilgængelig. Status for opdateringer kan ikke ændres i brugergrænsefladen under genstartsprocessen. 

De brugere, der interagerer med kapaciteten, mister det arbejde, der ikke er gemt, under en genstartsproces. Brugerne skal opdatere deres browsere, når genstarten er fuldført.

## <a name="how-do-i-restart-a-capacity"></a>Hvordan genstarter jeg en kapacitet?

Følg denne fremgangsmåde for at genstarte en kapacitet.

1. I Power BI-administrationsportalen skal du på fanen **Kapacitetsindstillinger** gå til din kapacitet. 

1. Føj *funktionsflaget* **CapacityRestart** til kapacitetens URL-adresse: `https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`.

1. Under **Avancerede indstillinger** > **CAPACITY RESTART** skal du vælge **Genstart kapacitet**.

    ![Genstart kapacitet](media/service-admin-premium-restart/restart-capacity.png)

1. I dialogboksen **Genstart kapacitet** skal du vælge **Ja, genstart kapacitet**.

    ![Bekræft genstart](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>Hvordan kan jeg undgå problemer i fremtiden?

Den bedste måde at undgå problemer på er at lære brugerne om effektiv datamodellering. Du kan finde flere oplysninger i vores [træningssession](https://powerbi.tips/2018/07/).

Vi anbefaler også, at du [overvåger kapaciteterne](service-admin-premium-monitor-capacity.md) jævnligt for tendenser, der indikerer, at der er underliggende problemer. Vi planlægger jævnligt versioner af appen til overvågning og andre værktøjer, så du kan overvåge og administrere kapaciteterne mere effektivt.

## <a name="next-steps"></a>Næste trin

[Hvad er Power BI Premium?](service-premium-what-is.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
