---
title: Retningslinjer for Power BI-visualiseringer
description: Du kan få mere at vide om, hvordan du publicerer din brugerdefinerede visualisering i Microsoft AppSource, så andre kan finde, købe og bruge den.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 08/12/2020
ms.openlocfilehash: 6e9da6e16d32f0093bc0e4be35415f1a23f7fa41
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748558"
---
# <a name="guidelines-for-power-bi-visuals"></a>Retningslinjer for Power BI-visualiseringer
Før du [publicerer](office-store.md) din Power BI-visualisering i Microsoft AppSource, så andre kan finde og bruge den, skal du sørge for at følge retningslinjerne for at skabe en fantastisk oplevelse for dine brugere.

## <a name="power-bi-visuals-with-additional-purchases"></a>Power BI-visualiseringer med ekstra køb

Du kan sende Power BI-visualiseringer, der er gratis, til Marketplace (Microsoft AppSource). Du kan også sende Power BI-visualiseringer, som har prismærket "Yderligere køb kan være påkrævet" til Microsoft AppSource. Power BI-visualiseringer med "Yderligere køb kan være påkrævet" er ligesom tilføjelsesprogrammer med apptilkøb i Office Store. 

En IAP Power BI-visualisering kan, på samme måde som en gratis Power BI-visualisering, også certificeres. Før du indsender din IAP Power BI-visualisering til certificering, skal du kontrollere, at den overholder [kravene til certificering](power-bi-custom-visuals-certified.md).

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>Hvad er en Power BI-visualisering med IAP-funktioner?

En IAP Power BI-visualisering er en *gratis* visualisering, der tilbyder *gratis funktioner*. Den indeholder også nogle avancerede funktioner, som man muligvis skal betale for. I beskrivelsen af Power BI-visualiseringen skal udviklerne give brugerne besked om, hvilke funktioner der kræver yderligere køb, før de kan anvendes. I øjeblikket leverer Microsoft ikke oprindelige API'er til understøttelse af apptilkøb og tilføjelsesprogrammer.

