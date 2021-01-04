---
title: Visning af flere eller færre detaljer i en visualisering
description: I denne artikel gennemgår vi, hvordan man foretager detailudledning i en visualisering i Microsoft Power BI-tjenesten.
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/21/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 17fe24957dbcccd7038ea34566a8db8f5684cb18
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721518"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Analysetilstand i en visualisering i Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]


I denne artikel gennemgår vi, hvordan man foretager detailudledning i en visualisering i Microsoft Power BI-tjenesten. Når du får vist flere eller færre detaljer for dine datapunkter, kan du udforske detaljerede oplysninger om dine data. 

## <a name="drill-requires-a-hierarchy"></a>Analysetilstand kræver et hierarki

Når et visuelt element har et hierarki, kan du foretage detailudledning for at finde flere detaljer. Du har f.eks. en visualisering, der kigger på optælling af olympiske medaljer ud fra et hierarki, der består af sport, disciplin og begivenhed. Som standard viser visualiseringen medaljeoptælling ud fra sportsgren – gymnastik, skiløb, vandsport osv. Men eftersom den har et hierarki, vises et stadigt mere detaljeret billede, når der vælges visuelle elementer (f.eks. et liggende søjlediagram, linjediagram eller boblediagram). Vælg elementet **vandsport** for at få vist data for svømning, udspring og vandpolo.  Vælg elementet **udspring** for at få vist detaljer for vippe, platform og discipliner med synkronudspring.

Datoer er en unik type i hierarkiet.  Rapport *designere* tilføjer ofte datohierarkier i visualiseringer. Et almindeligt datohierarki er et, der indeholder år, kvartal, måned og dag. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>Find ud af, hvilke visualiseringer der kan analyseres
Ved du, hvilke Power BI-visualiseringer der indeholder et hierarki? Peg på en visualisering. Hvis du får vist en kombination af disse analysekontrolelementer øverst, har visualiseringen et hierarki.

![Skærmbillede af analyseikonerne.](./media/end-user-drill/power-bi-drill-icons.png)  


## <a name="learn-how-to-drill-down-and-up"></a>Få mere at vide om, hvordan du zoomer ind på og ud fra detaljeniveauet

I dette eksempel bruger vi en træstruktur, der har et hierarki, der består af område, by, postnummer og butiksnavn. Træstrukturen viser de samlede enheder, der er solgt dette år efter område, før du foretager detailudledning. Område er det øverste niveau i hierarkiet.

![Skærmbillede af træstrukturen og de tilhørende filtre.](./media/end-user-drill/power-bi-treemap.png)  


### <a name="two-ways-to-access-the-drill-features"></a>To måder at få adgang til analysefunktionerne på

Du har to muligheder for at få adgang til funktionerne til at zoome ind og ud fra detaljeniveauet og til at udvide de visualiseringer, som har hierarkier. Prøv dem begge to, og vælg den, du synes bedst om.

- Den første måde: Peg på en visualisering for at få vist og bruge ikonerne. Aktivér først detailudledning ved at vælge pil ned. På den grå baggrund kan du se, at detailudledning er aktiv.   

    ![Skærmbillede af eksemplet med musen.](./media/end-user-drill/power-bi-drill-hover.png)

- Den anden måde: Højreklik på en visualisering for at få vist og bruge menuen.

    ![Skærmbillede af eksemplet med højreklik.](./media/end-user-drill/power-bi-drill-action-menu.png)



## <a name="drill-pathways"></a>Stier for analyse

### <a name="drill-down-all-fields-at-once"></a>Brug detailudledning på alle felter på en gang
![Ikonet for detailudledning](./media/end-user-drill/power-bi-drill-icon3.png)

Der er flere måder, hvorpå du kan få vist flere detaljer i din visualisering. Når du vælger dobbeltpilen ![ikonet for at få vist alle niveauer på én gang](./media/end-user-drill/power-bi-drill-icon3.png)åbner ikonet for detailudledning det næste niveau i hierarkiet. Hvis du kigger på niveauet **Område** for Kentucky og Tennessee, kan du foretage detailudledning for at gå til bynavnet for begge stater, derefter postnummerniveau for begge stater og til sidst niveauet for butiksnavn for begge stater. Hvert trin på stien viser nye oplysninger.

