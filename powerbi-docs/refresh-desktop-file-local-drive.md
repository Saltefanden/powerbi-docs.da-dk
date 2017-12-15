---
title: "Opdater et datasæt, der er oprettet via en Power BI Desktop-fil – lokalt"
description: "Opdater et datasæt, der er oprettet via en Power BI Desktop-fil på et lokalt drev"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: f314e475d7a08ffe252144add1a887086a32a24d
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/06/2017
---
# <a name="refresh-a-dataset-created-from-a-power-bi-desktop-file-on-a-local-drive"></a>Opdater et datasæt, der er oprettet via en Power BI Desktop-fil på et lokalt drev
## <a name="whats-supported"></a>Hvad understøttes?
I Power BI understøttes "Opdater nu" og "Planlæg opdatering" for datasæt, der er oprettet via Power BI Desktop-filer, som er importeret fra et lokalt drev, hvor "Hent data"/Forespørgselseditor bruges til at oprette forbindelse til og indlæse data fra en af følgende datakilder:

### <a name="power-bi-gateway---personal"></a>Power BI Gateway – Personlig
* Alle online-datakilder, der vises i "Hent data" og Forespørgselseditor i Power BI Desktop.
* Alle datakilder i det lokale miljø, der vises i "Hent data" og Forespørgselseditor i Power BI Desktop, undtagen Hadoop-fil (HDFS) og Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

> [!NOTE]
> En gateway skal være installeret og køres, før Power BI kan oprette forbindelse til datakilder i det lokale miljø, og datasættet opdateres.
> 
> 

Du kan udføre en manuel engangsopdatering direkte i Power BI Desktop ved at vælge Opdater på båndet Hjem. Når du vælger Opdater her, opdateres dataene i *filens* model med opdaterede data fra den oprindelige datakilde. Denne type opdatering, udelukkende fra selve Power BI Desktop-programmet, er forskellig fra den manuelle eller planlagte opdatering Power BI, og det er vigtigt at forstå forskellen.

![](media/refresh-desktop-file-local-drive/pbix-refresh.png)

Når du importere din Power BI Desktop-fil fra et lokalt drev, indlæses data og andre oplysninger om modellen i et datasæt i Power BI-tjenesten. Du vil opdatere dataene i datasættet i Power BI-tjenesten, ikke Power BI Desktop, da det er det, dine rapporter i Power BI-tjenesten er baseret på. Da datakilderne er eksterne, kan du manuelt opdatere datasættet vha. **Opdater nu**, eller du kan oprette en tidsplan for opdatering vha. **Planlæg opdatering**.

Når du opdaterer datasættet, oprettes der ikke forbindelse til filen på det lokale drev via Power BI for at forespørge om opdaterede data. Oplysningerne i datasættet bruges til at oprette forbindelse direkte til datakilderne for at forespørge om opdaterede data, som derefter indlæses i datasættet.

> [!NOTE]
> Opdaterede data i datasættet synkroniseres ikke med filen på det lokale drev igen.
> 
> 

## <a name="how-do-i-schedule-refresh"></a>Hvordan kan jeg planlægge en opdatering?
Når du konfigurerer en tidsplan for opdatering, oprettes der direkte forbindelse til datakilderne i Power BI vha. forbindelsesoplysningerne og legitimationsoplysningerne i datasættet for at forespørge om opdaterede data. Derefter indlæses de opdaterede data i datasættet. Alle visualiseringer i rapporter og dashboards, der er baseret på dette datasæt i Power BI-tjenesten, opdateres også.

Du kan finde oplysninger om, hvordan du konfigurerer en tidsplan for opdatering, under [Konfigurer tidsplan for opdatering](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Når det går galt
Når tingene går galt, skyldes det normalt, at Power BI ikke kan logge på datakilder, eller at gatewayen er offline, når datasættet opretter forbindelse til en datakilde i det lokale miljø. Kontrollér, at Power BI kan logge på datakilder. Hvis en adgangskode, du bruger til at logge på en datakilde med, ændres, eller Power BI logges af datakilden, skal du prøve at logge på datakilderne igen vha. legitimationsoplysningerne for datakilden.

Sørg for, at indstillingen **Send mig en mail med meddelelse om opdateringsfejl** er markeret. Du vil have det at vide med det samme, hvis en planlagt opdatering mislykkes.

## <a name="troubleshooting"></a>Fejlfinding
Nogle gange går opdateringen af data muligvis ikke som forventet. Dette er normalt et problem i forbindelse med en gateway. Se i artiklerne om fejlfinding af gatewayen for at få oplysninger om værktøjer og kendte problemer.

[Fejlfinding af datagateway i det lokale miljø](service-gateway-onprem-tshoot.md)

[Fejlfinding af Power BI Gateway – Personlig](service-admin-troubleshooting-power-bi-personal-gateway.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](http://community.powerbi.com/)
