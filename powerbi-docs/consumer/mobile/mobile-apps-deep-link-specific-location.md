---
title: Opret et link til en bestemt placering i Power BI-mobilappsene
description: Se, hvordan du kan oprette et dybt link til et bestemt dashboard, felt eller en rapport i Power BI-mobilappen ved hjælp af en URI (Uniform Resource Identifier).
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 11/16/2020
ms.openlocfilehash: 8c5b3c394d54df390d690d58b56e9084f9829733
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565653"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Opret et link til en bestemt placering i Power BI-mobilappsene
Du kan bruge links til at oprette direkte adgang til specifikt Power BI-indhold, f. eks. en bestemt rapport, en rapportside, et dashboard, et felt osv.

Der er hovedsageligt to scenarier, hvor du kan bruge links til at oprette adgang til indhold i Power BI-mobilappsene: 

* Hvis du vil åbne Power BI **uden for mobilappen**, og lande på specifikt indhold. Dette er normalt et integrationsscenarie, hvor du åbner Power BI-mobilappen fra en anden app. 
* Hvis du vil **navigere** i Power BI. Det sker som regel, når du vil oprette brugerdefineret navigation i Power BI.

Denne artikel omhandler følgende scenarier:
* Brug af links til at åbne bestemt Power BI-indhold i uden for mobilappen. Der beskrives to linkformater. I det ene bruges der en omdirigeringsmetode, og det kan bruges, uanset hvor Power BI åbnes. Det andet åbnes direkte i Power BI-mobilappen og fungerer kun på mobilenheder, hvor mobilappen er installeret.
* Brug af links i Power BI til at navigere til bestemt Power BI-indhold.

## <a name="use-links-from-outside-the-mobile-app"></a>Brug links uden for mobilappen
Når du vil oprette et link til et bestemt element i Power BI uden for mobilappen, er der to muligheder, afhængigt af hvor linket skal åbnes:

* Hvis linket skal åbnes korrekt, uanset om der klikkes på det i en computerbrowser eller på en mobilenhed, kan du oprette et link, der åbnes korrekt, uanset hvor der klikkes på det. Dette link har en særlig omdirigeringssyntaks, som aktiverer denne intelligente funktionsmåde.

* Hvis du ved, at linket kun skal åbnes på en mobilenhed, hvor Power BI-mobilappen er installeret, kan du undgå omdirigeringsomkostningerne i ovenstående metode og bruge en anden linksyntaks, der åbner linket direkte i Power BI-mobilappen på mobilenheden. Det er vigtigt at bemærke, at selvom dette link ikke medfører omdirigeringsomkostningerne for den første metode, fungerer det ikke, hvis det åbnes andre steder end på en mobilenhed, hvor Power BI-mobilappen er installeret.

### <a name="create-a-link-that-works-anywhere"></a>Opret et link, der fungerer overalt
Det linkformat, der er beskrevet i dette afsnit, bruger omdirigering til at sikre, at linket fungerer, uanset hvor der klikkes på det.
* Hvis der klikkes på linket på en mobilenhed, sikrer det, at enheden bruger Power BI-mobilappen til at åbne linket. Hvis mobilappen ikke er installeret på enheden, foreslås det at brugeren går til butikken for at hente den.
* Hvis der klikkes på linket på en pc, åbnes det relevante element i Power BI-webportalen.

Linket skal starte med et særligt præfiks efterfulgt af forespørgselsparametre:

https<nolink>://app.powerbi.com/Redirect? **[QUERYPARAMETERS]** </code>

> [!IMPORTANT]
> Hvis indholdet hostes i et særligt datacenter, f. eks. det offentlige, Kina osv., skal linket starte med den relevante Power BI-adresse, f. eks. **app.powerbigov.us** eller **app.powerbi.cn**.

Forespørgselsparametrene er følgende:

