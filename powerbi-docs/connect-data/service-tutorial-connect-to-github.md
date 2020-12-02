---
title: 'Selvstudium: Opret forbindelse til et GitHub-lager med Power BI'
description: I dette selvstudium opretter du forbindelse til virkelige data i GitHub-tjenesten med Power BI, og Power BI opretter automatisk dashboards og rapporter.
author: paulinbar
ms.author: painbar
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 10/30/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: d8b6277c64f2f6c55f1ab622d129556fdfc4c600
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96401621"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Selvstudium: Opret forbindelse til et GitHub-lager med Power BI
I dette selvstudium opretter du forbindelse til rigtige data: offentligt *lager* med Power BI-indhold i GitHub-tjenesten. Power BI opretter automatisk et dashboard og en rapport med dataene. Du kan se svar på spørgsmål som f.eks.: Hvor mange bidrager til det offentlige lager med Power BI-indhold? Hvem der bidrager mest? På hvilken ugedag er der flest bidrag? Og andre spørgsmål. 

Du kan også oprette forbindelse til dine egne private eller offentlige GitHub-lagre. I artiklen [Opret forbindelse til GitHub med Power BI](service-connect-to-github.md) forklares det, hvordan du bruger en *skabelonapp* i Power BI til at oprette forbindelse til dine lagre.

![GitHub-rapporten i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

I dette selvstudium kan du udføre følgende trin:

> [!div class="checklist"]
> * Opret en GitHub-konto, hvis du ikke allerede har en 
> * Log på din Power BI-konto, eller opret én, hvis du ikke allerede har en
> * Åbn Power BI-tjenesten
> * Find GitHub-appen
> * Angiv oplysningerne for det offentlige GitHub-lager i Power BI
> * Få vist dashboardet og rapporten med GitHub-data
> * Ryd op i ressourcer ved at slette appen

Hvis du ikke er tilmeldt Power BI, kan du [tilmelde dig en gratis prøveversion](https://app.powerbi.com/signupredirect?pbi_source=web), før du begynder.

## <a name="prerequisites"></a>Forudsætninger

Hvis du vil gennemføre dette selvstudium, skal du oprette en GitHub-konto, hvis du ikke allerede har en. 

- Tilmeld dig en [GitHub-konto](/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Sådan opretter du forbindelse
1. Log på Power BI-tjenesten (`https://app.powerbi.com`). 
2. Vælg **Apps** og derefter **Hent apps** i navigationsruden.
   
   ![Hent apps i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Vælg **Apps**, og skriv **GitHub** i søgefeltet > **Hent det nu**.
   
   ![Hent GitHub i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. Vælg **Installér** under **Installér denne Power BI-app?** .
5. Under **Din nye app er klar** skal du vælge **Gå til app**.
6. Under **Kom i gang med din nye app** skal du vælge **Opret forbindelse**.

    ![Kom i gang med din nye app](media/service-tutorial-connect-to-github/power-bi-new-app-connect-get-started.png)

7. Angiv lagernavnet og lagerejeren. URL-adressen til dette lager er https://github.com/MicrosoftDocs/powerbi-docs, så **Lagerejer** er **MicrosoftDocs**, og **Lager** er **powerbi-docs**. 
   
    ![Navn på GitHub-lager i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Angiv de GitHub-legitimationsoplysninger, du har oprettet. Power BI springer måske dette trin over, hvis du allerede er logget på GitHub i din browser. 

6. Som **Godkendelsesmetode** skal du bevare **oAuth2** valgt \> **Log på**.

7. Følg skærmbillederne for GitHub-godkendelse. Giv Power BI-tilladelse til GitHub-dataene.
   
   Nu kan Power BI oprette forbindelse til GitHub og oprette forbindelse til dataene.  Dataene opdateres én gang om dagen.

8. Når Power BI importerer dataene, får du vist indholdet af dit nye GitHub-arbejdsområde. 
9. Vælg pilen ud for navnet på arbejdsområdet i navigationsruden. Du kan se, at arbejdsområdet indeholder et dashboard og en rapport. 

    ![App i navigationsruden](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Vælg **Flere indstillinger** (...) ud for dashboardnavnet > **Omdøb** > skriv **GitHub-dashboard**.
 
    ![GitHub-felt i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Vælg ikonet for global navigation for at minimere navigationsruden, så du har mere plads.

    ![Ikonet til global navigation](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Vælg dit nye GitHub-dashboard.
    
    GitHub-dashboardet indeholder dynamiske data, så de værdier, du ser, kan være anderledes.

    ![GitHub-dashboard i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Stil et spørgsmål

1. Anbring din markør på **Stil et spørgsmål om dine data**. Power BI indeholder **spørgsmål om, hvordan du kan komme i gang**. 

1. Vælg, **hvor mange brugere der er**.
 
    ![Hvor mange brugere er der](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Mellem **hvor mange** og **brugere er der** skal du skrive **pull-anmodninger pr.**. 

     Power BI opretter et liggende søjlediagram, der viser antallet af pull-anmodninger pr. person.

    ![Hvor mange pull-anmodninger pr. bruger er der](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Vælg nålen for at fastgøre det til dit dashboard, og **afslut derefter Spørgsmål og svar**.

## <a name="view-the-github-report"></a>Få vist GitHub-rapporten 

1. På GitHub-dashboardet skal du vælge søjlediagrammet **Pull-anmodninger pr. måned** for at åbne den relaterede rapport.

    ![Søjlediagram over pull-anmodninger pr. måned](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Vælg et brugernavn i diagrammet **Samlede pull-anmodninger pr. bruger**. I dette eksempel kan vi se, at de fleste af deres timer var i februar.

    ![Fremhævelse af GitHub-rapport i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Vælg fanen **Hulkort** for at få vist den næste side i rapporten. 
 
    ![Hulkort for GitHub-rapport i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Det ser ud til, at tirsdag kl. 15 er det mest almindelige tidspunkt og den mest almindelige dag i ugen til *bekræftelser*, når medarbejdere tjekker deres arbejde ind.

## <a name="clean-up-resources"></a>Fjern ressourcer

Nu, hvor du har gennemført selvstudiet, kan du slette GitHub-appen. 

1. Vælg **Apps** i navigationsruden.
2. Peg på GitHub-feltet, og vælg **Slet** ud for skraldespanden.

    ![Slet GitHub-appen](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Næste trin

I dette selvstudie har du oprettet forbindelse til et offentligt GitHub-lager og hentet data, som Power BI har formateret på et dashboard og i en rapport. Du har besvaret nogle spørgsmål om dataene ved at udforske dashboardet og rapporten. Nu kan du få mere at vide om at oprette forbindelse til andre tjenester, f.eks. Salesforce, Microsoft Dynamics og Google Analytics. 
 
> [!div class="nextstepaction"]
> [Opret forbindelse til GitHub med en skabelonapp i Power BI](service-connect-to-github.md)
