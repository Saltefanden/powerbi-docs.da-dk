---
title: Always Encrypted på Microsoft Power BI-rapportserveren
description: Denne artikel indeholder en detaljeret beskrivelse af Always Encrypted-understøttelse på Power BI-rapportserveren, når du brugerdatakildetyperne Microsoft SQL Server og Microsoft Azure SQL Database.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.openlocfilehash: 4851a20ecd406ffe2a460ba52833cca420b517da
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415536"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Always Encrypted på Microsoft Power BI-rapportserveren

Denne artikel indeholder en detaljeret beskrivelse af Always Encrypted-understøttelse på Power BI-rapportserveren, når du brugerdatakildetyperne Microsoft SQL Server og Microsoft Azure SQL Database. Du kan finde flere oplysninger om Always Encrypted-funktioner i SQL Server i artiklen [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine).

## <a name="always-encrypted-user-isolation"></a>Always Encrypted-brugerisolation

På nuværende tidspunkt begrænser Microsoft Power BI-rapportserveren ikke adgangen til Always Encrypted-kolonner i rapporter, hvis en bruger har adgang til rapporten.  Det betyder, at hvis serveren har fået adgang til kolonnekrypteringsnøglerne via kolonnens masternøgle, har brugerne adgang til alle kolonnerne for de rapporter, de har adgang til.

## <a name="always-encrypted-column-usage"></a>Always Encrypted-kolonnebrug

### <a name="key-storage-strategies"></a>Vigtige lagringsstrategier

|Lager  |Understøttet  |
|---------|---------|
|Windows-certifikatlager | Ja |
|Azure Key Vault | Nej |
| CNG (Cryptography Next Generation) | Nej |

### <a name="certificate-storage-and-access"></a>Certifikatlagring og -adgang

Den konto, der kræver adgang til certifikatet, er tjenestekontoen. Certifikatet skal gemmes i certifikatlageret på den lokale computer. Her finder du flere oplysninger:

- [Konfigurer kontoen til rapportservertjenesten](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- Afsnittet [Making certificates available to applications and users](/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) i SQL Server-artiklen "Create and store column master keys for Always Encrypted".

### <a name="column-encryption-strategy"></a>Kolonnekrypteringsstrategi

På Microsoft Power BI-rapportserveren kan kolonnekrypteringsstrategien være *deterministisk* eller *tilfældig*. Følgende tabel indeholder en detaljeret oversigt af forskellene, afhængigt af hvilken strategi der bruges.

|Brug  |Deterministisk  |Tilfældig  |
|---------|---------|---------|
|Kan skrives som den er i resultaterne af en forespørgsel, f. eks. SELECT-sætninger. | Ja  | Ja  |
|Kan bruges som et Group by-objekt i forespørgslen. | Ja | Nej |
|Kan bruges som et sammenlægningsfelt, bortset fra COUNT og DISTINCT. | Nej, med undtagelse af COUNT og DISTINCT | Nej |
|Kan bruges som rapportparameter | Ja | Nej |

Læs mere om [deterministisk vs. tilfældige kryptering](/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Parameterbrug

Parameterbrug gælder kun for deterministisk kryptering.

**Parameter med en enkelt værdi**.  Du kan bruge en parameter med en enkelt værdi mod en Always Encrypted-kolonne.

**Parameter med flere værdier**. Du kan ikke bruge en parameter med flere værdier mod en Always Encrypted kolonne.

**Overlappende parametre**. Du kan bruge overlappende parametre med Always Encrypted, hvis *alle* følgende udsagn er sande:

- Alle Always Encrypted-kolonner skal være Always Encrypted med deterministisk strategi.
- Alle parametre, der bruges mod Always Encrypted-kolonner, er parametre med en enkelt værdi.
- Alle SQL-sammenligninger bruger operatoren Equals (=).

## <a name="datatype-support"></a>Understøttelse af datatyper

| SQL-datatype | Understøtter læsefelt | Understøtter brug som Gruppér efter-element | Understøttede sammenlægninger (COUNT, DISTINCT, MAX, MIN, SUM osv.) | Understøtter filtrering via lighed ved hjælp af parametre | Noter |
| --- | --- | --- | --- | --- | --- |
| int | Ja | Ja | COUNT, DISTINCT | Ja, som heltal |   |
| float | Ja | Ja | COUNT, DISTINCT | Ja, som flydende |   |
| nvarchar | Ja | Ja | COUNT, DISTINCT | Ja, som tekst | Deterministisk kryptering skal bruge en kolonnesortering med en binary2-sorteringsrækkefølge for tegnkolonner. Se SQL Server-artiklen [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) for at få flere oplysninger.  |
| varchar | Ja | Ja | COUNT, DISTINCT | Nej |   |
| decimal | Ja | Ja | COUNT, DISTINCT | Nej |   |
| numeric | Ja | Ja | COUNT, DISTINCT | Nej |   |
| dato og klokkeslæt | Ja | Ja | COUNT, DISTINCT | Nej |   |
| datetime2 | Ja | Ja | COUNT, DISTINCT | Ja, som dato/klokkeslæt | Understøttet, hvis kolonnen ikke har millisekund-præcision (med andre ord ingen datetime2 (0)) |

## <a name="aggregation-alternatives"></a>Sammenlægningsalternativer

I øjeblikket er de eneste understøttede sammenlægninger mod deterministiske Always Encrypted-kolonner de sammenlægninger, der direkte bruger operatoren Equals (=). Denne SQL Server-begrænsning skyldes Always Encrypted-kolonnernes beskaffenhed. Brugerne skal samles i rapporten i stedet for i databasen.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted i forbindelsesstrenge

Du skal aktivere Always Encrypted i forbindelsesstrengen for en SQL Server-datakilde. Læs mere om, hvordan du aktiverer [Always Encrypted i programforespørgsler](/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Næste trin

[Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine) i SQL Server og Azure SQL Database

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)