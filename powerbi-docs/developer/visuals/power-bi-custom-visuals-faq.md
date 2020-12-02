---
title: Ofte stillede spørgsmål om Power BI-visualiseringer
description: Gennemse en liste med ofte stillede spørgsmål og svar om Power BI-visualiseringer
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 09/30/2020
ms.openlocfilehash: f38aaf9ea5bcb62cabae6ce2b7aca99f97c75960
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386429"
---
# <a name="power-bi-visuals-faq"></a>Ofte stillede spørgsmål om visualiseringer i Power BI

## <a name="organizational-power-bi-visuals"></a>Power BI-visualiseringer til organisationer

På administrationsportalen kan du administrere Power BI-visualiseringer for din organisation.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>Hvordan kan administratoren administrere Power BI-visualiseringer til organisationer?

På administrationsportalen under fanen *Visualiseringer til organisationer* kan administratoren se og [administrere alle Power BI-visualiseringer i virksomheden](../../admin/organizational-visuals.md#organizational-visuals). Dette omfatter tilføjelse, deaktivering, aktivering og sletning af Power BI-visualiseringer.

Brugere i organisationen kan nemt finde Power BI-visualiseringer og importere dem til deres rapporter direkte fra Power BI Desktop eller Power BI-tjenesten.

Når administratoren uploader en ny version af en Power BI-visualisering til organisationer, får alle i organisationen den samme opdaterede version. Alle rapporter, der bruger opdaterede Power BI-visualiseringer, opdateres automatisk.

Brugerne kan finde Power BI-visualiseringer til organisationer i det indbyggede organisationslager til Power BI Desktop og Power BI-tjenesten under fanen *MIN ORGANISATION*. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-using-add-visual--from-appsource-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Hvis en administrator uploader en Power BI-visualisering fra den offentlige markedsplads til organisationslageret ved hjælp af *Tilføj visualisering > fra AppSource*, opdateres den så automatisk, når en leverandør opdaterer visualiseringen på den offentlige markedsplads?

Ja, visualiseringen opdateres automatisk fra den offentlige markedsplads. Hvis visualiseringen er certificeret, bevares certificeringen, herunder yderligere funktioner såsom eksport til PDF eller PowerPoint.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>Er det muligt at deaktivere organisationslageret?

Nej, brugerne kan altid se fanen *MIN ORGANISATION* i Power BI Desktop og Power BI-tjenesten. Hvis en administrator deaktiverer eller sletter alle Power BI-visualiseringer til organisationer fra administrationsportalen, bliver organisationslageret tomt.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Hvis administratoren deaktiverer Power BI-visualiseringer fra administrationsportalen (lejerindstillinger), har brugerne så stadig adgang til Power BI-visualiseringerne til organisationer?

Ja, det har ingen indflydelse på organisationslageret, at administratoren deaktiverer Power BI-visualiseringer fra administrationsportalen.

Nogle organisationer deaktiverer Power BI-visualiseringer og aktiverer kun håndplukkede visualiseringer, der er importeret og uploadet af Power BI-administratoren til organisationslageret.

Deaktivering af Power BI-visualiseringer fra Administrationsportal gennemtvinges ikke i Power BI Desktop. Desktop-brugere kan stadig tilføje og bruge Power BI-visualiseringer fra den offentlige markedsplads i deres rapporter. Men de offentlige Power BI-visualiseringer gengives ikke længere, når de publiceres på Power BI-tjenesten, og der udstedes en passende fejl. 

Når indstillingen for Power BI-visualiseringer på administrationsportalen håndhæves, kan brugerne af Power BI-tjenesten ikke importere Power BI-visualiseringer fra den offentlige markedsplads. Det er kun visualiseringer fra organisationslageret, der kan importeres.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Hvad er fordelene ved Power BI-visualiseringer i organisationslageret?

* Alle får den samme version af visualiseringerne, der styres af Power BI-administratoren. Når administratoren opdaterer versionen af visualiseringer på administrationsportalen, får alle brugere i virksomheden automatisk den opdaterede version.

* Det er ikke længere nødvendigt at dele visualiseringsfiler via mail eller delte mapper. Tilbud i organisationslageret er synlige for alle medlemmer, der er logget på.

* Sikkerhed og understøttelse – nye versioner af Power BI-visualiseringer til organisationer opdateres automatisk i alle rapporter.

* Administratorer kan styre, hvilke Power BI-visualiseringer der er tilgængelige i hele organisationen.

* Administratorer kan aktivere/deaktivere visualiseringer til test fra administrationsportalen.

## <a name="certified-power-bi-visuals"></a>Certificerede Power BI-visualiseringer

### <a name="what-are-certified-power-bi-visuals"></a>Hvad er certificerede Power BI-visualiseringer?

Certificerede Power BI-visualiseringer er Power BI-visualiseringer, der opfylder visse [krav](power-bi-custom-visuals-certified.md) og er certificeret af Microsoft.

På [markedspladsen](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) har certificerede Power BI-visualiseringer et gult badge, der angiver, at de er certificerede.

Microsoft er ikke forfatteren af Power BI-visualiseringer fra tredjepart. Vi råder kunderne til at kontakte forfatteren direkte for at bekræfte funktionaliteten af visualiseringer fra tredjepart.

### <a name="what-tests-are-done-during-the-certification-process"></a>Hvilke test udføres under certificeringsprocessen?

Test under certificeringsprocessen omfatter, men er ikke begrænset til: 
* Anmeldelse af koder
* Analyse af statisk kode
* Datalækage
* Fuzzytest af data
* Indtrængningstest
* Adgang til XSS-test
* Injektion af skadelige data
* Inputvalidering
* Funktionel test
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Kontrolleres certificerede Power BI-visualiseringer igen ved hver nye indsendelse (opgradering)?

Ja. Hver gang en ny version af en certificeret visualisering sendes til Marketplace, undergår versionsopdateringen af visualiseringen de samme certificeringskontroller.

Certificeringen af den opdaterede version sker automatisk. Hvis der er en overtrædelse, som medfører, at opdateringen afvises, sendes der en mail til udvikleren med en forklaring på, hvad der skal løses.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>Kan en certificeret Power BI-visualisering miste sin certificering efter en ny opdatering?

Nej, det kan ikke ske. En certificeret visualisering kan ikke miste sin certificering med en ny opdatering. Opdateringen afvises.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Skal jeg dele min kode i et offentligt lager, hvis jeg certificerer min Power BI-visualisering?

Nej, du behøver ikke at dele din kode offentligt.

Giv læserettigheder for at kontrollere koden for Power BI-visualiseringen. Ved f.eks. at bruge et privat lager i GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>Skal en certificeret Power BI-visualisering være på markedspladsen?

Ja. Private visualiseringer certificeres ikke.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Hvor lang tid tager det at certificere min visualisering?

Det kan tage op til fire uger at certificere en ny Power BI-visualisering (førstegangscertificering). 

Certificering af en opdateret version af en Power BI-visualisering kan tage op til tre uger. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>Sikrer certificeringsprocessen, at der ikke sker datalækage?

De udførte test er udviklet til at kontrollere, at visualiseringen ikke har adgang til eksterne tjenester eller ressourcer. 

Microsoft er ikke forfatteren af Power BI-visualiseringer fra tredjepart. Vi råder kunderne til at kontakte forfatteren direkte for at bekræfte funktionaliteten af Power BI-visualiseringer fra tredjepart.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Er det sikkert at anvende Power BI-visualiseringer, der ikke er certificeret?

Ikke-certificerede Power BI-visualiseringer er ikke nødvendigvis ensbetydende med usikre visualiseringer.

Nogle visualiseringer er ikke certificeret, fordi de ikke overholder et eller flere [certificeringskrav](power-bi-custom-visuals-certified.md#certification-requirements). Det kan f.eks. være i forbindelse med oprettelse af forbindelse til en ekstern tjeneste, som f.eks. kortvisualiseringer eller visualiseringer, der anvender kommercielle biblioteker.
 
## <a name="visuals-with-additional-purchases"></a>Visualiseringer med ekstra køb

### <a name="what-is-a-visual-with-additional-purchases"></a>Hvad er en visualisering med ekstra køb?

En visualisering med yderligere køb ligner tilføjelsesprogrammet for apptilkøb (IAP – In-App Purchase). Disse tilføjelsesprogrammer har prismærket **Yderligere køb kan være påkrævet**.

Power BI-visualiseringer med IAP er gratis Power BI-visualiseringer, der kan downloades. Brugerne betaler intet for at downloade disse Power BI-visualiseringer fra markedspladsen.

Visualiseringer med IAP tilbyder valgfri apptilkøb for avancerede funktioner.  

### <a name="what-is-changing-in-the-submission-process"></a>Hvad ændres i indsendelsesprocessen?

Indsendelsesprocessen for Power BI-visualiseringer med IAP til markedspladsen er den samme proces som for gratis Power BI-visualiseringer. Du kan indsende en Power BI-visualisering til certificering ved hjælp af [Partnercenter](/partner-center/).


Når du registrerer din Power BI-visualisering, skal du navigere til fanen *Produktkonfiguration* og markere afkrydsningsfeltet *Mit produkt kræver køb af en tjeneste*.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>Hvad skal jeg gøre, før jeg indsender min Power BI-visualisering med IAP?

Hvis du arbejder på en Power BI-visualisering med IAP, skal du kontrollere, at den opfylder [retningslinjerne](guidelines-powerbi-visuals.md).  

> [!NOTE]
> Gratis Power BI-visualiseringer med en tilføjet IAP-funktion, skal beholde de samme gratis funktioner, som tidligere blev tilbudt. Du kan føje valgfrie avancerede betalte funktioner til de eksisterende gratis funktioner. Vi anbefaler, at du indsender Power BI-visualiseringer med IAP med de avancerede funktioner som en ny Power BI-visualisering i stedet for at opdatere den gamle gratis visualisering.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Skal Power BI-visualiseringer med IAP certificeres?

[Certificeringsprocessen](power-bi-custom-visuals-certified.md) er valgfri. Det er op til udvikleren at beslutte, om vedkommendes Power BI-visualisering med IAP skal certificeres eller ej.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>Kan jeg få min Power BI-visualisering med IAP certificeret?

Ja, når din Power BI-visualisering med IAP er godkendt af AppSource-teamet, kan du indsende Power BI-visualiseringen til [certificering](power-bi-custom-visuals-certified.md).

Certificering er en valgfri proces, og det er op til dig at beslutte, om du vil have din visualisering med IAP certificeret.

## <a name="additional-questions"></a>Yderligere spørgsmål

### <a name="how-to-get-support"></a>Hvordan får jeg support?

Du er meget velkommen til at kontakte supportteamet til Power BI-visualiseringer på pbicvsupport@microsoft.com, hvis du har spørgsmål, kommentarer eller problemer.  

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger under [Fejlfinding af Power BI-visualiseringer](power-bi-custom-visuals-troubleshoot.md).