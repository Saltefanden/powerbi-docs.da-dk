---
title: Sikkerhed på rækkeniveau (RLS) med Power BI
description: Sådan konfigurerer du sikkerhed på rækkeniveau for importerede datasæt og DirectQuery i Power BI-tjenesten.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/17/2020
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: f1358cbafa08c0dbb3790322c414d7a746386f0f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408567"
---
# <a name="row-level-security-rls-with-power-bi"></a>Sikkerhed på rækkeniveau (RLS) med Power BI

Sikkerhed på rækkeniveau (RLS) med Power BI kan bruges til at begrænse adgang til datakilder for bestemte brugere. Filtre begrænser adgangen til data på rækkeniveau, og du kan definere filtre inden for roller. I Power BI-tjenesten har medlemmer af et arbejdsområde adgang til datasæt i arbejdsområdet. Sikkerhed på rækkeniveau (RLS) begrænser ikke adgangen til data.

Du kan konfigurere sikkerhed på rækkeniveau for datamodeller, der er importeret til Power BI, med Power BI Desktop. Du kan også konfigurere sikkerhed på rækkeniveau for datasæt, der anvender DirectQuery, f.eks. SQL Server. Hvis du vil have Analysis Services- eller Azure Analysis Services-liveforbindelser, skal du konfigurere sikkerhed på rækkeniveau i modellen, ikke i Power BI Desktop. Sikkerhedsindstillingen vises ikke for datasæt med liveforbindelse.

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

Filtrering af sikkerhed på rækkeniveau bruger som standard envejsfiltre, uanset om relationerne er angivet til envejs eller tovejs. Du kan aktivere tovejskrydsfiltrering med sikkerhed på rækkeniveau manuelt ved at vælge relationen og markere afkrydsningsfeltet **Anvend sikkerhedsfilter i begge retninger**. Du skal markere dette afkrydsningsfelt, når du også har implementeret dynamisk sikkerhed på rækkeniveau på serverniveau, hvor sikkerhed på rækkeniveau er baseret på brugernavn eller logon-id.

Du kan finde flere oplysninger på [Tovejskrydsfiltrering ved hjælp af DirectQuery i Power BI Desktop](../transform-model/desktop-bidirectional-filtering.md) og den tekniske artikel [Sikring af modellen for tabellarisk BI-semantik](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

![Anvend sikkerhedsfilter](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Administrer sikkerheden for din model

Hvis du vil administrere sikkerheden for din datamodel, skal du benytte følgende fremgangsmåde:

1. Vælg menuen **Flere indstillinger** for et datasæt i Power BI-tjenesten. Denne menu vises, når du peger på navnet på et datasæt, uanset om du vælger det i navigationsmenuen eller på arbejdsområdesiden.

    ![Menuen Flere indstillinger i arbejdsområdet](media/service-admin-rls/dataset-leftnav-more-options.png)

    ![Menuen Flere indstillinger i navigationsmenuen](media/service-admin-rls/dataset-canvas-more-options.png)

1. Vælg **Sikkerhed**.

   ![Vælg sikkerhed i menuen Flere indstillinger](media/service-admin-rls/dataset-more-options-menu.png)

Hvis du vælger Sikkerhed, kommer du til RLS-siden, hvor du skal føje medlemmer til en rolle, du har oprettet i Power BI Desktop. Kun ejerne af datasættet får vist indstillingen Sikkerhed. Hvis datasættet er i en gruppe, kan kun administratorer af gruppen se sikkerhedsindstillingen.

Du kan kun oprette eller redigere roller i Power BI Desktop.

## <a name="working-with-members"></a>Arbejd med medlemmer

### <a name="add-members"></a>Tilføj medlemmer

Du kan føje et medlem til rollen ved at skrive mailadressen eller navnet på brugeren eller sikkerhedsgruppen. Du kan ikke tilføje grupper, der er oprettet i Power BI. Du kan tilføje medlemmer, som [ikke er fra organisationen](../guidance/whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners).

![Tilføj et medlem](media/service-admin-rls/rls-add-member.png)

Du kan også se, hvor mange medlemmer der er en del af rollen, ud fra tallet i parentes ud for rollenavnet eller ud for Medlemmer.

![Medlemmer af rollen](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Fjern medlemmer

Du kan fjerne medlemmer ved at vælge X ud for medlemmets navn. 

![Fjern medlem](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validering af rollen i Power BI-tjenesten

Du kan bekræfte, at den rolle, du har defineret, fungerer korrekt, ved at teste rollen.

1. Vælg **Flere indstillinger** (...) ud for rollen.
2. Vælg **Test data som rolle**

![Test som rolle](media/service-admin-rls/rls-test-role.png)

Derefter får du vist rapporter, der er tilgængelige for denne rolle. Dashboards vises ikke i denne visning. I sidehovedet vises den rolle, der anvendes.

![Vises nu som <rolle>](media/service-admin-rls/rls-test-role2.png)

Du kan teste andre roller eller en kombination af roller ved at vælge **Får nu vist som**.

![Test andre roller](media/service-admin-rls/rls-test-role3.png)

Du kan vælge at få vist data som en bestemt person, eller du kan vælge en kombination af tilgængelige roller for at bekræfte, om de fungerer.

Hvis du vil vende tilbage til normal visning, skal du vælge **Tilbage til sikkerhed på rækkeniveau**.

[!INCLUDE [include-short-name](../includes/rls-usernames.md)]

## <a name="using-rls-with-workspaces-in-power-bi"></a>Brug sikkerhed på rækkeniveau med arbejdsområder i Power BI

Hvis du publicerer din Power BI Desktop-rapport i et arbejdsområde i Power BI-tjenesten, anvendes rollerne for medlemmer, som kun har tilladelse til at få vist indhold. Du skal angive, at medlemmerne kan få vist Power BI-indhold, i indstillingerne for arbejdsområdet.

> [!WARNING]
> Hvis du har konfigureret arbejdsområdet, så medlemmerne har redigeringstilladelser, anvendes rollerne for sikkerhed på rækkeniveau ikke for dem. Brugerne kan se alle dataene.

![Gruppeindstillinger](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Næste trin

- [Begræns dataadgang med sikkerhed på rækkeniveau (RLS) for Power BI Desktop](../create-reports/desktop-rls.md)
- [Sikkerhed på rækkeniveau (RLS) i Power BI Desktop](../guidance/rls-guidance.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
