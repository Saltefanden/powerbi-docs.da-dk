---
title: Videregiv en rapportparameter i en URL-adresse til en sideinddelt rapport i Power BI Report Builder
description: I dette emne beskrives det, hvordan du videregiver rapportparametre til en rapport ved at inkludere dem i en URL-adresse til en sideinddelt rapport.
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 05/01/2020
ms.openlocfilehash: ac3cd10ec4c356da92aca6983292ff57b16f58b3
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415582"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Videregiv en rapportparameter i en URL-adresse til en sideinddelt rapport i Power BI 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Du kan videregive rapportparametre til en rapport ved at inkludere dem i en URL-adresse til en sideinddelt rapport. Alle forespørgselsparametre kan have tilsvarende rapportparametre. Derfor videregiver du en forespørgselsparameter til en rapport ved at videregive den tilsvarende rapportparameter. Parameternavnet skal have præfikset `rp:`, så Power BI kan genkende det i URL-adressen. 

Der skelnes mellem store og små bogstaver og benyttes specialtegn i rapportparametre: 

- Et mellemrum i parameterdelen af URL-adressen erstattes med et plustegn (+).  Eksempel: 

    ```rp:Holiday=Christmas+Day```

- Et semikolon i en del af strengen erstattes med tegnene `%3A`.

Browsere bør automatisk udføre den korrekt kodning af URL-adresser. Du behøver ikke at kode nogen af tegnene manuelt. 

Hvis du vil angive en rapportparameter i en URL-adresse, skal du bruge følgende syntaks: 

```
rp:parameter=value
```

Hvis du f.eks. vil angive to parametre, "Salesperson" og "State", der er defineret i en rapport i dit Mit arbejdsområde, skal du bruge følgende URL-adresse: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Hvis du vil angive de samme to parametre, der er defineret i en rapport i en app, skal du bruge følgende URL-adresse: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&rp:State=Utah 
```

Hvis du vil videregive en null-værdi for en parameter, skal du bruge følgende syntaks: 

```
parameter:isnull=true
```

Eksempel:

```
rp:SalesOrderNumber:isnull=true
```

Hvis du vil videregive en boolesk værdi, skal du bruge 0 for falsk og 1 for sand. Hvis du vil videregive en flydende værdi, skal du inkludere decimalseparatoren for serverens landestandard.

> [!NOTE]
> Hvis din rapport indeholder en rapportparameter, som har en standardværdi, og værdien for egenskaben **Spørg** er **falsk** (dvs. egenskaben **Spørg bruger** ikke er valgt i Rapportstyring), kan du ikke videregive en værdi for den pågældende rapportparameter i en URL-adresse. Det giver administratorer mulighed for at forhindre, at slutbrugerne kan tilføje eller ændre værdierne for visse rapportparametre.
> 
> Power BI understøtter ikke en forespørgselsstreng på mere end 2.000 tegn.  Denne værdi kan overskrides, hvis du bruger URL-parametre til at få vist din sideinddelte rapport.  Det er især tilfældet, hvis du bruger parametre med flere værdier.

## <a name="additional-examples"></a>Yderligere eksempler 

Følgende eksempel på en URL-adresse indeholder en parameter med flere værdier for "Salesperson". Formatet for en parameter med flere værdier er at gentage parameternavnet for hver værdi. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

Følgende eksempel på en URL-adresse videregiver en enkel parameter for SellStartDate med værdien "7/1/2005" for en rapportserver i oprindelig tilstand.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Næste trin

- [URL-parametre i sideinddelte rapporter i Power BI](report-builder-url-parameters.md)
- [Hvad er sideinddelte rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
