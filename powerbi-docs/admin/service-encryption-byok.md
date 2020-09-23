---
title: Medbring dine egne krypteringsnøgler til Power BI
description: Få mere at vide om, hvordan du kan bruge dine egne krypteringsnøgler i Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/13/2020
LocalizationGroup: Premium
ms.openlocfilehash: 737a8df2f8f7e5d4da50259112ad1afd6ec2ecff
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90856823"
---
# <a name="bring-your-own-encryption-keys-for-power-bi"></a>Medbring dine egne krypteringsnøgler til Power BI

Power BI krypterer _inaktive_ og _igangværende_ data. Power BI bruger som standard Microsoft-administrerede nøgler til kryptering af dine data. Du kan også bruge dine egne nøgler i Power BI Premium til igangværende data, der importeres til et datasæt (se [Overvejelser vedrørende datakilde og -lager](#data-source-and-storage-considerations) for at få flere oplysninger). Denne fremgangsmåde beskrives ofte som _BYOK_ (Bring Your Own Key – medbring din egen nøgle).

## <a name="why-use-byok"></a>Hvorfor bruge BYOK?

BYOK gør det nemmere at imødekomme kravene til overholdelse af angivne standarder, som angiver nøgleordninger med cloudtjenesteudbyderen (i dette tilfælde Microsoft). Med BYOK skal du angive og styre krypteringsnøglerne til dine inaktive Power BI data på programniveau. Du har derfor kontrol over adgangen og kan tilbagekalde din organisations nøgler, hvis du beslutter at afslutte tjenesten. Når nøglerne tilbagekaldes, kan tjenesten ikke læse dataene inden for 30 minutter.

## <a name="data-source-and-storage-considerations"></a>Overvejelser vedrørende datakilde og -lager

Hvis du vil bruge BYOK, skal du uploade data til Power BI-tjenesten fra en PBIX-fil (Power BI Desktop). Du kan ikke bruge BYOK i følgende scenarier:

- Direkte Analysis Services-forbindelse
- Excel-projektmapper (medmindre data importeres først i Power BI Desktop)
- [Send datasæt via push](/rest/api/power-bi/pushdatasets)
- [Streamingdatasæt](../connect-data/service-real-time-streaming.md#set-up-your-real-time-streaming-dataset-in-power-bi)


BYOK anvendes kun på datasæt. Pushdatasæt, Excel-filer og CSV-filer, som brugere kan uploade til tjenesten, krypteres ikke med din egen nøgle. Brug følgende PowerShell-kommando til at identificere, hvilke artefakter der gemmes i dine arbejdsområder:

```PS C:\> Get-PowerBIWorkspace -Scope Organization -Include All```

> [!NOTE]
> Denne cmdlet kræver Power BI-administrationsmodulet v 1.0.840. Du kan se, hvilken version du har, ved at køre Get-InstalledModule -Name MicrosoftPowerBIMgmt. Installér den nyeste version ved at køre Install-Module -Name MicrosoftPowerBIMgmt. Du kan få flere oplysninger om Power BI-cmdletten og dens parametre i [PowerShell-cmdlet-modulet i Power BI](/powershell/power-bi/overview).

## <a name="configure-azure-key-vault"></a>Konfigurer Azure Key Vault

I dette afsnit finder du oplysninger om, hvordan du konfigurerer Azure Key Vault, der er et værktøj til sikker lagring og adgang til hemmelige oplysninger, som krypteringsnøgler. Du kan bruge en eksisterende key vault til at gemme krypteringsnøgler, eller du kan oprette en ny specielt til brug sammen med Power BI.

I vejledningen i dette afsnit antages det, at du har grundlæggende viden om Azure Key Vault. Du kan finde flere oplysninger under [Hvad er Azure Key Vault?](/azure/key-vault/key-vault-whatis). Konfigurer din nøgleboks på følgende måde:

1. Tilføj Power BI-tjenesten som en tjenesteprincipal til key vault med tilladelse til ombrydning og fjernelse af ombrydning.

1. Opret en RSA-nøgle med en længde på 4096-bit (eller brug en eksisterende nøgle af denne type) med tilladelse til ombrydning og fjernelse af ombrydning.

    > [!IMPORTANT]
    > Power BI BYOK understøtter kun RSA-nøgler med en længde på 4096-bit.

1. Anbefalet: Kontrollér, at din key vault har indstillingen til _blød sletning_ aktiveret.

### <a name="add-the-service-principal"></a>Tilføj tjenesteprincipalen

1. Under **Adgangspolitikker** i din key vault i Microsoft Azure-portal skal du vælge **Tilføj ny**.

1. Søg efter og vælg Microsoft.Azure.AnalysisServices under **Vælg principal**.

    > [!NOTE]
    > Hvis du ikke kan finde "Microsoft.Azure.AnalysisServices", skyldes det sandsynligvis, at det Azure-abonnement, der er tilknyttet din Azure Key Vault, aldrig har haft en Power BI-ressource tilknyttet. Prøv i stedet at søge efter følgende streng: 00000009-0000-0000-c000-000000000000.

1. Under **Key permissions** (Nøgletilladelser) skal du vælge **Unwrap Key** (Fjern ombrydning af nøgle) og **Wrap Key** (Ombryd nøgle).

    ![Komponenter i PBIX-fil](media/service-encryption-byok/service-principal.png)

1. Vælg **OK** og derefter **Gem**.

> [!NOTE]
> Hvis du vil tilbagekalde Power BI-adgangen til dine data i fremtiden, skal du fjerne adgangsrettighederne til denne tjenesteprincipal fra din Azure Key Vault.

### <a name="create-an-rsa-key"></a>Opret en RSA-nøgle

1. I din key vault under **Nøgler** skal du vælge **Generér/Importér**.

1. Vælg en **nøgletype** for RSA og en **RSA-nøglestørrelse** på 4096.

    ![Komponenter i PBIX-fil](media/service-encryption-byok/create-rsa-key.png)

1. Vælg **Opret**.

1. Under **Nøgler** skal du vælge den nøgle, du har oprettet.

1. Vælg GUID'et for den **aktuelle version** af nøglen.

1. Kontrollér, at **Wrap Key** (Ombryd nøgle) og **Unwrap Key** (Fjern ombrydning af nøgle) begge er markeret. Kopiér den **nøgleidentifikator**, der skal bruges, når du aktiverer BYOK i Power BI.

    ![Komponenter i PBIX-fil](media/service-encryption-byok/key-properties.png)

### <a name="soft-delete-option"></a>Indstilling til blød sletning

Vi anbefaler, at du aktiverer [blød sletning](/azure/key-vault/key-vault-ovw-soft-delete) i din key vault for at beskytte mod datatab i tilfælde af, at en nøgle – eller en key vault – ved et uheld bliver slettet. Du skal bruge [PowerShell til at aktivere egenskaben for "blød sletning"](/azure/key-vault/key-vault-soft-delete-powershell) i din key vault, fordi denne indstilling endnu ikke er tilgængelig fra Microsoft Azure-portalen.

Når Azure Key Vault er konfigureret korrekt, er du klar til at aktivere BYOK på din lejer.

## <a name="enable-byok-on-your-tenant"></a>Aktivér BYOK i din lejer

Du aktiverer BYOK på lejerniveau med [PowerShell](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Admin) ved først at registrere de krypteringsnøgler, du har oprettet og gemt i Azure Key Vault, i Power BI-lejeren. Derefter kan du tildele disse krypteringsnøgler til hver Premium-kapacitet til kryptering af indhold i kapaciteten.

### <a name="important-considerations"></a>Vigtige overvejelser

Før du aktiverer BYOK, skal du overveje følgende:

- På dette tidspunkt kan du ikke deaktivere BYOK, når funktionen er aktiveret. Afhængigt af, hvordan du angiver parametre for `Add-PowerBIEncryptionKey`, kan du styre, hvordan du kan bruge BYOK til en eller flere af dine kapaciteter. Du kan imidlertid ikke fortrydes registreringen af nøgler i din lejer. Du kan finde flere oplysninger under [Aktivér BYOK](#enable-byok).

- Du kan ikke _direkte_ flytte et arbejdsområde, der bruger BYOK, fra en dedikeret kapacitet i Power BI Premium til delt kapacitet. Du skal først flytte arbejdsområdet til en dedikeret kapacitet, der ikke har BYOK aktiveret.

- Hvis du flytter et arbejdsområde, der bruger BYOK fra en dedikeret kapacitet i Power BI Premium, til delt, vil rapporter og datasæt være utilgængelige, da de krypteres med nøglen. For at undgå denne situation skal du først flytte arbejdsområdet til en dedikeret kapacitet, der ikke har BYOK aktiveret.

### <a name="enable-byok"></a>Aktivér BYOK

Hvis du vil aktivere BYOK, skal du være lejeradministrator af Power BI-tjenesten og være logget på med cmdlet'en `Connect-PowerBIServiceAccount`. Brug derefter [`Add-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/Add-PowerBIEncryptionKey) til at aktivere BYOK som vist i følgende eksempel:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

Hvis du vil tilføje flere nøgler, skal du køre `Add-PowerBIEncryptionKey` med forskellige værdier for -`-Name` og `-KeyVaultKeyUri`. 

Cmdlet'en accepterer to switchparametre, der påvirker kryptering for aktuelle og fremtidige kapaciteter. Som standard er ingen af parametrene angivet:

- `-Activate`: Angiver, at denne nøgle bruges til alle eksisterende kapaciteter i lejeren, som ikke allerede er krypteret.

- `-Default`: Angiver, at denne nøgle nu er standard for hele lejeren. Når du opretter en ny kapacitet, arver kapaciteten denne nøgle.

> [!IMPORTANT]
> Hvis du angiver `-Default`, krypteres alle de kapaciteter, der er oprettet i din lejer herefter med den nøgle, du angiver (eller en opdateret standardnøgle). Du kan ikke fortryde standardhandlingen, så du mister muligheden for at oprette en Premium-kapacitet i din lejer, der ikke bruger BYOK.

Når du aktiverer BYOK på din lejer, kan du angive krypteringsnøglen for en eller flere kapaciteter i Power BI:

1. Brug [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity) til at hente kapacitetens id, der er påkrævet til næste trin.

    ```powershell
    Get-PowerBICapacity -Scope Individual
    ```

    Cmdlet'en returnerer output, der minder om følgende:

    ```
    Id              : xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    DisplayName     : Test Capacity
    Admins          : adam@sometestdomain.com
    Sku             : P1
    State           : Active
    UserAccessRight : Admin
    Region          : North Central US
    ```

1. Brug [`Set-PowerBICapacityEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/set-powerbicapacityencryptionkey) for at angive krypteringsnøglen:

    ```powershell
    Set-PowerBICapacityEncryptionKey -CapacityId xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -KeyName 'Contoso Sales'
    ```

Du kan styre, hvordan du bruger BYOK på tværs af din lejer. Hvis du f.eks. vil kryptere en enkelt kapacitet, skal du kalde `Add-PowerBIEncryptionKey` uden `-Activate` eller `-Default`. Kald derefter `Set-PowerBICapacityEncryptionKey` for den kapacitet, hvor du vil aktivere BYOK.

## <a name="manage-byok"></a>Administrer BYOK

Power BI omfatter yderligere cmdlet'er, der hjælpe med at administrere BYOK i din lejer:

- Brug [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity) til at få den nøgle, en kapacitet aktuelt bruger:

    ```powershell
    Get-PowerBICapacity -Scope Organization -ShowEncryptionKey
    ```

- Brug [`Get-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiencryptionkey) til at få den nøgle, din lejer aktuelt bruger:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- Brug [`Get-PowerBIWorkspaceEncryptionStatus`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiworkspaceencryptionstatus) til at se, om datasættene i et arbejdsområde er krypteret, og om deres krypteringsstatus er synkroniseret med arbejdsområdet:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Bemærk, at kryptering er aktiveret på kapacitetsniveau, men du får krypteringsstatus på datasætniveau for det angivne arbejdsområde.

- Brug [`Switch-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/switch-powerbiencryptionkey) at skifte (eller _rotere_) versionen af den nøgle, der bruges til kryptering. Cmdlet'en opdaterer blot `-KeyVaultKeyUri` for en nøgle `-Name`:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```



## <a name="next-steps"></a>Næste trin

* [PowerShell-cmdlet-modulet i Power BI](/powershell/power-bi/overview) 

* [Måder at dele dit arbejde på i Power BI](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtrer en rapport ved hjælp af parametre for forespørgselsstrengen i URL-adressen](../collaborate-share/service-url-filters.md)

* [Integrer med rapportwebdelen i SharePoint Online](../collaborate-share/service-embed-report-spo.md)

* [Publicer på internettet fra Power BI](../collaborate-share/service-publish-to-web.md)