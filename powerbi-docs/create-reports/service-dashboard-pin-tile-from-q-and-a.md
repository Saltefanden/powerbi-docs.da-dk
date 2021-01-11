---
title: Sådan fastgør du et felt til et dashboard fra Spørgsmål og svar
description: Dokumentation i at fastgøre et felt til et Power BI-dashboard fra spørgsmålsfeltet Spørgsmål og svar
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/05/2021
LocalizationGroup: Dashboards
ms.openlocfilehash: 5ae148feaa294c8779a7140ef450c832bd3376d8
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/06/2021
ms.locfileid: "97927169"
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>Fastgør et felt til et dashboard fra Spørgsmål og svar

Spørgsmål og svar er et værktøj i Power BI til at udforske data ved hjælp af et naturligt sprog. Brug for at finde en bestemt indsigt? Stil et spørgsmål om dine data, og få svar i form af en visualisering.

I denne vejledning åbner vi et [dashboard](../consumer/end-user-dashboards.md) i Power BI-tjenesten (app.powerbi.com), stiller et spørgsmål på et naturligt sprog for at oprette en visualisering og fastgør denne visualisering til et dashboard. Dashboards er ikke tilgængelige i Power BI Desktop. Du kan finde oplysninger om brug af Spørgsmål og svar med andre Power BI-værktøjer og andet Power Bi-indhold under [Spørgsmål og svar i Power BI – Oversigt](../consumer/end-user-q-and-a.md). 

Åbn [dashboardet Retail Analysis Sample](sample-retail-analysis.md) (Eksempel på detailhandelsanalyse) for at følge med.

## <a name="how-to-pin-a-tile-from-qa"></a>Sådan fastgør du et felt fra Spørgsmål og svar

1. Åbn et dashboard med mindst ét felt fastgjort fra en rapport. Når du stiller et spørgsmål, leder Power BI efter svaret i de datasæt, hvor et felt er fastgjort til dette dashboard.
2. I spørgsmålsfeltet øverst i dit dashboard skal du begynde at indtaste, hvad du vil vide om dine data.  
   ![Boks med spørgsmål og svar](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. Mens du f.eks. skriver "last year sales by month and territory"...  
   ![skriv et spørgsmål](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)

   giver spørgsmålsfeltet dig forslag.
4. Hvis du vil fastgøre diagrammet til dit dashboard som et felt, skal du vælge tegnestiften ![Tegnestiftikon](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png) øverst til højre på lærredet. Hvis dashboardet er blevet delt med dig, kan det ikke fastgøres til nogen visualiseringer.

5. Fastgør feltet til et eksisterende dashboard eller et nyt dashboard.

   ![Dialogboksen Fastgør til dashboard](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin-to-dashboard.png)

   * Eksisterende dashboard: Vælg navnet på dashboardet på rullelisten. Du vil kun kunne vælge blandt de dashboards, der findes i det aktuelle arbejdsområde.
   * Nyt dashboard: Skriv navnet på det nye dashboard, og det vil blive føjet til dit aktuelle arbejdsområde.

6. Vælg **Fastgør**.

   En meddelelse om fuldførelse (næsten helt oppe i højre hjørne) giver dig besked om, at visualiseringen er blevet føjet til dit dashboard som et felt.  

   ![Fastgjort til dashboard](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. Vælg **Gå til dashboard** for at se det nye felt. Der kan du [omdøbe, tilpasse størrelsen på, tilføje et link til, flytte feltet m.m.](service-dashboard-edit-tile.md) på dit dashboard.

   ![dashboard med felter](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding
* Når du begynder at indtaste et spørgsmål, begynder Spørgsmål og svar straks at søge efter det bedste svar fra alle de datasæt, der er knyttet til det aktuelle dashboard.  Det "aktuelle dashboard" er det dashboard, der er angivet i den øverste navigationsrude. Dette spørgsmål stilles f.eks. på dashboardet **Eksempel på analyse af detailhandel**, som er en del af arbejdsområdet **mihart**.

  ![brødkrummer](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **Hvordan ved Spørgsmål og svar, hvilke datasæt der skal bruges**?  Spørgsmål og svar har adgang til alle datasæt, der har mindst en visualisering fastgjort til det pågældende dashboard.

* **Hvis feltet med spørgsmål ikke vises**. Rådfør dig med din Power BI-administrator. Administratoren kan deaktivere Spørgsmål og svar.


## <a name="next-steps"></a>Næste trin
[Omdøb, tilpas størrelse, tilføj et hyperlink, flyt feltet og meget mere](service-dashboard-edit-tile.md)    
[Få vist dit dashboardfelt i fokustilstand](../consumer/end-user-focus.md)     
[Oversigt over Spørgsmål og svar i Power BI](../consumer/end-user-q-and-a.md)  
Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
