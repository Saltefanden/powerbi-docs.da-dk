---
title: Fjernkonfigurer mobilappadgang til rapportserveren
description: Få mere at vide om, hvordan du fjernkonfigurerer mobilappadgang til din rapportserver.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: 996e3835337ce8aa1002abce7682d707daec032e
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859123"
---
# <a name="configure-power-bi-mobile-app-access-to-report-server-remotely"></a>Konfigurer Power BI-mobilapps eksternt for rapportservere

Gælder for:

| ![iPhone](./media/configure-powerbi-mobile-apps-remote/ios-logo-40-px.png) | ![Android-telefon](./media/configure-powerbi-mobile-apps-remote/android-logo-40-px.png) |
|:--- |:--- |
| iOS |Android |

I denne artikel kan du se, hvordan du bruger din organisations MDM-værktøj til at konfigurere adgang til rapportserveren for Power BI-mobilapps. Det kræver, at it-administratorer opretter en appkonfigurationspolitik, hvor de nødvendige oplysninger pushes til appen. 

 Når rapportserverforbindelsen allerede er oprettet, kan brugerne af Power BI-mobilappen nemmere oprette forbindelse til organisationens rapportserver. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Opret appkonfigurationspolitikken i MDM-værktøjet 

Som administrator skal du følge disse trin i Microsoft Intune for at oprette appkonfigurationspolitikken. Trinnene og oprettelsen af appkonfigurationspolitikken kan være anderledes i andre MDM-værktøjer. 

1. Opret forbindelse til dit MDM-værktøj. 
2. Opret og navngiv en ny appkonfigurationspolitik. 
3. Vælg, hvilke brugere appkonfigurationspolitikken skal distribueres til. 
4. Opret nøgle/værdi-par. 

I følgende tabel kan du se disse par.

|Nøgle  |Type  |Beskrivelse  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL-adresse | Streng | URL-adresse til rapportserver <br> Skal starte med http/https |
| com.microsoft.powerbi.mobile.ServerBrugernavn | Streng | [valgfri] <br> Det brugernavn, der skal bruges til at oprette forbindelse til serveren. <br> Hvis der ikke findes et brugernavn, vil appen bede brugeren skrive brugernavnet til forbindelsen.| 
| com.microsoft.powerbi.mobile.ServerVist navn | Streng | [valgfri] <br> Standardværdien er "Rapportserver" <br> Et navn, der bruges til at repræsentere serveren i appen | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | Standardværdien er True <br>Når værdien er angivet til "True", tilsidesætter den alle eksisterende rapportserverdefinitioner på mobilenheden. Eksisterende servere, der allerede er konfigureret, slettes. <br> Dette forhindrer også, at brugeren kan fjerne konfigurationen. <br> Hvis indstillingen er angivet til “False”, tilføjes de overførte værdier, og eksisterende indstillinger ændres ikke. <br> Hvis den samme URL-adresse allerede er konfigureret i mobilappen, forbliver konfigurationen, som den er. Appen beder ikke brugeren om at godkende igen for den samme server. |

Her er et eksempel på, hvordan du indstiller konfigurationspolitikken ved hjælp af Intune.

![Intune-konfiguratonsindstillinger](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-report-server"></a>Slutbrugere opretter forbindelse til rapportserveren

 Lad os sige, at du publicerer appkonfigurationspolitikken for en distributionsliste. Når brugerne og enhederne på den pågældende distributionsliste starter mobilappen, oplever de følgende: 

1. De får vist en meddelelse om, at mobilappen er konfigureret med en rapportserver og skal trykke på **Log på**.

    ![Log på rapportserveren](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Detaljerne om rapportserveren er allerede udfyldt på siden **Opret forbindelse til server**. De trykker på **Opret forbindelse**.

    ![Rapportserveroplysningerne er udfyldt](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. De indtaster en adgangskode som godkendelse og trykker derefter på **Log på**. 

    ![Rapportserveroplysningerne er udfyldt](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Nu kan de få vist og interagere med KPI'er og Power BI-rapporter på rapportserveren.

## <a name="next-steps"></a>De næste trin

- [Aktivér fjernadgang til Power BI - Mobil med Azure AD-programproxy](/azure/active-directory/manage-apps/application-proxy-integrate-with-power-bi)
- [Administratoroversigt](admin-handbook-overview.md)  
- [Installér Power BI-rapportserver](install-report-server.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)