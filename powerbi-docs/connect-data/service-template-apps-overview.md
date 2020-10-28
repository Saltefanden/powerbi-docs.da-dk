---
title: Hvad er Power BI-skabelonprogrammer?
description: Denne artikel indeholder en oversigt over Power BI-skabelonprogrammet. Få mere at vide om, hvordan du udarbejder Power BI-programmer med kun lidt eller ingen kode og udruller dem til dine Power BI-kunder.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
ms.author: painbar
ms.openlocfilehash: 432f05ed7efe8438d21a285b732ead08d93b8732
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349385"
---
# <a name="what-are-power-bi-template-apps"></a>Hvad er Power BI-skabelonprogrammer?

Med de nye Power BI- *skabelonprogrammer* kan Power BI-partnere udarbejde programmer i Power BI med kun lidt eller ingen kode og udrulle dem til Power BI-kunder.  Denne artikel indeholder en oversigt over Power BI-skabelonprogrammet.

Som Power BI-partner kan du oprette indhold, der er klar til brug, for dine kunder og selv publicere det.  

Du kan udarbejde skabelonprogrammer, som gør det muligt for dine kunder at oprette forbindelse til og instantiere fra deres egne konti. Som domæneeksperter kan de låse op for data på en måde, så deres virksomhedsbrugere nemt kan bruge dem.  

