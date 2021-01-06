---
title: Opret forbindelse til en Impala-database i Power BI Desktop
description: Du kan nemt oprette forbindelse til og bruge en Impala-database i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: a9d817dc3e34cae2f496136fe19353ba5b993c8a
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926424"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Opret forbindelse til en Impala-database i Power BI Desktop
I Power BI Desktop kan du oprette forbindelse til en **Impala**-database og bruge de underliggende data på samme måde som med enhver anden datakilde i Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Opret forbindelse til en Impala-database
Følg disse trin for at oprette forbindelse til en **Impala**-database: 

1. Vælg **Hent data** på båndet **Hjem** i Power BI Desktop. 

2. Vælg **Database** blandt kategorierne til venstre. Derefter kan du se **Impala**.

    ![Hent data](media/desktop-connect-impala/connect_impala_2.png)

3. I vinduet **Impala**, der vises, skal du skrive eller indsætte navnet på din Impala-server i feltet. Vælg derefter **OK**. Du kan **importere** data direkte i Power BI, eller du kan bruge **DirectQuery**. Få mere at vide om [brug af DirectQuery](desktop-use-directquery.md).

    ![Impala-vindue](media/desktop-connect-impala/connect_impala_3a.png)

4. Angiv dine legitimationsoplysninger, når du bliver bedt om det, eller opret forbindelse anonymt. Impala-connectoren understøtter Anonymous-, Basic- (brugernavn + adgangskode) og Windows-godkendelse.

    ![Impala-connector](media/desktop-connect-impala/connect_impala_4.png)

    > [!NOTE]
    > Efter du har angivet dit brugernavn og din adgangskode for en bestemt **Impala**-server, anvendes de samme legitimationsoplysninger i efterfølgende forsøg på at oprette forbindelse via Power BI Desktop. Du kan ændre disse legitimationsoplysninger ved at gå til **Filer > Indstillinger > Indstillinger for datakilde**.


5. Efter du har oprettet forbindelse, vises vinduet **Navigator** og de data, der er tilgængelige på serveren. Blandt disse data kan du vælge elementer, som skal importeres og bruges i **Power BI Desktop**.

    ![Vinduet Navigator](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger
Der er et par begrænsninger og overvejelser, du skal være opmærksom på i forbindelse med **Impala**-connectoren:

* Impala-connectoren understøttes af datagatewayen i det lokale miljø via en af de tre understøttede godkendelsesmetoder.

## <a name="next-steps"></a>De næste trin
Du kan oprette forbindelse til mange forskellige datakilder ved hjælp af Power BI Desktop. Du kan finde flere oplysninger om datakilder i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Opret forbindelse til Excel-projektmapper i Power BI Desktop](desktop-connect-excel.md)   
* [Angiv data direkte i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
