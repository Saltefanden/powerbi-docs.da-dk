---
title: Sådan konfigurerer du en planlagt opdatering af en Power BI-rapport
description: Hvis du vil opdatere dataene i din Power BI-rapport, skal du oprette en plan for planlagt opdatering.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 06/10/2020
ms.openlocfilehash: 95119cf6ebebbf527245f5b75f0da541c1f87aef
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386314"
---
# <a name="how-to-configure-power-bi-report-scheduled-refresh"></a>Sådan konfigurerer du en planlagt opdatering af en Power BI-rapport
Hvis du vil opdatere data i din Power BI-rapport på Power BI-rapportserver, skal du oprette en plan for planlagt opdatering. Du kan oprette denne plan i området *Administrer* i en Power BI-rapport på rapportserveren.

![Vellykkede planlagt opdatering af en Power BI-rapport](media/configure-scheduled-refresh/scheduled-refresh-success.png)

## <a name="configure-data-source-credentials"></a>Konfigurer legitimationsoplysningerne for datakilden
Du skal bruge de nødvendige tilladelser til at oprette en plan for planlagt opdatering. Tilladelser er defineret i rolledefinitionerne for rapportserveren. Se [Rolledefinitioner – foruddefinerede roller](/sql/reporting-services/security/role-definitions-predefined-roles) i dokumentationen til SQL Server Reporting Services for at få flere oplysninger.

Før du kan oprette en plan for planlagt dataopdatering, skal du angive legitimationsoplysningerne for **hver enkelt datakilde**, der bruges i din Power BI-rapport.

1. Højreklik på Power BI-rapporten på webportalen, og vælg **Administrer**.
   
    ![Vælg Administrer i genvejsmenuen for Power BI-rapporten](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. I menuen til venstre skal du vælge fanen **Datakilder**.
3. Vælg den godkendelsestype, som skal bruges, når der oprettes forbindelse til datakilden for hver enkelt datakilde, der vises. Angiv de relevante legitimationsoplysninger.
   
    ![Legitimationsoplysninger for datakilden på skærmbilledet til administration af rapporter](media/configure-scheduled-refresh/data-source-credentials.png)

## <a name="creating-a-schedule-refresh-plan"></a>Oprettelse af en plan for planlagt opdatering
Følg disse trin for at oprette en plan for en planlagt opdatering.

1. Højreklik på Power BI-rapporten på webportalen, og vælg **Administrer**.
   
    ![Vælg Administrer i genvejsmenuen for Power BI-rapporten](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. I menuen til venstre skal du vælge fanen **Planlagt opdatering**.
3. På siden **Planlagt opdatering** skal du vælge **Ny plan for planlagt opdatering**.
   
    ![Ny plan for planlagt opdatering](media/configure-scheduled-refresh/new-scheduled-refresh-plan.png)
4. På siden **Ny plan for planlagt opdatering** skal du angive en beskrivelse og en tidsplan for, hvornår din datamodel skal opdateres.
5. Vælg **Opret plan for planlagt opdatering**, når du er færdig.
   
    ![Opret plan for planlagt opdatering](media/configure-scheduled-refresh/create-scheduled-refresh-plan.png)

## <a name="modifying-a-schedule-refresh-plan"></a>Redigering af en plan for planlagt opdatering
Redigering af en plan for planlagt opdatering minder om oprettelse af en plan.

1. Højreklik på Power BI-rapporten på webportalen, og vælg **Administrer**.
   
    ![Vælg Administrer i genvejsmenuen for Power BI-rapporten](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. I menuen til venstre skal du vælge fanen **Planlagt opdatering**.
3. På siden **Planlagt opdatering** skal du vælge **Rediger** ud for den opdateringsplan, du vil administrere.
   
    ![Klik på Rediger ud for den plan, du vil redigere](media/configure-scheduled-refresh/edit-scheduled-refresh-plan.png)
4. På siden **Rediger plan for planlagt opdatering** skal du angive en beskrivelse og en tidsplan for, hvornår din datamodel skal opdateres.
5. Vælg **Anvend**, når du er færdig.
   
    ![Siden Rediger plan for planlagt opdatering ligner skærmen for oprettelse](media/configure-scheduled-refresh/edit-scheduled-refresh-plan-page.png)

## <a name="viewing-the-status-of-schedule-refresh-plan"></a>Få vist status for Plan for planlagt opdatering
Få vist status for en plan for planlagt opdatering på webportalen.

1. Højreklik på Power BI-rapporten på webportalen, og vælg **Administrer**.
   
    ![Vælg Administrer i genvejsmenuen for Power BI-rapporten](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. I menuen til venstre skal du vælge fanen **Planlagt opdatering**.
3. På siden **Planlagt opdatering** vises statussen for en plan i kolonnen længst til højre.
   
   | **Status** | **Beskrivelse** |
   | --- | --- |
   | Ny plan for planlagt opdatering |Planen er blevet oprettet, men ikke kørt. |
   | Opdaterer |Opdateringsprocessen er startet. |
   | Streamingmodel til Analysis Server |Kopiering af modellen fra katalogdatabasen på rapportserveren til den hostede Analysis Services-instans. |
   | Opdatering af data |Opdatering af dataene i modellen. |
   | Fjernelse af legitimationsoplysninger fra modellen |De legitimationsoplysninger, der bruges til at oprette forbindelse til datakilden fra modellen, blev fjernet. |
   | Lagring af modellen i kataloget |Opdateringen af data er fuldført, og den opdaterede model gemmes i katalogdatabasen på rapportserveren igen. |
   | Fuldført: Opdatering af data |Opdateringen er færdig. |
   | Fejl: |Der opstod en fejl under opdateringen, og fejlen vises. |

Websiden skal opdateres, for at du kan se den aktuelle status. Status ændres ikke automatisk.

## <a name="next-steps"></a>Næste trin
Du kan få mere at vide om oprettelse og ændring af tidsplaner under [Opret, rediger og slet tidsplaner](/sql/reporting-services/subscriptions/create-modify-and-delete-schedules).

Du kan finde oplysninger om fejlfinding i forbindelse med planlagt opdatering under [Fejlfinding i forbindelse med planlagt opdatering på Power BI-rapportserver](scheduled-refresh-troubleshoot.md).

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)