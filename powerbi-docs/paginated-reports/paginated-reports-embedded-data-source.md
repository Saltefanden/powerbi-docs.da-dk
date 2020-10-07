---
title: Integrerede datakilder for sideinddelte rapporter i Power BI-tjenesten
description: I denne artikel kan du læse om, hvordan du opretter og redigerer en integreret datakilde i en sideinddelt rapport i Power BI-tjenesten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 03/02/2020
ms.openlocfilehash: e44b81120ef5eb1d2a384aae4f2d149525c3b7b4
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91632497"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service"></a>Opret en integreret datakilde for sideinddelte rapporter i Power BI-tjenesten

I denne artikel kan du læse om, hvordan du opretter og redigerer en integreret datakilde for en sideinddelt rapport i Power BI-tjenesten. Du definerer en integreret datakilde i en enkelt rapport og bruger den kun i denne rapport. I øjeblikket skal sideinddelte rapporter, der er publiceret i Power BI-tjenesten, bruge integrerede datasæt og datakilder, og de kan oprette forbindelse til følgende datakilder:

- Azure Analysis Services
- Azure SQL Database og 
- Azure SQL Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

I forbindelse med følgende datakilder skal du bruge følgende indstilling for [SQL Server Analysis Services-forbindelse](../admin/service-premium-connect-tools.md):

- Power BI Premium-datasæt

Sideinddelte rapporter opretter forbindelse til datakilder i det lokale miljø via en [Power BI-gateway](../connect-data/service-gateway-onprem.md). Du kan konfigurere gatewayen, når du har publiceret rapporten til Power BI-tjenesten.

Se [Rapportdata i Power BI Report Builder](report-builder-data.md) for at få mere detaljerede oplysninger.

## <a name="create-an-embedded-data-source"></a>Opret en integreret datakilde
  
1. Åbn Microsoft Power BI Report Builder.

1. På værktøjslinjen i ruden Rapportdata skal du vælge **Ny** > **Datakilde**. Dialogboksen **Egenskaber for datakilde** åbnes.

   ![Ny datakilde](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
1. I tekstfeltet **Navn** skal du skrive et navn til datakilden eller acceptere standardværdien.  
  
1. Vælg **Brug en forbindelse, som er integreret i min rapport**.  
  
1. På listen **Vælg forbindelsestype** skal du vælge en datakildetype. 

1. Angiv en forbindelsesstreng ved hjælp af en af disse metoder:  
  
   - Skriv forbindelsesstrengen direkte i tekstfeltet **Forbindelsesstreng**. 
  
   - Vælg **Byg** for at åbne dialogboksen **Forbindelsesegenskaber** for den datakilde, du har valgt i trin 2.  
  
     Udfyld felterne i dialogboksen **Forbindelsesegenskaber**, så de passer til datakilden. Forbindelsesegenskaber omfatter typen af datakilde, navnet på datakilden og de legitimationsoplysninger, du bruger. Når du har angivet værdier i denne dialogboks, skal du vælge **Test forbindelse** for at bekræfte, at datakilden er tilgængelig, og at de legitimationsoplysninger, du har angivet, er korrekte.  
  
1. Vælg **Legitimationsoplysninger**.  
  
   Angiv de legitimationsoplysninger, der skal bruges til denne datakilde. Ejeren af datakilden vælger typen af legitimationsoplysninger, der understøttes. Du kan finde flere oplysninger i [Angiv legitimationsoplysninger og forbindelsesoplysninger til rapportdatakilder](/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources).
  
1. Vælg **OK**.  
  
   Datakilden vises i ruden Rapportdata.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Sideinddelte rapporter, der opretter forbindelse til Power BI-datasæt, følger reglerne for delte datasæt i Power BI med nogle mindre ændringer.  For at brugere kan få vist sideinddelte rapporter korrekt ved hjælp af Power BI-datasæt og for at sikre, at sikkerhed på rækkeniveau er aktiveret og gennemtvunget for dine seere, skal du følge disse regler:

### <a name="classic-apps-and-workspaces"></a>Klassiske apps og arbejdsområder

- .rdl i samme arbejdsområde som datasæt (samme ejer): Understøttet
- .rdl i andet arbejdsområde end datasæt (samme ejer): Understøttet
- Delt .rdl: Du skal have tildelt tilladelsen Læs til hver bruger, der får vist rapporten på datasætniveau
- Delt app: Du skal have tildelt tilladelsen Læs til hver bruger, der får vist rapporten på datasætniveau
- .rdl i samme arbejdsområde som datasæt (anden ejer): Understøttet
- .rdl i et andet arbejdsområde som datasæt (anden bruger): Du skal have tildelt tilladelsen Læs for hver bruger, der får vist rapporten på datasætniveau
- Sikkerhed på rækkeniveau: Du skal have tildelt tilladelsen Læs for hver bruger, der får vist rapporten på datasætniveau, for at få den håndhævet.

### <a name="new-experience-apps-and-workspaces"></a>Apps og arbejdsområder med den nye oplevelse

- .rdl i samme arbejdsområde som datasæt: Understøttet
- .rdl i andet arbejdsområde end datasæt (samme ejer): Understøttet
- Delt .rdl: Du skal have tildelt tilladelsen Læs til hver bruger, der får vist rapporten på datasætniveau
- Delt app: Du skal have tildelt tilladelsen Læs til hver bruger, der får vist rapporten på datasætniveau
- .rdl i samme arbejdsområde som datasæt (anden ejer) – understøttet
- .rdl i andet arbejdsområde end datasæt (anden ejer): Du skal have tildelt tilladelsen Læs til hver bruger, der får vist rapporten på datasætniveau
- Sikkerhed på rækkeniveau: Du skal have tildelt tilladelsen Læs for hver bruger, der får vist rapporten på datasætniveau, for at få den håndhævet

## <a name="next-steps"></a>Næste trin

- [Opret et integreret datasæt til en sideinddelt rapport i Power BI-tjenesten](paginated-reports-create-embedded-dataset.md)
- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)