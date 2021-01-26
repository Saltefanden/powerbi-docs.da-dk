---
title: Registrer diagnosticeringsoplysninger for support
description: Instruktioner til manuel indsamling af diagnosticeringsoplysninger fra Power BI-tjeneste. Send disse oplysninger til support for at hjælpe dem med at foretage fejlfinding.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/21/2021
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 59e434d571c5b8d10c944bc385fb4e18ed89963c
ms.sourcegitcommit: 84f0e7f31e62cae3bea2dcf2d62c2f023cc2d404
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/26/2021
ms.locfileid: "98781387"
---
# <a name="capture-diagnostic-information-from-the-power-bi-service"></a>Registrer diagnosticeringsoplysninger fra Power BI-tjeneste

Før du kontakter Microsoft support for at få hjælp med et problem, som du har med Power BI-tjeneste, kan du indsamle filer, der kan hjælpe os med at løse problemet. Vi anbefaler, at du får et browser spor fra din browsersession. Et browser spor er en diagnosticerings fil, der kan give vigtige oplysninger om, hvad der sker i Power BI-tjeneste, når problemet opstår.

Power BI administratorer kan bruge **support til hjælp + support** i [administrations centeret til Power-platformen](https://admin.powerplatform.microsoft.com/) til at få løsninger til selvhjælp og til at kontakte support. De diagnostiske filer, du indsamler ved hjælp af nedenstående fremgangsmåde, kan vedhæftes i din supportanmodning for at hjælpe med fejlfinding. Du kan finde flere supportmuligheder under [Power bi supportmuligheder](service-support-options.md).

Hvis du vil indsamle en browser sporing og andre sessionsoplysninger, skal du følge nedenstående trin for den browser, du bruger.

## <a name="collect-a-browser-trace"></a>Indsaml en browser sporing

> [!IMPORTANT]
>Log på Power BI-tjeneste, [](https://app.powerbi.com) *før* du begynder at indsamle oplysninger om browser sporing, uanset hvilken browser du bruger. Dette trin er vigtigt, hvis du vil sikre, at sporingsoplysningerne ikke indeholder følsomme oplysninger, der er relateret til dit logon.

#### <a name="google-chrome-or-microsoft-edge"></a>[Google Chrome eller Microsoft Edge](#tab/google-chrome-or-microsoft-edge)

Google Chrome og Microsoft Edge (chrom) er begge baseret på det [chroms åbne kilde projekt](https://www.chromium.org/Home). I nedenstående fremgangsmåde kan du se, hvordan du bruger udviklerværktøjerne, der ligner hinanden i de to browsere. Du kan finde flere oplysninger i [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) og [Microsoft Edge (chrom) udviklerværktøj](/microsoft-edge/devtools-guide-chromium).

1. Når du er logget på, skal du trykke på F12 på dit tastatur. Eller vælg indstillinger i Microsoft Edge **(...)**  >  **Flere værktøjer**  >  **Udviklerværktøjer**. I Google Chrome skal du vælge **Tilpas og styre menuen med indstillinger for Google Chrome** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/chromium-icon-settings.png" alt-text="Google Chrome." border="false"::: > **Flere værktøjer**  >  **Udviklerværktøjer**.
1. Forbered hentning af browser sporingen ved at angive sporingsindstillinger. Du stopper også og rydder alle oplysninger, der blev indsamlet, inden du går i gang med at genskabe problemet. Som standard gemmer browseren kun sporingsoplysninger for den side, der er indlæst i øjeblikket. Følg disse trin for at konfigurere browseren til at beholde alle sporingsoplysninger, også selvom dine gendannelses går over til mere end én side:
    1. Vælg fanen **netværk** i vinduet **udviklerværktøjer** . Vælg derefter **Bevar log**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-preserve-log.png" alt-text="Udviklerværktøjer med fanen Network og Bevar log valgt." :::

     2. Vælg fanen **konsol** , og vælg derefter **Indstillinger**  >  **Bevar log**. 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-console-settings.png" alt-text="Udviklerværktøjer med konsol fane og Bevar log valgt." :::

        Vælg **Indstillinger** igen for at lukke **konsolindstillingerne**.

3. Derefter skal du stoppe og rydde alle igangværende optagelser. Vælg fanen **netværk** , Vælg **stop registrering af netværks loggen**, og **Ryd** derefter.
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="Udviklerværktøjer med fanen Network og stopper og rydder indstillinger for optagelse valgt." :::
     
2. Nu vil du genskabe det problem, du var i Power BI-tjeneste. Hvis du vil starte, skal du vælge fanen **netværk** i **udviklerværktøjer** . Vælg **Registrer netværks logfil**.

    > [!IMPORTANT]
    >Opdater browsersiden i Power BI-tjeneste, før du går i gang med at genskabe problemet, så spor registreres korrekt.

   Reproducerer de trin, der resulterede i det problem, du har brug for hjælp til.

     :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-record-network-log.png" alt-text="Udviklerværktøjer med fanen Network og post Network log valgt." :::

    Når du genskaber problemet, kan du se output, der svarer til følgende billede, i vinduet **udviklerværktøjer** .

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-output.png" alt-text="Udviklerværktøjer med fanen netværk med visning af sessions output." :::
    
3. Når du har genoprettet problemets funktionsmåde, skal du gemme logfilerne og vedhæfte dem i din supportanmodning.
    1. Hvis du vil eksportere netværks loggen, skal du i **udviklerværktøjer** vælge fanen **netværk** . Vælg **stop registrering af netværks logfil**. Vælg derefter **Export har...** og Gem filen.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-export-har.png" alt-text="Udviklerværktøjer med fanen netværk, stop optagelse og eksport af HAR er valgt." :::

    2. Hvis du vil eksportere konsol outputtet, skal du i **udviklerværktøjer** vælge fanen **konsol** . Højreklik på en vist meddelelse, og vælg derefter **Gem som...**, og Gem konsol outputtet i en tekstfil.
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-save-as.png" alt-text="Udviklerværktøjer med fanen konsol valgt og Gem som den viste indstilling." :::

   Pak den gemte HAR-fil, konsol output og skærmoptagelse i et komprimeret format, f. eks. post, og Vedhæft filen til din supportanmodning.

#### <a name="apple-safari"></a>[Apple Safari](#tab/apple-safari)

I nedenstående fremgangsmåde kan du se, hvordan du bruger udviklerværktøjerne i Apple Safari. Du kan finde flere oplysninger under [Safari udviklerværktøj oversigt](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/11.0/mac).

1. Når du har logget på, skal du aktivere udviklerværktøjerne i Apple Safari:
    1. Vælg **Safari**-indstillinger på sidehovedet  >  .
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-preferences.png" alt-text="Apple Safari-menu med indstillinger valgt." :::

    2. Vælg **Avanceret**, og vælg derefter **Vis menuen udvikling på menulinjen** for at aktivere udviklerværktøjerne.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-show-develop-menu.png" alt-text="Menuen Avanceret i Safari, hvor menuen Vis udvikling er valgt i menulinjen." :::

2. Derefter skal du angive indstillinger i **Webinspektionen** for at gøre det muligt for din browser at bevare alle sporingsoplysninger. Som standard gemmer browseren kun sporingsoplysninger for den side, der er indlæst i øjeblikket. Disse indstillinger sikrer, at sporingsoplysninger indsamles, selvom dine gendannelses kræver mere end én side.

    1. Vælg **udvikling** af WebFrem  >  **viser**.
    
        :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-web-inspector.png" alt-text="Vis menuen udvikling, der er valgt i Vis Web-fremviser." :::

    2. Vælg **netværks**  >  **bevarelses logfil**
       
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-network-preserve-log.png" alt-text="Menuen web-fremviser med netværks-og Bevar log valgt." :::

    1. Vælg **konsolens**  >  **bevarelses logfil**
   
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-console-preserve-log.png" alt-text="Menuen web-fremviser med konsol og Bevar log valgt." :::

3. Når indstillingerne er angivet, skal du vælge **netværks**  >  **Ryd netværkselementer** for at sikre, at dine logfiler kun indeholder detaljer om problemet gendannelses.

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-clear-network-items.png" alt-text="Menuen web-fremviser med netværk og rydde netværkselementer valgt." :::


4. Nu er du klar til at genskabe problemet. 
    > [!IMPORTANT]
    >Opdater browsersiden i Power BI-tjeneste, før du går i gang med at genskabe problemet, så spor registreres korrekt.

    Gennemgå trinnene for at genskabe det problem, du har. Når du genskaber problemet, kan du se output, der svarer til følgende billede, i vinduet **netværk** .

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-session-output.png" alt-text="Netværks vindue, hvor eksempel output vises." :::

5. Når du har genoprettet problemets funktionsmåde, skal du gemme logfilerne og vedhæfte dem i din supportanmodning.

    1. Hvis du vil eksportere netværks loggen, skal du vælge **Eksportér** og gemme filen i har-format under fanen **netværk** .

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-export.png" alt-text="Indstillingen Eksportér er valgt på fanen netværk." :::

    2. Hvis du vil eksportere konsol outputtet, skal du i ruden **udvikling** af værktøjer vælge **konsol** fanen og udvide vinduet. Placer markøren i starten af konsol outputtet, og træk og vælg hele indholdet af outputtet. Brug kommando C til at kopiere outputtet og gemme det i en tekstfil.

   Pak den gemte HAR-fil, konsol output og skærmoptagelse i et komprimeret format, f. eks. post, og Vedhæft filen til din supportanmodning.

#### <a name="firefox"></a>[Firefox](#tab/firefox)

I nedenstående fremgangsmåde kan du se, hvordan du bruger udviklerværktøjerne i Firefox. Du kan finde flere oplysninger i [Firefox-udviklerværktøjer](https://developer.mozilla.org/docs/Tools).

1. Når du er logget på, skal du trykke på F12 på dit tastatur. Eller i Firefox skal du vælge menuen med **åben menu** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-menu.png" alt-text="Firefox." border="false"::: > **Web Developer**  >  **Slå værktøjer til/fra**. Værktøjerne vises nederst på skærmen.

1. Derefter skal du angive indstillinger i **fremviseren** for at gøre det muligt for din browser at bevare alle sporingsoplysninger. Som standard gemmer browseren kun sporingsoplysninger for den side, der er indlæst i øjeblikket. Disse indstillinger sikrer, at sporingsoplysninger indsamles, selvom dine gendannelses kræver mere end én side.

    1. Vælg fanen **netværk** i **fremviser** vinduet. Vælg derefter **faste logge**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-network-persist-logs.png" alt-text="Værktøjer til fremviser med netværks fane og faste logge valgt." :::

     2. Vælg fanen **konsol** , og vælg derefter **konsol indstillinger**  >  **Gem logge**. 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-console-persist-logs.png" alt-text="Værktøjer til fremviser med konsol fane og faste logge valgt." :::

3. Når indstillingerne er angivet, skal du rydde en vilkårlig igangværende optagelse. Vælg fanen **netværk** , og **Fjern markeringen i afkrydsnings** feltet.
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="Udviklerværktøjer med fanen Network og stopper og rydder indstillinger for optagelse valgt." :::
     
2. Nu er du klar til at genskabe problemet. 
    > [!IMPORTANT]
    >Opdater browsersiden i Power BI-tjeneste, før du går i gang med at genskabe problemet, så spor registreres korrekt.
 
    Gennemgå trinnene for at genskabe det problem, du har.
    
3. Når du har genoprettet problemets funktionsmåde, skal du gemme logfilerne og vedhæfte dem i din supportanmodning.
    1. Hvis du vil eksportere netværks loggen, skal du vælge **netværks**  >  **har Export/Import** og derefter **gemme alle som har**.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-save-har.png" alt-text="Fanen netværk med HAR Export/Import menu og Gem alle valgte indstillinger." :::

    2. Hvis du vil eksportere konsol outputtet, skal du vælge fanen **konsol** . Højreklik på en vist meddelelse, vælg derefter **Eksportér synlige meddelelser til**, og Gem konsol outputtet i en tekstfil.
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-export-visible-messages.png" alt-text="Fanen konsol valgt, og indstillingen Eksportér synlige meddelelser vises." :::

   Pak den gemte HAR-fil, konsol output og skærmoptagelse i et komprimeret format, f. eks. post, og Vedhæft filen til din supportanmodning.

---

Når du har indsamlet diagnosefilerne, kan du vedhæfte dem i din supportanmodning for at hjælpe support teknikene med at løse problemet. HAR-filen indeholder alle de oplysninger om netværksanmodninger, der findes mellem browservinduet og Power BI-tjeneste, herunder:

* Aktivitets-id'erne for hver anmodning.

* Det nøjagtige tidsstempel for hver anmodning.

* Alle fejloplysninger, der returneres til klienten.

Denne sporingen vil også indeholde de data, der bruges til at udfylde de visuelle elementer, der vises på skærmen.

## <a name="next-steps"></a>Næste trin

* [Spor Power BI-tjenestetilstand i Microsoft 365](service-admin-health.md)
* [Aktiver meddelelser om tjenesteafbrydelser](service-interruption-notifications.md)
* [Deltag i Power BI-community'et](https://community.powerbi.com/)
