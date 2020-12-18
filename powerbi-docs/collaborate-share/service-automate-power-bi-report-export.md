---
title: Eksportér og send en rapport via mail med Power Automate
description: I denne artikel skal du bruge Power Automate til at automatisere eksport og distribution af Power BI-rapporter i forskellige understøttede formater og scenarier.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098623"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>Eksportér og send en Power BI-rapport via mail med Power Automate

Med [Power Automate](/power-automate/getting-started) kan du automatisere eksport og distribution af Power BI-rapporter til en række understøttede formater og scenarier. I denne artikel skal du oprette dit eget flow fra bunden. Du skal bruge handlingen Eksportér til fil til Power BI-rapporter for automatisk at distribuere en Power BI-rapport via mail.

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="Trin i Power Automate til at eksportere og sende en rapport via mail.":::

## <a name="prerequisites"></a>Forudsætninger  

Hvis du vil følge med, skal du sørge for, at du har:

- Mindst ét arbejdsområde i din Power BI-lejer skal understøttes af en reserveret kapacitet. Denne kapacitet kan være en af A1/EM1-A6/P3-SKU'erne. Læs mere om [reserverede kapaciteter i Power BI Premium](../admin/service-premium-what-is.md).
- Få adgang til standardforbindelser i Power Automate, som medfølger ethvert Office 365-abonnement.

## <a name="create-a-flow-from-scratch"></a>Opret et flow fra bunden 

I denne opgave skal du oprette et enkelt flow fra bunden. Flowet eksporterer en Power BI-rapport som en PDF-fil og vedhæfter den til en mail, der skal sendes ugentligt.  

1. Log på Power Automate (flow.microsoft.com).
2. Vælg **Opret** > **Planlagt flow**. 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="Opret et planlagt flow i Power Automate.":::

3. Angiv et navn til flowet i **Opret et planlagt flow**. 
4. I **Kør dette flow** skal du vælge startdato og -klokkeslæt for dit flow samt gentagelsesfrekvensen.
5. I **På disse dage** skal du vælge, hvilke dage dit flow skal køre, og vælge **Opret**.

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power Automate, planlæg flowet.":::

6. I **Gentagelse** skal du vælge **Vis avancerede indstillinger** og angive en værdi i **På dette klokkeslæt** og **På dette minuttal** for at angive et bestemt tidspunkt for, hvornår dit flow skal køre.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="Angiv gentagelse i Power Automate.":::

7. Vælg **Nyt trin**.
8. Søg efter **Power BI** i **Vælg en handling**, og vælg **Eksportér til fil for Power BI-rapporter**.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="Vælg en handling i Power Automate.":::

9. I **Eksportér til fil for Power BI-rapporter** skal du vælge et **arbejdsområde** og en **rapport** i rullemenuerne.
10. Vælg det ønskede **Eksportformat** til din Power BI-rapport.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="Vælg eksportformat i Power Automate.":::

11. Du kan også angive, at bestemte sider skal eksporteres, i feltet **Sider pageName -1**. Bemærk, at parameteren for sidenavn adskiller sig fra visningens sidenavn. Find sidenavnet ved at navigere til siden i Power BI-tjenesten og kopiere den sidste del af URL-adressen.
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="Vælg navnet på ruden i URL-adressen.":::

12. Du kan også angive et bestemt bogmærke, der skal vises i feltet **Bogmærkenavn for sider**. På samme måde som med parameteren for sidenavn kan du finde parameteren for bogmærkenavn i rapportens URL-adresse. Du kan angive yderligere parametre for Power BI-rapporten. Find detaljerede beskrivelser af parametrene i [connectorreferencen til REST-API til Power BI](/connectors/powerbi/#export-to-file-for-power-bi-reports).

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="Vælg bogmærkenavnet i URL-adressen.":::

13. Vælg **Nyt trin**.
14. Søg efter **Outlook** i **Vælg en handling**, og vælg **Send en mail (v2)** .
15. I **Send en mail (v2)** skal du udfylde felterne **Til**, **Emne** og **Brødtekst** for din mail.
16. Vælg **Vis avancerede indstillinger**. I **Navn på vedhæftede filer – 1** skal du angive et navn for den vedhæftede fil. Føj et filtypenavn til filnavnet (f.eks. PDF), der svarer til dit foretrukne **eksportformat**.
17. Vælg **Filindhold** i **Indhold af vedhæftet fil** for at vedhæfte den eksporterede Power BI-rapport.  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="Vælg den eksporterede rapport, du vil sende via mail.":::

18. Når du er færdig, skal du vælge **Næste trin** eller **Gem**. Med Power Automate oprettes og evalueres flowet, og du får besked, hvis der findes fejl.
1. Hvis der er fejl, skal du vælge **Rediger flow** for at løse dem. Ellers skal du vælge pilen **Tilbage** for at få vist flowoplysningerne og køre det nye flow.
    Når du kører flowet, eksporterer Power Automate en Power BI-rapport i det angivne format og sender den som en vedhæftet fil som planlagt.  

## <a name="next-steps"></a>Næste trin

- [Integrer Power BI-databeskeder med Power Automate](service-flow-integration.md)
- [Kom godt i gang med Power Automate](/power-automate/getting-started/)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
