---
title: Planlagt vedligeholdelse af Power BI
description: Oplysninger til administratorer om, hvordan planlagt vedligeholdelse af Power BI påvirker deres organisation og de næste trin, de muligvis skal udføre.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/19/2020
ms.author: kfollis
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: 19933ccbf18003e293e823c2b1f201e953c7bde0
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90854776"
---
# <a name="power-bi-planned-maintenance"></a>Planlagt vedligeholdelse af Power BI

Den planlagte vedligeholdelse af Power BI-tjenesten er en nødvendig del af vores bestræbelser på at tilbyde vores kunder et pålideligt produkt. Når den planlagte vedligeholdelse sker, er Power BI-tjenesten ikke tilgængelig for din organisation i et stykke tid. Brugere kan muligvis ikke få adgang til Power BI-tjenesten, og baggrundshandlinger kan mislykkes. Efter vedligeholdelsesvinduet forventer vi, at tjenesten fungerer normalt, og at både interaktive handlinger og baggrundshandlinger kan fuldføres.  

Vedligeholdelse er planlagt til at ske uden for normal åbningstid, så den påvirker organisationens drift mindst muligt. Vi er klar over, at "uden for normal åbningstid" kan være et bredt begreb for organisationer, der har brugere over hele verden. Vi undskylder for de forstyrrelser, brugerne måtte opleve. Vi arbejder hårdt på at forbedre Power BI og på at minimere disse vedligeholdelsesvinduer.

Hvis din organisation berøres, giver vi dig besked på forhånd. Microsoft 365-administratorer får vist en forhåndsmeddelelse i Microsoft 365 Meddelelsescenter og modtager en mail. Derudover informeres kunder, der har Premier Support-kontrakter, via deres Microsoft-kontoteam.

## <a name="actions-to-take-now"></a>Handlinger, der skal udføres nu

* Microsoft 365-administratorer skal kontrollere, om der er meddelelser om planlagt vedligeholdelse af Power BI i [Meddelelsescenter](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). Del meddelelsen med personer, der bør vide det, men som ikke har adgang til Meddelelsescenter.
* Hvis du ikke er Microsoft 365-administrator, skal du spørge it-afdelingen eller de interne supportteams om kommende vedligeholdelse.

## <a name="actions-to-take-when-maintenance-is-complete"></a>Handlinger, der skal udføres, når vedligeholdelsen er fuldført

* Brugerne bør opdatere alle åbne browservinduer.
* Brugere af Power BI – Mobil-appen skal bekræfte, at de bruger den nyeste version, logge af og derefter logge på appen igen. Se telefonens app store, eller se siden [Power BI – Mobil](https://powerbi.microsoft.com/mobile/).
* Kunder, der aktivt har redigeret eller publiceret rapporter, hvor der bruges organisatoriske visuals, skal enten importere visual'et igen via organisationens visualbutik eller downloade en opdateret PBIX, før de publicerer igen. Det gælder uanset om visuals lokale eller fra OneDrive- og SharePoint-placeringer. Hvis du vil have flere oplysninger om organisatoriske visuals, kan du se [Organisatoriske visuals](organizational-visuals.md).
* Hvis Excel-projektmapper, der bruger funktionen Analysér i Excel, ikke opdateres, skal du muligvis opdatere forbindelsesstrengen eller hente ODC-forbindelsen for det pågældende datasæt igen. Se [Analysér i Excel](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data) for at få flere oplysninger.
* Links til Power BI, der er integreret i indhold kan muligvis ikke oprette forbindelse, når vedligeholdelsen er fuldført. Et integreret link i SharePoint eller Teams kan f. eks. resultere i en brugerfejl. Du kan løse problemet ved at gendanne det integrerede link i Power BI og derefter opdatere de placeringer, hvor det bruges. Hvis du vil vide mere om integrerede links, kan du se [Integrer en rapportwebdel i SharePoint Online](../collaborate-share/service-embed-report-spo.md) og [Samarbejd i Microsoft Teams med Power BI](../collaborate-share/service-collaborate-microsoft-teams.md).

## <a name="next-steps"></a>Næste trin

* [Aktiver meddelelser om tjenesteafbrydelser](service-interruption-notifications.md)
* [Spor forestående ændringer i Meddelelsescenter](/microsoft-365/admin/manage/message-center?view=o365-worldwide)