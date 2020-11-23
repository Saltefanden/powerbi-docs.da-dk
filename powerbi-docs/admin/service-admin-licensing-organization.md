---
title: Power BI-licenser for brugere i din organisation
description: Oversigt over de forskellige brugerlicenstyper, der er tilgængelige i Power BI, og hvordan administratorer køber og administrerer licenser for brugere i deres organisation.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/11/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 46d620df1140d4fea8ffb9b4bdb9dd292e3659cd
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512280"
---
# <a name="licensing-the-power-bi-service-for-users-in-your-organization"></a>Licens til Power BI-tjenesten for brugere i din organisation

Det, en bruger kan gøre i Power BI-tjenesten, afhænger af den type af licens pr. bruger, som vedkommende har. Det adgangsniveau, som brugeren får gennem sin licens, afhænger af, om det arbejdsområde, der oprettes adgang til, er et Premium-arbejdsområde. Alle brugere af Power BI-tjenesten skal have en licens.

Brugerne kan få en licens på to måder. Brugerne kan få deres egen gratis licens eller en Pro- eller Premium pr. bruger-licens ved hjælp af funktionaliteten til tilmelding via selvbetjening og deres arbejds- eller skolekonto. Eller administratorer kan få en Power BI-licens og tildele licenser til brugere.

I denne artikel fokuseres der på køb af tjenester og licenser pr. bruger set fra en administrators perspektiv. Du kan finde flere oplysninger om, hvordan brugerne kan få deres egne licenser, under [Tilmelding til Power BI som enkeltperson](../fundamentals/service-self-service-signup-for-power-bi.md).

## <a name="who-can-purchase-and-assign-licenses"></a>Hvem kan købe og tildele licenser?

