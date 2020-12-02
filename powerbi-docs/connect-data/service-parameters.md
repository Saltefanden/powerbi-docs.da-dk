---
title: Rediger parameterindstillinger i Power BI-tjenesten
description: Forespørgselsparametre oprettes i Power BI Desktop, men kan gennemses og opdateres i Power BI-tjenesten
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/04/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 29468ea50625b1d354bd431f77c5e89edf5a889d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402081"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Rediger parameterindstillinger i Power BI-tjenesten
Rapportoprettere føjer forespørgselsparametre til rapporter i Power BI Desktop. Parametre gør det muligt for dem at oprette dele af rapporter, der afhænger af en eller flere parameter *værdier*. En rapportopretter kan f.eks. oprette en parameter, der begrænser dataene til et enkelt land/område, eller en parameter, der definerer acceptable formater for felter, såsom datoer, klokkeslæt og tekst.

![Fanen Hjem, der viser indstillingen Administrer parametre i Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Gennemse og rediger parametre i Power BI-tjenesten

Som rapportopretter definerer du parametre i Power BI Desktop. Når du [udgiver rapporten i Power BI-tjenesten](../create-reports/desktop-upload-desktop-files.md), følger parameterindstillingerne og markeringerne med. Du kan gennemse og redigere parameterindstillinger i Power BI-tjenesten, men ikke oprette dem.

1. Vælg tandhjulsikonet ![tandhjulsikon](media/service-parameters/power-bi-cog.png) i Power BI-tjenesten for at åbne **Indstillinger**.

2. Vælg fanen for **Datasæt**, og fremhæv et datasæt på listen. 
    
    ![Vinduet Indstillinger med fanen Datasæt valgt](media/service-parameters/power-bi-select-dataset2.png)

3. Udvid **Parametre**.  Hvis det valgte datasæt ikke indeholder parametre, får du vist en meddelelse med et link til at få mere at vide om forespørgselsparametre. Hvis datasættet ikke har parametre, vil udvidelse af overskriften **Parametre** vise disse parametre. 

    ![Vinduet Indstillinger med udvidede Parametre](media/service-parameters/power-bi-settings.png)

    Gennemse parameterindstillingerne, og foretag de nødvendige ændringer. Nedtonede felter kan ikke redigeres. 


## <a name="next-steps"></a>De næste trin
En ad hoc-metode til at tilføje enkle parametre er at [ændre URL-adressen](../collaborate-share/service-url-filters.md).
