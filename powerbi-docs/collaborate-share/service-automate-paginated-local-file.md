---
title: Gem en sideinddelt rapport i en lokal mappe med Power Automate
description: I denne artikel skal du bruge en skabelon til at konfigurere tilbagevendende eksporter af en sideinddelt rapport til dit filsystem i et ønsket format.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098617"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>Gem en sideinddelt Power BI-rapport i en lokal mappe med Power Automate

Med [Power Automate](/power-automate/getting-started) kan du automatisere eksport og distribution af sideinddelte Power BI-rapporter til en række understøttede formater og scenarier. I denne artikel skal du bruge en skabelon til at konfigurere tilbagevendende eksporter af en sideinddelt rapport til dit filsystem i et ønsket format. Se forudsætningerne, hvis det er første gang, du bruger handlingen Eksportér til fil for sideinddelte rapporter i et Power Automate-flow.

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="Konfigurer tilbagevendende eksporter af en sideinddelt rapport.":::

Leder du efter andre Power Automate-skabeloner til sideinddelte Power BI-rapporter? Se [Eksportér sideinddelte Power BI-rapporter med Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Forudsætninger  

Hvis du vil følge med, skal du sørge for, at du har:

- Mindst ét arbejdsområde i din Power BI-lejer skal understøttes af en reserveret kapacitet. Denne kapacitet kan være en hvilken som helst af SKU'erne A4/P1-A6/P3. Læs mere om [reserverede kapaciteter til sideinddelte rapporter i Power BI Premium](../admin/service-premium-what-is.md#paginated-reports).
- Få adgang til standardforbindelser i Power Automate, som medfølger ethvert Office 365-abonnement.

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>Gem en sideinddelt Power BI-rapport i en lokal mappe

1. Vælg skabelonen **Gem en sideinddelt Power BI-rapport i et lokalt filsystem**. Sørg for, at du er logget på Power BI og har forbindelse til dit lokale filsystem. Vælg **Fortsæt**. 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="Gem en sideinddelt Power BI-rapport i et lokalt filsystem":::.

2. Du skal muligvis vælge **Tilføj ny forbindelse** for at oprette forbindelse til filsystemet. 
1. Angiv et **forbindelsesnavn**, stien til den ønskede **rodmappe**, og godkend den ved at angive dit **brugernavn** og din **adgangskode**. Vælg en **gateway** på rullelisten, hvis du bruger en datagateway i det lokale miljø.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="Angiv et forbindelsesnavn og en rodmappe.":::
 
3. Hvis du vil angive **gentagelsesfrekvensen** for dit flow, skal du vælge en indstilling på rullelisten **Frekvens** og angive den ønskede værdi for **Interval**.  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="Angiv gentagelsesfrekvensen for dit flow.":::

4. Du kan også vælge **Vis avancerede indstillinger**. Angiv yderligere parametre for **gentagelsen**, f.eks. **Tidszone**, **Starttidspunkt**, **På disse dage,** **På dette klokkeslæt** og **På dette minuttal**. 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="Angiv avancerede indstillinger for gentagelsen.":::

5. I feltet **Arbejdsområde** skal du vælge et arbejdsområde i en reserveret kapacitet, hvor rapporten er. I feltet **Rapport** skal du vælge den sideinddelte rapport i arbejdsområdet, som du vil eksportere. I feltet **Eksportformat** skal du vælge det ønskede eksportformat. Alternativt kan du angive parametre for den sideinddelte rapport. Find detaljerede beskrivelser af parametrene i [connectorreferencen til REST-API til Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="Vælg arbejdsområdet og rapporten.":::

6. Under **Mappesti** i dialogboksen **Opret fil** skal du vælge den mappe, som du vil eksportere din sideinddelte rapport til.
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="Vælg den mappe, som du vil eksportere din sideinddelte rapport til":::

7. I Power Automate genereres et **filnavn** og **filindholdet** automatisk for dig. Du kan ændre **filnavnet**, men behold den dynamisk genererede værdi for **filindhold**.
8. Når du er færdig, skal du vælge **Næste trin** eller **Gem**. Power Automate gemmer og evaluerer flowet.
9. Hvis Power Automate finder fejl, skal du vælge **Rediger flow** for at løse dem. Ellers skal du vælge pilen Tilbage for at få vist flowoplysningerne og køre det nye flow.
10. Når du kører flowet, eksporterer Power Automate en sideinddelt rapport i det angivne format til den valgte mappe i dit filsystem.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="Power Automate eksporterer en sideinddelt rapport i det angivne format.":::

## <a name="next-steps"></a>Næste trin

- [Eksportér sideinddelte Power BI-rapporter med Power Automate](service-automate-paginated-integration.md)
- [Kom godt i gang med Power Automate](/power-automate/getting-started/)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

