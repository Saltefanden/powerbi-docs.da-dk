---
title: Eksportér rapporter til PDF
description: Få mere at vide om, hvordan du eksporterer en Power BI-rapport til PDF.
author: mihart
ms.author: mihart
ms.custom: ''
ms.reviewer: cmfinlan
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 01/11/2021
LocalizationGroup: Share your work
ms.openlocfilehash: d9d4677e8f0fe415f7a0169fb48ede7187c3fcf5
ms.sourcegitcommit: e8c3f327ac0fc73c118874a24d2601733f8f9e45
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718548"
---
# <a name="export-reports-from-power-bi-to-pdf"></a>Eksportér rapporter fra Power BI til PDF

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]


Med Power BI kan du publicere din rapport i PDF-format og nemt oprette et dokument ud fra din Power BI-rapport. Når du eksporterer til PDF, bliver hver side i Power BI-rapporten en individuel side i PDF-dokumentet.

## <a name="export-your-power-bi-report-to-pdf"></a>Eksportér din Power BI-rapport til PDF
Vælg en rapport for at vise den på lærredet i Power BI-tjenesten. Du kan også vælge en rapport fra din **startside**, dine **programmer** eller en hvilken som helst objektbeholder i navigationsruden.

1. Vælg **Eksportér** > **PDF** på menulinjen.

    ![Vælg Eksportér på menulinjen](media/end-user-pdf/power-bi-export-pdfs.png)

    Der vises et pop op-vindue, hvor du har mulighed for at vælge **Aktuelle værdier** eller **Standardværdier**. Med **Aktuelle værdier** eksporteres rapporten i den aktuelle tilstand, hvilket omfatter de aktive ændringer, du har foretaget af udsnits- og filterværdier. De fleste brugere vælger denne indstilling. Alternativt kan du vælge **Standardværdier**, hvor rapporten eksporteres i sin oprindelige tilstand, som *designeren* har delt den, og hvor ændringer, du har foretaget af den oprindelige tilstand, ikke afspejles.
    
    Derudover er der et afkrydsningsfelt, hvor du kan markere, om du vil eksportere skjulte faner i en rapport. Markér afkrydsningsfeltet, hvis du kun vil eksportere de rapportfaner, der er synlige for dig i browseren. Hvis du foretrækker at inkludere alle skjulte faner i din eksport, kan du undlade at markere afkrydsningsfeltet. Hvis afkrydsningsfeltet er nedtonet, er der ingen skjulte faner i rapporten. Når du har foretaget dine valg, skal du vælge **Eksportér** for at fortsætte.
    
    Du kan også vælge kun at eksportere den aktuelle side, du får vist i en rapport, ved at markere indstillingen **Eksportér kun den aktuelle side**.  Indstillingen er ikke markeret som standard, så alle sider i rapporten eksporteres som udgangspunkt.
    
    Der vises en statuslinje i øverste højre hjørne. Eksporten kan tage et par minutter. Du kan fortsætte med at arbejde i Power BI, mens rapporten eksporteres.

    ![Meddelelse om eksportstatus](media/end-user-pdf/power-bi-export-progress.png)

    Når eksportprocessen er fuldført i Power BI-tjenesten, ændres meddelelsesbanneret for at give dig besked.

2. Derefter finder du din fil der, hvor din browser viser downloadede filer. På det følgende billede vises det som et downloadbanner i bunden af browservinduet.

    ![Placering af den downloadede fil](media/end-user-pdf/power-bi-export-done.png)

Så nemt er det. Du kan downloade filen og åbne den med en hvilken som helst PDF-fremviser, f.eks. den der er tilgængelig i Microsoft Edge.


## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser
Der er nogle få overvejelser og begrænsninger, du skal huske på, når du arbejder med funktionen **Eksportér til PDF**.

