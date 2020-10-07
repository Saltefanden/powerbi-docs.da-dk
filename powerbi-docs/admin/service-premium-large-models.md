---
title: Store modeller i Power BI Premium (prøveversion)
description: Funktionen Store modeller gør det muligt at øge størrelsen på datasæt i Power BI Premium til mere end 10 GB.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 03/03/2020
LocalizationGroup: Premium
ms.openlocfilehash: 3095cfbfd4ed1a965e0a54f1cee0907cb468170d
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/30/2020
ms.locfileid: "91598819"
---
# <a name="large-models-in-power-bi-premium-preview"></a>Store modeller i Power BI Premium (prøveversion)

I Power BI-datasæt kan der gemmes data i en højkomprimeret cache i hukommelsen for at optimere forespørgselsydeevnen og muliggøre hurtig brugerinteraktivitet på tværs af store datasæt. Funktionen Store modeller gør det muligt at øge størrelsen på datasæt i Power BI Premium til mere end 10 GB. Datasættets størrelse er i stedet begrænset af Power BI Premium-kapacitetens størrelse, som minder om, hvordan Azure Analysis Services fungerer i forbindelse med begrænsninger for modelstørrelser. Du kan finde flere oplysninger om kapacitetsstørrelser i Power BI Premium under Kapacitetsnoder. Du kan konfigurere store modeller for alle Premium P-SKU'er og integrerede A-SKU'er, men de fungerer kun sammen med [nye arbejdsområder](../collaborate-share/service-create-the-new-workspaces.md).

Store modeller påvirker ikke PBIX-uploadstørrelsen, der stadig er begrænset til 10 GB. I stedet øges datasæt til mere end 10 GB i tjenesten ved opdatering. Du kan bruge trinvis opdatering til at konfigurere et datasæt, så det bliver større end 10 GB.

## <a name="enable-large-models"></a>Aktivér store modeller

Følg disse trin for at oprette et datasæt, der øges til mere end 10 GB:

1. Opret et datasæt i Power BI Desktop, og konfigurer en [trinvis opdatering](service-premium-incremental-refresh.md).

1. Publicer datasættet til Power BI Premium-tjenesten.

1. Aktivér datasættet til store modeller ved at køre PowerShell-cmdlet'er nedenfor. Disse cmdlet'er får Power BI til at gemme datasættet i Azure Premium-filer og ikke gennemtvinge grænsen på 10 GB.

1. Kald en opdatering for at indlæse historiske data baseret på politikken for trinvis opdatering. Det kan tage et stykke tid at indlæse historikken ved den første opdatering. Efterfølgende opdateringer bør være hurtigere, da de er trinvise.

### <a name="powershell-cmdlets"></a>PowerShell-cmdlet'er

Aktivér datasættet til lagring i Premium-filer ved hjælp af PowerShell-cmdlet'er i den aktuelle version af store modeller. Du skal have administratorrettigheder til kapacitet og arbejdsområde for at køre PowerShell-cmdlet'er.

1. Find datasæt-id’et (GUID). Du kan se id'et i URL'en under datasætindstillingerne under fanen **Datasæt** for arbejdsområdet.

    ![GUID for datasæt](media/service-premium-large-models/dataset-guid.png)

1. Installér [MicrosoftPowerBIMgmt](/powershell/module/microsoftpowerbimgmt.data/)-modulet fra en PowerShell-administratorprompt.

    ```powershell
    Install-Module -Name MicrosoftPowerBIMgmt
    ```

1. Kør følgende cmdlet'er for at logge på og kontrollere lagringstilstanden for datasættet.

    ```powershell
    Login-PowerBIServiceAccount

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    Svaret skal være følgende. Lagringstilstanden er ABF (Analysis Services-sikkerhedskopifil), som er standard.

    ```
    Id                   StorageMode

    --                   -----------

    <Dataset ID>         Abf
    ```

1. Kør følgende cmdlet'er for at indstille lagringstilstanden til Premium-filer og kontrollere den. Det kan tage et par sekunder at konvertere til Premium-filer.

    ```powershell
    Set-PowerBIDataset -Id <Dataset ID> -TargetStorageMode PremiumFiles

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    Svaret skal være følgende. Lagringstilstanden er nu angivet til Premium-filer.

    ```
    Id                   StorageMode
    
    --                   -----------
    
    <Dataset ID>         PremiumFiles
    ```

Du kan kontrollere status for datasætkonvertering til og fra Premium-filer ved hjælp af cmdlet'en [Get-PowerBIWorkspaceMigrationStatus](/powershell/module/microsoftpowerbimgmt.workspaces/get-powerbiworkspacemigrationstatus).

## <a name="dataset-eviction"></a>Fjernelse af datasæt

