---
title: Tovejskrydsfiltrering i Power BI Desktop
description: Aktivér krydsfiltrering ved hjælp af DirectQuery i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 01/15/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 96e0e60adcd1858fa031eb81e8f0762690cbe0c7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415973"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Aktivér tovejskrydsfiltrering for DirectQuery i Power BI Desktop

Ved filtrering af tabeller for at oprette den relevante visning af data står rapportoprettere og dataudviklere, over for udfordringer, når de skal fastlægge, hvordan filtrering anvendes på en rapport. Tidligere blev tabellens filterkontekst opbevaret på den ene side af relationen, men ikke den anden. Dette arrangement krævede ofte en kompleks DAX-formel for at give de ønskede resultater.

Med tovejskrydsfiltrering har rapportoprettere og dataudviklere nu større kontrol over, hvordan de kan anvende filtre, når de arbejder med relaterede tabeller. Tovejskrydsfiltrering gør det muligt for dem at anvende filtre på *begge* sider af en tabelrelation. Du kan anvende filtrene ved at overføre filterkonteksten til en anden relateret tabel på den anden side af en tabelrelation.

## <a name="enable-bidirectional-cross-filtering-for-directquery"></a>Aktivér tovejskrydsfiltrering for DirectQuery

Du kan aktivere krydsfiltrering i dialogboksen **Rediger relation**. Hvis du vil aktivere krydsfiltrering for en relation, skal du konfigurere følgende indstillinger:

* Angiv **Tværgående filterretning** til **Begge**.
* Vælg **Anvend sikkerhedsfilter i begge retninger**.

  ![Konfigurer tovejskrydsfiltrering i Power BI Desktop.](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Når du opretter DAX-formler til krydsfiltrering i Power BI Desktop, skal du bruge *UserPrincipalName*. Dette felt er ofte det samme som en brugers logon, f. eks. <em>joe@contoso.com</em> i stedet for *UserName*. Det er muligt, at du bliver nødt til at oprette en relateret tabel, der knytter *UserName* eller *EmployeeID* til *UserPrincipalName*.

Hvis du vil have flere oplysninger og eksempler på, hvordan tovejskrydsfiltrering fungerer, skal du se [hvidbogen om tovejskrydsfiltrering for Power BI Desktop](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx).

