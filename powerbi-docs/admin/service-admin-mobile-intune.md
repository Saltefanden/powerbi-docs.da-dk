---
title: Konfiguration af mobilapps med Microsoft Intune
description: Sådan konfigurerer du Power BI-mobilapps med Microsoft Intune. Dette omfatter, hvordan du tilføjer og installerer programmet. Og hvordan du opretter politikken for mobilapps til at styre sikkerheden.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Administration
ms.openlocfilehash: 6ca9b241fe2d6f2914a603e722f2dd2c216e05df
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408774"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Konfiguration af mobilapps med Microsoft Intune

Microsoft Intune giver organisationer mulighed for at administrere enheder og programmer. Power BI-mobilprogrammerne til iOS og Android kan integreres med Intune. Denne integration gør det muligt for dig at administrere programmet på dine enheder og styre sikkerheden. Ved hjælp af konfigurationspolitikker kan du kontrollere elementer som at anmode om pinkode for at give adgang, hvordan data håndteres af programmet og tilmed kryptere programdata, når appen ikke er i brug.

Microsoft Power BI-mobilappen gør det muligt for dig at få adgang til dine vigtige forretningsoplysninger. Du kan få vist og interagere med dine dashboards og rapporter for alle organisationens administrerede enheds- og appforretningsdata. Du kan finde flere oplysninger om understøttede Intune-apps under [Beskyttede Microsoft Intune-apps](/intune/apps/apps-supported-intune-apps).

## <a name="general-mobile-device-management-configuration"></a>Konfiguration af generel administration af mobilenheder

Denne artikel forudsætter, at Intune er konfigureret korrekt, og at du har enheder tilmeldt i Intune. Artiklen er ikke tænkt som en komplet konfigurationsvejledning til Microsoft Intune. Du kan finde flere oplysninger om Intune under [Hvad er Intune?](/intune/introduction-intune/)

Microsoft Intune kan fungere sammen med administration af mobilenheder i Microsoft 365. Hvis du bruger MDM, vises "tilmeldt MDM" på enheden, men den kan administreres i Intune.

Før slutbrugere kan bruge Power BI-appen på deres enheder, skal en Intune-administrator føje appen til Intune og også tildele appen til slutbrugere.

> [!NOTE]
> Når du konfigurerer Intune, er dataopdatering i baggrunden slået fra for Power BI-mobilappen på din iOS- eller Android-enhed. Power BI opdaterer dataene via Power BI-tjenesten på internettet, når du åbner appen.

## <a name="step-1-add-the-power-bi-app-to-intune"></a>Trin 1: Føj appen Power BI til Intune

Hvis du vil føje appen Power BI til Intune, skal du følge de trin, der er angivet i følgende emner:
- [Tilføj apps fra iOS Store til Microsoft Intune](/intune/apps/store-apps-ios)
- [Tilføj apps fra Android Store til Microsoft Intune](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>Trin 2: Tildel appen til dine slutbrugere

Når du har føjet appen Power BI til Microsoft Intune, kan du tildele appen til brugere og enheder. Det er vigtigt at bemærke, at du kan tildele en app til en enhed, uanset om enheden administreres af Intune.

Hvis du vil tildele appen Power BI til brugere og enheder, skal du bruge de trin, der er angivet i [Tildel apps til grupper med Microsoft Intune](/intune/apps/apps-deploy).

## <a name="step-3-create-and-assign-app-protection-policies"></a>Trin 3: Opret og tildel politikker for appbeskyttelse

Politikker for appbeskyttelse er regler, der sikrer, at en organisations data forbliver sikre eller findes i en administreret app. En politik kan være en regel, der gennemtvinges, når brugeren forsøger at få adgang til eller flytte "firmadata" eller et sæt handlinger, der ikke er tilladt eller overvåges, når brugeren befinder sig i appen. En administreret app er en app, hvor der anvendes en politik for beskyttelse af apps, og som kan administreres af Intune.

Med politikker for administration af mobilapps kan du administrere og beskytte din organisationens data i et program. Med politikker for administration af mobilapps uden tilmelding kan en arbejds- eller skolerelateret app, der indeholder følsomme data, administreres på næsten alle enheder, herunder personlige enheder i BYOD-scenarier (Bring-Your-Your-Device). Du kan finde flere oplysninger under [Oversigt over politikker for appbeskyttelse](/intune/apps/app-protection-policy).

Hvis du vil oprette og tildele en politik for appbeskyttelse til Power BI-appen, skal du bruge de trin, der er angivet i [Sådan opretter og tildeler du politikker for appbeskyttelse](/intune/apps/app-protection-policies).

## <a name="step-4-use-the-application-on-a-device"></a>Trin 4: Brug programmet på en enhed

Administrerede apps er apps, som din virksomhedssupport kan konfigurere for at beskytte virksomhedens data, som du har adgang til i den pågældende app. Når du åbner virksomhedsdata i en administreret app på din enhed, kan du opleve, at appen fungerer lidt anderledes end forventet. For eksempel kan du muligvis ikke kopiere og indsætte beskyttede virksomhedsdata, eller du kan muligvis ikke gemme disse data på bestemte placeringer.

Hvis du vil vide, hvordan dine slutbrugere kan bruge appen Power BI på deres enhed, skal du gennemgå de trin, der er angivet i følgende artikler:
- [Brug administrerede apps på din iOS-enhed](/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [Brug administrerede apps på din Android-enhed](/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>Næste trin

[Sådan opretter og tildeler du politikker for appbeskyttelse](/intune/app-protection-policies) 

[Power BI-apps til mobilenheder](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)