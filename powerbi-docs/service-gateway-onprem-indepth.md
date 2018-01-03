---
title: "Datagateway i det lokale miljø – detaljeret"
description: "Denne artikel ser detaljeret på gatewayen i det lokale miljø. Vi ser på, hvordan tjenesten fungerer sammen med Azure Active Directory og dit lokale Active Directory, når du arbejder med Analysis Services"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: fbb1b22b930a00fa9e090b3ebc5ab9fd1ffc88c0
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/06/2017
---
# <a name="on-premises-data-gateway-in-depth"></a>Datagateway i det lokale miljø – detaljeret
Det er muligt for brugere i din organisation at få adgang til lokale data (som de allerede er godkendt til at få adgang til), men før disse brugere kan oprette forbindelse til datakilden i det lokale miljø, skal en lokal datagateway installeres og konfigureres. Gatewayen muliggør hurtig og sikker kommunikation bag kulisserne mellem en bruger i clouden, til din lokale datakilde og derefter tilbage til clouden.

Installation og konfiguration af en gateway foretages normalt af en administrator. Der kræves muligvis særlig viden om dine lokale servere, og administratortilladelser til serveren kan i nogle tilfælde være påkrævet.

Denne artikel er ikke en trinvis vejledning i, hvordan du installerer og konfigurerer gatewayen. Se [Datagateway i det lokale miljø](service-gateway-onprem.md) for at få oplysninger om dette. I denne artikel får du en detaljeret beskrivelse af, hvordan gatewayen virker. Vi vil også i et vist omfang beskæftige os detaljeret med brugernavne og sikkerhed i både Azure Active Directory og Analysis Services, samt hvordan cloudtjenesten bruger mailadressen, som en bruger logger på med, gatewayen og Active Directory til sikkert at oprette forbindelse til og forespørge på dine lokale data.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>Logonkonto
Brugere skal logge på med enten en arbejds- eller skolekonto. Dette er din organisationskonto. Hvis du har tilmeldt dig et tilbud på Office 365 og ikke angav din rigtige arbejdsmailadresse, kan den se ud som nancy@contoso.onmicrosoft.com. På en cloudtjeneste gemmes din konto i en lejer i Azure Active Directory (AAD). I de fleste tilfælde vil AAD-kontoens UPN svare til mailadressen.

## <a name="authentication-to-on-premises-data-sources"></a>Godkendelse til datakilder i det lokale miljø
Gemte legitimationsoplysninger bruges til at oprette forbindelse til lokale datakilder fra gatewayen bortset fra Analysis Services. Gatewayen anvender de gemte legitimationsoplysninger til at oprette forbindelse, uanset den enkelte bruger.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Godkendelse til en live Analysis Services-datakilde
Hver gang en bruger interagerer med Analysis Services, overføres det effektive brugernavn til gatewayen og derefter til den lokale Analysis Services-server. Brugerens hovednavn (UPN), typisk den mailadresse, du logger på clouden med, er det, vi sender til Analysis Services som den effektive bruger. UPN'et overføres i forbindelsesegenskaben EffectiveUserName. Denne mailadresse skal svare til et UPN, der er defineret i det lokale Active Directory-domæne. UPN'et er en egenskab for en Active Directory-konto. Den pågældende Windows-konto skal være til stede i en Analysis Services-rolle for at have adgang til serveren. Hvis der ikke findes et match i Active Directory, kan der ikke logges på.

Analysis Services kan også levere filtrering baseret på denne konto. Filtreringen kan finde sted med rollebaseret sikkerhed eller sikkerhed på rækkeniveau.

## <a name="role-based-security"></a>Rollebaseret sikkerhed
Modeller giver sikkerhed, som er baseret på brugerroller. Roller er defineret for et bestemt modelprojekt under oprettelse i SQL Server Data Tools – Business Intelligence (SSDT BI), eller når en model er installeret, ved hjælp af SQL Server Management Studio (SSMS). Roller indeholder medlemmer efter Windows-brugernavn eller efter Windows-gruppe. Roller definerer tilladelser, som en bruger har til at forespørge på eller udføre handlinger på modellen. De fleste brugere vil tilhøre en rolle med læsetilladelser. Andre roller er beregnet til administratorer med tilladelser til at behandle elementer, administrere databasefunktioner og administrere andre roller.