Du skal have tildelt en administratorrolle for at kunne købe eller tildele licenser for din organisation. Administratorroller tildeles ved hjælp af Azure Active Directory Administration eller Microsoft 365 Administration. I følgende tabel kan du se, hvilken rolle der kræves for at udføre opgaver relateret til køb og licenser. Du kan finde flere oplysninger om administratorroller i Azure Active Directory under [Få vist og tildel administratorroller i Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal). Hvis du vil have mere at vide om administratorroller i Microsoft 365, herunder bedste praksis, skal du se [Om administratorroller](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

| Hvem kan købe tjenester og licenser? | Hvem kan administrere brugerlicenser? |
| --------------- | --------------- |
| Faktureringsadministrator | Licensadministrator |
| Global administrator | Brugeradministrator |
|  | Global administrator |

Disse roller administrerer organisationen. Du kan finde flere oplysninger om administratorroller i Power BI-tjenesten under [Beskrivelse af administratorroller i Power BI](service-admin-role.md).

## <a name="get-power-bi-for-your-organization"></a>Få Power BI til din organisation

Du kan finde oplysninger om prisfastsættelse under [Prisfastsættelse og produktsammenligning](https://powerbi.microsoft.com/pricing/).

En global administrator eller en faktureringsadministrator kan tilmelde sig Power BI-tjenesten og købe licenser til brugerne i organisationen. Hvis du ikke er klar til at købe, skal du vælge Power BI Pro (prøveversion). Du får 25 licenser, som du kan bruge i én måned. Du kan se en trinvis vejledning til, hvordan du tilmelder dig, under [Få et Power BI-abonnement til din organisation](service-admin-org-subscription.md).

## <a name="about-self-service-sign-up"></a>Om tilmelding via selvbetjening

De enkelte brugere kan få deres egen Power BI-licens ved at tilmelde sig med deres arbejds- eller skolekonto. Med en gratis licens kan brugerne udforske Power BI med henblik på personlig dataanalyse og visualisering ved hjælp af Mit arbejdsområde, men de kan ikke dele med andre brugere. Der kræves en Power BI Pro-licens for at dele indhold. En Power BI Premium-licens låser op for adgang til en række forskellige funktioner og indholdstyper, der kun er tilgængelige via Premium. En Premium pr. bruger-licens kan begrænse adgangen til disse funktioner udelukkende til andre brugere med Premium pr. bruger-licens, og kapacitetsbaseret Premium-licens giver brugere med Free-licens adgang til indhold, mens det kun er brugere med en Pro-licens, der kan oprette indhold. Brugerne kan opgradere deres licenstype til Pro eller tilmelde sig Pro direkte, hvis organisationen bruger det kommercielle cloudmiljø. Direkte køb af eller opgradering til Pro er ikke tilgængelig til uddannelsesinstitutioner eller organisationer, der er udrullet i cloudmiljøerne Azure Government, Azure Tyskland eller Azure China 21Vianet.

Hvis du ikke vil have, at brugerne i din organisation bruger tilmelding via selvbetjening, skal du se [Aktivér eller deaktiver tilmelding via selvbetjening](service-admin-disable-self-service.md) for at få mere at vide om, hvordan du slår det fra.

Når du deaktiverer tilmelding via selvbetjening, kan brugerne ikke udforske Power BI med henblik på datavisualisering og -analyse. Hvis du blokerer individuel tilmelding, kan det være en god idé at anskaffe Power BI (gratis)-licenser til din organisation og tildele dem til alle brugere. Følg disse trin for automatisk at tildele en Power BI (gratis)-licens til alle eksisterende brugere:

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) ved hjælp af dine legitimationsoplysninger som global administrator eller faktureringsadministrator.
1. Vælg **Fakturering** > **Køb tjenester** i navigationsmenuen.
1. Søg eller rul for at finde Power BI (gratis)-tilbuddet. Vælg tilbuddet, og vælg derefter **Hent nu**.
1. Angiv det antal licenser, der kræves for at dække alle dine brugere.
1. Vælg **Tildel automatisk alle brugere uden licenser**, og tjek derefter ud.

  ![Skærmbillede af det gratis automatisk tildelte abonnement Power BI-abonnement med der viser tilmelding til selvbetjening.](media/service-admin-licensing-organization/m365-auto-assign.png)

Hvis du vil se, hvilke brugere i din organisation der måske allerede har en licens, skal du se [Få vist og administrer brugerlicenser](service-admin-manage-licenses.md).

## <a name="license-types-and-capabilities"></a>Licenstyper og funktionalitet

Der er to slags licenser pr. bruger i Power BI: gratis Pro og Premium. Den type licens, som en bruger har brug for, bestemmes af, hvor indholdet gemmes, hvordan brugeren vil interagere med dette indhold, og om det pågældende indhold bruger Premium-funktioner. Organisationens [licenstype](#license-types) afgør, hvor indhold kan gemmes.

Den kapacitetsbaserede licens [Power BI Premium](service-admin-premium-purchase.md) giver brugere med en gratis licens mulighed for at arbejde med indhold i arbejdsområder, der er tildelt til en Premium-kapacitet. Uden for en Premium-kapacitet kan en bruger med en gratis licens kun bruge Power BI-tjenesten til at oprette forbindelse til data og oprette rapporter og dashboards i **Mit arbejdsområde**. De kan ikke dele indhold med andre eller publicere indhold til andre arbejdsområder. Hvis du vil vide mere om arbejdsområdetyper, skal du se [Typer af arbejdsområder](../consumer/end-user-workspaces.md#types-of-workspaces).

En Power BI-licens med Free- og Pro-licens pr. bruger anvender kun en delt og begrænset kapacitet til at behandle indhold. Hvis indhold gemmes i den pågældende delte kapacitet, kan brugere, der har fået tildelt en Power BI Pro-licens, kun samarbejde med andre Power BI Pro-brugere. De kan forbruge indhold, der er delt med andre brugere, publicere indhold til apparbejdsområder, dele dashboards og abonnere på dashboards og rapporter.  Når arbejdsområder befinder sig i en Premium-kapacitet, kan Pro-brugere distribuere indhold til brugere, der ikke har en Power BI Pro-licens.

Når du bruger Premium pr. bruger-licenser, kan indhold, der er oprettet af en bruger med en Premium pr. bruger-licens, kun deles med andre brugere, der har en Premium-licens, medmindre det pågældende indhold specifikt er placeret i et arbejdsområde, der er hostet på en Premium-kapacitet. I nedenstående tabel opsummeres den grundlæggende funktionalitet for hver licenstype. Hvis du vil have en detaljeret oversigt over tilgængelige funktioner i hver licenstype, skal du se [Funktioner efter licenstype](../fundamentals/service-features-license-type.md).

| Licenstype | Funktionalitet, når arbejdsområdet befinder sig i en delt kapacitet | Yderligere funktionalitet, når arbejdsområdet befinder sig i en Premium-kapacitet |
| --------- | ----------- | ----------- |
| Power BI (gratis) | Adgang til indhold i Mit arbejdsområde | Forbruge indhold, der deles med dem |
| Power BI Pro | Publicere indhold til andre arbejdsområder, dele dashboards, abonnere på dashboards og rapporter, dele med brugere, der har en Pro-licens | Distribuere indhold til brugere, der har gratis licenser |

## <a name="license-types"></a>Licenstyper

Alle brugerbaserede, kommercielle licenser fra Microsoft er baseret på Azure Active Directory-identiteter. Hvis du vil bruge Power BI-tjenesten, skal du logge på med en identitet, som understøttes af Azure Active Directory til kommercielle licenser. Du kan føje Power BI til en hvilken som helst Microsoft-licens, der bruger Azure Active Directory til identitetstjenester. Nogle licenser, f.eks. Office 365 E5, indeholder en Power BI Pro-licens, så det er ikke nødvendigt at tilmelde sig Power BI separat.

Der findes to typer Power BI-licenser til organisationer: Standard og Premium.

Med en selvbetjent Power BI Pro-standardlicens kan administratorer tildele pr. bruger-licenser. Der er et månedligt gebyr pr. bruger for Power BI Pro-licenser. Denne licenstype gør det muligt at samarbejde, publicere, dele og udføre ad hoc-analyser. Indhold gemmes i en delt lagerkapacitet, som er fuldt administreret af Microsoft.

Med en Power BI Premium-licens tildeles en kapacitet til en organisation. Premium er velegnet til BI i virksomheder, big data-analyse samt rapportering i cloudmiljøet og det lokale miljø. Det muliggør avanceret administration og styring af udrulning. Dedikerede beregnings- og lagerressourcer administreres af kapacitetsadministratorer i organisationen. Der er en månedlig omkostning for dette dedikerede miljø. Foruden andre Premium-fordele kan indhold, der gemmes i en Premium-kapacitet, tilgås af og distribueres til brugere, der ikke har Power BI Pro-licenser. Mindst én bruger skal være tildelt en Power BI Pro-licens for at bruge Premium, og indholdsskabere og udviklere skal stadig have en Power BI Pro-licens.

De to licensstyper udelukker ikke hinanden. Du kan have både Power BI Premium og Power BI Pro. I denne konfiguration kan indhold, der er gemt i en Premium-kapacitet, deles med alle brugere, og delt indhold er også tilgængeligt. Du kan finde oplysninger om kapacitetsgrænser under [Administrer datalager i Power BI-arbejdsområder](service-admin-manage-your-data-storage-in-power-bi.md).

Du kan se en sammenligning af funktioner og priser i [Power BI-priser](https://powerbi.microsoft.com/pricing).

## <a name="guest-user-access"></a>Adgang for gæstebruger

Du har måske brug for at distribuere indhold til brugere uden for din organisation. Du kan dele indhold med eksterne brugere ved at invitere dem til at få vist indhold som en gæst. Med Azure Active Directory Business-to-business (Azure AD B2B) er det muligt at dele indehold med eksterne gæstebrugere. Følgende forudsætninger skal være opfyldt, før du kan dele med eksterne brugere:

- Muligheden for at dele indhold med eksterne brugere skal være aktiveret

- Gæstebrugeren skal have den korrekte licens for at få vist det delte indhold

Se flere oplysninger om adgang for gæstebrugere under [Distribuer Power BI-indhold til eksterne gæstebrugere med Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="purchase-power-bi-pro-licenses"></a>Køb Power BI Pro-licenser

Som administrator kan du købe Power BI Pro-licenser via Microsoft 365 eller via en Microsoft-partner. Når du har købt licenserne, kan du tildele dem til individuelle brugere. Du kan finde flere oplysninger i [Køb og tildel Power BI Pro-licenser](service-admin-purchasing-power-bi-pro.md).

### <a name="power-bi-pro-license-expiration"></a>Udløb af Power BI Pro-licens

Der er en respitperiode, efter en Power BI Pro-licens er udløbet. For licenser, der er en del af et volumenlincenskøb, er respitperioden 90 dage. Hvis du har købt licensen direkte, er respitperioden 30 dage.

Power BI Pro har den samme licenslivscyklus som Microsoft 365. Du kan finde flere oplysninger under [Hvad sker der med mine data og min adgang, når mit abonnement på Microsoft 365 til virksomheder slutter?](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires)


## <a name="next-steps"></a>Næste trin

- [Køb og tildel Power BI Pro-licenser](service-admin-purchasing-power-bi-pro.md)
- [Virksomhedsabonnementer og faktureringsdokumentation](/microsoft-365/commerce/?view=o365-worldwide)
- [Find Power BI-brugere, der er logget på](service-admin-access-usage.md)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)


Power BI har introduceret Power BI Premium Gen2 som et prøveversionstilbud, der forbedrer Power BI Premium-oplevelsen på følgende områder:
* Ydeevne
* Licens pr. bruger
* Større skalering
* Forbedrede målepunkter
* Automatisk skalering
* Reducerede administrationsomkostninger

Du kan finde flere oplysninger om Power BI Premium Gen2 under [Power BI-Premium – Generation 2 (prøveversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).