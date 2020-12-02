---
title: Opdateringsoversigter i Power BI
description: Få mere at vide om, hvordan du bruger opdateringsoversigter i Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/27/2020
LocalizationGroup: Data refresh
ms.openlocfilehash: 285bc76ddb0a0afa571fba06096358c22781a121
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410775"
---
# <a name="refresh-summaries-for-power-bi"></a>Opdateringsoversigter i Power BI

Siden med **opdateringsoversigter** i Power BI, der findes på Power BI-administrationsportalen, giver dig kontrol over og indsigt i dine opdateringsplaner, kapaciteter og potentielle overlap i opdateringsplanen. Du kan bruge siden med opdateringsoversigter til at fastlægge, om du bør tilpasse opdateringsplanerne, til at få mere at vide om fejlkoder knyttet til opdateringsproblemer og til at administrere planen for opdatering af dine data korrekt. 

Der er to visninger af siden med opdateringsoversigter:

* **Historik** – viser historikken for opdateringsoversigten for Power BI Premium-kapaciteter, som du er administrator for.

* **Plan** – viser planen for planlagte opdateringer, som også kan afdække problemer med tidsintervaller, der overlapper.

Du kan også eksportere oplysninger om en opdateringshændelse til en .CSV-fil, hvilket kan give vigtige oplysninger om og indsigt i opdateringshændelser eller fejl, der kan have indvirkning på ydeevnen eller fuldførelsen af planlagte opdateringshændelser.

I de følgende afsnit ser vi nærmere på disse visninger skiftevist. 

## <a name="refresh-history"></a>Opdater historik

Du kan vælge visningen **Historik** ved at klikke på **Historik** på siden med opdateringsoversigter.

![Visningen Historik i opdateringsoversigter](media/refresh-summaries/refresh-summaries-01a.jpg)

Historik giver et overblik over resultaterne af de nyeste planlagte opdateringer af kapaciteter, som du har administratorrettigheder til. Du kan sortere visningen efter en hvilken som helst kolonne ved at klikke på kolonnen. Du kan vælge at sortere visningen efter den valgte kolonne i stigende eller rækkefølge eller ved hjælp af tekstfiltre.

![sortér visningen Historik](media/refresh-summaries/refresh-summaries-01b.jpg)

I visningen Historik er de data, der er knyttet til en given opdatering, baseret på op til de 60 nyeste poster for hver planlagte opdatering.

Du kan også eksportere oplysninger for en hvilken som helst planlagt opdatering til en. CSV-fil, som indeholder detaljerede oplysninger, herunder fejlmeddelelser for hver opdateringshændelse. Eksport til en .CSV-fil giver dig mulighed for at sortere filen efter en hvilken som helst af kolonnerne, søge efter ord, sortere efter fejlkoder eller ejere osv. På følgende billede vises et eksempel på en eksporteret .CSV-fil. 

![Eksportér oplysninger om en opdatering](media/refresh-summaries/refresh-summaries-05.jpg)

Med oplysningerne i den eksporterede fil kan du gennemse kapaciteten, varigheden og en hvilken som helst fejlmeddelelse, der blev registreret for opdateringsforekomsten. 


## <a name="refresh-schedule"></a>Opdater plan

Du kan vælge visningen **Plan** ved at klikke på **Plan** i opdateringsoversigterne. Visningen Plan viser planlægningsoplysninger for ugen opdelt i tidsintervaller på 30 minutter. 

![Skærmbillede, der viser et nærbillede af fanen Tidsplan på siden Opdater tidsplan.](media/refresh-summaries/refresh-summaries-02a.jpg)

Visningen Plan er meget nyttig til at fastslå, om der er nok plads mellem de planlagte opdateringshændelser, hvilket giver alle opdateringerne mulighed for at blive fuldført uden overlap, eller om du har planlagte opdateringshændelser, der tager for lang tid og skaber ressourcekonflikter. Hvis du finder sådanne ressourcekonflikter, bør du tilpasse dine opdateringsplaner for at undgå konflikter eller overlap, så dine planlagte opdateringer kan blive fuldført korrekt. 

![Skærmbillede, der viser fanen Tidsplan på siden Opdater tidsplan.](media/refresh-summaries/refresh-summaries-02.jpg)

Kolonnen *Reserveret opdateringstid (minutter)* er en beregning af gennemsnittet af op til 60 poster for hvert tilknyttet datasæt. Den numeriske værdi for hvert 30-minutters tidsinterval er det samlede antal minutter beregnet for alle planlagte opdateringer, som er planlagt til at starte i tidsintervallet **og** eventuelle planlagte opdateringer, som er angivet til at starte i det *forrige* tidsinterval, men hvis gennemsnitlige varighed løber over i det valgte tidsinterval.

Kolonnen *Opdateringstid til rådighed (minutter)* er en beregning af, hvor mange minutter der er til rådighed til opdatering for hvert tidspunkt fratrukket en eventuel opdatering, som allerede er planlagt til det pågældende tidspunkt. Hvis dit P2-abonnement f.eks. muliggør 12 samtidige opdateringer, har du 12 tidsintervaller af 30 minutters varighed, hvilket vil sige 12 opdateringer x 30 minutter = 360 minutter til rådighed til opdatering for det pågældende tidspunkt. Hvis du har en opdatering på 20 minutter, som allerede er booket til det pågældende tidspunkt, er den *opdateringstid, du har til rådighed (i minutter)* for det pågældende tidspunkt 340 minutter (360 minutter minus de 20 minutter, som allerede er booket = 340 minutter). 

Du kan vælge et tidsinterval og derefter vælge den tilknyttede knap med **detaljer** for at se, hvilke planlagte opdateringshændelser der bidrager til den reserverede opdateringstid, deres ejere, og hvor lang tid det tager at fuldføre dem.

Lad os kigge på et eksempel for at se, hvordan dette fungerer. Følgende dialogboks vises, når vi vælger tidspunktet søndag kl. 20.30 og klikker på **detaljer**.

![Skærmbillede, der viser detaljer om opdateringer for et bestemt tidspunkt.](media/refresh-summaries/refresh-summaries-04.jpg)

Der er tre planlagte opdateringshændelser i dette tidsinterval. 

De planlagte opdateringer 1 og 3 er begge planlagt til kl. 20.30, hvilket vi kan se ved at kigge på værdien i kolonnen **Planlagt tidspunkt**. Deres gennemsnitlige varighed er henholdsvis 4:39 og 6 sekunder (0:06). Alt er godt der.

Den planlagte opdatering 2 er dog planlagt til kl. 20.00, men fordi den i gennemsnit tager mere end 48 minutter at fuldføre (se kolonnen **Gennemsnitlig varighed**) løber denne opdateringshændelse over i det næste 30-minutters tidsinterval. 

Det er ikke godt. I dette tilfælde skal administratoren kontakte ejerne af denne planlagte opdatering og foreslå, at de finder et andet tidsinterval for den planlagte opdatering eller ændrer tidspunktet for de andre opdateringer, så der ikke er noget overlap, eller at de finder en anden løsning for at forhindre sådan et overlap. 


## <a name="next-steps"></a>Næste trin

- [Opdatering af data i Power BI](refresh-data.md)  
- [Power BI Gateway – Personal](service-gateway-personal-mode.md)  
- [Datagateway i det lokale miljø (personlig tilstand)](service-gateway-onprem.md)  
- [Fejlfinding af datagatewayen i det lokale miljø](service-gateway-onprem-tshoot.md)  
- [Fejlfinding af Power BI Gateway – Personlig](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)