![Diagram, der viser sti til detailudledning](./media/end-user-drill/power-bi-drill-path.png)

Vælg ikonet for færre detaljer ![Ikon for færre detaljer,](./media/end-user-drill/power-bi-drill-icon5.png) indtil du kommer tilbage til Samlet antal enheder dette år efter område.

### <a name="expand-all-fields-at-once"></a>Udvid alle felter på én gang
![Ikonet Udvid](./media/end-user-drill/power-bi-drill-icon6.png)

**Udvid** føjer et ekstra hierarkiniveau til den aktuelle visning. Så hvis du kigger på niveauet **Område**, kan du udvide alle aktuelle blade i træet på samme tid.  Din første detailudledning tilføjer bydata for både **KY** og **TN**. Ved næste detailudledning tilføjes postnummerdata for både **KY** og **TN**, og bydata bevares også. Hvert trin på stien viser de samme oplysninger og tilføjer et niveau med nye oplysninger.

![Diagram, der viser sti til at udvide](./media/end-user-drill/power-bi-expand-path.png)


### <a name="drill-down-one-field-at-a-time"></a>Detailudledning på ét felt ad gangen


1. Vælg ikonet for detailudledning for at aktivere funktionen ![Skærmbillede af ikonet for detailudledning til/fra, der er aktiveret.](./media/end-user-drill/power-bi-drill-icon2.png).

    Nu kan du bruge detailudledning for **ét felt ad gangen** ved at vælge et visuelt element. Eksempler på visuelle elementer er: liggende søjlediagram, boblediagram og blad.

    ![Skærmbillede af visualisering med en pil, der peger på ikonet for detailudledning til/fra, der er aktiveret.](media/end-user-drill/power-bi-select-drill-icon.png)

    Hvis du ikke aktiverer detailudledning, finder der ingen detailudledning sted, når du vælger et visuelt element (f.eks. et søjlediagram, boblediagram eller blad). I stedet for krydsfiltreres de andre diagrammer på rapportsiden.

1. Vælg bladet for **TN**. Din træstruktur viser nu alle de byer i Tennessee, hvor der er en butik.

    ![Skærmbillede af træstrukturen, der kun viser data for TN.](media/end-user-drill/power-bi-drill-down-first.png)

1. På nuværende tidspunkt kan du:

    1. Fortsætte med at detailudlede for Tennessee.

    1. Detailudlede for en bestemt by i Tennessee.

    1. Udvid i stedet.

    Lad os fortsætte med detailudledning på ét felt ad gangen.  Vælg **Knoxville, TN**. Din træstruktur viser postnummeret for din butik i Knoxville.

    ![Skærmbillede af træstrukturen, der viser postnummeret 37919.](media/end-user-drill/power-bi-drill-twice.png)

    Bemærk, at titlen ændres, når du foretager detailudledning eller fjerner detaljerne igen.

    Og foretag detailudledning på mere end ét felt. Vælg postnummeret **37919**, og foretag detailudledning til butiksnavn. 

    ![Skærmbillede af træstrukturen, der viser Knoxville Lindseys.](media/end-user-drill/power-bi-drill-last.png)    

    Hvis du vil bruge disse data, er det muligvis ikke interessant at foretage detailudledning af alle niveauer på en gang. Lad os i stedet prøve at udvide.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Udvid alle, og udvid ét felt ad gangen

Det giver ikke meget mening at have en træstruktur, der kun viser et postnummer eller et butiksnavn.  Lad os *udvide* ét niveau ned i hierarkiet.  

1. Først skal du fjerne detaljerne for postnummerniveauet igen.     
1. Med træstrukturen aktiveret kan du vælge ikonet *udvid ned*![skærmbillede af ikonet udvid ned](./media/end-user-drill/power-bi-drill-icon6.png). Nu vises der to niveauer af hierarkiet i træstrukturen: postnummer og butiksnavn.

    ![Skærmbillede af træstrukturen, der viser postnummer og butiksnavn](./media/end-user-drill/power-bi-expand.png)