|Parameter  | Værdi  | Beskrivelse |
|---------|---------|---------|
|**action** (obligatorisk)    | OpenApp<br>OpenReport<br>OpenDashboard<br>OpenTile | |
|**appId**| GUID på 36 tegn | Skal angives, hvis du vil åbne en rapport eller et dashboard, der er en del af en app<br>Eksempel: **appId=baf4b16d-b5bd-4360-8a3a-51d11242c09b** |
|**groupObjectId**| GUID på 36 tegn | Angiver arbejdsområdet, hvis du vil åbne en rapport eller et dashboard, der er en del af Mit arbejdsområde.<br>Eksempel: **groupObjectId=9a3841c6-74b3-46f1-85fd-bdd78f27b30e** |
| **dashboardObjectId** | GUID på 36 tegn | Dashboardobjekt-id (hvis action er OpenDashboard eller OpenTile)<br>Eksempel: **dashboardObjectId=033bb049-5b68-4392-b3ef-ae9a43738a4a** |
| **reportObjectId** | GUID på 36 tegn | Rapportobjekt-id (hvis action er OpenReport)<br>Eksempel: **reportObjectId=6114cec7-78e1-4926-88ff-0bc5338452cf** |
| **tileObjectId** | GUID på 36 tegn | Feltobjekt-id (hvis action er OpenTile)<br>Eksempel: **tileObjectId=a845dcb8-a289-43a8-94ea-67a8c0a068f9** |
| **reportPage** | ReportSection&lt;num&gt; | Sidenavn, hvis du vil åbne en bestemt rapportside. (hvis handlingen er OpenReport)<br>Eksempel: **reportPage = ReportSection6**  |
| **bookmarkGuid** | GUID på 36 tegn | Bogmærke-id, hvis du vil åbne en bestemt bogmærkevisning. (hvis handlingen er OpenReport)<br>Eksempel: **bookmarkGuid=18e8872f-6db8-4cf8-8298-3b2ab254cc7f** |
| **ctid** | GUID på 36 tegn | Elementorganisations-id (relevant for B2B-scenarier. Dette kan udelades, hvis elementet tilhører brugerens organisation)<br>Eksempel: **ctid=5367c770-09d0-4110-bf6a-d760cb5ef681** . |
||||

**Eksempler:**

I følgende eksempler fremhæves pladsholdere for parameterværdierne med fed. Hvis du vil hente de faktiske værdier, skal du gå til Power BI-tjenesten, åbne det element, du vil oprette et link til, og udtrække de værdier, du har brug for, fra elementets URL-adresse.

* **Åbn en app**

    https<nolink>://app.powerbi.com/Redirect?action=OpenApp&appId= **&lt;appid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**
   
* **Åbn et dashboard, der er en del af en app**

    https<nolink>://app.powerbi.com/Redirect?action=OpenDashboard&appId= **&lt;appid-guid&gt;** &dashboardObjectId= **&lt;dashboardid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**

* **Åbn en rapport, der er en del af et andet arbejdsområde end Mit arbejdsområde**

    https<nolink>://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId= **&lt;reportid-guid&gt;** &groupObjectId= **&lt;groupobjectid-guid&gt;** &reportPage=**ReportSection&lt;num&gt;**

### <a name="how-to-get-the-correct-link-format"></a>Sådan opnår du det rette linkformat

#### <a name="links-to-apps-and-items-in-apps"></a>Links til apps og elementer i apps

For de **apps, rapporter og dashboards, der er en del af en app**, er det nemmest at oprette linket ved at gå til arbejdsområdet for appen og vælge **Opdater app**. Dette åbner oplevelsen "Publicer app". Åbn fanen tilladelser, og udvid afsnittet Links for at se linkene til appen og hele dens indhold. Du kan bruge disse links uden for Power BI til at få direkte adgang til appen og dens indhold.

