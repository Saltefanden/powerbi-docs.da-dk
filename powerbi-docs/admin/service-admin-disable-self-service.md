---
title: Aktivér eller deaktiver tilmelding og køb via selvbetjening
description: Oplysninger til administratorer om, hvordan de deaktiverer muligheden for, at brugerne tilmelder sig Power BI-tjenesten eller opgraderer en licens.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 01/31/2021
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 80e263cc6e67c28b7593fcf10aea4c81c9f4af86
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494299"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Aktivér eller deaktiver tilmelding og køb via selvbetjening

## <a name="what-is-self-service"></a>Hvad er selvbetjenings tjenester?

Selvbetjening henviser til muligheden for, at personer i en organisation (arbejde eller skole) kan tilmelde sig til at bruge tjenester, der betales i forbindelse med deres organisations abonnement, eller bruge gratis tjenester, uden at de bliver spurgt, om de vil handle på deres vegne. Personen går til et Microsoft-websted, finder en skybaseret tjeneste, som deres organisation tilbyder, og bruger deres organisations mailadresse til at tilmelde sig tjenesten. 

I mange tilfælde har organisationen betalt et gebyr for et abonnement på den pågældende tjeneste. I andre tilfælde er personen den første bruger og bliver administrator for tjenesten. For en prøveversion eller gratis licens er det ikke nødvendigt at købe noget. Men for Power BI Pro er organisationen ansvarlig for betaling af det månedlige gebyr. 

Som Microsoft 365 administrator kan du se, hvem der tilmelder sig test, licenser og abonnementer.

> [!NOTE]
> Tilmelding via selvbetjening gælder kun for kommercielle Cloud-kunder og ikke for statslige og offentlige Clouds-kunder.

## <a name="when-to-use-self-service-sign-up-and-purchase"></a>Hvornår du skal bruge selvbetjenings tilmelding og køb

### <a name="self-service-is-a-good-idea"></a>Self Service er en god idé: 

- I større og decentrale organisationer (arbejde eller skole), hvor enkeltpersoner ofte får fleksibiliteten til at købe SaaS (software som en service) til deres egen brug. 
- Til enkeltpersoner eller små organisationer, der kun skal købe én Power BI Pro licens eller kun nogle få licenser.
- For personer, der er interesseret i at prøve Power BI, kan du få proficient, før du køber et abonnement for hele organisationen.
- For aktuelle brugere med en Power BI gratis licens, som nu vil oprette og dele indhold og opgradere til en Power BI Pro prøveversion. 

### <a name="you-may-want-to-disable-self-service-when"></a>Det kan være en god idé at deaktivere selvbetjeningstjenesten, når:

- Din organisation har indkøbsprocesser på plads for at imødekomme krav om overholdelse, lovgivningsmæssige regler, sikkerhed og ledelse. Du skal sikre, at alle Power BI Pro licenser godkendes og administreres i henhold til definerede processer. 
- Din organisation har krav til nye Power BI Pro brugere, f. eks. obligatorisk uddannelse eller Brugerbekræftelse af politikker for databeskyttelse.
- Din organisation forbyder brugen af Power BI-tjeneste på grund af beskyttelse af personlige oplysninger eller andre bekymringer og har behov for at kontrollere tildelingen af Power BI gratis licenser meget tæt på hinanden.
- for at sikre at alle Power BI Pro licenser falder under Enterprise Agreement for at kunne drage fordel af de forhandlede/nedsatte licens satser.
- For de aktuelle brugere med en Power BI gratis licens, bliver du bedt om at prøve eller direkte købe en Power BI Pro licens. Organisationen vil muligvis ikke have, at disse brugere opgraderes pga. sikkerhed, beskyttelse af personlige oplysninger eller udgifter.


## <a name="enable-and-disable-self-service"></a>Aktivér og Deaktiver selvbetjening

Som administrator bestemmer du, om du vil aktivere eller deaktivere tilmelding via selvbetjening. Du kan også afgøre, om brugerne i din organisation kan foretage køb af selvbetjening, så de kan få deres egne licenser. 

Når du deaktiverer tilmelding via selvbetjening, kan brugerne ikke udforske Power BI med henblik på datavisualisering og -analyse. Hvis du blokerer individuel tilmelding, kan det være en god idé at anskaffe Power BI (gratis)-licenser til din organisation og tildele dem til alle brugere. 

