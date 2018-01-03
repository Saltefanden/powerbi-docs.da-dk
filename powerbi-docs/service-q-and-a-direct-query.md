---
title: "Brug af Spørgsmål og svar via direkte forbindelser)"
description: "Dokumentationen til brug for forespørgsler på naturlige sprog via Power BI-spørgsmål og svar med direkte forbindelser til Analysis Services-data og datagateway i lokalt miljø."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: mihart
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/28/2017
ms.author: mihart
ms.openlocfilehash: 453a2a9dd4ea5e41d404d3e81cebbff7c35f1b6c
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/23/2017
---
# <a name="enable-qa-for-live-connections"></a>Aktivér Spørgsmål og svar til direkte forbindelser
## <a name="what-is-on-premises-data-gateway--what-is-a-live-connection"></a>Hvad er datagateway i lokalt miljø?  Hvad er en direkte forbindelse?
Datasæt i Power BI kan importeres til Power BI, eller du kan oprette en direkte forbindelse til dem. Datasæt til direkte forbindelser bliver ofte kaldt "on-premises (i det lokale miljø)". De direkte forbindelser administreres ved hjælp af en [gateway](service-gateway-onprem.md), og data og forespørgsler sendes frem og tilbage ved hjælp af direkte forespørgsler.

## <a name="qa-for-on-premises-data-gateway-datasets"></a>Spørgsmål og svar til datasæt i datagateway i lokalt miljø
Hvis du vil bruge Spørgsmål og svar med datasæt, får du adgang via en gateway, men du skal aktivere dem først.

Når Power BI er aktiveret, opretter den et indeks for datakilden og uploader et undersæt af disse data til Power BI for at aktivere funktionen for at stille spørgsmål. Det kan tage flere minutter at oprette det første indeks, og Power BI vedligeholder og opdaterer indekset automatisk, når data ændres. Når du bruger Spørgsmål og svar med disse datasæt, fungerer det på samme måde som med data, der er publiceret til Power BI. Det fulde sæt af funktioner, der er tilgængelige i Spørgsmål og svar-oplevelsen, er understøttet i begge tilfælde, herunder brug af datakilden med Cortana.

Når du stiller spørgsmål i Power BI, afgør Spørgsmål og svar, hvad der er den bedste visuelle gengivelse for konstruktions- eller rapporteringsark, der skal bruges til at svare på dit spørgsmål ved hjælp af et indeks på datasættet. Når Spørgsmål og svar har fastlagt det bedst mulige svar, bruger Spørgsmål og svar DirectQuery til at hente data direkte fra datakilden via gateway'en for at udfylde diagrammer og grafer. Dette sikrer, at Power BI-spørgsmål og svar altid viser de seneste data direkte fra den underliggende datakilde.

Da Power BI-spørgsmål og svar bruger værdierne for tekst og skema fra din datakilde til at bestemme, hvordan der skal forespørges om den underliggende model for at få svar, afhænger søgninger efter specifikke nye eller slettede tekstværdier (f.eks anmode om en kundenavn, der er knyttet til en post med nytilføjet tekst), af, at indekset er opdateret med de nyeste værdier. Power BI opdaterer automatisk tekst- og skemaindekset i et 60-minuttersintervaller, hvor der kan ske ændringer.

Her finder du flere oplysninger:

* Hvad er [datagateway i lokalt miljø](service-gateway-onprem.md)?
* [Introduktion til Power BI-spørgsmål og svar](service-q-and-a.md)

## <a name="enable-qa"></a>Aktivering af Spørgsmål og svar
Når du har konfigureret datagateway'en, kan du oprette forbindelse til dine data fra Power BI.  Opret et dashboard ved hjælp af dataene i det lokale miljø, eller overfør en .pbix-fil, der bruger lokale data.  Du har måske også allerede data i lokalt miljø i dashboards, rapporter og datasæt, der er blevet delt med dig.

1. I øverste højre hjørne af Power BI skal du vælge tandhjulsikonet ![](media/service-q-and-a-direct-query/power-bi-cog.png) og vælge **Indstillinger**.
   
   ![](media/service-q-and-a-direct-query/powerbi-settings.png)
2. Vælg **Datasæt**, og vælg det datasæt, der aktiverer Spørgsmål og svar.
   
   ![](media/service-q-and-a-direct-query/power-bi-q-and-a-settings.png)
3. Udvid **Spørgsmål og svar og Cortana**, vælg afkrydsningsfeltet for **Aktivér Spørgsmål og svar for dette datasæt**, og vælg **Anvend**.
   
    ![](media/service-q-and-a-direct-query/power-bi-q-and-a-directquery.png)

## <a name="what-data-is-cached-and-how-is-privacy-protected"></a>Hvilke data cachelagres, og hvordan beskyttes privatliv?
Når du aktiverer Spørgsmål og svar for dataene i det lokale miljø, cachelagres et undersæt af dine data i tjenesten. Det sker for at sikre, at Spørgsmål og svar fungerer sammen med en rimelig ydeevne. Vi udelukker værdier med flere end 24 tegn fra cachelagring. Cachen slettes inden for et par timer, når du deaktiverer Spørgsmål og svar ved at fjerne markeringen **Aktivér Spørgsmål og svar for dette datasæt**, eller når du sletter dit datasæt.

## <a name="considerations-and-troubleshooting"></a>Emner og fejlfinding
Under Visningsfasen til denne funktion er der flere begrænsninger:

* Til at begynde med er funktionen kun tilgængelig for SQL Server 2016 Analysis Services Tabular-datakilder. Funktionen er optimeret til at arbejde med data i tabelformat. Nogle funktioner er tilgængelige for flerdimensionelle datakilder, men den fulde oplevelse med Spørgsmål og svar understøttes endnu ikke for flerdimensionelle. Der udrulles flere datakilder, som understøttes af den lokale datagateway, under den offentlige prøveversion.
* Fuld understøttelse af sikkerhed på rækkeniveau, der er defineret i SQL Server Analysis Services, er ikke tilgængelig til at begynde med i den offentlige prøveversion. Når der stilles spørgsmål i Spørgsmål og svar, kan den automatiske udfyldning af spørgsmål under skrivningen vise strengværdier, som brugerne ikke har adgang til. Dog overholdes den RLS, der er defineret i modellen, for visning af rapporter og diagrammer, så ingen underliggende numeriske data kan fremvises. Indstillinger til at styre denne funktionsmåde vil blive udgivet i kommende opdateringer.
* Direkte forbindelser understøttes kun med datagateway i lokalt miljø. Denne funktion kan derfor ikke bruges med den personlige gateway.

## <a name="next-steps"></a>Næste trin
[Datagateway i lokalt miljø](service-gateway-onprem.md)  
[Administrer din datakilde – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Hurtig indsigt i Power BI](service-insights.md)  
[Optimer dine data til Power BI Quick Insights](service-insights-optimize.md)  
[Power BI – Grundlæggende begreber](service-basic-concepts.md)  
[Dashboards i Power BI](service-dashboards.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](http://community.powerbi.com/)
