---
title: URL-parametre i sideinddelte rapporter – Power BI Report Builder
description: Få mere at vide om, hvordan du sender kommandoer til sideinddelte rapporter i Power BI ved at føje en parameter til en URL-adresse, som du kan inkludere i en mail eller på en webside.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 09/09/2020
ms.openlocfilehash: 0816ba6f3ff606a73c835ac71af66655fd49acfd
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298053"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>URL-parametre i sideinddelte rapporter i Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Du kan sende kommandoer til sideinddelte rapporter i Power BI ved at føje en parameter til en URL-adresse. For eksempel har du måske fået vist rapporten ved hjælp af et bestemt sæt rapportparameterværdier. Du kan indkapsle disse oplysninger i URL-adressen ved hjælp af foruddefinerede URL-adgangsparametre. Du kan desuden tilpasse, hvordan Power BI behandler rapporten, ved at integrere parametre for gengivelsesformater eller for udseendet og funktionaliteten af rapportværktøjslinjen. Du kan derefter indsætte denne URL-adresse direkte i en mail eller på en webside, så andre kan opleve din rapport på samme måde i browseren. 

Her er de handlinger, du kan udføre via URL-adgangsparametre: 

- Sende rapportparametre til en rapport. 
- Starte eksporten af rapportindholdet i et understøttet filformat. 
- Skjule eller vise ruden med parametre. 
- Angive indstillingen DeviceInfo. 

Du kan finde en komplet liste over de kommandoer og indstillinger, der er tilgængelige via URL-adgang, under  [Reference til URL-adgang](#url-access-parameter-reference) senere i denne artikel. 

## <a name="url-access-concepts"></a>Begreber til URL-adgang 

URL-anmodninger til Power BI indeholder parametre, der behandles af tjenesten. Den måde, tjenesten håndterer URL-anmodninger på, afhænger af parametre, parameterpræfikser og de typer elementer, der er inkluderet i URL-adressen. URL-funktionalitet i sideinddelte rapporter er kompatibel med de fleste browsere og programmer, der understøtter URL-standardadresser. 

## <a name="url-access-syntax"></a>URL-adgangssyntaks 

URL-anmodninger kan indeholde flere parametre, der er angivet i en vilkårlig rækkefølge. Parametre skal være adskilt af et &-tegn. Navn og værdipar adskilles med et lighedstegn (=). Eksempel:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>syntaksbeskrivelse 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Webtjenestens URL-adresse for Power BI-lejeren. Eksempel: 

**&** Bruges til at adskille navne og værdipar for URL-adgangsparametre.

**præfiks** Et præfiks for URL-parameteren (f.eks. rp: elle rdl:), der angiver en handling i Power BI-tjenesten. 

> [!NOTE]
> Rapportparametre kræver et parameterpræfiks, og der skelnes mellem store og små bogstaver. 

**parameter** Navnet på parameteren. 

### <a name="value"></a>værdi 

URL-tekst, der svarer til værdien af den parameter, der bruges. 

Du kan finde eksempler på, hvordan du videregiver rapportparametre for URL-adressen i  [Videregiv en rapportparameter i en URL-adresse](report-builder-url-pass-parameters.md).

## <a name="url-access-parameter-reference"></a>Reference til URL-adgangsparameter

Du kan bruge følgende parametre som en del af en URL-adresse til at konfigurere udseendet og funktionaliteten af dine sideinddelte rapporter i Power BI. De mest almindelige parametre er angivet i dette afsnit. Der skelnes mellem store og små bogstaver i parametre, og de starter med parameterpræfikset `rdl:` , hvis de er relateret til outputformatet.  

### <a name="report-commands-rdl"></a>Rapportkommandoer (`rdl:`) 

**Eksportformat** Angiver det format, der skal gengives og eksporteres i en rapport.

Eksempel: rdl:format=PDF

Tilgængelige værdier er:
 
- PPTX (PowerPoint)
- MHTML 
- BILLEDE 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- ACCESSIBLEPDF (PDF)
- XML 

**Rapportvisning** angiver den type visning, der skal bruges til at vise rapporten.

-   rdl:reportView

    - 'Interactive' (standard): Indlæs rapporten i interaktiv tilstand.
    - 'pageView': Indlæs rapporten i sidevisningstilstand.

**Parameterpanel** angiver, om parameterpanelet er lukket eller åbent, når rapporten indlæses, eller er fuldstændig skjult.

-   rdl:parameterPanel

    - 'collapsed': Indlæs rapporten med parameterpanelet lukket. Parameterknappen er aktiveret, så brugerne kan klikke på knappen for at udvide.
    - 'hidden': Indlæs rapporten med parameterpanelet lukket og parameterknappen deaktiveret.
    - 'expanded' (standard): Indlæs rapporten med parameterpanelet åbent og parameterknappen aktiveret.

**Enhedsoplysninger** Du kan angive yderligere outputparametre for følgende eksportformater. 

PDF/ACCESSIBLEPDF:

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginBottom=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageHeight=decimal(in)
    - rdl:StartPage=integer
    
CSV:

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - RDL: UseFormattedValues = true/false
    
WORDOPENXML (WORD):

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL):

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint):
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginBottom=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML:

- rdl:XSLT=string
- rdl:MIMEType=string
- RDL: UseFormattedValues = true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:Schema=true/false

**Åbn link i samme browservindue** Du kan føje 'rdl:targetSameWindow=true' til URL-adressen til links i din rapport for at give Power BI mulighed for at åbne dette link i det samme browservindue. Hvis du vil have oplysninger om, hvordan du føjer links til en rapport, skal du se [Føj et link til en URL-adresse](/sql/reporting-services/report-design/add-a-hyperlink-to-a-url-report-builder-and-ssrs) i dokumentationen til SQL Server Reporting Services.

## <a name="next-steps"></a>Næste trin

- [Videregiv en rapportparameter i en URL-adresse til en sideinddelt rapport i Power BI](report-builder-url-pass-parameters.md)
- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)