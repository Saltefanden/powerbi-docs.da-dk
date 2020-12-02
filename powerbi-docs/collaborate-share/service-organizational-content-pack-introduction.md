---
title: Introduktion til organisationsindholdspakker i Power BI
description: Læs om at pakke dine dashboards, rapporter, Excel-projektmapper og datasæt som organisationsindholdspakker, som du kan dele med dine kollegaer.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 10/23/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bd7fdea827d0fbaf4c56f373ea028a8fffdc3123
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411695"
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Introduktion til organisationsindholdspakker i Power BI
> [!NOTE]
> Du kan ikke oprette organisationsindholdspakker eller installere dem i de nye arbejdsområdeoplevelser. Nu er det et godt tidspunkt at opgradere dine indholdspakker til apps, hvis du ikke er startet endnu. Få [mere at vide om den nye arbejdsområdeoplevelse](service-create-the-new-workspaces.md).
> 

Distribuerer du jævnligt rapporter via mail til dit team? Prøv dette i stedet: Lav en pakke med dine dashboards, rapporter, Excel-projektmapper og datasæt, og publicer dem for dit team som en *organisationsindholdspakke*. Indholdspakker, du opretter, er nemme for dit team at finde &#151; de findes alle sammen i AppSource. Da de er en del af Power BI, udnytter de alle funktionerne i Power BI, herunder interaktiv udforskning af data, nye visuals, spørgsmål og svar, integration med andre datakilder, opdatering af data med mere.

![Skærmbillede af et dashboard, der viser organisationsindholdspakker.](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

Oprettelse af indholdspakker adskiller sig fra deling af dashboards eller samarbejde om dem i et arbejdsområde. Læs [Hvordan kan jeg samarbejde på og dele dashboards og rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md) for at finde det bedste valg til din situation. 

I AppSource kan du gennemse eller søge efter indholdspakker, der er publiceret til hele organisationen, til distribution eller sikkerhedsgrupper og til [Microsoft 365-grupper, du er medlem af](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9). Hvis du ikke er medlem af en bestemt gruppe, kan du ikke se indholdspakker, som er delt med denne gruppe. Alle medlemmer af gruppen har samme skrivebeskyttede adgang til indholdspakkens data, rapporter, projektmapper og dashboards (medmindre det er en SSAS-datakilde (SQL Server Analysis Services), hvorved dine rettigheder nedarves sammen med datakilden).

Disse dashboards, rapporter og Excel-projektmapper er skrivebeskyttede, men du kan kopiere og bruge de dashboards og rapporter som udgangspunkt for at oprette din egen personligt tilpassede version af indholdspakken.

> [!NOTE]
> Organisationsindholdspakker er kun tilgængelige, når du og dine kollegaer har [Power BI Pro-licenser](../fundamentals/service-features-license-type.md).
> 
> 

## <a name="what-is-appsource"></a>Hvad er *AppSource*?
Publicering af en organisationsindholdspakke føjer den til AppSource.  Dette centraliserede lager gør det nemt for medlemmer at gennemse og fremsøge dashboards, rapporter og datasæt, der er publiceret til dem.  

* Hvis du vil have vist AppSource, skal du vælge **Hent data** > **Min organisation** > **Hent**.

## <a name="the-life-cycle-of-an-organizational-content-pack"></a>Livscyklus for en organisationsindholdspakke
Alle Power BI Pro-brugere kan oprette, publicere og få adgang til organisationsindholdspakkerne. Kun vedkommende, der har oprettet indholdspakken, kan redigere projektmappen og datasættet, planlægge opdatering og slette den.

Livscyklus ser noget nær således ud:

1. I Power BI Pro opretter Nate en indholdspakke og publicerer den til distributionsgruppen Marketing. Indstillingerne for opdatering nedarves i datasættet og kan kun ændres af Nate.
   
   > [!NOTE]
   > Hvis Nate opretter indholdspakken inde fra et [Power BI-arbejdsområde](service-create-distribute-apps.md), som han hører til, så kan andre i Power BI-arbejdsområdet overtage ejerskabet, også selvom Nate forlader arbejdsområdet.
   > 
   > 
2. Nate sender mails til distributionsgruppen, hvor han fortæller dem om den nye indholdspakke.
3. I Power BI Pro søger Jane, som er medlem af distributionsgruppen Marketing, efter og opretter forbindelse til en indholdspakke i AppSource. Jane har nu en skrivebeskyttet kopi. Jane ved, at den er skrivebeskyttet, da der i navigationsruden er et delingsikon til venstre for navnet på dashboardet og rapporten. Og når Jane vælger dashboardet, vises der et låseikon, som fortæller Jane, at hun ser på et dashboard for en indholdspakke. 
4. Måske ønsker Jane at tilpasse det. Jane har nu sin egen kopi af dashboardet og rapporterne. Janes arbejde påvirker ikke kilden, den oprindelige indholdspakke eller andre medlemmer af distributionsgruppen. De arbejder nu på hver sin kopi af dashboardet og rapporten.
5. Nate foretager opdateringer af dashboardet, og når det er klar, publicerer han en ny version af indholdspakken.
   
   * Julio, som også er medlem af distributionsgruppen, har ikke tilpasset den oprindelige indholdspakke. De nye ændringer anvendes automatisk på Julios version af indholdspakken.  
   * Jane tilpassede indholdspakken. Jane modtager derefter en meddelelse om, at der er en ny version.  Jane kan gå til AppSource og hente den opdaterede indholdspakke uden at miste sin personligt tilpassede version. Jane har nu to versioner: den personligt tilpassede version og den opdaterede indholdspakke.
6. Nu ændrer Nate sikkerhedsindstillingerne. Julio og Jane har ikke længere adgang til indholdet. Det kan også være, at de bliver fjernet fra distributionsgruppen Marketing.
   
   * Julio tilpassede ikke den oprindelige indholdspakke, så indholdet fjernes automatisk. 
   * Jane tilpassede indholdspakken. Næste gang, Jane åbner dashboardet, er alle felterne fra den oprindelige indholdspakke forsvundet, men de felter, hun fastgjorde fra andre rapporter (som hun stadig har tilladelse til at bruge), vises stadig. De tilknyttede rapporter og datasættet er ikke længere tilgængelige (og vises ikke i navigationsruden).
7. Eller Nate sletter indholdspakken.
   
   * Julio tilpassede ikke den oprindelige indholdspakke, så indholdet fjernes automatisk. 
   * Jane tilpassede indholdspakken. Næste gang, Jane åbner dashboardet, er alle felter fra den oprindelige indholdspakke forsvundet, men felter, der er fastgjort fra andre rapporter, vises stadig. De tilknyttede rapporter og datasættet er ikke længere tilgængelige (og vises ikke i navigationsruden).

## <a name="data-security"></a>Datasikkerhed
Alle medlemmer af distributionsgruppen har de samme tilladelser til dataene som vedkommende, der har oprettet indholdspakken. Den eneste undtagelse er tabellariske SSAS-datasæt (SQL Server Analysis Services) i det lokale miljø. Fordi rapporter og dashboards opretter direkte forbindelse til SSAS-modellen i det lokale miljø, bruges legitimationsoplysningerne for hvert enkelte medlem af distributionsgruppen til at bestemme, hvilke data de kan få adgang til.

## <a name="next-steps"></a>Næste trin
* [Opret og publicer en organisationsindholdspakke](service-organizational-content-pack-create-and-publish.md)
* [Opret og distribuer en app i Power BI](service-create-distribute-apps.md) 
* [Grundlæggende begreber for designere i Power BI-tjenesten](../fundamentals/service-basic-concepts.md)
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
