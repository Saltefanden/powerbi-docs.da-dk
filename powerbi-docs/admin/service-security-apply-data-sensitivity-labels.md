---
title: Sådan anvendes følsomhedsmærkater i Power BI
description: Få mere at vide om,hvordan du anvender følsomhedsmærkater i Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 12/09/2020
LocalizationGroup: Data from files
ms.openlocfilehash: a50a8c8514a4316f16a6a38647804aabf878d5ad
ms.sourcegitcommit: 1872a167d1e4d731ad00cf8a6d951c31aa54bcce
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/28/2021
ms.locfileid: "98925689"
---
# <a name="how-to-apply-sensitivity-labels-in-power-bi"></a>Sådan anvendes følsomhedsmærkater i Power BI

Følsomhedsmærkater for Microsoft Information Protection på dine rapporter, dashboards, datasæt, dataflow og .pbix-filer kan beskytte dit følsomme indhold mod uautoriseret dataadgang og -lækage. Hvis du forsyner dine data med følsomhedsmærkater korrekt, sikrer du, at det kun er godkendte personer, som kan få adgang til dine data. I denne artikel kan du se, hvordan du anvender følsomhedsmærkater i Power BI-tjenesten og Power BI Desktop.

Du kan finde flere oplysninger om følsomhedsmærkater i Power BI under [Følsomhedsmærkater i Power BI](service-security-sensitivity-label-overview.md).

## <a name="apply-sensitivity-labels-in-the-power-bi-service"></a>Anvend følsomhedsmærkater i Power BI-tjenesten

I Power BI-tjenesten kan du anvende følsomhedsmærkater på rapporter, dashboards, datasæt og dataflow.

