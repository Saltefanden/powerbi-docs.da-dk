---
title: Opret forbindelse til LinkedIn Sales Navigator i Power BI Desktop
description: Opret nemt forbindelse til og brug data fra LinkedIn i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: 6121e2050fdb4d9c94732508dc96c8719598fec3
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926999"
---
# <a name="connect-to-linkedin-sales-navigator-in-power-bi-desktop"></a>Opret forbindelse til LinkedIn Sales Navigator i Power BI Desktop

I **Power BI Desktop** kan du oprette forbindelse til **LinkedIn Sales Navigator** for nemmere at finde og oprette relationer på samme måde som enhver anden datakilde i Power BI Desktop og oprette færdiglavede rapporter om dine fremskridt.

![Fanen Brug i LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-01.png)


Hvis du vil oprette forbindelse til LinkedIn-data ved hjælp af **LinkedIn Sales Navigator**, skal du have en Sales Navigator Enterprise-plan og enten være administrator eller rapportbruger i Sales Navigator-kontrakten.

Følgende video giver en hurtig rundvisning i og et selvstudium til brugen af **LinkedIn Sales Navigator**-skabelonappen, der beskrives detaljeret [senere i denne artikel](#using-the-linkedin-sales-navigator-template-app). 

> [!VIDEO https://www.youtube.com/embed/ZqhmaiORLw0]

## <a name="connect-to-linkedin-sales-navigator"></a>Opret forbindelse til LinkedIn Sales Navigator

Du opretter forbindelse til **LinkedIn Sales Navigator**-data ved at vælge **Hent data** på båndet **Hjem** i Power BI Desktop. Vælg **Onlinetjenester** i kategorierne til venstre, og rul derefter, indtil du kan se **LinkedIn Sales Navigator (Beta)** .

![Hent data i Power BI Desktop](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-02.png)

Du bliver underrettet om, at du opretter forbindelse til en tredjeparts-connector, der stadig er under udvikling. 

![Advarsel om tredjepart](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-03.png)

Når du vælger **Fortsæt**, bliver du bedt om at angive de ønskede data.

![Bed om de oplysninger der skal angives](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-04.png)


I vinduet **LinkedIn Sales Navigator**, der vises, skal du vælge, hvilke data du vil returnere, enten *Alle kontakter* eller *Valgte kontakter* fra den første rullevælger. Du kan derefter angive start-og slutdatoer for at begrænse de data, der modtages, til et bestemt tidsvindue.

Når du har angivet oplysningerne, opretter Power BI Desktop forbindelse til de data, der er knyttet til din LinkedIn salgs Navigator-kontrakt. Brug den samme mailadresse, som du bruger til at logge på LinkedIn Sales Navigator, via webstedet. 

![Log på LinkedIn](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-05.png)

Når du har oprettet forbindelse, bliver du bedt om at vælge, hvilke data der skal hentes fra din LinkedIn Sales Navigator-kontrakt, i et **Navigator**-vindue.

![Vælg data ved hjælp af Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-09.png)

Du kan oprette alle de rapporter, du vil, med dine LinkedIn Sales Navigator-data. For at gøre tingene nemmere er der også en LinkedIn Sales Navigator-.PBIX-fil, du kan downloade, hvor der allerede er angivet eksempeldata, så du kan blive fortrolig med dataene og rapporterne uden at skulle starte fra bunden.

Du kan downloade PBIX-filen fra følgende sted:
* [PBIX til LinkedIn Sales Navigator](service-template-apps-samples.md)

Ud over filen PBIX har LinkedIn Sales Navigator også en skabelonapp, du også kan downloade og bruge. I det næste afsnit beskrives skabelonappen mere detaljeret.


## <a name="using-the-linkedin-sales-navigator-template-app"></a>Brug af LinkedIn Sales Navigator-skabelonappen

Hvis du vil bruge **LinkedIn Sales Navigator** så nemt som muligt, kan du bruge [skabelonappen](service-template-apps-overview.md), der automatisk opretter en færdiglavet rapport fra dine LinkedIn Sales Navigator-data.

![Skabelonapp til LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-10.png)

Når du downloader appen, kan du vælge, om du vil oprette forbindelse til dine data eller udforske appen med eksempeldata. Du kan altid gå tilbage og oprette forbindelse til dine egne LinkedIn Sales Navigator-data, når du har udforsket eksempeldataene. 

![Opret forbindelse til data for LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-11.png)



Du kan downloade **LinkedIn Sales Navigator**-skabelonappen fra følgende link:
* [LinkedIn Sales Navigator-skabelonapp](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.linkedin_navigator)

Skabelonappen indeholder fire faner, der kan hjælpe dig med at analysere og dele dine oplysninger:

* Brug
* Search
* InMail
* SSI

Under fanen **Brug** kan du se de samlede LinkedIn Sales Navigator-data.

![Under fanen Brug i LinkedIn Sales Navigator kan du se de samlede LinkedIn Sales Navigator-data.](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-12.png)

Under fanen **Søg** kan du få flere detaljer om dine søgeresultater:

![Fanen Søg i LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-13.png)

**InMail** giver indsigt i din brug af InMail, herunder antallet af sendte mails, acceptrater og andre nyttige oplysninger:

![Fanen InMail i LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-14.png)

Under fanen **SSI** kan du få flere detaljer om dit SSI (Social Selling Index):

![Fanen SSI i LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-15.png)

Hvis du vil gå fra eksempeldataene til dine egne data, skal du vælge **Rediger app** i det øverste højre hjørne (blyantsikonet) og derefter vælge **Opret forbindelse til dine data** fra det skærmbillede, der vises.

![Opret forbindelse til dine egne data](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-16.png)

Herfra kan du oprette forbindelse til dine egne data og vælge, hvor mange dages data, der skal indlæses. Du kan indlæse op til 365 dages data. Du skal logge på igen og bruge den samme mailadresse, som du bruger til at logge på LinkedIn Sales Navigator, via webstedet. 

![Log på](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-17.png)

Skabelonappen opdaterer derefter dataene i appen med dine data. Du kan også konfigurere en planlagt opdatering, så dataene i din app er lige så aktuelle, som opdateringshyppigheden angiver. 

Når dataene er opdateret, kan du se, at appen er udfyldt med dine egne data.

## <a name="getting-help"></a>Få hjælp

Hvis du støder på problemer, når du opretter forbindelse til dine data, kan du kontakte support til LinkedIn Sales Navigator på https://www.linkedin.com/help/sales-navigator. 

## <a name="next-steps"></a>De næste trin
Du kan oprette forbindelse til mange forskellige typer data ved hjælp af Power BI Desktop. Hvis du vil have mere at vide om datakilder, kan du se følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Opret forbindelse til Excel-projektmapper i Power BI Desktop](desktop-connect-excel.md)   
* [Angiv data direkte i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