* PDF-filen indeholder de data og visualiseringer, der er synlige på dit Power BI-lærred. Hvis visual'et indeholder rullepaneler, medtages visual'et i PDF-filen i standardtilstanden, hvor der ikke er rullet.  
* R-visualiseringer og Python understøttes ikke i øjeblikket. Disse visualiseringer er tomme i PDF'en, og der vises en fejlmeddelelse. 
* Power BI-visuals, der er blevet certificeret, understøttes. I [Få en Power BI-visual certificeret](../developer/visuals/power-bi-custom-visuals-certified.md) kan du finde flere oplysninger om certificerede Power BI-visuals, herunder hvordan du får en Power BI-visual certificeret. Power BI-visuals, der ikke er blevet certificeret, understøttes ikke. De vises med en fejlmeddelelse i PDF'en.
* ESRI-visualiseringen understøttes ikke.
* Power BI rapporter med mere end 50 rapportsider kan ikke eksporteres i øjeblikket. Sideinddelte rapporter har ikke denne begrænsning. Se [udskrive en sideinddelt rapport](end-user-paginated-report.md#interact-with-a-paginated-report) for at få flere oplysninger. 
* Rapporter, der er større end 500 MB, kan ikke eksporteres i øjeblikket. 
* Processen med at eksportere rapporten til PDF kan tage nogle minutter at fuldføre, så vær tålmodig. Faktorer, som kan påvirke den tid, det kræver, omfatter rapportens struktur og den aktuelle belastning på Power BI-tjenesten.
* Hvis menupunktet **Eksportér til PDF** ikke er tilgængeligt i Power BI-tjenesten, er det sandsynligvis fordi, din Power BI-administrator har deaktiveret funktionen. Kontakt administratoren for at få detaljer.
* Baggrundsbilleder beskæres med diagrammets omgivende område. Det anbefales, at du fjerner baggrundsbilleder, før du eksporterer til PDF.
* Rapporter, der ejes af en bruger uden for dit Power BI-lejerdomæne, f.eks. en rapport, der ejes af nogen uden for din organisation, og som er delt med dig, kan ikke publiceres til PDF.
* Hvis du deler et dashboard med en person uden for din organisation og dermed en bruger, der ikke er i din Power BI-lejer, kan denne bruger ikke eksportere det delte dashboards tilknyttede rapporter til PDF. Hvis du f.eks. er aaron@contoso.com, kan du dele med cassie@northwinds.com. Men cassie@northwinds.com kan ikke eksportere de tilknyttede rapporter til PDF.
* Når du eksporterer rapporter til PDF, som indeholder et baggrundsbillede, kan du muligvis se et forvrænget billede i eksporten, hvis du bruger indstillingen **Normal** eller **Udfyld** til **sidens baggrund**. Du får de bedste resultater ved at bruge indstillingen **Udfyld** for at undgå problemer med dit eksporterede dokument.
* I Power BI-tjenesten anvendes din Power BI-sprogindstilling som sprog i forbindelse med PDF-eksporten. Hvis du vil se eller angive dine sprogindstillinger, skal du vælge tandhjulsikonet ![Tandhjulsikon](media/end-user-powerpoint/power-bi-settings-icon.png) > **Indstillinger** > **Generelt** > **Sprog**.
* Filtre for URL-dresser respekteres ikke i øjeblikket, når du vælger **Aktuelle værdier** til din eksport.
* Der kan være problemer med rapporter med usædvanlige brugerdefinerede sidestørrelser i eksportscenarier. For at få de bedste resultater bør du overveje at skifte til en standardsidestørrelse for din rapport.
* Når du eksporterer til PDF, udskiftes brugerdefinerede skrifttyper med standardskrifttyper i rapporter, hvor der bruges temaer med brugerdefinerede skrifttyper.
* Mens vi forsøger at tilbyde en ensartet oplevelse, kan vi ikke garantere, at den eksporterede PDF-fil fra Power BI-tjenesten altid vil svare til den eksporterede PDF-fil fra en lokal Power BI Desktop-fil.
* Når du eksporterer til PDF, kan vi ikke garantere pixel-perfekt nøjagtig gengivelse af PBIX-rapporter.

## <a name="next-steps"></a>De næste trin
[Udskriv en rapport](end-user-print.md)