## <a name="row-level-security"></a>Sikkerhed på rækkeniveau
Sikkerhed på rækkeniveau er specifik for Analysis Services-sikkerhed på rækkeniveau. Modeller kan levere dynamisk sikkerhed på rækkeniveau. I modsætning til at have mindst én rolle, som brugere tilhører, er dynamisk sikkerhed ikke påkrævet for en tabelmodel. På et højt niveau definerer dynamisk sikkerhed en brugers læseadgang til data helt ned til en bestemt række i en bestemt tabel. I lighed med roller er dynamisk sikkerhed på rækkeniveau afhængig af en brugers Windows-brugernavn.

En brugers mulighed for at forespørge på og få vist data i modellen bestemmes først af de roller, som deres Windows-brugerkonto er medlem af, og derefter af dynamisk sikkerhed på rækkeniveau, hvis det er konfigureret.

Det er uden for denne artikels omfang at drøfte implementering af roller og dynamisk sikkerhed på rækkeniveau i modeller.  Du kan få yderligere oplysninger i [Roller (SSAS-tabel)](https://msdn.microsoft.com/library/hh213165.aspx) og [Sikkerhedsroller (Analysis Services – flerdimensionelle data)](https://msdn.microsoft.com/library/ms174840.aspx) på MSDN. Og for den mest detaljerede beskrivelse af sikkerhed med tabelmodel kan du downloade og læse hvidbogen Securing the [Tabular BI Semantic Model](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>Hvad med Azure Active Directory?
Microsoft-cloudtjenester bruger [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) til at godkende brugere. Azure Active Directory er lejeren, der indeholder brugernavne og sikkerhedsgrupper. Typisk er den mailadresse, som en bruger logger på med, den samme som kontoens UPN.

Hvad er min lokale Active Directory-rolle?

For at Analysis Services kan bestemme, om en bruger, der opretter forbindelse til den, tilhører en rolle med tilladelser til at læse data, skal serveren konvertere det effektive brugernavn, der sendes fra AAD til gatewayen og videre til Analysis Services-serveren. Analysis Services-serveren overfører det effektive brugernavn til en Windows Active Directory-domænecontroller (DC). Active Directory-domænecontrolleren validerer derefter, at det effektive brugernavn er et gyldigt UPN, på en lokal konto, og returnerer den pågældende brugers Windows-brugernavn til Analysis Services-serveren.

EffectiveUserName kan ikke bruges på en Analysis Services-server, der ikke er tilsluttet et domæne. Analysis Services-serveren skal tilsluttes et domæne for at undgå eventuelle logonfejl.

## <a name="how-do-i-tell-what-my-upn-is"></a>Hvordan kan jeg se, hvad mit UPN er?
Du ved måske ikke, hvad dit UPN er, og du er muligvis ikke domæneadministrator. Du kan bruge følgende kommando fra din arbejdsstation til at finde frem til UPN'et for din konto.

    whoami /upn

Resultatet ligner en mailadresse, men det er det UPN, der er på din lokale domænekonto. Hvis du bruger en Analysis Services-datakilde til live forbindelser, skal det matche, hvad der blev sendt til EffectiveUserName fra gatewayen.

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Tilknyt brugernavne for Analysis Services-datakilder
I Power BI kan brugernavne tilknyttes for Analysis Services-datakilder. Du kan konfigurere regler for at knytte et brugernavn, der er logget på med Power BI, til et navn, der er sendt for EffectiveUserName på Analysis Services-forbindelsen. Funktionen til tilknytning af brugernavne er god måde at løse problemet på, når dit brugernavn i AAD ikke stemmer overens med et UPN i dit lokale Active Directory. Hvis din mailadresse for eksempel er nancy@contoso.onmicrsoft.com, kan du knytte den til nancy@contoso.com, og denne værdi vil blive overført til gatewayen. Du kan få mere at vide mere om, hvordan du [tilknytter brugernavne](service-gateway-enterprise-manage-ssas.md#map-user-names).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synkroniser en lokal Active Directory med Azure Active Directory
Dine lokale Active Directory-konti skal stemme overens med Azure Active Directory, hvis du vil bruge live Analysis Services-forbindelser. Da UPN skal matche mellem kontiene.

Cloudtjenesterne kender kun til konti på Azure Active Directory. Det har ingen betydning, hvis du har tilføjet en konto i dit lokale Active Directory. Hvis den ikke findes i AAD, kan den ikke bruges. Du kan matche dine lokale Active Directory-konti med Azure Active Directory på forskellige måder.

1. Du kan føje konti manuelt til Azure Active Directory.
   
   Du kan oprette en konto på Azure-portalen eller i Office 365-administrationsportalen, og kontonavnet matcher UPN i den lokale Active Directory-konto.
2. Du kan bruge værktøjet [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) til at synkronisere lokale konti med din Azure Active Directory-lejer.
   
   Værktøjet Azure AD Connect indeholder indstillinger til synkronisering af kataloger og adgangskoder. Hvis du ikke er administrator af lejere eller lokal domæneadministrator, skal du kontakte it-administratoren for at få dette konfigureret.
3. Du kan konfigurere ADFS (Active Directory Federation Services).
   
   Du kan knytte din ADFS-server til din AAD-lejer med værktøjet [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/). ADFS gør brug af katalogsynkronisering beskrevet ovenfor, men giver mulighed for enkeltlogon (SSO). Hvis du f.eks. er på dit arbejdsnetværk, når du opretter forbindelse til en cloudtjeneste, og går til logon, bliver du muligvis ikke bedt om at angive et brugernavn eller en adgangskode. Du skal drøfte med din it-administrator, om dette er tilgængeligt for din organisation.

Ved at bruge Azure AD Connect sikrer du, at UPN'et matcher mellem AAD og dit lokale Active Directory.

> [!NOTE]
> Når konti synkroniseres med værktøjet Azure AD Connect, oprettes der nye konti i din AAD-lejer.
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>Her kommer så gatewayen ind i billedet
Gatewayen fungerer som en bro mellem clouden og din lokale server. Dataoverførsler mellem clouden og gatewayen sikres ved hjælp af [Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/). Service Bus opretter en sikker kanal mellem clouden og serveren i det lokale miljø via en udgående forbindelse på gatewayen.  Der er ingen indgående forbindelser, som du skal åbne på firewallen i det lokale miljø.

Hvis du har en Analysis Services-datakilde, skal du installere gatewayen på en computer, der er tilsluttet det samme område/domæne som din Analysis Services-server.

Jo tættere gatewayen er på serveren, desto hurtigere er forbindelsen. Hvis du kan få gatewayen på den samme server som datakilden, vil det være det bedste for at undgå netværksventetid mellem gatewayen og serveren.

## <a name="what-to-do-next"></a>Hvad skal du så gøre?
Når du har fået gatewayen installeret, skal du oprette datakilder til denne gateway. Du kan tilføje datakilder på skærmen **Administrer gateways**. Du kan finde flere oplysninger i artiklerne om at administrere datakilder.

[Administrer din datakilde – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Administrer din datakilde – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Administrer din datakilde – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Administrer din datakilde – Oracle](service-gateway-onprem-manage-oracle.md)  
[Administrer din datakilde – Import/Planlagt opdatering](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Hvor ting kan gå galt
Installation af gatewayen mislykkes af og til. Eller måske ser det ud til, at gatewayen blev installeret korrekt, men tjenesten stadig ikke kan arbejde med den. Det er i mange tilfælde noget enkelt som f.eks. adgangskoden til de legitimationsoplysninger, som gatewayen bruger til at logge på datakilden.

I andre tilfælde kan der være problemer med den type af mailadresse, som brugere logger på med, eller Analysis Services kan ikke fortolke et effektivt brugernavn. Hvis du har flere domæner med tillidsforhold mellem dem, og din gateway er i ét domæne og Analysis Services i et andet, kan det sommetider medføre nogle problemer.

I stedet for at beskrive fejlfinding af gatewayen her har vi lagt en række fejlfindingstrin ind i en anden artikel. [Fejlfinding af datagateway i det lokale miljø](service-gateway-onprem-tshoot.md). Forhåbentlig får du ikke problemer. Men hvis du gør, bør det være en hjælp at forstå, hvordan det fungerer, og det samme gælder artiklen om fejlfinding.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>Næste trin
[Fejlfinding af datagateway i det lokale miljø](service-gateway-onprem-tshoot.md)  
[Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/)  
[Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)  
Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](http://community.powerbi.com/)
