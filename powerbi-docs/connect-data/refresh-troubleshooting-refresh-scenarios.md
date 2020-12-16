---
title: Fejlfinding i forbindelse med opdatering af scenarier
description: Fejlfinding i forbindelse med opdatering af scenarier
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 12/14/2020
LocalizationGroup: Data refresh
ms.openlocfilehash: eba044de4918ad3cc62ce8b47144eab25c34702a
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491799"
---
# <a name="troubleshooting-refresh-scenarios"></a>Fejlfinding i forbindelse med opdatering af scenarier

Her kan du finde oplysninger om forskellige scenarier, som du kan stå overfor, når du opdaterer data i Power BI-tjenesten.

> [!NOTE]
> Hvis du oplever et scenarie, der ikke er angivet nedenfor, og det medfører problemer for dig, kan du bede om yderligere hjælp på [communitywebstedet](https://community.powerbi.com/), eller du kan oprette en [supportanmodning](https://powerbi.microsoft.com/support/).
>

Du skal altid sikre, at de grundlæggende krav til opdatering er opfyldt og bekræftet. Disse grundlæggende krav omfatter:

* Kontrollér, at gatewayversionen er opdateret
* Kontrollér, at rapporten har en gateway markeret – hvis ikke, kan datakilden være ændret, eller den mangler muligvis

Når du har bekræftet, at disse krav er opfyldt, kan du gennemgå følgende afsnit for at få mere at vide om fejlfinding. 


## <a name="email-notifications"></a>Mailmeddelelser

Hvis du kommer til denne artikel fra en mailmeddelelse, og du ikke længere vil modtage mails om opdateringsproblemer, skal du kontakte din Power BI-administrator. Bed vedkommende om at fjerne din mailadresse eller en mailliste, du abonnerer på, fra de relevante datasæt i Power BI. Administratoren kan gøre det fra følgende område på Power BI-administrationsportalen.

![Mail med opdateringsmeddelelser](media/refresh-troubleshooting-refresh-scenarios/refresh-email.png)

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>Opdater ved at bruge Web-connector virker ikke korrekt

Hvis du har et webconnectorscript, der bruger funktionen [**Web.Page**](/powerquery-m/web-page), og du har opdateret dit datasæt eller din rapport efter d. 18. november 2016, skal du bruge en gateway, før opdateringen fungerer korrekt.

## <a name="unsupported-data-source-for-refresh"></a>Ikke-understøttet datakilde til opdatering

Når du konfigurerer et datasæt, kan du få en fejl, der indikerer, at datasættet bruger en ikke-understøttet datakilde til opdatering. Du kan finde yderligere oplysninger i [Fejlfinding af ikke-understøttet datakilde til opdatering](service-admin-troubleshoot-unsupported-data-source-for-refresh.md).

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>Dashboard viser ikke ændringer efter opdatering

Vent ca. 10-15 minutter på, at en opdatering afspejles i dashboardfelterne. Hvis den stadig ikke vises, skal du fastgøre visualiseringen til dashboardet igen.

## <a name="gatewaynotreachable-when-setting-credentials"></a>GatewayNotReachable ved indstilling af legitimationsoplysninger

Du kan støde på `GatewayNotReachable`, når du forsøger at angive legitimationsoplysninger for en datakilde. Dette kan skyldes en forældet gateway. Installér den seneste gateway, og prøv igen.

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>Behandlingsfejl: Følgende systemfejl opstod: Uoverensstemmelse mellem datatyper

Det kan skyldes et problem med dit M-script i din Power BI Desktop-fil eller Excel-projektmappe. Det kan også skyldes en forældet version af Power BI Desktop.

## <a name="tile-refresh-errors"></a>Fejl ved feltopdatering

Se en liste over fejl, du kan støde på ved dashboardfelter, og forklaringer i [Fejlfinding af feltfejl](refresh-troubleshooting-tile-errors.md).

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>Opdater mislykkes ved opdatering af data fra kilder, der bruger AAD OAuth

Azure Active Directory (**AAD**) OAuth-token, der bruges af mange forskellige datakilder, udløber om ca. en time. Du kan løbe ind i situationer, hvor indlæsning af data tager længere tid end tokenudløb (mere end en time), da Power BI-tjenesten venter i op til to timer ved indlæsning af data. I den situation kan dataindlæsningsprocessen mislykkes med en fejl i legitimationsoplysninger.

Datakilder, der bruger AAD OAuth, omfatter bl.a. **Microsoft Dynamics CRM Online**, **SharePoint Online** (SPO). Hvis du opretter forbindelse til disse datakilder og får en fejl i legitimationsoplysninger, når indlæsning af data tager længere tid end en time, kan dette være årsagen.

Microsoft undersøger en løsning, der giver dataindlæsningsprocessen mulighed for at opdatere tokenen og fortsætte. Hvis din forekomst af Dynamics CRM Online eller SharePoint Online (eller anden AAD OAuth-datakilde) er så stor, at den kan støde på grænsen for dataindlæsning på to timer, kan du også opleve en timeout for dataindlæsning fra Power BI-tjenesten.

Bemærk også, at for at opdatering skal virke korrekt, skal du, når du opretter forbindelse til en **SharePoint Online**-datakilde ved brug af AAD OAuth, bruge den samme konto, som når du logger på **Power BI-tjenesten**.

## <a name="uncompressed-data-limits-for-refresh"></a>Ikke-komprimerede datagrænser for opdater

Den maksimale størrelse for datasæt, der importeres i **Power BI-tjenesten**, er 1 GB. Disse datasæt er meget komprimerede for at sikre høj ydeevne. I en delt kapacitet sætter tjenesten derudover en grænse for mængden af ikke-komprimeret data, der behandles under en opdatering, til 10 GB. Denne grænse tager højde for komprimeringen, og er derfor meget højere end 1 GB. Datasæt i Power BI Premium er ikke underlagt denne grænse. Hvis opdatering i Power BI-tjenesten mislykkedes af denne årsag, skal du reducere mængden af data, der importeres i Power BI, og prøve igen.

## <a name="scheduled-refresh-timeout"></a>Timeout for planlagt opdatering

Planlagt opdatering for importerede datasæt får timeout efter to timer. Denne timeout er øget til fem timer for datasæt på **Premium**-arbejdsområder. Hvis du støder på denne grænse, kan du overveje at reducere størrelsen eller kompleksiteten af dit datasæt eller overveje at inddele datasættet i mindre dele.

## <a name="scheduled-refresh-failures"></a>Fejl i planlagte opdateringer

Hvis en planlagt opdatering mislykkes fire gange i træk, deaktiveres opdateringen i Power BI. Løs det underliggende problem, og genaktiver derefter den planlagte opdatering.

## <a name="access-to-the-resource-is-forbidden"></a>Der er ikke adgang til ressourcen  

Denne fejl kan opstå pga. udløbne cachelagrede legitimationsoplysninger. Ryd din browsers cache ved at logge på Power BI og gå til `https://app.powerbi.com?alwaysPromptForContentProviderCreds=true`. Dette gennemtvinger en opdatering af dine legitimationsoplysninger.

## <a name="data-refresh-failure-because-of-password-change-or-expired-credentials"></a>Fejl under opdatering af data på grund af ændret adgangskode eller udløbne legitimationsoplysninger

Opdateringen af data kan også mislykkes på grund af udløbne cachelagrede legitimationsoplysninger. Ryd din browsers cache ved at logge på Power BI og gå til `https://app.powerbi.com?alwaysPromptForContentProviderCreds=true`. Dette gennemtvinger en opdatering af dine legitimationsoplysninger.

## <a name="next-steps"></a>Næste trin

- [Opdatering af data i Power BI](refresh-data.md)  
- [Fejlfinding af datagatewayen i det lokale miljø](service-gateway-onprem-tshoot.md)  
- [Fejlfinding af Power BI Gateway – Personlig](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Har du flere spørgsmål? [Prøv at spørge Microsoft Power BI-community'et](https://community.powerbi.com/)
