---
title: Aktivér eller deaktiver tilmelding og køb via selvbetjening
description: Oplysninger til administratorer om, hvordan de deaktiverer muligheden for, at brugerne tilmelder sig Power BI-tjenesten eller opgraderer en licens.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: ff695d49caeab7bed88b932cec6aaec11ec4df29
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413673"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Aktivér eller deaktiver tilmelding og køb via selvbetjening

I de fleste organisationer er tilmelding via selvbetjening som standard aktiveret. Individuelle brugere i din organisation kan tilmelde sig Power BI med deres arbejds- eller skolekonto. Brugerne får muligvis også tilbudt muligheden for at købe en Power BI Pro-licens direkte, hvis de forsøger at bruge en funktion, der kræver Pro. Som administrator bestemmer du, om du vil aktivere eller deaktivere tilmelding via selvbetjening. Du kan også styre, om brugerne i din organisation kan foretage køb via selvbetjening, så de kan få deres egne licenser.

> [!NOTE]
>Hvis du har fået Power BI via en Microsoft Cloud Solution Provider (CSP), er indstillingen muligvis deaktiveret for at blokere brugerne fra at tilmelde sig individuelt. Din CSP fungerer muligvis også som global administrator for din organisation, hvilket kræver, at du kontakter vedkommende for at få hjælp til at ændre denne indstilling.
>
>

Du kan bruge PowerShell-kommandoer til at ændre de indstillinger, der styrer tilmelding og køb via selvbetjening. Der er to indstillinger, der styrer, om brugerne i din organisation kan tilmelde sig eller foretage køb via selvbetjening.

- Hvis du vil deaktivere alle tilmeldinger via selvbetjening, skal du ændre en indstilling i Azure Active Directory, som hedder **AllowAdHocSubscriptions**, ved hjælp af Azure AD PowerShell-kommandoer. Følg trinnene i denne artikel for at [aktivere eller deaktivere tilmelding via selvbetjening](#enable-or-disable-self-service-signup). Denne indstilling slår tilmelding via selvbetjening fra for *alle* cloudbaserede Microsoft-apps og -tjenester.

- Hvis du vil forhindre brugerne i at købe deres egen Pro-licens, skal du ændre indstillingen **AllowSelfServicePurchase** ved hjælp af MSCommerce PowerShell-kommandoer. Denne indstilling giver dig mulighed for at slå køb via selvbetjening fra for bestemte produkter. Følg trinnene i denne artikel for at [aktivere eller deaktivere køb af Power BI Pro-licenser via selvbetjening](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Aktivér eller deaktiver tilmelding via selvbetjening

Hvis tilmelding via selvbetjening er aktiveret, er værdien af **AllowAdHocSubscriptions** angivet til *sand*. Lad os se, hvad der sker, når du ændrer denne indstilling til *falsk*:

- Hvis du ændrer indstillingen fra sand til falsk, blokeres individuel tilmelding for nye brugere i din organisation. Alle brugere, der har tilmeldt sig Power BI, før du ændrede indstillingen, beholder deres licenser.

- Hvis du ændrer indstillingen til falsk, kan brugere, der allerede har en Power BI-licens (gratis), stadig tilmelde sig en individuel prøveversion af Power BI Pro.

- Administratoren skal tildele alle Power BI-licenser til nye brugere, der har brug for en.

### <a name="before-you-begin"></a>Inden du starter

I disse trin bruges Azure Active Directory PowerShell-kommandoer til at ændre værdien af indstillingen **AllowAdHocSubscriptions**. Azure AD PowerShell-modulet skal være installeret, før disse kommandoer er tilgængelige. Du kan finde flere oplysninger om brugen af PowerShell under [Introduktion til Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Hvis du vil installere Azure AD-modulet, skal du starte Windows PowerShell som administrator. Sørg for, at din lokale udførelsespolitik tillader, at du kører scripts. Hvis du støder på problemer, kan du se [PowerShell-udførelsespolitikker](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) for at få mere at vide om, hvordan du ændrer din lokale politik.

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

## <a name="enable-or-disable-self-service-purchase"></a>Aktivér eller deaktiver køb via selvbetjening

Hvis køb via selvbetjening er aktiveret, er værdien af **AllowSelfServicePurchase** angivet til *sand*. Lad os se, hvad der sker, når du ændrer denne indstilling til *falsk*:

- Hvis du ændrer indstillingen fra sand til falsk, blokeres brugerne i din organisation fra at købe deres egen Power BI Pro-licens. Alle brugere, der har købt en licens, før du ændrede indstillingen, beholder deres licenser.

- Hvis du ændrer indstillingen til falsk, kan brugere, der har en Power BI-licens (gratis), ikke få en individuel Power BI Pro-licens. 

- En administrator skal tildele en Pro-licens til alle de brugere, der har brug for en.

### <a name="before-you-begin"></a>Inden du starter

I disse trin bruges MSCommerce PowerShell-kommandoer til at ændre værdien af indstillingen **AllowSelfServicePurchase**. MSCommerce PowerShell-modulet skal være installeret, før disse kommandoer er tilgængelige. Du kan finde flere oplysninger om brugen af PowerShell under [Introduktion til Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Hvis du vil installere MSCommerce-modulet, skal du starte Windows PowerShell som administrator. Sørg for, at din lokale udførelsespolitik tillader, at du kører scripts. Hvis du støder på problemer, kan du se [PowerShell-udførelsespolitikker](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) for at få mere at vide om, hvordan du ændrer din lokale politik.

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

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om køb via selvbetjening i Power BI og den resterende Power Platform i disse artikler:

- [Ofte stillede spørgsmål om køb via selvbetjening](/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)