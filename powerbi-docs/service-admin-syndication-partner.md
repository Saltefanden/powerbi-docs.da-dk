---
title: "Det var ikke muligt at føje Power BI til O365-partner"
description: "Det var ikke muligt at føje Power BI til en Office 365-syndikeringspartner. Den syndikerede model er en indkøbsmodel, der bruges af Office 365."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 09/05/2017
ms.author: asaxton
ms.openlocfilehash: e5b2540461464e64acac4bc3b2be2e6ac5ee3f1d
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/13/2017
---
# <a name="unable-to-add-power-bi-to-office-365-partner-subscription"></a>Det var ikke muligt at føje Power BI til en partners Office 365-abonnement
Office 365 giver virksomheder mulighed for at forhandle Office 365 samlet og integreret med deres egne løsninger, hvorved slutkunder får adgang til et enkelt kontaktpunkt for køb, fakturering og support.

Hvis du er interesseret i at købe Power BI sammen med dit Office 365-abonnement, så anbefaler vi dig at kontakte din partner i denne forbindelse. Hvis din partner ikke tilbyder Power BI, så kan du benytte dig af nogle andre muligheder.

1. Du kan købe tjenesten via en anden kanal, enten direkte fra Microsoft eller en anden partner. Denne mulighed er ikke tilgængelig for alle kunder, alt afhængigt af deres relation til partneren. Du kan bekræfte dette ved at gå til **Office 365-administrationsportalen** > **Fakturering** > **Abonnementer**. Hvis du får vist **Abonnementer**, kan du købe tjenesten direkte af Microsoft, eller du kan også kontakte en partner, der tilbyder Power BI.
   
    ![](media/service-admin-syndication-partner/billingsub.png)
2. Hvis **Abonnementer** ikke er angivet under **Fakturering**, kan du ikke købe direkte fra Microsoft eller nogen anden partner. 
   
   ![](media/service-admin-syndication-partner/billing.png)

Hvis du ikke kan købe Power BI direkte, og alt afhængigt af hvilken type af Power BI-abonnement du er interesseret i, kan du stadig benytte dig af visse muligheder.

[Power BI (gratis)](#power-bi-free)

[Power BI Pro og Premium](#power-bi-pro)

## <a name="power-bi-free"></a>Power BI (gratis)
Hvis du er tilfreds med den gratis version af Power BI, kan du tilmelde dig den gratis tjeneste. Som standard er individuelle tilmeldinger, også kaldet ad-hoc-abonnementer, deaktiveret. Når du forsøger at tilmelde dig Power BI, får du vist en meddelelse om, at it-afdelingen har slået tilmelding til Microsoft Power BI fra.

    Your IT department has turned off signup for Microsoft Power BI.

![](media/service-admin-syndication-partner/sorry.png)

Hvis du vil aktivere ad hoc-abonnementer, kan du kontakte din partner og anmode om at få aktiveret dem. Hvis du er administrator for din lejer, og du ved, hvordan du benytter Azure Active Directory PowerShell-kommandoer, så kan du selv aktivere ad-hoc-abonnementer. [Få mere at vide](https://technet.microsoft.com/library/jj151815.aspx)

1. Du skal først logge på Azure Active Directory ved hjælp af dine legitimationsoplysninger til Office 365. Den første linje beder dig om dine legitimationsoplysninger. Den anden linje opretter forbindelse til Azure Active Directory.
   
        $msolcred = get-credential
        connect-msolservice -credential $msolcred
   
    ![](media/service-admin-syndication-partner/aad-signin.png)
2. Når du er logget på, kan du udstede følgende kommando for at aktivere gratis tilmeldinger.
   
        Set-MsolCompanySettings -AllowAdHocSubscriptions $true

## <a name="power-bi-pro-and-premium"></a>Power BI Pro og Premium
Hvis du vil købe et abonnement af Power BI Pro eller Power BI Premium, skal du i samarbejde med din partner overveje dine muligheder.

* Din partner kan acceptere at føje Power BI til sin portefølje, så du kan købe af den pågældende partner.
* Din partner kan lade dig overgå til en model, hvor du kan købe Power BI direkte af Microsoft eller en anden partner, som tilbyder Power BI.

Denne video handler om Office 365-syndikering og køb af Power BI:

<iframe width="560" height="315" src="https://www.youtube.com/embed/C357phT94A8" frameborder="0" allowfullscreen></iframe>

## <a name="next-steps"></a>Næste trin
[Administrer Azure AD ved hjælp af Windows PowerShell](https://technet.microsoft.com/library/jj151815.aspx)  
[Power BI Premium – hvad er det?](service-premium.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](http://community.powerbi.com/)