> [!NOTE]
>Hvis du har købt Power BI via en Microsoft Cloud Solution Provider (CSP), kan indstillingen muligvis være deaktiveret for at forhindre brugere i at tilmelde sig hver for sig. Din CSP fungerer muligvis også som global administrator for din organisation, hvilket kræver, at du kontakter vedkommende for at få hjælp til at ændre denne indstilling.
>


 Du skal bruge PowerShell-kommandoer til at ændre de indstillinger, der styrer tilmelding til selvbetjening og indkøb. 

- Hvis du vil deaktivere alle tilmeldinger via selvbetjening, skal du ændre en indstilling i Azure Active Directory, som hedder **AllowAdHocSubscriptions**, ved hjælp af Azure AD PowerShell-kommandoer. Følg trinnene i denne artikel for at [aktivere eller deaktivere tilmelding via selvbetjening](#enable-or-disable-self-service-sign-up-for-your-organization). Denne indstilling slår tilmelding via selvbetjening fra for *alle* cloudbaserede Microsoft-apps og -tjenester.

- Hvis du vil forhindre brugerne i at købe deres egen Pro-licens, skal du ændre indstillingen **AllowSelfServicePurchase** ved hjælp af MSCommerce PowerShell-kommandoer. Denne indstilling giver dig mulighed for at slå køb via selvbetjening fra for bestemte produkter. Følg trinnene i denne artikel for at [aktivere eller deaktivere køb af Power BI Pro-licenser via selvbetjening](#enable-or-disable-self-service-purchase-in-your-organization).

## <a name="enable-or-disable-self-service-sign-up-for-your-organization"></a>Aktivér eller Deaktiver tilmelding til selvbetjening til din organisation

Hvis tilmelding via selvbetjening er aktiveret, er værdien af **AllowAdHocSubscriptions** angivet til *sand*. Lad os se, hvad der sker, når du ændrer denne indstilling til *falsk*:

- Nye brugere i din organisation er blokeret fra at tilmelde sig hver for sig. Alle brugere, der har tilmeldt sig Power BI, før du ændrede indstillingen, bevarer deres licenser.

- Brugere, der allerede har en Power BI (gratis) licens, kan stadig tilmelde sig en individuel Power BI Pro prøveversion.

- En administrator skal tildele alle Power BI licenser til nye brugere, der har brug for det.

### <a name="before-you-begin"></a>Inden du starter

I disse trin bruges Azure Active Directory PowerShell-kommandoer til at ændre værdien af indstillingen **AllowAdHocSubscriptions**. Azure AD PowerShell-modulet skal være installeret, før disse kommandoer er tilgængelige. Du kan finde flere oplysninger om brugen af PowerShell under [Introduktion til Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

Hvis du vil installere Azure AD-modulet, skal du starte Windows PowerShell som administrator. Sørg for, at din lokale udførelsespolitik tillader, at du kører scripts. Hvis du støder på problemer, kan du se [PowerShell-udførelsespolitikker](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies) for at få mere at vide om, hvordan du ændrer din lokale politik.

Kør følgende kommando for at installere Azure AD-modulet:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Ret politikken for tilmelding via selvbetjening

I PowerShell skal du køre følgende kommando for at oprette forbindelse til Azure AD:

```powershell
Connect-MsolService
```

Angiv dine administratorlegitimationsoplysninger i logondialogboksen, og fuldfør evt. påkrævet tofaktorgodkendelse. Efter bekræftelse vender du automatisk tilbage til PowerShell-vinduet.

Hvis du vil have vist den aktuelle indstilling, skal du køre følgende kommando. Outputtet overføres til en formateret liste ved hjælp af parameteren "fl".

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Kør følgende kommando for at ændre den aktuelle indstilling:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

Når du har kørt denne kommando, er tilmelding via selvbetjening deaktiveret for alle brugere. Hvis du vil slå det til igen, skal du køre denne kommando igen og angive værdien til $true.

## <a name="enable-or-disable-self-service-purchase-in-your-organization"></a>Aktivér eller Deaktiver køb via selvbetjening i din organisation

Hvis køb via selvbetjening er aktiveret, er værdien af **AllowSelfServicePurchase** angivet til *sand*. Lad os se, hvad der sker, når du ændrer denne indstilling til *falsk*:

- Brugere i din organisation er blokeret fra at købe deres egen Power BI Pro licens. Brugere, der har købt en licens, før du ændrede indstillingen, bevarer deres licenser.

- Brugere, der har en Power BI (gratis) licens, kan ikke hente en individuel Power BI Pro licens. 

- En administrator skal tildele en Pro-licens til alle de brugere, der har brug for den.

### <a name="before-you-begin"></a>Inden du starter

I disse trin bruges MSCommerce PowerShell-kommandoer til at ændre værdien af indstillingen **AllowSelfServicePurchase**. MSCommerce PowerShell-modulet skal være installeret, før disse kommandoer er tilgængelige. Du kan finde flere oplysninger om brugen af PowerShell under [Introduktion til Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

Hvis du vil installere MSCommerce-modulet, skal du starte Windows PowerShell som administrator. Sørg for, at din lokale udførelsespolitik tillader, at du kører scripts. Hvis du støder på problemer, kan du se [PowerShell-udførelsespolitikker](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies) for at få mere at vide om, hvordan du ændrer din lokale politik.

Kør følgende kommando for at installere MSCommerce-modulet:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Ret politikken for tilmelding via selvbetjening

I PowerShell skal du køre følgende kommando for at oprette forbindelse:

```powershell
Connect-MSCommerce
```

Angiv dine administratorlegitimationsoplysninger i logondialogboksen, og fuldfør evt. påkrævet tofaktorgodkendelse. Efter bekræftelse vises en vellykket forbindelse i PowerShell-vinduet.

Hvis du vil have vist den aktuelle indstilling, skal du køre følgende kommando. For at undgå, at tekst afkortes, overføres outputtet til en formateret liste ved hjælp af parameteren "fl".

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

Du kan deaktivere den indstilling, der tillader køb via selvbetjening for et enkelt produkt, ved at angive dets **Produkt-id**. Kør denne kommando for at ændre den aktuelle indstilling for Power BI-tjenesten:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

Når du har kørt denne kommando, er køb af Power BI via selvbetjening deaktiveret for alle brugere. Hvis du vil slå det til igen, skal du køre denne kommando igen og angive værdien til $true.

## <a name="what-to-do-if-individuals-have-already-used-self-service"></a>Hvad skal jeg gøre, hvis enkeltpersoner allerede har brugt selv service

Tilmelding via selvbetjening og køb er begge aktiveret som standard. Det gør det muligt for personer i din organisation allerede have Power BI licenser og abonnementer. Uanset om du foretager en handling eller ej, skal du have et tydeligt billede af det, der allerede findes.

Brugere, der har tilmeldt sig lejeren via selvbetjent logon, tildeles en unik licens, som du kan filtrere efter i din aktive brugerrude på administratordashboardet. Følg disse trin for at oprette denne nye visning.

1. Naviger til Microsoft 365 Administration.

1. Vælg **Brugere** > **Aktive brugere** i navigationsruden.

1. I menuen Visninger skal du vælge **Tilføj brugerdefineret visning**.

1. Navngiv din nye visning. Under Tildel produktlicens vælger du herefter Power BI (gratis) eller Power BI Pro.

    Du kan kun have en licens pr. valgt visning. Hvis du har både Power BI (gratis) - og Power BI Pro-licenser i organisationen, kan du oprette to visninger.

1. Angiv alle de andre betingelser, du ønsker, og vælg derefter **Tilføj**.

    Når du har oprettet den nye visning, er den tilgængelig fra menuen Visninger.


    > [!NOTE]
    > Hvis din organisation ikke har et Microsoft 365 miljø, der er knyttet til dit maildomæne, er selvbetjenings brugere føjet til en ny brugermappe, der kun findes i skyen. Det kan være nødvendigt at finde, kræve og [overtage de lejere, der allerede er oprettet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover). 

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om køb via selvbetjening i Power BI og den resterende Power Platform i disse artikler:

- [Ofte stillede spørgsmål om køb via selvbetjening](/microsoft-365/commerce/subscriptions/self-service-purchase-faq#admin-capabilities)
- [Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell)