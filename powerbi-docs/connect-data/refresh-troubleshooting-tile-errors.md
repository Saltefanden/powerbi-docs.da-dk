---
title: Fejlfinding af feltfejl
description: Almindelige fejl, der kan opstå, når et felt forsøger at opdatere i Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 12/06/2018
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f82c6c97b954745e264fe213b5070a9a498de939
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410706"
---
# <a name="troubleshooting-tile-errors"></a>Fejlfinding af feltfejl
Nedenfor er de mest almindelige fejl, der kan opstå med felter, sammen med en forklaring.

> [!NOTE]
> Hvis der opstår en fejl, der ikke er angivet nedenfor, og det medfører problemer for dig, kan du bede om yderligere hjælp på [community-webstedet](https://community.powerbi.com/), eller du kan oprette en [supportbillet](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Fejl
**Der opstod en uventet fejl i Power BI under indlæsning af modellen. Prøv igen senere.**
eller **Datamodellen kunne ikke hentes. Kontakt ejeren af dashboardet for at sikre, at datakilderne og modellen eksisterer og er tilgængelige.**

Vi kunne ikke få adgang til dine data, fordi datakilden ikke var tilgængelig. Dette kan ske, hvis datakilden blev fjernet, omdøbt, flyttet, er offline, eller hvis tilladelserne er blevet ændret. Kontrollér, at kilden stadig er på den placering, vi peger på, og at du stadig har tilladelse til at få adgang til den. Hvis det ikke er problemet, kan kilden muligvis være langsom. Prøv igen på et senere tidspunkt, når belastningen på kilden er mindre. Hvis det er en lokal kilde, kan ejeren af datakilden muligvis give flere oplysninger.

**Du har ikke tilladelse til at få vist dette felt eller åbne projektmappen.**

Kontakt ejeren af dashboardet for at sikre, at datakilderne og modellen findes og er tilgængelige for din konto.

**Power BI-visuals er blevet deaktiveret af din administrator.**

Din Power BI-administrator har deaktiveret brugen af Power BI-visuals for din organisation eller sikkerhedsgruppe.
Du kan ikke bruge Power BI-visuals fra [Microsoft Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) eller importere private visuals fra en fil. Du kan kun bruge de foruddefinerede pakkede sæt af visualiseringer.


**Dataformer skal indeholde mindst én gruppe eller beregning med data som output. Kontakt ejeren af dashboardet.**

Vi har ikke nogen data, der kan vises, fordi forespørgslen er tom. Prøv at føje nogle felter fra feltlisten til det visuelle element og fastgøre det igen.

**Dataene kan ikke vises, da Power BI ikke kan fastslå relationen mellem to eller flere felter.**

Du forsøger at bruge to eller flere felter fra tabeller, der ikke er relateret. Du skal fjerne de ikke-relaterede felter fra det visuelle element og derefter oprette en relation mellem tabellerne. Når du har ændret dette, kan du igen føje felterne til visualiseringen. Det kan gøres i Power BI Desktop eller Power Pivot til Excel. [Få mere at vide](../transform-model/desktop-create-and-manage-relationships.md)

**Grupperne på den primære og den sekundære akse overlapper hinanden. Grupperne på den primære akse må ikke have samme nøgler som grupperne på den sekundære akse.**

Det er som regel et midlertidigt problem. Det sker typisk, når du flytter grupper fra rækker til kolonner. I dette tilfælde skal fejlen forsvinde, når du er færdig med at flytte alle grupperne. Hvis meddelelsen stadig vises, skal du forsøge at skifte mellem rækkerne og kolonnerne eller akseforklaringen eller fjerne felter fra det visuelle element.  

**Dette visuelle element har overskredet de tilgængelige ressourcer. Prøv at filtrere for at mindske mængden af data, der vises.**

Det visuelle element har forsøgt at forespørge på for mange data, og vi kan ikke fuldføre resultatet med de tilgængelige ressourcer. Prøv at filtrere det visuelle element for at mindske mængden af data i resultatet.

**Vi kan ikke identificere følgende felter: {0}. Opdater det visuelle element med felter, der findes i datasættet.**

Feltet blev sandsynligvis slettet eller omdøbt. Du kan fjerne det ødelagte felt fra det visuelle element, tilføje et andet felt og fastgøre det igen.

**Dataene kunne ikke hentes for dette visuelle element. Prøv igen senere.**

Det er normalt et midlertidigt problem. Hvis du prøver igen senere, og du stadig får vist denne meddelelse, skal du kontakte support.

**Felter viser fortsat ufiltrerede data efter aktivering af enkeltlogon (SSO).**

Dette kan ske, hvis det underliggende datasæt er konfigureret til at bruge DirectQuery-tilstand eller en direkte forbindelse til Analysis Services via en datagateway i det lokale miljø. I dette tilfælde fortsætter felterne med at vise de ufiltrerede data efter aktivering af SSO for datakilden indtil næste opdatering af feltet. Ved næste opdatering af feltet bruger Power BI SSO som konfigureret, og felterne viser dataene filtreret i henhold til brugeridentiteten. 

Hvis du vil se de filtrerede data med det samme, kan du gennemtvinge en opdatering af felter ved at vælge **Flere indstillinger** (...) øverst til højre på et dashboard og derefter vælge **Opdater dashboardfelter**.

Som ejer af et datasæt kan du også ændre intervallet for opdatering af felter og angive det til 15 minutter for at fremskynde feltopdateringen. Vælg tandhjulsikonet i øverste højre hjørne af Power BI-tjenesten, og vælg derefter **Indstillinger**. Vælg fanen **Datasæt** på siden **Indstillinger**. Udvid **Planlagt cacheopdatering**, og rediger **Opdateringshastighed**. Sørg for at nulstille konfigurationen til den oprindelige opdateringshastighed, når Power BI har udført den næste feltopdatering.

> [!NOTE]
> Afsnittet **Planlagt cacheopdatering** er kun tilgængeligt for datasæt i tilstanden DirectQuery/direkte forbindelse. Datasæt i importtilstand kræver ikke en separat feltopdatering, fordi felterne opdateres automatisk under den næste planlagte opdatering af data.

## <a name="contact-support"></a>Kontakt support
Hvis du stadig har et problem, skal du [kontakte support](https://support.powerbi.com) for at undersøge det yderligere.

## <a name="next-steps"></a>Næste trin
[Fejlfinding af datagatewayen i det lokale miljø](service-gateway-onprem-tshoot.md)  
[Fejlfinding af Power BI Personal Gateway](service-admin-troubleshooting-power-bi-personal-gateway.md)  
Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