Du sender skabelonprogrammer til Partnercenter. Programmerne bliver derefter offentligt tilgængelige på [markedspladsen til Power BI-programmer](https://app.powerbi.com/getdata/services) og på [Microsoft AppSource](https://appsource.microsoft.com/?product=power-bi). Her er en overordnet oversigt over oplevelsen med at oprette en offentlig skabelon.

## <a name="power-bi-apps-marketplace"></a>Markedsplads til Power BI-programmer

Med Power BI-skabelonprogrammer kan brugere af Power BI Pro eller Power BI Premium få øjeblikkelig indsigt via dashboards og rapporter, der er pakket på forhånd, og som kan forbindes til livedatakilder. Mange Power BI-programmer er allerede tilgængelige på [markedspladsen til Power BI-programmer](https://app.powerbi.com/getdata/services).

:::row:::
    :::column:::
        [![Webappen Microsoft Project](./media/service-template-apps-overview/project-web.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_msprojectonline.pbi-microsoftprojectwebapp)
    :::column-end:::
    :::column:::
        [![Webappen Microsoft 365 Usage Analytics](./media/service-template-apps-overview/microsoft365-usage-analytics.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)
    :::column-end:::
    :::column:::
        [![Webappen Dynamisk 365 Business Central – Sales](./media/service-template-apps-overview/dynamics-sales.png)](https://app.powerbi.com/groups/me/getapps/services/microsoftdynsmb.businesscentral_sales)
    :::column-end:::
    :::column:::
        [![Webappen Microsoft Forms Pro Customer Satisfaction](./media/service-template-apps-overview/forms-pro.png)](https://app.powerbi.com/groups/me/getapps/services/msfp.formsprocustomersatisfaction)
    :::column-end:::
:::row-end:::

## <a name="process"></a>Proces
Der er flere faser i den generelle proces for udvikling og indsendelse af et skabelonprogram. Nogle faser kan indeholde mere end én aktivitet samtidigt.


| Fase | Power BI Desktop |  |Power BI-tjenesten  |  |Partner Center  |
|---|--------|--|---------|---------|---------|
| **Et** | Udarbejd en datamodel og en rapport i en .pbix-fil |  | Opret et arbejdsområde. Importér en PBIX-fil. Opret et supplerende dashboard  |  | Registrer dig som partner |
| **To** |  |  | Opret en testpakke, og kør intern validering        |  | |
| **Tre** | |  | Hæv testpakken til præproduktion, så den kan valideres uden for din Power BI-lejer, og send den til AppSource  |  | Ved hjælp af din præproduktionspakke kan du oprette et tilbud på et Power BI-skabelonprogram og starte valideringsprocessen |
| **Fire** | |  | Hæv præprodukstionspakken til produktion |  | Gå live |

## <a name="before-you-begin"></a>Inden du starter

Du skal have tilladelse til at oprette et skabelonprogram. Du kan finde flere oplysninger på Power BI-administrationsportal, indstillingen Skabelonprogram. 

Hvis du vil udgive et skabelonprogram i Power BI-tjenesten og AppSource, skal du opfylde kravene til at [blive udgiver på Partnercenter](/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Overordnede trin

Her er de overordnede trin. 

1. [Gennemse kravene](#requirements), så du er sikker på, at du opfylder dem. 

2. Udarbejd en rapport i Power BI Desktop. Brug parametre, så du kan gemme den som en fil, som andre kan bruge. 

3. Opret et arbejdsområde til dit skabelonprogram i din lejer i Power BI-tjenesten (app.powerbi.com). 

4. Importér din .pbix-fil, og føj indhold såsom et dashboard til dit program. 

5. Opret en testpakke for selv at teste skabelonprogrammet i din organisation. 

6. Hæv testprogrammet til præproduktion for at indsende programmet til validering i AppSource og teste det uden for din egen lejer. 

7. Indsend indholdet til [Partnercenter](/azure/marketplace/partner-center-portal/create-power-bi-app-offer) med henblik på udgivelse. 

8. Gå "live" med dit tilbud i AppSource, og flyt programmet til produktion i Power BI.

9. Nu kan du begynde at udvikle den næste version i præproduktion i det samme arbejdsområde. 

## <a name="requirements"></a>Krav

Du skal have tilladelse til at oprette et skabelonprogram. Du kan finde flere oplysninger på Power BI[-administrationsportal, indstillingen Skabelonprogram](../admin/service-admin-portal.md#template-apps-settings).

Hvis du vil udgive et skabelonprogram i Power BI-tjenesten og AppSource, skal du opfylde kravene til at [blive udgiver på Partnercenter](/azure/marketplace/become-publisher).
 > [!NOTE] 
 > Indsendelser af skabelonprogrammer administreres i [Partnercenter](/azure/marketplace/partner-center-portal/create-power-bi-app-offer). Brug den samme Microsoft Developer Center-registreringskonto for at logge på. Du skal kun have én Microsoft-konto til dine tilbud i AppSource. Konti skal ikke være specifikke for individuelle tjenester eller tilbud.

## <a name="tips"></a>Tip! 

- Sørg for, at dit program indeholder eksempeldata, så alle kan komme i gang med et enkelt klik. 
- Undersøg omhyggeligt dit program ved at installere det i din lejer og i en sekundær lejer. Sørg for, at kunderne kun ser det, du gerne vil have, at de skal se. 
- Brug AppSource som din onlinebutik til at hoste dit program. På denne måde kan alle, der bruger Power BI, finde dit program. 
- Overvej at tilbyde mere end ét skabelonprogram til de enkelte unikke scenarier. 
- Aktivér datatilpasning, f.eks. understøttelse af brugerdefineret forbindelse og konfiguration af parametre af installationsprogrammet.

Du kan finde flere forslag under [Tip til udarbejdelse af skabelonprogrammer i Power BI](service-template-apps-tips.md).

## <a name="known-limitations"></a>Kendte begrænsninger

| Udvalgt | Kendt begrænsning |
|---------|---------|
|Indhold:  Datasæt   | Nøjagtigt ét datasæt skal være til stede. Der tillades kun datasæt, som er udarbejdet i Power BI Desktop (.pbix-filer). <br>Understøttes ikke: Datasæt fra andre skabelonprogrammer, datasæt på tværs af arbejdsområder, sideinddelte rapporter (.rdl-filer), Excel-projektmapper |
|Indhold: Dashboards | Felter i realtid tillades ikke (med andre ord, understøttes push- eller streamingdatasæt ikke) |
|Indhold: Dataflow | Understøttes ikke: Dataflow |
|Indhold fra filer | Der tillades kun PBIX-filer. <br>Understøttes ikke: .rdl-filer (sideinddelte rapporter), Excel-projektmapper   |
| Datakilder | Der tillades datakilder, som understøttes for planlagt dataopdatering i cloudmiljøet. <br>Understøttes ikke: <li>Direkte forbindelser (ingen Azure AS)</li> <li>Datakilder i det lokale miljø (personlige gateways og virksomhedsgateways understøttes ikke)</li> <li>Realtid (pushdatasæt understøttes ikke)</li> <li>Sammensatte modeller</li></ul> |
| Datasæt: på tværs af arbejdsområde | Datasæt på tværs af arbejdsområder er ikke tilladt  |
| Forespørgselsparametre | Understøttes ikke: Parametre af typen "Any" eller "Binary" blokerer opdateringshandlinger for datasæt |
| Power BI-visualiseringer | Der understøttes kun offentligt tilgængelige Power BI-visuals. [Power BI-visuals til organisationer](../developer/visuals/power-bi-custom-visuals-organization.md) understøttes ikke |
| Nationale cloudmiljøer | Skabelonapps er ikke tilgængelige i nationale cloudmiljøer |

## <a name="support"></a>Support
Hvis du vil have support under udvikling, skal du bruge [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Vi overvåger og administrerer aktivt dette websted. Kundehændelser finder hurtigt vej til det relevante team.

## <a name="next-steps"></a>Næste trin

[Opret et skabelonprogram](service-template-apps-create.md)