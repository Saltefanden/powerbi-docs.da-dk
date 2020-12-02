---
title: 'Selvstudium: Angiv databeskeder i dashboards i Power BI-tjenesten'
description: I dette selvstudium får du mere at vide om, hvordan du angiver beskeder, så du får besked, når dataene i dine dashboards ændres ud over de grænser, du har angivet i Microsoft Power BI-tjenesten.
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: removed
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 08/05/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: be3ed6d8a836b626ba26e5e9acce7f0f2df3c6ea
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96391984"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Selvstudium: Angiv beskeder i dashboards i Power BI

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Angiv beskeder i Power BI-tjenesten, så du får besked, når dataene i dashboards ændres ud over de grænser, du har angivet. Der kan kun angives beskeder på felter, der er fastgjort via rapportvisualiseringer, og kun på målere, KPI'er og kort. 

![felt, kort, KPI](media/end-user-alerts/card-gauge-kpi.png)

Beskeder kan oprettes i dashboards:
- du har oprettet og gemt i **Mit arbejdsområde**
- der er blevet delt med dig i en [Premium-kapacitet](end-user-license.md). 
- i et arbejdsområde, som du kan få adgang til, hvis du har en Power BI Pro-licens.    

Beskeder fungerer kun i forbindelse med opdaterede data. Når data opdateres, kontrolleres det via Power BI, om der er angivet en besked for disse data. Hvis dataene har nået grænsen for en besked, udløses der en besked. 