![Links til publicering i apps i Power BI ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-to-items-that-are-not-in-an-app"></a>Links til elementer, der ikke er i en app 

For rapporter og dashboards, der ikke er en del af en app, skal du udtrække de objekt-id'er, du har brug for, fra elementets URL-adresse. Det kan du gøre ved at gå til Power BI-tjenesten, navigere til det element, du vil oprette et link til, og søge efter de værdier, du har brug for, i den URL-adresse, du får vist i adresselinjen i browseren.

I nedenstående eksempler kan du se, hvor du kan finde de id'er, du har brug for, i URL-adresserne for de elementer, du vil oprette et link til.

* Hvis du vil finde et dashboardobjekt-id på 36 tegn, skal du navigere til det pågældende dashboard, du vil oprette et link til, i Power BI-tjenesten og finde dashboardobjekt-id'et og andre påkrævede id'er de steder, der er angivet nedenfor:

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;dashboard-object-id&gt;** ?ctid= **&lt;org-object-id&gt;**

* Hvis du vil finde et rapportobjekt-id på 36 tegn, skal du navigere til den specifikke rapport, du vil oprette et link til, i Power BI-tjenesten og finde de nødvendige id'er som vist nedenfor. Bemærk, at dette eksempel indeholder en reference til en bestemt rapport side og et bestemt bogmærke.

    https<nolink>://app.powerbi.com/groups/me/reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;num&gt;** ?bookmarkGuid= **&lt;bookmark-id&gt;**

* Hvis du vil oprette et link til et element i et andet arbejdsområde end Mit arbejdsområde, skal du udtrække gruppeobjekt-id'et. I dette eksempel vises der en rapport fra et andet arbejdsområde end Mit arbejdsområde.

    https<nolink>://app.powerbi.com/groups/ **&lt;group-object-id&gt;** /reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;report-section-num&gt;** ?ctid= **&lt;org-object-id&gt;**

### <a name="create-a-link-that-opens-only-on-a-device-that-has-the-power-bi-mobile-app-installed"></a>Opret et link, der kun åbner på en enhed, hvor Power BI-mobilappen er installeret

Det linkformat, der er beskrevet i dette afsnit, er links til en bestemt placering i Power BI-mobilappsene på alle mobilplatforme: iOS, Android-enheder og Windows 10. Dette link format åbner placeringen direkte uden nogen af de omdirigeringer, der er blev brugt i den metode, der beskrives i forrige afsnit. **Dette format kan kun åbnes på mobilenheder, hvor Power BI mobilappen er installeret**.

Links med dette format kan pege direkte på dashboards, felter og rapporter. Destinationen for det dybe link bestemmer dets format. Følg disse trin for at oprette dybe links til forskellige placeringer. 

* **Åbn Power BI-mobilappen**

    Brug dette link til at åbne Power BI-mobilappen på en hvilken som helst enhed:

    mspbi://app/

* **Åbn på et bestemt dashboard**

    Dette link åbner Power BI-mobilappen i et bestemt dashboard:

    mspbi://app/OpenDashboard?DashboardObjectId= **<36-character-dashboard-id>**

    Du kan finde det dashboardobjekt-id’et på 36 tegn ved at gå til det pågældende dashboard i Power BI-tjenesten og udtrække det fra URL-adressen (https://powerbi.com). Dashboardobjekt-id'et er f. eks. fremhævet i følgende URL-adresse fra Power BI-tjenesten:

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;61b7e871-cb98-48ed-bddc-6572c921e270&gt;**

    Hvis dashboardet ikke findes i Mit arbejdsområde, skal du også tilføje gruppeobjekt-id'et, enten før eller efter dashboard-id'et. Det dybe link, der vises nedenfor, har gruppeobjekt-id-parameteren tilføjet efter dashboardobjekt-id'et:

    mspbi://app/OpenDashboard?DashboardObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**</code>

    Bemærk og-tegnet (&) mellem de to parametre.

* **Åbn med et bestemt felt i fokus**

    Dette link åbner Power BI-mobilappen med et bestemt felt i fokus:

    mspbi://app/OpenTile?DashboardObjectId= **<36-character-dashboard-id>** &TileObjectId= **<36-character-tile-id>**

    Du kan finde dashboard- og felt-id'erne på 36 tegn ved at gå til det pågældende dashboard i Power BI-tjenesten og åbne feltet i fokustilstand. I eksemplet nedenfor er dashboard- og felt-id'erne fremhævet.

    https<nolink>://app.powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

    Hvis du vil åbne dette felt direkte, ville linket være:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

    Bemærk og-tegnet (&) mellem de to parametre.

    Hvis dashboardet ikke findes i mit arbejdsområde, skal du tilføje parameteren GroupObjectId, f. eks. & GroupObjectId = < 36-tegn-gruppe-id >

* **Åbn på en bestemt rapport**

    Dette link åbner en bestemt rapport i Power BI-mobilappen:

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>**

    Du kan finde det rapportobjekt-id'et på 36 tegn ved at gå til den pågældende rapport i Power BI-tjenesten. Følgende URL-adresse fra Power BI-tjenesten illustrerer det rapport-id, du skal udtrække.

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

    Hvis rapporten ikke findes i Mit arbejdsområde, skal du også tilføje **& GroupObjectId = < gruppe-id-på-36-tegn>** , enten før eller efter rapport-id'et. I dette tilfælde er det dybe link f. eks.:

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**

    Bemærk og-tegnet (&) mellem de to parametre.

* **Åbn på en bestemt rapportside**

    Dette link åbner en bestemt rapportside i Power BI-mobilappen:

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>** &reportPage=**ReportSection&lt;number&gt;**

    Rapportsiden har navnet **ReportSection** efterfulgt af et tal. Hvis du vil finde de værdier, du har brug for, skal du åbne rapporten i Power BI-tjenesten, gå til den pågældende rapportside og udtrække de nødvendige værdier fra URL-adressen. De fremhævede afsnit af denne URL-adresse repræsenterer f. eks. de værdier, du skal bruge for at åbne på en bestemt rapportside:

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**/**ReportSection11**</code>

* **Åbn i fuldskærmsvisning (kun Windows-enheder)**

    For Windows-enheder kan du også tilføje parameteren **openFullScreen** for at åbne en bestemt rapport i fuldskærmsvisning. I følgende eksempel åbnes en rapportside i fuldskærmsvisning:

    mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&**openFullScreen=true**

* **Tilføj kontekst** (valgfrit)

    Du kan også føje kontekst til strengen. Hvis du får brug for at kontakte os, kan vi bruge denne kontekst til at filtrere vores data og finde det, der er relevant for din app. Hvis du vil tilføje en kontekst, skal du føje parameteren **context =&lt;app-name&gt;** til linket:

    Følgende eksempel viser f. eks. et link, der indeholder en kontekstparameter: 

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**&**context=SlackDeepLink**

## <a name="use-links-inside-power-bi"></a>Brug links i Power BI

I Power BI-mobilappsene fungerer links i Power BI på samme måde, som i Power BI-tjenesten.

Hvis du vil føje et link til din rapport, der peger på et andet Power BI-element, kan du blot kopiere dette elements URL-adresse fra browserens adresselinje. Læs mere om, [hvordan du føjer et link til et tekstfelt i en rapport](../../create-reports/service-add-hyperlink-to-text-box.md).

## <a name="next-steps"></a>Næste trin
Din feedback hjælper os med at afgøre, hvad der skal implementeres fremover, så husk at stemme på andre funktioner, du gerne vil se i Power BI-mobilapps. 

* [Power BI-apps til mobilenheder](mobile-apps-for-mobile-devices.md)
* Følg @MSPowerBI på Twitter
* Deltag i samtalen i [Power BI-communityet](http://community.powerbi.com/)
* [Hvad er Power BI?](../../fundamentals/power-bi-overview.md)