1. Hvis du vil have vist alle fire hierarkiniveauer for Tennessee, skal du vælge pilen for at gå et niveau op, indtil du kommer til det andet niveau, **Samlet antal enheder i år efter område og by**.

    ![Skærmbillede af træstrukturen, der viser alle data for TN.](media/end-user-drill/power-bi-expand-second.png)

1. Sørg for, at detailudledning stadig er slået til, ![skærmbillede af detailudledning til/fra-ikonet, der er aktiveret.](./media/end-user-drill/power-bi-drill-icon2.png) og vælg ikonet *udvid ned*![skærmbillede af ikonet for udvid ned.](./media/end-user-drill/power-bi-drill-icon6.png). Din træstruktur viser nu det samme antal blade (felter), men hvert blad har flere detaljer. I stedet for kun at vise by og stat vises postnummer også.

    ![Skærmbillede af visualiseringen, der viser by, stat og postnummer.](./media/end-user-drill/power-bi-expand-third.png)

1. Vælg ikonet *udvid ned* en gang til for at få vist alle fire hierarkiniveauer med detaljer for Tennessee i træstrukturen. Peg på et blad for at få vist flere detaljer.

    ![Skærmbillede af træstrukturen, der viser et værktøjstip med bladspecifikke data.](./media/end-user-drill/power-bi-expand-final.png)

## <a name="show-the-data-as-you-drill"></a>Vis dataene under detailudledning
Brug **Vis som en tabel** for at få et overblik over, hvad der sker bag kulisserne. Hver gang du foretager detailudledning eller udvider, viser **Vis som en tabel** de data, der bruges til at bygge visualiseringen. Det kan hjælpe dig med at forstå, hvordan hierarkier, analyser og udvidelser fungerer sammen til at bygge visuelle elementer. 

Vælg **Flere handlinger** (...) i øverste højre hjørne, og vælg **Vis som en tabel**. 

![Skærmbillede af ellipsemenuen.](./media/end-user-drill/power-bi-more-actions.png)

Power BI åbner træstrukturen, så den udfylder lærredet. De data, der udgør træstrukturen, vises under visualiseringen. 

![Skærmbillede af træstruktur med datatabellen vises nedenfor.](./media/end-user-drill/power-bi-show-table.png)

Fortsæt med at foretage detailudledning kun med visualiseringen på lærredet. Se, hvordan dataene i tabellen ændres, så de afspejler de data, der bruges til at oprette træstrukturen. I følgende tabel vises resultaterne af detailudledning af alle felter på én gang fra område til butiksnavn. Den første tabel repræsenterer hierarkiets øverste niveau, hvor træstrukturen viser to blade, én for **KY** og én for **TN**. De næste tre tabeller viser træstrukturens data, når du foretager detailudledning på alle niveauer på én gang – fra område til by til postnummer til butiksnavn.


![Skærmbillede af visning af data for alle fire niveauer af detailudledningen.](./media/end-user-drill/power-bi-show-data.png)

Bemærk, at totalerne er de samme for **By**, **Postnummer** og **Navn**. Du vil ikke altid få matchende totaler.  Men for disse data er der kun én butik i hvert postnummer og i hver by.  



## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger
- Detailudledning filtrerer ikke andre visualiseringer i en rapport som standard. Rapportdesigneren kan dog ændre denne standardfunktionsmåde. Når du foretager detailudledning, kan du se, om der filtreres eller fremhæves på tværs af de andre visualiseringer på siden.

- Hvis du får vist en rapport, der er blevet delt med dig, skal du have en Power BI Pro- eller Premium-licens, for at rapporten kan gemmes i Power BI Premium-kapacitet. [Hvilken licens har jeg?](end-user-license.md)


## <a name="next-steps"></a>Næste trin

[Visualiseringer i Power BI-rapporter](../visuals/power-bi-report-visualizations.md)

[Power BI-rapporter](end-user-reports.md)

[Power BI – Grundlæggende begreber](end-user-basic-concepts.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
