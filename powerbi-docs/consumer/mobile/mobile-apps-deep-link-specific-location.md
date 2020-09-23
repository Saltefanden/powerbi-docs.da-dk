---
title: Opret et link til en bestemt placering i Power BI-mobilappsene
description: Se, hvordan du kan oprette et dybt link til et bestemt dashboard, felt eller en rapport i Power BI-mobilappen ved hjælp af en URI (Uniform Resource Identifier).
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: b414457c15155053ff6d316d1147536ec9ca5a8e
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90856639"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Opret et link til en bestemt placering i Power BI-mobilappsene
Du kan bruge links til at få direkte adgang til bestemte elementer i Power BI: Rapport, Dashboard og Felt.

Der er hovedsageligt to scenarier, hvor du kan bruge links i Power BI - Mobil: 

* Hvis du vil åbne Power BI **uden for appen**, og lande på bestemt indhold (rapport/dashboard/app). Dette er som regel et integrationsscenarie, når du vil åbne Power BI - Mobil fra en anden app. 
* Hvis du vil **navigere** i Power BI. Det er som regel, når du vil oprette brugerdefineret navigation i Power BI.


## <a name="use-links-from-outside-of-power-bi"></a>Brug links, der ikke er fra Power BI
Når du bruger et link, der ikke fra Power BI-appen, skal du sikre dig, at det åbnes af appen, og at brugeren bliver tilbudt at installere appen, hvis den ikke er installeret på enheden. Vi har oprettet et særligt linkformat for at understøtte præcist dette. Dette linkformat sikrer, at enheden bruger appen til at åbne linket, og at brugeren bliver tilbudt at få appen hentet fra Store, hvis den ikke er installeret på enheden.

Linket skal starte med følgende  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> Hvis dit indhold hostes i et særligt datacenter som f.eks. Goverment, Kina osv. Linket skal starte med den rigtige Power BI-adresse, f.eks. `app.powerbigov.us` eller. `app.powerbi.cn`.   
>


**QUERY PARAMS** er:
* **action** (obligatorisk) = OpenApp / OpenDashboard / OpenTile / OpenReport
* **appId** = hvis du vil åbne en rapport eller et dashboard, der er en del af en app 
* **groupObjectId** = hvis du vil åbne en rapport eller et dashboard, der er en del af et arbejdsområde (men ikke mit arbejdsområde)
* **dashboardObjectId** = dashboardobjekt-id (hvis action er OpenDashboard eller OpenTile)
* **reportObjectId** = rapportobjekt-id (hvis action er OpenReport)
* **tileObjectId** = feltobjekt-id (hvis action er OpenTile)
* **reportPage** = hvis du vil åbne en specifik rapportsektion (hvis action er OpenReport)
* **ctId** = elementorganisations-id (relevant for B2B-scenarie. Dette kan udelades, hvis elementet tilhører brugerens organisation).

**Eksempler:**

* Åbn applink 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* Åbn et dashboard, der er en del af en app 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* Åbn en rapport, der er en del af et arbejdsområde
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>Sådan får du det rette linkformat

#### <a name="links-of-apps-and-items-in-app"></a>Links i apps og elementer i app

For de **apps, rapporter og dashboards, der er en del af en app**, er det nemmest at oprette linket ved at gå til arbejdsområdet og vælge "Opdater app". Derved åbnes oplevelsen "Publicer app", og under fanen Adgang kan du finde sektionen **Links**. Hvis du udvider denne sektion, får du vist en liste over appen og alle appens indholdslinks, som kan bruges til at få direkte adgang til dem.

![Links til publicering i apps i Power BI ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>Links til elementer, der ikke er i en app 

For rapporter og dashboards, der ikke er en del af en app, skal du udtrække id'erne fra elementets URL-adresse.

Du kan f.eks. finde det 36 tegn lange objekt-id for **dashboardet** ved at gå til det pågældende dashboard i Power BI-tjenesten 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

Du kan finde det 36 tegn lange objekt-id for **rapporten** ved at gå til den pågældende rapport i Power BI-tjenesten.
Dette er et eksempel på en rapport fra "Mit arbejdsområde"

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
Ovenstående URL-adresse indeholder også en bestemt rapportside **"ReportSection3"** .

Dette er et eksempel på en rapport fra et arbejdsområde (ikke Mit arbejdsområde)

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>Brug links i Power BI

Links i Power BI fungerer i mobilapps præcist på samme måde som i Power BI-tjenesten.

Hvis du vil føje et link til din rapport, der peger på et andet Power BI-element, kan du blot kopiere dette elements URL-adresse fra browserens adresselinje. Læs mere om, [hvordan du føjer et link til et tekstfelt i en rapport](../../create-reports/service-add-hyperlink-to-text-box.md).

## <a name="use-report-url-with-filter"></a>Brug rapportens URL-adresse med filter
På samme måde som Power BI-tjenesten understøtter Power BI - Mobil-apps også URL-adresser til rapporter, der indeholder en parameter for filterforespørgsel. Du kan åbne en rapport i Power BI - Mobil-appen og filtrere den til en bestemt tilstand. Denne URL-adresse åbner f.eks. salgsrapporten og filtrerer den efter distrikt

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

Læs mere om, [hvordan du opretter forespørgselsparametre for at filtrere rapporter](../../collaborate-share/service-url-filters.md).

## <a name="next-steps"></a>Næste trin
Din feedback hjælper os med at afgøre, hvad der skal implementeres fremover, så husk at stemme på andre funktioner, du gerne vil se i Power BI-mobilapps. 

* [Power BI-apps til mobilenheder](mobile-apps-for-mobile-devices.md)
* Følg @MSPowerBI på Twitter
* Deltag i samtalen i [Power BI-communityet](https://community.powerbi.com/)
* [Hvad er Power BI?](../../fundamentals/power-bi-overview.md)