Denne funktion er stadig under udvikling, og du kan få flere oplysninger i afsnittet [Tip og fejlfinding nedenfor](#tips-and-troubleshooting).



Det er kun dig, der kan se de angivne beskeder, selvom du deler dashboardet. Databeskeder er fuldt synkroniseret på tværs af platforme. Angiv og få vist databeskeder [i Power BI-mobilapps](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) og i Power BI-tjenesten. 

> [!WARNING]
> Disse beskeder indeholder oplysninger om dine data. Hvis du får vist dine data i Power BI på en mobilenhed, og enheden bliver stjålet, anbefaler vi, at du bruger Power BI-tjenesten til at slå alle beskeder fra.
> 

Denne artikel omhandler følgende:
> [!div class="checklist"]
> * Hvem kan indstille beskeder
> * Hvilke visualiseringer understøtter beskeder
> * Hvem kan indstille beskeder
> * Virker beskeder i Power BI Desktop og Mobil
> * Sådan opretter du en besked
> * Hvor modtager jeg mine beskeder

## <a name="prerequisites"></a>Forudsætninger

Hvis du ikke er tilmeldt Power BI, kan du [tilmelde dig en gratis prøveversion](https://app.powerbi.com/signupredirect?pbi_source=web), før du begynder.

1. I dette eksempel bruges et dashboardkort fra Eksempel på salg og marketing. Åbn Power BI-tjenesten (app.powerbi.com), log på, og åbn **Mit arbejdsområde**.    
    ![Åbn Mit arbejdsområde](media//end-user-alerts/power-bi-my-workspace.png)

2. Vælg **Hent data** i nederste venstre hjørne.

    ![Vælg Hent data](media//end-user-alerts/power-bi-get-data.png)

3. Vælg **Eksempler** på siden Hent data, der vises.

4. Vælg Eksempel på salg og marketing, og vælg derefter **Opret forbindelse**.

    ![Download Eksempel på salg og marketing](media//end-user-alerts/power-bi-sample.png)

5. Når Power BI har oprettet forbindelse til eksemplet, skal du vælge **Gå til dashboard** fra den dialogboks, der vises.     
    ![Åbn Eksempel på salg og marketing](media//end-user-alerts/power-bi-go-to-dashboard.png)

## <a name="add-an-alert-to-a-dashboard-tile"></a>Føj en besked til et dashboardfelt

1. Vælg ellipsen i en dashboardmåler, et KPI eller et kortfelt.
   
   ![kortfelt](media/end-user-alerts/power-bi-card.png)

2. Vælg ikonet Vigtig besked ![Ikonet Vigtig besked](media/end-user-alerts/power-bi-alert-icon.png) eller **Administrer beskeder** for at tilføje en eller flere beskeder for kortet **Markedsandel**.

   ![Kortfelt med de valgte ellipser](media/end-user-alerts/power-bi-manage.png)

   
1. I ruden **Administrer beskeder** skal du vælge **+ Tilføj påmindelsesregel**.  Kontrollér, at skyderen er angivet til **Til**, og giv beskeden en titel. Titler hjælper dig med let at genkende dine beskeder.
   
   ![Vinduet Tilføj en påmindelsesregel](media/end-user-alerts/power-bi-alert-manage.png)
4. Rul ned, og angiv oplysninger om beskederne.  I dette eksempel opretter vi en besked, som skal sendes til os én gang om dagen, hvis markedsandelen når over 40. Beskederne vises i [Meddelelsescenter](end-user-notification-center.md). Vi får også Power BI til at sende os en mail.
   
   ![Vinduet Administrer beskeder, angiv grænseværdi](media/end-user-alerts/power-bi-manage-alert-detail.png)

5. Vælg **Gem og luk**.
 


   > 

## <a name="receiving-alerts"></a>Modtag beskeder
Når de sporede data når en af de angivne tærskelværdier, sker der flere ting. Først tjekker Power BI, om der er gået mere end én time eller mere end et døgn (afhænger af den valgte indstilling), siden den seneste besked blev sendt. Du får en besked, så længe dataene har overskredet grænsen.

Derefter sendes en besked til meddelelsescenteret og evt. en mail via Power BI. Hver enkelt besked indeholder et direkte link til dine data. Vælg linket for at se det relevante felt.  

1. Hvis du har indstillet beskeden til at sende en mail til dig, modtager du mail i din indbakke. Dette er en vigtig besked, vi angiver for kortet **Synspunkt**.
   
   ![Mail med vigtig besked](media/end-user-alerts/power-bi-email.png)
2. Power BI føjer også en meddelelse til **Meddelelsescenter**.
   
   ![Meddelelsesikon i Power BI-tjeneste](media/end-user-alerts/power-bi-task.png)
3. Åbn dit meddelelsescenter for at få vist oplysningerne for beskeder.
   
    ![læs beskeden](media/end-user-alerts/power-bi-notifications.png)
   
  

## <a name="managing-alerts"></a>Administration af beskeder

Der er mange måder, du kan administrere dine beskeder på: fra selve dashboardfeltet, fra menuen Indstillinger for Power BI og på et individuelt felt i [Power BI-mobilappen på iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) eller i [Power BI-mobilappen til Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>Fra selve feltet

1. Hvis du vil ændre eller fjerne en besked fra et felt, skal du genåbne vinduet **Administrer beskeder** ved at vælge ikonet Vigtig besked ![Ikonet Vigtig besked](media/end-user-alerts/power-bi-alert-icon.png). Alle de beskeder, du har angivet for dette felt, vises.
   
    ![Vinduet Administrer beskeder](media/end-user-alerts/power-bi-manage-alert.png).
2. Hvis du vil redigere en besked, skal du vælge pilen til venstre for beskednavnet.
   
    ![pil ud for Beskednavn](media/end-user-alerts/power-bi-alert-modify.png).
3. Hvis du vil slette en besked, skal du vælge skraldespanden til højre for beskednavnet.
   
      ![Skraldespandsikonet er valgt](media/end-user-alerts/power-bi-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>I menuen Indstillinger for Power BI

1. Vælg tandhjulsikonet på menulinjen i Power BI.
   
    ![tandhjulsikon](media/end-user-alerts/power-bi-gear-icon.png).
2. Under **Indstillinger** skal du vælge **Beskeder**.
   
    ![Fanen Beskeder i vinduet Indstillinger](media/end-user-alerts/power-bi-settings.png)
3. Her kan du slå beskeder til og fra, åbne vinduet **Administrer beskeder** for at ændre eller slette beskeden.

## <a name="tips-and-troubleshooting"></a>Tip og fejlfinding 

* Hvis du ikke kan angive en besked for en måler, en KPI eller et kort, skal du kontakte din Power BI-administrator eller it-helpdesk for at få hjælp. Nogle gange er beskeder slået fra eller utilgængelige for dit dashboard eller for bestemte typer dashboardfelter.
* Beskeder fungerer kun i forbindelse med opdaterede data. De fungerer ikke med statistiske data. De fleste af de eksempler, der leveres af Microsoft, er statiske. 
* Muligheden for at modtage og få vist delt indhold kræver en Power BI Pro- eller Premium-licens. Du kan få flere oplysninger ved at læse [Hvilken licens har jeg?](end-user-license.md)
* Beskeder kan angives på visuelle elementer, der er oprettet ud fra streamingdatasæt, som er fastgjort fra en rapport til et dashboard. Der kan ikke angives beskeder for streamingfelter, der er oprettet direkte på dashboardet ved hjælp af **Tilføj felt** > **Brugerdefinerede streamingdata**.


## <a name="clean-up-resources"></a>Fjern ressourcer
Fremgangsmåden til sletning af beskeder er beskrevet ovenfor. Vælg tandhjulsikonet på menulinjen i Power BI. Vælg **Beskeder** under **Indstillinger**, og slet beskeden.

> [!div class="nextstepaction"]
> [Angiv databeskeder på din mobilenhed](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