Power BI bruger dynamisk hukommelsesadministration til at fjerne inaktive datasæt fra hukommelsen. Power BI fjerner datasæt, så der kan indlæses andre datasæt til at håndtering af brugerforespørgsler. Administration af dynamisk hukommelse giver mulighed for, at summen af datasætstørrelser bliver betydeligt større end den hukommelse, der er tilgængelig på kapaciteten, men et enkelt datasæt skal kunne være i hukommelsen. Du finder flere oplysninger om administration af dynamisk hukommelse under [Sådan fungerer kapaciteter](service-premium-what-is.md#how-capacities-function).

Du bør overveje virkningen af fjernelse på store modeller. På trods af hurtig indlæsning af datasæt kan der stadig være en mærkbar forsinkelse for brugere, hvis de skal vente på, at store fjernede datasæt genindlæses. Derfor anbefales funktionen Store modeller i sin nuværende form primært til kapaciteter, der er dedikeret til virksomheds-BI-krav frem for kapaciteter, der er blandet med selvbetjenings-BI-krav. Der er mindre sandsynlighed for, at kapaciteter, der er dedikeret til virksomheds-BI-krav, udløser fjernelse og behov for at genindlæse datasæt. Kapaciteter for selvbetjenings-BI kan på den anden side kan have mange små datasæt, der oftere indlæses i og uden for hukommelsen.

## <a name="checking-dataset-size"></a>Kontrol af datasætstørrelsen

Når du har indlæst historiske data, kan du bruge [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) via [XMLA-slutpunktet](service-premium-connect-tools.md) til at kontrollere størrelsen på det anslåede datasæt i vinduet modelegenskaber.

![Anslået datasætstørrelse](media/service-premium-large-models/estimated-dataset-size.png)

Du kan også kontrollere størrelsen på datasættet ved at køre følgende DMV-forespørgsler fra SQL Server Management Studio. Læg kolonnerne DICTIONARY\_SIZE og USED\_SIZE fra outputtet sammen for at se datasætstørrelsen i byte.

```sql
SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMNS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum DICTIONARY_SIZE (bytes)

SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum USED_SIZE (bytes)
```

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Vær opmærksom på følgende begrænsninger, når du bruger store modeller:

- **Multi-Geo-understøttelse**: Datasæt, der er aktiveret til Premium-filer, mislykkes på kapaciteter, hvor [Multi-Geo](service-admin-premium-multi-geo.md) også er aktiveret.

- **Download Power BI Desktop**: Hvis et datasæt er gemt i Premium-filer, mislykkes [download som en. pbix](../create-reports/service-export-to-pbix.md)-fil.
- **Understøttede områder**: Store modeller understøttes i alle Azure-områder, der understøtter Premium files Storage. Hvis du vil vide mere, skal du se [Produkter, der er tilgængelige efter område](https://azure.microsoft.com/global-infrastructure/services/?products=storage), og se tabellen i det følgende afsnit.


## <a name="availability-in-regions"></a>Tilgængelighed efter område

Store modeller i Power BI er kun tilgængelige i visse Azure-områder, der understøtter [Azure Premium File Storage](/azure/storage/files/storage-files-planning#storage-tiers).

Følgende liste indeholder områder, hvor store modeller i Power BI er tilgængelige. Det er kun de områder, der er på følgende liste, hvor store modeller understøttes:


|Azure-område  |Forkortelse for Azure-område  |
|---------|---------|
|Det østlige Australien     | australiaeast        |
|Det sydøstlige Australien     | Det sydøstlige Australien        |
|Det centrale USA     | Det centrale USA        |
|Det østlige Asien     | eastasia        |
|Det østlige USA     | Det østlige USA        |
|Det østlige USA 2     | eastus2        |
|Det østlige Japan     | Det østlige Japan        |
|Det vestlige Japan     | japanwest        |
|Det centrale Sydkorea     | koreacentral        |
|Det sydlige Sydkorea     | koreasouth        |
|Det nordcentrale USA     | northcentralus        |
|Det nordlige Europa     | northeurope        |
|Det sydcentrale USA     | Det sydcentrale USA        |
|Det sydøstlige Asien     | Det sydøstlige Asien        |
|Det sydlige Storbritannien     | uksouth        |
|Det vestlige Storbritannien     | ukwest        |
|Det vestlige Europa     | Det vestlige Europa        |
|Det vestlige USA     | westus        |
|Det vestlige USA 2     | Det vestlige USA 2        |



## <a name="next-steps"></a>Næste trin

Følgende links indeholder oplysninger, der kan være nyttige til at arbejde med store modeller:

* [Azure Premium Files Storage](/azure/storage/files/storage-files-planning#storage-tiers)
* [Konfigurer understøttelse af Multi-Geo til Power BI Premium](service-admin-premium-multi-geo.md)
* [Medbring dine egne krypteringsnøgler til Power BI](service-encryption-byok.md)
* [Sådan fungerer kapaciteter](service-premium-what-is.md#how-capacities-function)
* [Trinvis opdatering](service-premium-incremental-refresh.md)