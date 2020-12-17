---
title: Forbind en rapport til et datasæt ved hjælp af dynamisk binding i integreret analyse i Power BI
description: Få mere at vide om, hvordan du integrerer en rapport ved hjælp af dynamisk binding.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: d8a460f68838faab11cdab6d39f0e757a9789899
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098369"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Forbind en rapport til et datasæt ved hjælp af dynamisk binding 

Når en rapport har forbindelse til et datasæt, kan du bruge dynamisk binding. Forbindelsen mellem rapporten og datasættet kaldes for *binding*. Når bindingen fastsættes under integreringen – i modsætning til tidligere, hvor den blev fastsat på forhånd – kaldes bindingen en dynamisk binding.

Når du integrerer en Power BI rapport ved hjælp af *dynamisk binding*, kan du forbinde den samme rapport til forskellige datasæt, afhængigt af brugerens legitimationsoplysninger.

Det betyder, at du kan bruge én rapport til at vise forskellige oplysninger, afhængigt af det datasæt den er forbundet til. En rapport, der viser værdier for detailhandel, kan f.eks. forbindes til forskellige detailhandleres datasæt og give forskellige resultater, afhængigt af hvilken detailhandlers datasæt den er forbundet til.

Rapporten og datasættet behøver ikke at være placeret i det samme arbejdsområde. Begge arbejdsområder (det, der indeholder rapporten, og det, der indeholder datasættet) skal være tildelt en [kapacitet](azure-pbie-create-capacity.md).

Som en del af integreringsprocessen skal du sørge for, at du *genererer et token med tilstrækkelige tilladelser* og *tilpasser konfigurationsobjektet*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Generering af et token med tilstrækkelige tilladelser

Dynamisk binding understøttes til scenarier både med *Integrering for din organisation* og *Integrering for dine kunder*. I nedenstående tabel beskrives overvejelserne for hvert scenarie.

|Scenarie  |Ejerskab af data  |Token  |Krav  |
|---------|---------|---------|---------|
|*Integrering for din organisation*    |Brugeren ejer data         |Adgangstoken til Power BI-brugere         |Den bruger, hvis Azure AD-token bruges, skal have de relevante tilladelser til alle artefakter.         |
|*Integrering for dine kunder*     |Appen ejer data         |Adgangstoken til brugere, der ikke har Power BI         |Skal indeholde tilladelser til både rapporten og det dynamisk bundne datasæt. Brug [API'en til generering af et integreringstoken til flere elementer](/rest/api/power-bi/embedtoken/generatetoken) for at generere et integreringstoken, der understøtter flere artefakter.         |

## <a name="adjusting-the-config-object"></a>Tilpasning af konfigurationsobjektet
Føj `datasetBinding` til konfigurationsobjektet. Brug eksemplet nedenfor som reference.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Næste trin

Hvis du er nybegynder i forhold til at integrere i Power BI, kan du gennemse disse selvstudier for at få mere at vide om, hvordan du integrerer dit Power BI-indhold:
* [Selvstudium: Integrer Power BI-indhold i en applikation for dine kunder](embed-sample-for-customers.md)
* [Selvstudium: Integrer Power BI-indhold i en applikation for din organisation](embed-sample-for-your-organization.md)