Hvis du vil anvende følsomhedsmærkater i Power BI-tjenesten, skal du gøre følgende:
* Du skal have en [Power BI Pro-licens](./service-admin-purchasing-power-bi-pro.md) og redigeringstilladelser til det indhold, du vil forsyne med en mærkat.
* Følsomhedsmærkater skal være aktiveret for din organisation. Kontakt din Power BI-administrator, hvis du ikke er sikker på dette.
* Du skal tilhøre en sikkerhedsgruppe, der har tilladelse til at anvende følsomhedsmærkater, som beskrevet i [Aktivér følsomhedsmærkater i Power BI](./service-security-enable-data-sensitivity-labels.md).
* Alle [licenskrav og andre krav](./service-security-enable-data-sensitivity-labels.md#licensing-and-requirements) skal være opfyldt.

Når databeskyttelse er aktiveret på din lejer, vises følsomhedsmærkater i kolonnen med følsomhed i listevisningen af dashboards, rapporter, datasæt og dataflow.

![Aktivér følsomhedsmærkater](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-01.png)

**Sådan anvender eller ændrer du en følsomhedsmærkat på en rapport eller et dashboard**
1. Klik på **Flere indstillinger (...)** .
1. Vælg **Indstillinger**.
1. I ruden med indstillinger skal du vælge den relevante følsomhedsmærkat.
1. Gem indstillingerne.

Følgende billede illustrerer disse trin i en rapport

![Angiv følsomhedsmærkater](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-02.png)

**Sådan anvender eller ændrer du en følsomhedsmærkat på et datasæt eller dataflow**

1. Klik på **Flere indstillinger (...)** .
1. Vælg **Indstillinger**.
1. Vælg fanen Datasæt eller Dataflow, afhængigt af hvad der er relevant.
1. Udvid afsnittet om følsomhedsmærkater, og vælg den relevante følsomhedsmærkat.
1. Anvend indstillingerne.

De følgende to billeder illustrerer disse trin i et datasæt.

Vælg **Flere indstillinger (...)** og derefter **Indstillinger**.

![Åbn indstillinger for datasæt](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-05.png)

Åbn afsnittet med følsomhedsmærkater under fanen med indstillinger for datasættet, vælg den ønskede følsomhedsmærkat, og klik på **Anvend**.

![Vælg følsomhedsmærkat](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-06.png)

## <a name="apply-sensitivity-labels-in-power-bi-desktop-preview"></a>Anvend følsomhedsmærkater i Power BI Desktop (prøveversion)

Sådan bruger du følsomhedsmærkater i Power BI Desktop:
* Du skal have en [Power BI Pro-licens](./service-admin-purchasing-power-bi-pro.md).
* Følsomhedsmærkater skal være aktiveret for din organisation. Kontakt din Power BI-administrator, hvis du ikke er sikker på dette.
* Du skal tilhøre en sikkerhedsgruppe, der har tilladelse til at anvende følsomhedsmærkater, som beskrevet i [Aktivér følsomhedsmærkater i Power BI](./service-security-enable-data-sensitivity-labels.md).
* Alle [licenskrav og andre krav](./service-security-enable-data-sensitivity-labels.md#licensing-and-requirements) skal være opfyldt.
* Kontakten til prøveversionsfunktionen Information Protection i Power BI Desktop skal være slået til. Hvis du kan se knappen for følsomhed under fanen Hjem, er prøveversionsfunktionen slået til. Hvis du ikke kan se knappen, skal du gå til **Filer > Indstillinger > Indstillinger > Prøveversionsfunktioner** og markere afkrydsningsfeltet ud for **Information Protection**.

    ![Skærmbillede af siden med prøveversionsfunktioner i Desktop.](media/service-security-apply-data-sensitivity-labels/desktop-preview-features-page.png)

    >[!Important]
    >Efter du har slået prøveversionsfunktionen Information Protection til, skal du genstarte Desktop for at begynde at bruge følsomhedsmærkater.
    >
    >Hvis Desktop går ned, når du genstarter den, kan det skyldes, at computeren mangler den påkrævede version af Visual C++ Redistributable-runtimebiblioteket. Hvis du oplever et sådant nedbrud, kan du gå til [siden Microsoft Visual C++ 2015 Distributed Update 3 download](https://www.microsoft.com/download/details.aspx?id=53587) for at få oplysninger om, hvordan du downloader og installerer opdateringen. Når du har installeret opdateringen, kan du prøve at starte computeren igen.

    Hvis du ikke kan se indstillingen til prøveversionen Information Protection, kan prøveversionsfunktionen Information Protection være blokeret af din organisation. I dette tilfælde skal du kontakte din Power BI-administrator.

* Du skal være logget på.

Hvis du vil anvende en følsomhedsmærkat på den fil, du arbejder på, skal du klikke på knappen for følsomhed under fanen Hjem og vælge den ønskede mærkat i den viste menu.

![Skærmbillede af menuen for følsomhedsmærkat i Desktop.](media/service-security-apply-data-sensitivity-labels/sensitivity-label-menu-desktop.png)

>[!NOTE]
> Hvis du har slået funktionen for følsomhedsmærkater til under Prøveversionsfunktioner, men stadig ikke kan se knappen for følsomhed, kan det indikere, at du ikke har en passende licens, eller at du ikke er medlem af en sikkerhedsgruppe, der har tilladelse til at anvende følsomhedsmærkater, som beskrevet i [Aktivér følsomhedsmærkater i Power BI](./service-security-enable-data-sensitivity-labels.md).

Når du har anvendt mærkaten, bliver den synlig på statuslinjen.

![Skærmbillede af følsomhedsmærkat på statuslinjen i Desktop.](media/service-security-apply-data-sensitivity-labels/sensitivity-label-in-desktop-status-bar.png)

### <a name="sensitivity-labels-when-uploading-or-downloading-pbix-files-tofrom-the-service"></a>Følsomhedsmærkater i forbindelse med upload eller download af .pbix-filer til/fra tjenesten
* Når du publicerer en .pbix-fil til Power BI-tjenesten fra Desktop, eller når du uploader en .pbix-fil til Power BI-tjenesten direkte ved hjælp af **Hent data**, anvendes .pbix-filens mærkat både på rapporten og det datasæt, der oprettes i tjenesten. Hvis den .pbix-fil, du publicerer eller uploader, erstatter eksisterende ressourcer (dvs. ressourcer, der har det samme navn som .pbix-filen), overskriver .pbix-filens mærkat alle mærkater på disse ressourcer. Hvis. pbix-filen ikke er navngivet, bevares etiketterne i tjenesten.
* Hvis den rapport og det datasæt, der downloades, begge har mærkater, og hvis disse mærkater er forskellige, anvendes den mærkat, der er mest restriktiv af de to, når du bruger "Download til .pbix" i Power BI-tjenesten.

## <a name="remove-sensitivity-labels"></a>Fjern følsomhedsmærkater

### <a name="service"></a>Tjeneste
Hvis du vil fjerne en følsomhedsmærkat fra en rapport, et dashboard, et datasæt eller et dataflow, skal du følge [samme fremgangsmåde som for at anvende mærkater i Power BI-tjenesten](#apply-sensitivity-labels-in-the-power-bi-service), men vælge **(Ingen)** , når du bliver bedt om at klassificere dataenes følsomhed.

### <a name="desktop"></a>Desktop
Fjernelse af følsomhedsmærkaten fra en .pbix-fil, efter den er blevet gemt med mærkaten, understøttes ikke i Desktop i øjeblikket. I sådanne tilfælde anbefales det, at du publicerer filen i Power BI-tjenesten og derefter fjerner mærkaten i tjenesten fra den efterfølgende rapport og det efterfølgende datasæt.

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Se [Følsomhedsmærkater i Power BI](service-security-sensitivity-label-overview.md#limitations) for at få vist en liste over begrænsninger for følsomhedsmærkater i Power BI.

## <a name="next-steps"></a>Næste trin

Denne artikel indeholdt en beskrivelse af, hvordan du anvender følsomhedsmærkater i Power BI. Følgende artikler indeholder flere oplysninger om databeskyttelse i Power BI. 

* [Oversigt over følsomhedsmærkater i Power BI](./service-security-sensitivity-label-overview.md)
* [Aktivér følsomhedsmærkater i Power BI](./service-security-enable-data-sensitivity-labels.md)
* [Brug af Microsoft Cloud App Security-kontrolelementer i Power BI](./service-security-using-microsoft-cloud-app-security-controls.md)