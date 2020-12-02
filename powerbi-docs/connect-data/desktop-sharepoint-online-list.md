---
title: Opret en rapport på en SharePoint-liste
description: Dette selvstudium viser, hvordan du kan transformere dine SharePoint-listedata til en Power BI-rapport.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/10/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 5347405c13f71fa0932c48eb218618b28a9f03c8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404519"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>Opret en rapport på en SharePoint-liste

Mange teams og organisationer bruger lister i SharePoint Online til at lagre data, da det er nemt at konfigurere og nemt for brugerne at opdatere dem.  Nogle gange er et diagram en meget nemmere måde, så brugerne hurtigt kan forstå dataene i stedet for at se selve listen. I dette selvstudium viser vi, hvordan du kan transformere dine SharePoint-listedata til en Power BI-rapport.

Se denne 5-minutters instruktionsvideo, eller rul ned for at få en trinvis vejledning.

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>Del 1: Opret forbindelse til din SharePoint-liste

1. Hvis du ikke allerede har Power BI Desktop, kan du [downloade](https://powerbi.microsoft.com/desktop/) og installere det.
2. Åbn Power BI Desktop, og vælg **Hent data** > **Mere** på fanen Hjem på båndet.
3. Vælg **Online Services**, og vælg derefter **SharePoint Online-liste**.  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="Screenshot shows the Get Data dialog box with Online Services selected." width="350"/>

4. Vælg **Opret forbindelse**.
4. Find adressen (også kendt som en URL-adresse) for dit SharePoint Online-websted, der indeholder listen.  På en side i SharePoint Online kan du som regel få webstedsadressen ved at vælge **Hjem** i navigationsruden eller ikonet for webstedet øverst og derefter kopiere adressen fra adresselinjen i webbrowseren.

   Se en video om dette trin:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. Indsæt adressen i feltet **URL-adresse for websted** i den åbne dialogboks i Power BI Desktop.

6. Du kan muligvis se en SharePoint-adgangsskærm som på følgende billede.  Hvis du ikke kan se den, skal du gå til trin 10.  Hvis du kan se den, skal du vælge **Microsoft-konto** til venstre på siden.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. Vælg **Log på**, og angiv det brugernavn og den adgangskode, du bruger til at logge på Microsoft 365.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. Når du er færdig med at logge på, skal du vælge **Opret forbindelse**.

9. I venstre side af navigatoren skal du markere afkrydsningsfeltet ud for den SharePoint-liste, du vil oprette forbindelse til.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="Screenshot shows the Navigator page with BudgetRequests selected." width="450"/>

10. Vælg **Indlæs**.  Power BI indlæser listedataene i en ny rapport.

## <a name="part-2-create-a-report"></a>Del 2: Opret en rapport

1. I venstre side skal du vælge ikonet **data** for at se, om dine SharePoint-listedata blev indlæst.

2. Sørg for, at dine listekolonner med tal viser sum- eller Sigma-ikonet i ruden **Felter** til højre.  Hvis der er nogle kolonner, hvor det ikke er tilfældet, skal du vælge kolonneoverskriften i tabelvisningen, vælge fanen **Udformning** og derefter ændre **datatype** til **decimaltal** eller **heltal**, afhængigt af dataene.  Hvis du bliver bedt om at bekræfte ændringen, skal du vælge **Ja**.  Hvis dit tal har et særligt format, f.eks. valuta, kan du også vælge det ved at angive **Format**.

   Se en video om dette trin:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. Vælg ikonet **Rapport** i venstre side.
4. Vælg de kolonner, du vil visualisere, ved at markere afkrydsningsfeltet ud for dem i ruden **Felter** til højre.

   Se en video om dette trin:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. Skift visualiseringstype, hvis du vil det.
6. Du kan oprette flere visualiseringer i den samme rapport ved at fjerne markeringen af den eksisterende visualisering og derefter markere afkrydsningsfelter ud for andre kolonner i ruden **Felter**.
7. Vælg **Gem** for at gemme din rapport.
