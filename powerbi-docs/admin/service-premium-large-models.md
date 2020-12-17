---
title: Store datasæt i Power BI Premium
description: Med Lagerformat af store datasæt kan størrelsen af datasæt i Power BI Premium øges til mere end 10 GB.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 12/10/2020
ms.custom: references_regions
LocalizationGroup: Premium
ms.openlocfilehash: 7256e17f561aa79d63b7fefd268df560903de6b2
ms.sourcegitcommit: 772c65b7b440ab082510bf3f64b871d19139d451
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/12/2020
ms.locfileid: "97353099"
---
# <a name="large-datasets-in-power-bi-premium"></a>Store datasæt i Power BI Premium

Power BI-datasæt kan gemme data i en yderst komprimeret cache i hukommelsen, hvilket sikrer en optimeret forespørgselsydeevne og muliggør hurtig brugerinteraktivitet. Med Premium-kapaciteter muliggøres store datasæt over standardgrænsen på 10 GB via indstillingen **Lagerformat af store datasæt**. Når funktionen er aktiveret, begrænses størrelsen af datasættet af størrelsen af Premium-*kapaciteten* eller den maksimale størrelse, som administratoren har angivet.

Store datasæt er mulige for alle Premium P SKU'er og integrerede A SKU'er. Grænsen for størrelsen af store datasæt i Premium kan sammenlignes med Azure Analysis Services, hvad angår begrænsninger for størrelsen af datamodellen.

Indstillingen Lagerformat af store datasæt kræves, før størrelsen af datasæt kan øges til mere end 10 GB, men den giver også yderligere fordele. Hvis du har planer om at bruge værktøjer, der er baseret på XMLA-slutpunkter, til skrivehandlinger for datasættet, skal du sørge for at aktivere indstillingen, selv for datasæt, som du ikke nødvendigvis ville karakterisere som et *stort* datasæt. Når indstillingen er aktiveret, kan Lagerformat af store datasæt forbedre ydeevnen af XMLA-skrivehandlinger.

Store datasæt i tjenesten påvirker ikke størrelsen af upload af Power BI Desktop-modeller, som stadig er begrænset til 10 GB. Datasæt kan i stedet øges til mere end 10 GB i tjenesten i forbindelse med opdatering.

## <a name="enable-large-datasets"></a>Muliggør store datasæt

Disse trin indeholder en beskrivelse af, hvordan du muliggør store datasæt for en ny model, der er publiceret i tjenesten. Det er kun trin tre, der er nødvendig til eksisterende datasæt.

1. Opret en model i Power BI Desktop. Hvis dit datasæt bliver større og gradvist bruger mere hukommelse, skal du konfigurere [Trinvis opdatering](service-premium-incremental-refresh.md).

1. Publicer modellen til tjenesten som et datasæt.

1. I tjenesten > datasæt > **Indstillinger** skal du udvide **Lagerformat af store datasæt**, sætte skyderen til **On** og derefter klikke på **Anvend**.

    :::image type="content" source="media/service-premium-large-models/enable-large-dataset.png" alt-text="Skyder til muliggørelse af store datasæt":::

1. Kald en opdatering for at indlæse historiske data baseret på politikken for trinvis opdatering. Det kan tage et stykke tid at indlæse historikken ved den første opdatering. Efterfølgende opdateringer bør være hurtigere, afhængigt af din politik for trinvis opdatering.

## <a name="set-default-storage-format"></a>Angiv standardlagerformat

Alle nye datasæt, der oprettes i et arbejdsområde, som er tildelt en Premium-kapacitet, kan som standard have indstillingen Lagerformat af store datasæt aktiveret.

1. Klik på **Indstillinger** > **Premium** i arbejdsområdet.

1. Under **Standardlagerformat** skal du vælge **Lagerformat af store datasæt** og derefter klikke på **Gem**.

    :::image type="content" source="media/service-premium-large-models/default-storage-format.png" alt-text="Aktivér standardlagerformat":::

### <a name="enable-with-powershell"></a>Aktivér med PowerShell

Du kan også aktivere indstillingen Lagerformat af store datasæt ved hjælp af PowerShell. Du skal have administratorrettigheder til kapacitet og arbejdsområde for at køre PowerShell-cmdlet'er.

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

1. Kør følgende cmdletter for at angive lagertilstanden. Det kan tage et par sekunder at konvertere til Premium-filer.

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

Vær opmærksom på følgende begrænsninger, når du bruger store datasæt:

- **Nye arbejdsområder er påkrævet**: Store datasæt fungerer kun sammen med [Nye arbejdsområder](../collaborate-share/service-create-the-new-workspaces.md).

- **Download Power BI Desktop**: Hvis et datasæt er gemt i Premium-filer, mislykkes [download som en. pbix](../create-reports/service-export-to-pbix.md)-fil.
- **Understøttede områder**: Store datasæt understøttes i alle Azure-områder, der understøtter Premium File Storage. Hvis du vil vide mere, skal du se [Produkter, der er tilgængelige efter område](https://azure.microsoft.com/global-infrastructure/services/?products=storage), og se tabellen i det følgende afsnit.

- **Angivelse af den maksimale størrelse af datasættet**: Maksimal størrelse af datasættet kan angives af administratorer. Maksimumværdien kan angives fra 0,1 GB og op til den maksimale kapacitet af SKU'en.

## <a name="region-availability"></a>Områdetilgængelighed

Store datasæt i Power BI er kun tilgængelige i bestemte Azure-områder, der understøtter [Azure Premium File Storage](/azure/storage/files/storage-files-planning#storage-tiers).

Følgende liste indeholder områder, hvor store datasæt i Power BI er tilgængelige. Det er kun de områder, der er på følgende liste, hvor store modeller understøttes:

|Azure-område  |Forkortelse for Azure-område  |
|---------|---------|
|Det østlige Australien     | australiaeast        |
|Det sydøstlige Australien     | Det sydøstlige Australien        |
|Det østlige Canada     | canadaeast        |
|Det centrale Canada     | canadacentral        |
|Det centrale Indien     | Det centrale Indien        |
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
|Det vestlige Indien     | westindia        |
|Det vestlige USA     | westus        |
|Det vestlige USA 2     | Det vestlige USA 2        |

## <a name="next-steps"></a>Næste trin

Følgende links indeholder oplysninger, der kan være nyttige til at arbejde med store modeller:

* [Azure Premium Files Storage](/azure/storage/files/storage-files-planning#storage-tiers)
* [Konfigurer understøttelse af Multi-Geo til Power BI Premium](service-admin-premium-multi-geo.md)
* [Medbring dine egne krypteringsnøgler til Power BI](service-encryption-byok.md)
* [Sådan fungerer kapaciteter](service-premium-what-is.md#how-capacities-function)
* [Trinvis opdatering](service-premium-incremental-refresh.md)

Power BI har introduceret Power BI Premium Gen2 som et prøveversionstilbud, der forbedrer Power BI Premium-oplevelsen på følgende områder:
* Ydeevne
* Licens pr. bruger
* Større skalering
* Forbedrede målepunkter
* Automatisk skalering
* Reducerede administrationsomkostninger

Du kan finde flere oplysninger om Power BI Premium Gen2 under [Power BI-Premium – Generation 2 (prøveversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).
