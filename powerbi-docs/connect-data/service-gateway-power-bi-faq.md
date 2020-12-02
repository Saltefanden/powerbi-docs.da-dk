---
title: Ofte stillede spørgsmål om datagatewayen i det lokale miljø – Power BI
description: Denne artikel handler om ofte stillede spørgsmål om datagatewayen i det lokale miljø til Power BI. Denne artikel samler ofte stillede spørgsmål om den gateway, der bruges i Power BI, på ét sted.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: f9a51e6150c7ae351cea968c0d7ea39d2d0d6c32
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392214"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Ofte stillede spørgsmål om datagatewayen i det lokale miljø – Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Spørgsmål:** Skal jeg opgradere datagatewayen i det lokale miljø (personlig tilstand)?

**Svar:** Nej, du kan blive ved med at bruge gatewayen (personlig tilstand) til Power BI.

**Spørgsmål:** Kræves der specialtilladelser for at installere gatewayen og administrere den i Power BI-tjenesten?

**Svar:** Der kræves ingen specialtilladelser.

**Spørgsmål:** Kan jeg uploade Excel-projektmapper med Power Pivot-datamodeller, der opretter forbindelse til datakilder i det lokale miljø? Har jeg brug for en gateway til dette scenarie? 

**Svar:** Ja, du kan uploade projektmapper. Og nej, du behøver ikke en gateway. Men eftersom dataene vil være placeret i Excel-datamodellen, vil rapporter i Power BI, der er baseret på Excel-projektmappen, ikke være dynamiske. For at opdatere rapporter i Power BI skal du hver gang uploade en opdateret projektmappe igen. Eller bruge gateway'en med planlagt opdatering.

**Spørgsmål:** Hvis brugerne deler dashboards, der har en DirectQuery-forbindelse, vil de andre brugere så kunne se dataene, også selvom de måske ikke har de samme tilladelser? 

**Svar:** For et dashboard forbundet til Azure Analysis Services kan brugerne kun se de data, de har adgang til. Hvis brugerne ikke har de samme tilladelser, vil de ikke kunne se nogen data. Alle brugere vil dele de legitimationsoplysninger, der er angivet af administratoren for den pågældende datakilde, for andre datakilders vedkommende.

**Spørgsmål:** Hvorfor kan jeg ikke oprette forbindelse til Oracle-serveren? 

**Svar:** Du skal muligvis installere Oracle-klienten og konfigurere tnsnames.ora-filen med oplysninger om den korrekte server for at oprette forbindelse til Oracle-serveren. Dette er en separat installation uden for gateway'en. Du kan finde flere oplysninger under [Installér Oracle-klienten](service-gateway-onprem-manage-oracle.md#install-the-oracle-client).

**Spørgsmål:** Jeg bruger R-script. Understøttes det?

**Svar**: R-scripts understøttes kun i forbindelse med personlig tilstand.

## <a name="analysis-services-in-power-bi"></a>Analysis Services i Power BI

**Spørgsmål:** Kan jeg bruge msmdpump.dll til at oprette brugerdefinerede effektive brugernavnstilknytninger til Analysis Services? 

**Svar:** Nej. Denne brug understøttes ikke på nuværende tidspunkt.

**Spørgsmål:** Kan jeg bruge gatewayen til at oprette forbindelse til en flerdimensionel (OLAP) forekomst? 

**Svar:** Ja. Datagateway'en i lokalt miljø understøtter dynamiske forbindelser til såvel Analysis Services-tabelmodeller som flerdimensionelle modeller.

**Spørgsmål:** Hvad sker der, hvis jeg installerer gatewayen på en computer med et andet domæne end min lokale server, der bruger Windows-godkendelse? 

**Svar:** Vi garanterer ikke noget i dette tilfælde. Det afhænger alt sammen af tillidsforholdet mellem de to domæner. Hvis de to forskellige domæner er i en pålidelig domænemodel, er gateway'en muligvis i stand til at oprette forbindelse til Analysis Services-serveren, og det effektive brugernavn kan løses. Hvis det ikke er tilfældet, kan der opstå en loginfejl.

**Spørgsmål:** Hvordan kan jeg finde ud af, hvilket effektivt brugernavn der overføres til min lokale Analysis Services-server? 

**Svar:** Vi har svaret på dette spørgsmål i artiklen om [Fejlfinding](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Næste trin

* [Fejlfinding af datagateway i det lokale miljø](/data-integration/gateway/service-gateway-tshoot)

Har du flere spørgsmål? Prøv at spørge [Power BI-community'et](https://community.powerbi.com/).
