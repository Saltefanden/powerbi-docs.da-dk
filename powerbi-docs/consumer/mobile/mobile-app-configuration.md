---
title: Konfigurationsindstillinger i Power BI-appen
description: Sådan tilpasser du funktionsmåden for Power BI ved hjælp af MDM-værktøjet
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 07/14/2020
ms.openlocfilehash: a867c0480e9c0762d1594016fb807cab8261c14c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414593"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Du kan fjernkonfigurere Power BI-appen ved hjælp af MDM-værktøjet (Mobile Device Management)

Appen Power BI – Mobil til iOS og Android understøtter appindstillinger, der gør det muligt for administratorer af MDM-tjenester (Mobile Device Management), f.eks. Intune, at tilpasse appens funktionsmåde.

Appen Power BI – Mobil understøtter følgende konfigurationsscenarier:

* Konfiguration af rapportserveren (iOS og Android)
* Indstillinger for databeskyttelse (iOS og Android)
* Deaktiver enkeltlogon (iOS og Android)
* Indstillinger for interaktioner (iOS og Android)

## <a name="report-server-configuration-ios-and-android"></a>Konfiguration af rapportserveren (iOS og Android)

Power BI-appen til iOS og Android gør det muligt for administratorer at fjern-"pushe" konfigurationen af rapportserveren til tilmeldte enheder.

| Nøgle | Type | Beskrivelse |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL-adresse | Streng | URL-adresse til rapportserver.<br><br>Skal starte med http/https.|
| com.microsoft.powerbi.mobile.ServerBrugernavn | Streng | [valgfri]<br><br>Det brugernavn, der skal bruges til at oprette forbindelse til serveren.<br><br>Hvis der ikke findes et brugernavn, vil appen bede brugeren skrive brugernavnet til forbindelsen.|
| com.microsoft.powerbi.mobile.ServerVist navn | Streng | [valgfri]<br><br>Standardværdien er "Rapportserver"<br><br>Et navn, der bruges i appen til at repræsentere serveren. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolesk | [valgfri]<br><br>Standardværdien er True. Når værdien er angivet til True, tilsidesætter den alle eksisterende rapportserverdefinitioner på mobilenheden. Eksisterende servere, der allerede er konfigureret, slettes. Dette forhindrer også, at brugeren kan fjerne konfigurationen.<br><br>Hvis indstillingen er angivet til "False", tilføjes de overførte værdier, og eksisterende indstillinger ændres ikke. Hvis den samme URL-adresse allerede er konfigureret i mobilappen, forbliver konfigurationen, som den er. Appen beder ikke brugeren om at godkende igen for den samme server. |

## <a name="data-protection-settings-ios-and-android"></a>Indstillinger for databeskyttelse (iOS og Android)

Power BI-mobilappen til iOS og Android giver administratorer mulighed for at tilpasse standardkonfigurationen for sikkerhed og indstillinger for beskyttelse af personlige oplysninger. I forbindelse med iOS kan du gennemtvinge, at brugerne skal angive deres Face ID, Touch ID eller en adgangskode, når de åbner Power BI-mobilappen. Hvis der bruges Android, kan du tvinge brugerne til at anvende biometrisk godkendelse (fingeraftryks-id).

| Nøgle | Type | Beskrivelse |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolesk | Standardværdien er False. <br><br>Biometriske data, f.eks TouchID eller FaceID (iOS) eller fingeraftryks-id (Android), kan være påkrævet, for at brugerne kan få adgang til appen på deres enhed. Når det er påkrævet, bruges biometriske data ud over godkendelse.<br><br>Hvis du bruger politikker for appbeskyttelse, anbefaler Microsoft, at du deaktiverer denne indstilling for at forhindre dobbelte adgangsprompter. |

>[!NOTE]
>Indstillinger for databeskyttelse vil kun blive anvendt på Android-enheder, der understøtter biometrisk godkendelse.

## <a name="disable-single-sign-on-ios-and-android"></a>Deaktiver enkeltlogon (iOS og Android)

