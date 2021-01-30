---
title: Køb og tildel Power BI Pro-licenser
description: Få mere at vide om, hvordan du køber og tildeler Power BI Pro-brugerlicenser, så dine brugere kan få adgang til indhold og samarbejde med kolleger i Power BI-tjenesten.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 0184e549911afb784e06b1ee829bf113ff97e067
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086297"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Køb og tildel Power BI Pro-brugerlicenser

>[!IMPORTANT]
>Denne artikel er til administratorer. Er du bruger og klar til at opgradere til en Power BI Pro-licens? Gå direkte til [Introduktion til Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro) for at konfigurere din konto.

Power BI Pro er en individuel brugerlicens, der giver brugerne mulighed for at læse og interagere med rapporter og dashboards, som andre har publiceret til Power BI-tjenesten. Brugere med denne licenstype kan dele indhold og samarbejde med andre Power BI Pro-brugere. Det er kun brugere med en Power BI Pro-brugerlicens, der kan publicere eller dele indhold med andre brugere eller bruge indhold, der er oprettet af andre, medmindre indholdet er hostet i en Power BI Premium-kapacitet. Du kan få flere oplysninger om de tilgængelige licens- og abonnementstyper under [Power BI-licenser i din organisation](service-admin-licensing-organization.md).

## <a name="purchase-power-bi-pro-user-licenses"></a>Køb Power BI Pro-brugerlicenser

I denne artikel forklares det, hvordan du køber Power BI Pro-brugerlicenser i Microsoft 365 Administration. Når du har købt licenser, kan du tildele dem til brugere enten i Microsoft 365 Administration eller i Azure Portal.

> [!NOTE]
> Fra og med den 14. januar 2020 er selvbetjeningsindkøb, abonnements- og licensstyringsfunktioner til Power Platform-produkter (Power BI, Power Apps og Power Automate) tilgængelige til kommercielle Cloud-kunder. Du kan få flere oplysninger under [Ofte stillede spørgsmål om køb via selvbetjening](/microsoft-365/commerce/subscriptions/self-service-purchase-faq). Hvis du vil aktivere eller deaktivere købsmuligheder via selvbetjening, kan du se under [Aktivér eller deaktiver tilmelding og køb via selvbetjening](./service-admin-disable-self-service.md).

### <a name="prerequisites"></a>Forudsætninger

Hvis du vil købe og tildele licenser via Microsoft 365 Administration, skal du være medlem af rollen [Global administrator eller Faktureringsadministrator](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) i Microsoft 365.

Du skal være ejer af det Azure-abonnement, som Power BI bruger til opslag i Azure Active Directory, for at tildele licenser via Azure Portal.

### <a name="purchase-licenses-in-microsoft-365"></a>Køb licenser i Microsoft 365

> [!NOTE]
> Hvis du normalt køber licenser via en volumenlicensaftale, f.eks. en Enterprise Aftale, og ønsker at modtage en faktura i stedet for at købe med et kreditkort eller en bankkonto, skal du indsende ordren anderledes. Kontakt din Microsoft-forhandler, eller gå gennem Volume Licensing Service Center for at tilføje eller fjerne licenser. Du kan finde flere oplysninger under [Administrer abonnementslicenser](/microsoft-365/commerce/licenses/buy-licenses).

Følg disse trin for at købe Power BI Pro-licenser via Microsoft 365 Administration:

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com).

2. I navigationsmenuen skal du vælge **Fakturering** > **Køb tjenester**.

3. Søg efter eller rul for at finde det abonnement, du vil købe. Du kan finde **Power BI** under **andre kategorier, der kan have interesse for dig**, nederst på siden. Vælg linket for at få vist de Power BI-abonnementer, der er tilgængelige for din organisation.

4. Vælg **Power BI Pro**.

5. Vælg **Køb** på siden **Køb tjenester**.

6. Vælg **Betal en gang om måneden** eller **Betal for et helt år**, afhængigt af hvordan du vil betale.

7. Angiv det ønskede antal licenser, du vil købe, under **Hvor mange brugere ønsker du?** , og vælg derefter **Gå til kassen** for at gennemføre transaktionen.

8. Du bekræfter dit køb ved at gå til **Fakturering** > **Produkter og tjenester** og finde **Power BI Pro**.

9. Hvis du vil tilføje flere licenser senere, skal du finde **Power BI Pro** på siden **Produkter og tjenester** og derefter vælge **Tilføj/Fjern licenser**.


## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Tildel licenser via Microsoft 365 Administration

Du kan finde flere oplysninger om tildeling af licenser i Microsoft 365 Administration under [Tildel licenser til brugere](/office365/admin/manage/assign-licenses-to-users).

For gæstebrugere skal du se [Tildel licenser til brugere på siden Licenser](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Før du tildeler Pro-licenser til gæstebrugere, skal du kontakte din Microsoft-kontorepræsentant for at sikre, at du overholder vilkårene i din aftale med Microsoft.

## <a name="assign-licenses-in-the-azure-portal"></a>Tildel licenser via Azure Portal

Benyt følgende fremgangsmåde for at tildele Power BI Pro-licenser til individuelle brugerkonti:

1. Log på [Azure Portal](https://portal.azure.com/).

2. Søg efter og vælg **Azure Active Directory**.

3. Under **Administrer** i ressourcemenuen **Azure Active Directory** skal du vælge **Licenser**.

4. Vælg **Alle produkter** under **Licenser – oversigt**, og vælg derefter **Power BI Pro** for at få vist en liste over brugere med licens.

5. Vælg **+ Tildel** på kommandolinjen. På siden **Tildel licens** skal du først vælge en bruger og derefter vælge **Tildelingsindstillinger** for at aktivere en Power BI Pro-licens for den valgte brugerkonto.

## <a name="next-steps"></a>Næste trin

- [Power BI-licenser i din organisation](service-admin-licensing-organization.md)

 - [Find Power BI-brugere, der er logget på](service-admin-access-usage.md)

 - [Tilmeld dig Power BI som enkeltperson](../fundamentals/service-self-service-signup-for-power-bi.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)