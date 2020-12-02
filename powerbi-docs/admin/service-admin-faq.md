---
title: Administration af Power BI – ofte stillede spørgsmål
description: Find svar på ofte stillede spørgsmål om tilmelding til Power BI, lejeradministration og andre administrative opgaver.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
LocalizationGroup: Administration
ms.openlocfilehash: 5a30ff855616eef04db4827b4a25cb0facb9db1b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413696"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administration af Power BI – ofte stillede spørgsmål

Denne artikel omhandler ofte stillede spørgsmål om Power BI-administration. Du kan finde en oversigt over Power BI-administration under [Hvad er Power BI-administration?](service-admin-administering-power-bi-in-your-organization.md)

## <a name="whats-in-this-article"></a>I denne artikel

### <a name="sign-up-for-power-bi-section"></a>Tilmeld dig afsnittet Power BI

* [Brug af PowerShell](#using-powershell)
* [Hvordan tilmelder brugerne sig Power BI?](#how-do-users-sign-up-for-power-bi)
* [Hvordan tilmelder individuelle brugere i min organisation sig?](#how-do-individual-users-in-my-organization-sign-up)
* [Hvordan kan jeg forhindre brugere i at tilmelde sig min eksisterende organisation?](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [Hvordan kan jeg tillade brugere at tilmelde sig min eksisterende organisation?](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [Hvordan kontrollerer jeg, om blokering er aktiveret i lejeren?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Hvordan kan jeg forhindre mine eksisterne brugere i at begynde at bruge Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Hvordan kan jeg tillade mine eksisterende brugere at tilmelde sig Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Administration af afsnittet Power BI

* [Hvordan vil dette ændre den måde, jeg administrerer identiteter for brugerne i organisationen på i dag?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Hvordan administrerer vi Power BI?](#how-do-we-manage-power-bi)
* [Hvad er processen til administration af en lejer, der er oprettet af Microsoft for brugerne?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Kan jeg styre den Microsoft 365-lejer, som brugerne føjes til, hvis jeg har flere domæner?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [Hvordan fjerner jeg Power BI for brugere, der allerede er tilmeldt?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Hvordan får jeg besked, når nye brugere tilmelder sig min lejer?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Er der andet jeg skal være forberedt på?](#are-there-any-additional-things-i-should-prepare-for)
* [Hvor findes min Power BI-lejer?](#where-is-my-power-bi-tenant-located)
* [Hvad er Power BI SLA (Serviceniveauaftale)?](#what-is-the-power-bi-sla)
* [Hvordan håndterer Power BI høj tilgængelighed og failover?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Sikkerhed i afsnittet Power BI

* [Opfylder Power BI nationale, regionale og branchespecifikke overholdelseskrav?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Hvordan fungerer sikkerhed i Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Tilmeld dig Power BI

### <a name="using-powershell"></a>Brug af PowerShell

Nogle af procedurerne i dette afsnit kræver Windows PowerShell-scripts. Hvis du ikke er bekendt med PowerShell, anbefaler vi [Introduktion til PowerShell](/powershell/scripting/overview). For at køre scripts skal du først installere den nyeste 64-bit version af [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/overview).

### <a name="how-do-users-sign-up-for-power-bi"></a>Hvordan tilmelder brugerne sig Power BI?

Som administrator af Microsoft 365 kan du tilmelde dig Power BI via [Power BI-webstedet](https://powerbi.microsoft.com) eller på siden [Køb tjenester](https://admin.microsoft.com/AdminPortal/Home#/catalog) i Microsoft 365 Administration. Når en administrator af Microsoft 365 tilmelder sig Power BI, kan vedkommende tildele brugerlicenser til brugere, der skal have adgang.

Individuelle brugere i din organisation kan derudover muligvis tilmelde sig Power BI på [Power BI-webstedet](https://powerbi.microsoft.com). Når en bruger i organisationen tilmelder sig Power BI, tildeler tjenesten automatisk brugeren en Power BI-licens. Du kan finde flere oplysninger under [Tilmelding til Power BI som enkeltperson](../fundamentals/service-self-service-signup-for-power-bi.md) og [Power BI-licenser i din organisation](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hvordan tilmelder individuelle brugere i min organisation sig?

Der er tre scenarier, der kan gøre sig gældende for brugere i din organisation:

* **Scenarie 1**: Din organisation har allerede et Microsoft 365-miljø, og brugeren, der tilmelder sig Power BI, har allerede en Microsoft 365-konto.
    I dette scenarie, hvor en bruger allerede har en arbejds- eller skolekonto i lejeren (f.eks. contoso.com), men endnu ikke har Power BI, aktiverer Microsoft blot planen for Power BI (gratis) for den pågældende konto. Brugeren får automatisk besked om, hvordan Power BI-tjenesten bruges.

* **Scenarie 2**: Din organisation har allerede et Microsoft 365-miljø, men brugeren, der tilmelder sig Power BI, har ikke en Microsoft 365-konto.
    I dette scenarie har brugeren en mailadresse på organisationens domæne (f.eks. contoso.com), men brugeren har endnu ikke en Microsoft 365-konto. I dette tilfælde kan brugeren tilmelde sig Power BI og får automatisk en konto. Denne handling giver brugeren adgang til Power BI-tjenesten. Hvis en medarbejder med navnet Nancy f.eks. bruger sin arbejdsmailadresse (såsom nancy@contoso.com) til at tilmelde sig, tilføjer Microsoft automatisk Nancy som bruger i Microsoft 365-miljøet for Contoso og aktiverer Power BI for den pågældende konto.

* **Scenarie 3**: Din organisation har ikke et Microsoft 365-miljø knyttet til dit maildomæne.
    Din organisation behøver ikke at udføre nogen administrative handlinger for at kunne nyde godt af Power BI. Tjenesten føjer brugere til en ny brugermappe, der udelukkende bruges i cloudmiljøet. Du kan dog også vælge at overtage lejeren som Global administrator i Microsoft 365 og administrere dem.

> [!IMPORTANT]
> Hvis organisationen har flere maildomæner, og du foretrækker, at alle mailadresseudvidelser er i den samme lejer, skal du føje alle mailadressedomæner til en Azure Active Directory-lejer, før nogen brugere tilmelder sig. Når du først har oprettet brugerne, er der er ikke en automatisk mekanisme, der kan flytte brugerne på tværs af lejere. Du kan finde flere oplysninger om denne proces under [Kan jeg styre den Microsoft 365-lejer, som brugerne føjes til, hvis jeg har flere domæner?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to) senere i denne artikel og [Føj et domæne til Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>Hvordan forhindrer jeg, at brugerne tilmelder sig min eksisterende Microsoft 365-lejer?

Som global administrator er der nogle trin, du kan udføre, for at forhindre, at brugerne tilmelder sig din eksisterende Microsoft 365-lejer. Hvis du blokerer adgangen, mislykkes brugernes forsøg på at tilmelde sig, og der vises en besked om, at de skal kontakte administratoren for deres organisation. Du behøver ikke at gentage denne proces, hvis du allerede har deaktiveret automatisk licensdistribution (f.eks. via Office 365 for Education til studerende, undervisere og ansatte).

Brug følgende PowerShell-script til at forhindre, at nye brugere tilmelder sig en administreret lejer. ([Få mere at vide om PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Blokering af adgangen forhindrer, at nye brugere i din organisation kan tilmelde sig Power BI. Brugere, der tilmelder sig Power BI før deaktivering af nye tilmeldinger, beholder deres licenser. Hvis du vil fjerne en bruger, skal du se [Hvordan fjerner jeg Power BI for brugere, der allerede er tilmeldt?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) senere i denne artikel.

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>Hvordan giver jeg brugerne tilladelse til at tilmelde sig min eksisterende Microsoft 365-lejer ?

Brug følgende PowerShell-script til at gøre det muligt for nye brugere at tilmelde sig en administreret lejer. ([Få mere at vide om PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Hvordan kontrollerer jeg, om blokering er aktiveret i lejeren?

Brug følgende PowerShell-script til at kontrollere indstillingerne. *AllowEmailVerifiedUsers* skal være falsk. ([Få mere at vide om PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hvordan kan jeg forhindre mine eksisterne brugere i at begynde at bruge Power BI?

Den Azure AD-indstilling, der styrer dette, er **AllowAdHocSubscriptions**. For de fleste lejere er denne indstilling angivet til *sand*, hvilket betyder, at den er aktiveret. Hvis du har fået Power BI via en partner, kan indstillingen være angivet til *falsk*, hvilket betyder, at den er deaktiveret.

Brug følgende PowerShell-script til at deaktivere ad hoc-abonnementer. ([Få mere at vide om PowerShell][1].)

1. Log på Azure Active Directory ved hjælp af dine legitimationsoplysninger til Microsoft 365. I den første linje i følgende PowerShell-script bliver du bedt om dine legitimationsoplysninger. Den anden linje opretter forbindelse til Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Skærmbillede af Azure Active Directory-logon via PowerShell.](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Når du logger på, skal du køre følgende kommando for at se, hvordan din lejer i øjeblikket er konfigureret.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Kør følgende kommando for at aktivere (`$true`) eller deaktivere (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Brug flaget **AllowAdHocSubscriptions** til at kontrollere flere brugeregenskaber i organisationen, herunder muligheden for at brugere kan tilmelde sig Azure Rights Management Service. Alle disse egenskaber påvirkes, hvis flaget ændres. Med indstillingen *falsk* kan brugerne stadig tilmelde sig en individuel Power BI Pro-prøveversion.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hvordan kan jeg tillade mine eksisterende brugere at tilmelde sig Power BI?

Hvis du vil tillade dine eksisterne brugere at tilmelde sig Power BI, skal du køre den kommando, der er angivet i det foregående spørgsmål, men send `$true` i stedet for `$false` i det sidste trin.

## <a name="administration-of-power-bi"></a>Administration af Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Hvordan vil dette ændre den måde, jeg administrerer identiteter for brugerne i organisationen på i dag?

Der er tre scenarier, der kan gøre sig gældende for brugere i din organisation:

* **Scenarie 1**: Hvis din organisation allerede har et eksisterende Microsoft 365-miljø, og alle brugerne i organisationen har en Microsoft 365-konto, sker der ingen ændring i den måde, du administrerer identiteter på.

* **Scenarie 2**: Hvis din organisation allerede har et eksisterende Microsoft 365-miljø, men det ikke er alle brugerne i organisationen, der har en Microsoft 365-konto, opretter vi en bruger i lejeren og tildeler licenser på baggrund af brugerens arbejds- eller skolemailadresse.

    Det betyder, at antallet af brugere, som du administrerer på et givent tidspunkt, stiger, efterhånden som brugerne i organisationen tilmelder sig tjenesten.

* **Scenarie 3**: Hvis din organisation ikke har et Microsoft 365-miljø, der er forbundet til dit maildomæne, sker der ingen ændring i den måde, du administrerer identiteter på.

    Tjenesten føjer brugere til en ny mappe, der kun findes i cloudmiljøet, som du kan vælge at overtage som Global administrator i Microsoft 365 Global og administrere dem.

### <a name="how-do-we-manage-power-bi"></a>Hvordan administrerer vi Power BI?

Power BI indeholder en Power BI-administrationsportal til brugere med rollen Global administrator i Microsoft 365 og brugere med rollen Administrator i Power BI-tjenesten. Hvis du vil bruge Power BI-administrationsportalen, skal du markere din konto som **Global administrator** i Microsoft 365 eller Azure Active Directory, eller nogen skal tildele rollen Administrator i Power BI-tjenesten til din brugerkonto. Få mere at vide under [Beskrivelse af rollen som Power BI-administrator](service-admin-role.md) og [Power BI-administrationsportalen](service-admin-portal.md). Portalen indeholder muligheden for at styre indstillingerne i hele lejeren, få vist brugsstatistikker for Power BI og et link til Microsoft 365-administrationscentret, hvor du kan administrere brugere og grupper.

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Hvad er processen til administration af en lejer, der er oprettet af Microsoft for brugerne?

Når en bruger via selvbetjening melder sig til en cloudtjeneste, som bruger Azure AD, føjer tjenesten brugeren til en ikke-administreret Azure AD-mappe, der er baseret på brugerens maildomæne. Du kan gøre krav på og administrere en lejer, som nogen har oprettet ved hjælp af en proces, der kaldes *administrationsovertagelse*. Få mere at vide under [Overtag en ikke-administreret mappe som administrator i Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover). Den form for overtagelse, du foretager, afhænger af, om der er en eksisterende administreret lejer knyttet til dit domæne:

* Power BI understøtter intern administratorovertagelse. Når du udfører en _intern_ administratorovertagelse af en ikke-administreret Azure-mappe, tilføjes du som global administrator af den ikke-administrerede mappe. Ingen brugere, domæner eller tjenesteplaner overføres til andre mapper, som du administrerer.

* Power BI understøtter ikke længere ekstern administratorovertagelse. Når du udfører en _ekstern_ administratorovertagelse af en ikke-administreret Azure-mappe, føjer du DNS-domænenavnet for den ikke-administrerede mappe til din administrerede Azure-mappe. Ekstern overtagelse medfører tab af adgang til alt Power BI-indhold på den oprindelige lejer, der ikke administreres. Power BI-rapporter skal publiceres igen i den nye lejer, og Power BI-dashboards og -programmer skal oprettes igen i den nye lejer.

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>Kan jeg styre den Microsoft 365-lejer, som brugerne føjes til, hvis jeg har flere domæner?

Hvis du ikke foretager dig noget, opretter tjenesten en lejer for hvert brugermaildomæne og underdomæne. Hvis du ønsker, at alle brugerne skal være i samme lejer uanset deres mailadresseudvidelser: Opret en destinationslejer i forvejen, eller brug en eksisterende lejer. Tilføj derefter alle eksisterende domæner og underdomæner, der skal konsolideres i den pågældende lejer. Alle brugerne med mailadresser, der slutter med de pågældende domæner og underdomæner, tilføjes automatisk i destinationslejeren, når de tilmelder sig.

> [!IMPORTANT]
> Når du først har oprettet brugerne, er der er ikke en automatisk mekanisme, der kan flytte brugerne på tværs af lejere. Hvis du vil have mere at vide om tilføjelse af domæner til en enkelt Microsoft 365-lejer, skal du se [Føj dine brugere og domæner til Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hvordan fjerner jeg Power BI for brugere, der allerede er tilmeldt?

Hvis en bruger er tilmeldt Power BI, men du ikke længere ønsker, at vedkommende skal have adgang til Power BI, kan du fjerne Power BI-licensen fra brugeren.

1. Gå til [Microsoft 365 Administration](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Vælg **Brugere** > **Aktive brugere** i navigationsruden.

1. Find den bruger, du vil fjerne licensen fra, og vælg derefter vedkommendes navn.

    Du kan administrere mange licenser for brugere. Gør dette ved at vælge mange brugere og derefter vælge **Rediger produktlicenser**.

1. Ud for **Produktlicenser** på siden med brugerdetaljer skal du vælge **Rediger**.

1. Afhængigt af hvilken licens der er gældende for brugerens konto, skal du angive enten **Power BI (gratis)** eller **Power BI Pro** til **Fra**.

1. Vælg **Gem**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Hvordan får jeg besked, når nye brugere slutter sig til min lejer?

Brugere, der har tilmeldt sig lejeren via selvbetjent logon, tildeles en unik licens, som du kan filtrere efter i din aktive brugerrude på administratordashboardet. Følg disse trin for at oprette denne nye visning.

1. Naviger til [Microsoft 365 Administration](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Vælg **Brugere** > **Aktive brugere** i navigationsruden.

1. I menuen **Visninger** skal du vælge **Tilføj brugerdefineret visning**.

1. Navngiv din nye visning. Under **Tildel produktlicens** vælger du herefter **Power BI (gratis)** eller **Power BI Pro**.

    Du kan kun have en licens pr. valgt visning. Hvis du har både **Power BI (gratis)** - og **Power BI Pro**-licenser i organisationen, kan du oprette to visninger.

1. Angiv alle de andre betingelser, du ønsker, og vælg derefter **Tilføj**.

1. Når du har oprettet den nye visning, er den tilgængelig fra menuen **Visninger**.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Er der andet jeg skal være forberedt på?

Du oplever måske en stigning i anmodninger om nulstilling af adgangskode. Få mere at vide om denne proces under [Nulstil en brugers adgangskode](/office365/admin/add-users/reset-passwords).

Du kan fjerne en bruger fra lejeren vha. standardprocessen i Microsoft 365 Administration. Men hvis brugeren stadig har en aktiv mailadresse fra organisationen, kan vedkommende tilmelde sig igen, medmindre du blokerer alle brugere fra at tilmelde sig.

### <a name="where-is-my-power-bi-tenant-located"></a>Hvor er min Power BI-lejer placeret?

Få mere at vide om, hvilket dataområde din Power BI-lejer befinder sig i, under [Hvor er min Power BI-lejer placeret?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Hvad er Power BI SLA?

Du kan finde oplysninger om Power BI SLA (Serviceniveauaftale) i artiklen [Licensvilkår og dokumentation](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) i afsnittet **Licenser** på webstedet Microsoft Licensing.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Hvordan håndterer Power BI høj tilgængelighed og failover?

Du kan finde oplysninger om høj tilgængelighed og failover under [Ofte stillede spørgsmål om høj tilgængelighed, failover og it-katastroferedskab i Power BI](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Sikkerhed i Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Opfylder Power BI nationale, regionale og branchespecifikke overholdelseskrav?

Få mere at vide om Power BI-overholdelse ved at se [Microsoft Center for sikkerhed og rettighedsadministration](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Hvordan fungerer sikkerhed i Power BI?

Microsoft har skabt Power BI med Microsoft 365 som grundlag, der igen er bygger videre på Azure-tjenester såsom Azure Active Directory. Se en oversigt over Power BI-arkitektur i [Sikkerhed i Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Næste trin

[Power BI-administrationsportal](service-admin-portal.md)  
[Beskrivelse af rollen som Power BI-administrator](service-admin-role.md)  
[Tilmelding via selvbetjening til Power BI](../fundamentals/service-self-service-signup-for-power-bi.md)  
[Køb Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Hvad er Power BI Premium?](service-premium-what-is.md)  
[Hvordan køber jeg Power BI Premium?](service-admin-premium-purchase.md)  
[Hvidbog om Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Administrer din gruppe i Power BI og Microsoft 365](../collaborate-share/service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Administration af arbejds- eller skolekonto](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Administration af Microsoft 365-gruppe](/office365/admin/email/create-edit-or-delete-a-security-group/)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

[1]: /powershell/scripting/overview