Som standard giver Power BI-mobilappen en bruger en praktisk enkeltlogons-oplevelse ved at minimere det antal gange, brugeren skal angive et brugernavn og en adgangskode. Denne enkeltlogons-funktionsmåde er baseret på den antagelse, at enheden er brugerens personlige enhed, og at der kun er én bruger, der bruger enheden og apps på den.

Administratorer kan aktivere indstillingen **DisableSingleSignOn** i app-konfigurationsfilen for at fjernkonfigurere appen for at deaktivere enkeltlogon og eksplicit anmode om brugerens adgangskode, når vedkommende logger på.

Denne indstilling er kun for administratorer og konfigureres via fjernforbindelse. Slutbrugeren kan ikke ændre denne indstilling.

| Nøgle | Type | Beskrivelse |
|---|---|---|
| com.microsoft.powerbi.mobile.DisableSingleSignOn | Boolesk | Standardværdien er False.<br><br>Når en bruger logger af, genbruger appen ikke eksisterende legitimationsoplysninger, men beder den næste bruger om at angive en adgangskode for at godkende og oprette forbindelse til Power BI-tjenesten.
 |

## <a name="interaction-settings-ios-and-android"></a>Indstillinger for interaktioner (iOS og Android)

Power BI-appen til iOS og Android giver administratorer mulighed for at konfigurere interaktionsindstillinger, hvis det er besluttet, at standardindstillinger for interaktion skal ændres på tværs af grupper af brugere i en organisation.

>[!NOTE]
>Det er ikke alle interaktioner, der understøttes på alle enheder i øjeblikket. Se [Konfiguration af indstillinger for rapportinteraktioner](mobile-app-interaction-settings.md) for et diagram, der viser den aktuelle tilgængelighed på tværs af enheder.

| Nøgle | Type | Værdier | Beskrivelse |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | Streng |  <nobr>single-tap</nobr><br><nobr>double-tap</nobr> | Konfigurer, om et tryk på en visualisering også foretager en datapunktsmarkering. |
| com.microsoft.powerbi.mobile.EnableMultiSelect | Boolesk |  <nobr>True</nobr><br><nobr>False</nobr> | Konfigurerer, om et tryk på et datapunkt erstatter den aktuelle markering eller føjes til den aktuelle markering. |
| com.microsoft.powerbi.mobile.RefreshAction | Streng |  <nobr>pull-to-refresh</nobr><br>knappen | Konfigurer, om brugeren skal have en knap til at opdatere rapporten, eller om vedkommende skal bruge trækopdatering. |
| com.microsoft.powerbi.mobile.FooterAppearance | Streng |  forankret<br>dynamisk | Konfigurer, om rapportfoden skal fastgøres nederst i rapporten eller skjules automatisk. |

## <a name="deploying-app-configuration-settings"></a>Udrulning af konfigurationsindstillinger for apps

Følgende er de trin, du skal følge for at oprette en appkonfigurationspolitik. Når du har oprettet konfigurationspolitikken, kan du tildele dens indstillinger til grupper af brugere.

1. Opret forbindelse til dit MDM-værktøj.
2. Opret og navngiv en ny appkonfigurationspolitik.
3. Vælg, hvilke brugere appkonfigurationspolitikken skal distribueres til.
4. Opret nøgleværdipar for den indstilling, du vil pushe til dine brugere.

Intune-portalen gør det muligt for administratorer nemt at installere disse indstillinger til Power BI-appen via konfigurationspolitikker for apps. Dog understøttes en eventuel MDM-udbyder. Hvis du ikke bruger Intune, skal du se din MDM-dokumentation for at få oplysninger om, hvordan du installerer disse indstillinger.

## <a name="next-steps"></a>Næste trin

* Hent Power BI-mobilappen i [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) og [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Følg [@MSPowerBI på Twitter](https://twitter.com/MSPowerBI)
* Deltag i samtalen i [Power BI-community'et](https://community.powerbi.com/)