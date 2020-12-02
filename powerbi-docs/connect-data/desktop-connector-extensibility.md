---
title: Forbindelsesudvidelse i Power BI
description: Forbindelsesudvidelse, funktioner, sikkerhedsindstillinger og certificerede forbindelser
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 01/02/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 6b78309ad17446aabacd39006968b6d397a51037
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411235"
---
# <a name="connector-extensibility-in-power-bi"></a>Forbindelsesudvidelse i Power BI

Power BI kan oprette forbindelse til data ved hjælp af eksisterende connectors og generiske datakilder, f.eks. ODBC, OData, OLE DB, web, CSV, XML og JSON. Udviklere kan også aktivere nye datakilder med brugerdefinerede dataudvidelser, der kaldes *brugerdefinerede connectors*. Nogle brugerdefinerede connectors certificeres og distribueres af Microsoft som *certificerede connectors*.

Hvis du vil bruge ikke-certificerede brugerdefinerede connectors, som du eller en tredjepart har udviklet, skal du justere sikkerhedsindstillingerne for Power BI Desktop, så du tillader udvidelser at blive indlæst uden validering eller advarsel. Eftersom denne kode kan håndtere legitimationsoplysninger, herunder at sende dem via HTTP, og ignorere niveauer for beskyttelse af personlige oplysninger, skal du kun bruge denne sikkerhedsindstilling, hvis du har fuld tillid til dine brugerdefinerede connectors.

En anden mulighed er, at udvikleren skal signere connectoren med et certifikat og angive de oplysninger, du har brug for, for at kunne bruge den uden at ændre dine sikkerhedsindstillinger. Du kan få flere oplysninger under [Om tredjepartsconnectors, der er tillid til](desktop-trusted-third-party-connectors.md).

## <a name="custom-connectors"></a>Brugerdefinerede connectorer

Ikke-certificerede brugerdefinerede connectors kan variere fra små API'er, som er vigtige for din virksomhed, til store branchespecifikke tjenester, som Microsoft ikke har frigivet en connector til. Mange connectors distribueres af leverandører. Hvis du skal bruge en bestemt dataconnector, skal du kontakte leverandøren. 

Hvis du vil bruge en ikke-certificeret brugerdefineret connector, skal du placere filen *.pq*, *.pqx*, *.m* eller *.mez* i mappen *\[Dokumenter]\\Power BI Desktop\\Brugerdefinerede connectors*. Hvis ikke mappen findes, skal du oprette den.

Juster sikkerhedsindstillingerne for dataudvidelsen på følgende måde:

Vælg **Filer** > **Indstillinger** > **Indstillinger** > **Sikkerhed** i Power BI Desktop.

Under **Dataudvidelser** skal du vælge **(Anbefales ikke) Tillad indlæsning af en hvilken som helst udvidelse uden validering eller advarsel**. Vælg **OK**, og genstart derefter Power BI Desktop. 

![Tillad ikke-certificerede brugerdefinerede connectors i sikkerhedsindstillinger for dataudvidelse](media/desktop-connector-extensibility/data-extension-security-1.png)

Standardindstillingen for dataudvidelser i Power BI Desktop er **(anbefales) Giv kun Microsoft Certified og andre pålidelige tredjepartsudvidelser tilladelse til at indlæse**. Hvis der er ikke-certificerede brugerdefinerede connectors på dit system, vises dialogboksen **Ikke-certificerede connectors** i forbindelse med denne indstilling, ved start af Power BI Desktop og viser de connectors, der ikke kan indlæses korrekt.

![Dialogboksen Ikke-certificerede connectors](media/desktop-connector-extensibility/data-extension-security-2.png)

Hvis du vil løse fejlen, kan du enten ændre sikkerhedsindstillingerne for dine **Dataudvidelser** eller fjerne de ikke-certificerede connectors fra mappen *Brugerdefinerede connectors*.

## <a name="certified-connectors"></a>Certificerede forbindelser

Et begrænset undersæt af dataudvidelser anses som *certificerede*. Selvom Microsoft distribuerer disse connectors, er de ikke ansvarlige for deres ydeevne og fortsatte funktion. Den tredjepartsudvikler, der oprettede connectoren, er ansvarlig for dens vedligeholdelse og support. 

I Power BI Desktop vises certificerede tredjepartsconnectors på listen i dialogboksen **Hent data** sammen med generiske og almindelige connectors. Du behøver ikke at justere sikkerhedsindstillingerne for at bruge certificerede connectors.

Hvis du vil certificere en brugerdefineret connector, skal du bede din leverandør om at kontakte dataconnectors@microsoft.com.