Udviklere kan bruge et hvilket som helst betalingssystem fra tredjepart til disse køb. Du kan finde flere oplysninger i [vores politik for Store](/legal/marketplace/certification-policies#11002-displaying-ads).


>[!IMPORTANT]  
> Hvis du opdaterer din Power BI-visualisering fra gratis til "Yderligere køb kan være påkrævet", skal brugerne modtage det samme niveau af gratis funktionalitet som før opdateringen. Du kan tilføje valgfrie avancerede betalte funktioner udover de eksisterende gratis funktioner.

### <a name="watermarks"></a>Vandmærker

Du kan bruge vandmærker, så kunderne fortsætter med at bruge de avancerede IAP-funktioner uden betaling. 

Vandmærker kan bruges til at vise den fulde funktionalitet af Power BI-visualiseringen, før der foretages et køb. 

* Vandmærker må kun bruges på de betalte funktioner, der bruges uden en gyldig licens.
* Vandmærker er ikke tilladt i Power BI-visualiseringer med prismærket *gratis*.
* Vandmærker er ikke tilladt i IAP-visualiseringer, når brugeren benytter gratis funktioner. 

### <a name="pop-up-window"></a>Pop op-vindue

Du kan bruge et pop op-vindue til at forklare, hvordan du køber en licens, når der bruges en ugyldig (eller udløbet) licens sammen med din Power BI IAP-visualisering.

### <a name="submission-process"></a>Indsendelsesproces

Følg [indsendelsesprocessen](office-store.md#submitting-to-appsource), og naviger derefter til fanen *Produktkonfiguration*, og markér afkrydsningsfeltet *Mit produkt kræver køb af en tjeneste*.

Efter Power BI-visualiseringen er blevet valideret og godkendt, angives "Yderligere køb kan være påkrævet" under prismulighederne for IAP Power BI-visualiseringen i Microsoft AppSource.

## <a name="context-menu"></a>Genvejsmenu
Genvejsmenuen er den menu, du kommer til ved at højreklikke, som vises, når brugeren holder markøren over en visualisering.
Genvejsmenuen bør være aktiveret i alle Power BI-visualiseringer for at sikre en ensartet oplevelse.
Læs [denne artikel](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md) for at få mere at vide om, hvordan du tilføjer en genvejsmenu.

>[!div class="mx-imgBorder"]
>![Et skærmbillede af genvejsmenuen i en Power BI-visualisering.](media/guidelines-powerbi-visuals/context-menu.png)

## <a name="commercial-logo"></a>Kommercielt logo
I dette afsnit beskrives specifikationerne for tilføjelse af kommercielle logoer i Power BI-visualiseringer. Kommercielle logoer er ikke obligatoriske. Hvis de tilføjes, skal de følge disse retningslinjer.

> [!NOTE]
> * Begrebet "kommercielt logo" i denne artikel refererer til et ikon for en vilkårlig kommerciel virksomhed, som beskrevet i nedenstående billeder.
> * Microsofts kommercielle logo bruges kun som eksempel i denne artikel. Brug dit eget kommercielle logo sammen med din Power BI-visualisering.

> [!IMPORTANT]
> Kommercielle logoer er kun tilladt i *redigeringstilstand*. Kommercielle logoer *må ikke* vises i visningstilstand.

### <a name="commercial-logo-type"></a>Kommerciel logotype

Der er tre typer kommercielle logoer:
* **Logo** – et logo består af to elementer, et ikon og et navn, der er låst sammen.

    ![Et skærmbillede af Microsoft-logoet.](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **Symbol** – et grafikobjekt uden tekst.

    ![Et skærmbillede af Microsoft-symbolet.](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **Logotype** – et logo uden et ikon, som kun består af tekst.

    ![Et skærmbillede af Microsoft-logoet uden et ikon.](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>Farve på kommercielt logo

Når du bruger et kommercielt logo, skal logoet være gråt (hex-farve #C8C8C8). Du må ikke føje effekter som f.eks. gradueringer til det kommercielle logo.

* **Logo**

    ![Et skærmbillede af Microsoft-logoet i farven grå.](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **Symbol** – et grafikobjekt uden tekst.

    ![Et skærmbillede af Microsoft-symbolet i farven grå.](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **Logotype** – et logo uden et ikon, som kun består af tekst.

    ![Et skærmbillede af Microsoft-logoet uden et ikon i farven grå.](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * Hvis din Power BI-visualisering indeholder grafik, kan det være en god idé at føje en hvid baggrund (med 10 px margener) til dit logo.
> * Overvej at føje en skyggeeffekt (30 % uigennemsigtighed, sort) til dit logo.

### <a name="commercial-logo-size"></a>Størrelse på kommercielt logo

En Power BI-visualisering kræver to kommercielle logoer, ét til store felter og ét til små felter. Placer logoet i en afgrænsningsramme, der er placeret i det øverste eller nederste højre hjørne, med 4 px margener.

I følgende tabel beskrives størrelsesovervejelserne for Power BI-visualiseringer.

|Indstillinger  |Lille Power BI-visualisering  |Stor Power BI-visualisering  |
|---------|---------|---------|
|*Logobredde*    |Op til 240 px         |Større end 240 px         |
|*Logohøjde*     |Op til 160 px         |Større end 160 px         |
|*Størrelse på afgrænsningsramme*     |40 x 15 px         |101 x 30 px         |
|*Eksempel på kommercielt logo*     |![Et skærmbillede af den lille version af Microsoft Commercial-logoet.](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Et skærmbillede af Microsoft Commercial-logoet.](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|*Eksempel på afgrænsningsramme*    |![Et skærmbillede af dimensionerne i et lille logo.](media/guidelines-powerbi-visuals/small-logo-box.png)         |![Et skærmbillede af dimensionerne i et stort logo.](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>Funktionsmåde for kommercielt logo

Kommercielle logoer er kun tilladt i redigeringstilstand. Når der klikkes på et kommercielt logo, må det kun indeholde følgende funktioner:

* Når der klikkes på det kommercielle logo, omdirigeres der til dit websted.

* Når der klikkes på det kommercielle logo, åbnes et pop op-vindue med flere oplysninger. Pop op-vinduet skal inddeles i to afsnit:
    * Et markedsføringsområde, der kan omfatte et kommercielt logo, en visualisering og en markedsbedømmelse.
    * Et informationsområde, som kan indeholde oplysninger og links.    


### <a name="things-to-avoid"></a>Undgå følgende

* Kommercielle logoer må ikke vises i visningstilstand.

* Et animeret kommercielt logo kan vise animationen for op til fem sekunder.

* Hvis din Power BI-visualisering indeholder informative ikoner (i) i læsetilstand, skal de overholde farven, størrelsen og placeringen for det kommercielle logo som beskrevet ovenfor.

* Undgå et farverigt eller sort kommercielt logo. Det kommercielle logo skal være gråt (hex-farve #C8C8C8).

    ![Et skærmbillede af et uautoriseret farverigt Microsoft-logo.](media/guidelines-powerbi-visuals/no-color-logo.png) ![Et skærmbillede af et uautoriseret sort Microsoft-logo](media/guidelines-powerbi-visuals/black-logo.png)

* Et kommercielt logo med effekter som f.eks. gradueringer eller stærke skygger.

    ![Et skærmbillede af et eksempel på et uautoriseret logo i Microsoft-stil.](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>Bedste praksis

Når du publicerer en Power BI-visualisering, bør du overveje følgende anbefalinger for at give brugerne en god oplevelse.

### <a name="visual-landing-page"></a>Landingsside for visualisering

Brug landingssiden til at tydeliggøre over for brugerne, hvordan de kan bruge din Power BI-visualisering, og hvor de kan købe licensen. Undlad at inkludere videoer, der udløses automatisk. Tilføj kun materiale, der hjælper med at forbedre brugeroplevelsen, f.eks. oplysninger eller links til oplysninger om licenskøb, og hvordan funktioner for apptilkøb bruges.

### <a name="license-key-and-token"></a>Licensnøgle og -token

Af hensyn til brugerne skal du tilføje en licensnøgle eller tokenrelaterede felter øverst i formateringsruden.

## <a name="faq"></a>Ofte stillede spørgsmål

Du kan finde flere oplysninger om Power BI-visualiseringer under [Ofte stillede spørgsmål om Power BI-visualiseringer med yderligere køb](power-bi-custom-visuals-faq.md#visuals-with-additional-purchases).

## <a name="next-steps"></a>Næste trin

Få mere at vide om, hvordan du kan publicere din brugerdefinerede Power BI-visualisering i Microsoft AppSource, så andre kan finde og bruge den.

>[!div class="nextstepaction"]
>[Publicer Power BI-visuals](office-store.md)