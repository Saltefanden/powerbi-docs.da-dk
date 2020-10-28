---
title: Organiser arbejde i nye arbejdsområder i Power BI
description: Få mere at vide om de nye arbejdsområder, der er samlinger af dashboards og rapporter, som er udviklet til at levere vigtige målepunkter for din organisation.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/21/2020
ms.author: maggies
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: 1ea5e7633fb81b2792459c3a428c9c43827a5137
ms.sourcegitcommit: fddba666c6ea90d525a1c3188bbd3c4a03410cdc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/23/2020
ms.locfileid: "92462210"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organiser arbejde i nye arbejdsområder i Power BI

*Arbejdsområder* er steder, hvor du kan samarbejde med kolleger om at oprette samlinger af dashboards, rapporter, datasæt og sideinddelte rapporter. Den nye arbejdsområdeoplevelse hjælper dig med bedre at administrere adgang til indhold. I denne artikel beskrives de nye arbejdsområder, og hvordan de adskiller sig fra de klassiske arbejdsområder.  På samme måde som med klassiske arbejdsområder bruges arbejdsområder stadig til at oprette og distribuere apps. 

Er du parat til at oprette et nyt arbejdsområde? Læs [Opret en ny arbejdsområdeoplevelse](service-create-the-new-workspaces.md).

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Den nye arbejdsområdeoplevelse i Power BI":::

Nye opgraderede arbejdsområder og eksisterende klassiske arbejdsområder eksisterer side om side. Den nye arbejdsområdeoplevelse er standardtypen for arbejdsområder. Du kan stadig oprette og bruge [klassiske arbejdsområder](service-create-workspaces.md), der er baseret på Microsoft 365-grupper, hvis du har brug for det. Er du klar til at overføre dit klassiske arbejdsområde? Se [Opgrader klassiske arbejdsområder til de nye arbejdsområder i Power BI](service-upgrade-workspaces.md) for at få flere oplysninger.

## <a name="new-and-classic-workspace-differences"></a>Forskelle på det nye og det klassiske arbejdsområde

Vi har givet nogle af funktionerne i de nye arbejdsområder et nyt design. Her er de væsentligste forskelle.

- **Oprettelse af de nye arbejdsområder opretter ikke Microsoft 365-grupper** på samme måde som klassiske arbejdsområder. Al administration af nye arbejdsområder sker i Power BI, ikke i Office 365. Du kan fortsætte med at administrere brugeradgang til indhold via Microsoft 365-grupper, hvis du vil det. Du skal blot tilføje en Microsoft 365-gruppe på adgangslisten for arbejdsområdet.
- **Brug mere detaljerede arbejdsområderoller** til administration af mere fleksible tilladelser i et arbejdsområde.  I de klassiske arbejdsområder kan du kun føje enkeltpersoner til medlems- og administratorlisterne. 
- **Tildel brugergrupper til arbejdsområderoller** : I de nye arbejdsområder kan du føje flere Active Directory-sikkerhedsgrupper, distributionslister eller Microsoft 365-grupper til disse roller for at lette administrationen af brugere. 
- **Kontaktliste** : I de nye arbejdsområder kan du angive, hvem der modtager besked om aktiviteten i arbejdsområdet.
- **Opret skabelonapps** : Du kan kun oprette *skabelonapps* i de nye arbejdsområder. Skabelonapps er apps, du kan distribuere til kunder uden for din organisation. Disse kunder kan derefter oprette forbindelse til deres egne data med din skabelonapp. Få mere at vide om [skabelonapps](../connect-data/service-template-apps-overview.md).
- **Del datasæt** : Hvis du vil dele et datasæt uden for et bestemt arbejdsområde, skal du gemme den rapport, der indeholder datasættet, i et af de nye arbejdsområder. Du kan ikke dele datasæt fra klassiske arbejdsområder. Læs mere om [delte datasæt](../connect-data/service-datasets-across-workspaces.md).
- **Organisationsindholdspakker** : Du opretter og bruger organisationsindholdspakker i klassiske arbejdsområder. Du kan ikke oprette eller forbruge dem i de nye arbejdsområder. Apps- og skabelonapps erstatter organisationsindholdspakker i de nye arbejdsområder.

I denne artikel forklares disse funktioner mere detaljeret.

> [!NOTE]
> Power BI fortsætter med at vise alle Microsoft 365-grupper, som du er medlem af. Dette forhindrer, at eksisterende arbejdsprocesser ændres.

### <a name="features-that-work-differently"></a>Funktioner, som fungerer anderledes

I de nye arbejdsområder fungerer visse funktioner anderledes. Disse forskelle er bevidst og er baseret på den feedback, vi har modtaget fra kunder. De giver mulighed for en mere fleksibel tilgang til samarbejde i arbejdsområder.

- **Håndhævelse af licenser** : Publicering af rapporter til den nye arbejdsområdeoplevelse sker på baggrund af de eksisterende licensregler. Brugere, der samarbejder i nye arbejdsområder eller deler indhold med andre i Power BI-tjenesten, skal bruge en Power BI Pro-licens. Brugere uden en Pro-licens får vist fejlmeddelelsen "Kun brugere med Power BI Pro-licenser kan publicere til dette arbejdsområde".
- **Indstillingen Medlemmer må dele igen** : Rollen som bidragyder i de nye arbejdsområder erstatter indstillingen Medlemmer må dele igen i de klassiske arbejdsområder.
- **Skrivebeskyttede arbejdsområder** : Rollen som læser i de nye arbejdsområder erstatter tildelingen af læseadgang til et klassisk arbejdsområde. Rollen som læser giver tilsvarende skrivebeskyttet adgang til indholdet i et nyt arbejdsområde.
- **Brugere uden en Pro-licens** kan få adgang til et nyt arbejdsområde, hvis det er i en Power BI Premium-kapacitet, men kun hvis de har rollen som læser.
- **Tillad brugere at eksportere data** : Brugere med rollen som læser i det nye arbejdsområde kan eksportere data, hvis de har tilladelse til at oprette for datasættene i arbejdsområdet. Læs mere om [tilladelsen Opret for datasæt](../connect-data/service-datasets-build-permissions.md).
- Der er ingen knap af typen **Forlad arbejdsområde** i de nye arbejdsområder.

### <a name="workspace-contact-list"></a>Liste over arbejdsområdekontakter

Den nye **kontaktlistefunktion** gør det muligt at angive, hvilke brugere der modtager en meddelelse om de problemer, der opstår i det nye arbejdsområde. Som standard får alle brugere eller grupper, der er angivet som arbejdsområdeadministrator, besked. Du lave tilføjelser til listen. Brugere eller grupper på kontaktlisten vises også i brugergrænsefladen (UI) for de nye arbejdsområder, så slutbrugere i arbejdsområdet ved, hvem de skal kontakte. 

Læs mere om, [hvordan du opretter kontaktlisten i arbejdsområdet](service-create-the-new-workspaces.md#create-a-contact-list).

### <a name="workspace-onedrive"></a>Arbejdsområde for OneDrive

Som vi har angivet, opretter Power BI ikke en Microsoft 365-gruppe bag kulisserne, når du opretter et af de nye arbejdsområder. Det kan stadig være en fordel at have et OneDrive, der er knyttet til det nye arbejdsområde. Funktionen Arbejdsområde for OneDrive i de nye arbejdsområder giver dig mulighed for at konfigurere en Microsoft 365-gruppe, hvis fillager for SharePoint-dokumentbibliotek er tilgængeligt for brugere af arbejdsområdet. Du opretter gruppen uden for Power BI.
 
Power BI synkroniserer ikke mellem Microsoft 365-gruppemedlemskab og tilladelser for brugere eller grupper, der har adgang til det nye arbejdsområde. Du kan synkronisere dem: Administrer adgang til arbejdsområdet via den samme Microsoft 365-gruppe, hvis fillager du konfigurerer i denne indstilling. 

Læs mere om, hvordan du [konfigurerer et arbejdsområde for OneDrive](service-create-the-new-workspaces.md#set-a-workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Roller i de nye arbejdsområder

Du kan bruge roller til at administrere, hvem der kan gøre hvad i de nye arbejdsområder, så teams kan samarbejde. Nye arbejdsområder gør det muligt at tildele roller til enkeltpersoner og til brugergrupper: sikkerhedsgrupper, Microsoft 365-grupper og distributionslister. 

Hvis du vil give adgang til et nyt arbejdsområde, skal du føje brugergrupper eller enkeltpersoner til en af arbejdsområderollerne: Administrator, Medlem, Bidragyder eller Læser. Alle i en brugergruppe får den rolle, du har tildelt dem. Hvis en person er i flere brugergrupper, får personen det højeste tilladelsesniveau, der er angivet for den rolle, personen er blevet tildelt. Hvis du indlejrer brugergrupper, har alle brugere i grupperne tilladelse. Al denne funktionalitet, undtagen visning og interaktion, kræver en Power BI Pro-licens. Læs mere om [licensering](#licenses) i denne artikel.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - Du kan tildele brugere til roller enten alene eller i en gruppe, selvom de ikke kan bruge rollen. Du kan med andre ord tildele brugere, der ikke har Power BI Pro-licenser, til en rolle, der kræver en licens. Se [Licenser](#licenses) i denne artikel for at få flere oplysninger.
> - Hvis du vil gennemtvinge [sikkerhed på rækkeniveau (RLS)](../admin/service-admin-rls.md) for brugere, der gennemser indhold i et arbejdsområde, kan du bruge rollen Fremviser. Du kan også gennemtvinge RLS uden at give adgang til det nye arbejdsområde. Du kan også [udgive en app](service-create-distribute-apps.md) og distribuere den til disse brugere eller bruge [deling til at distribuere indhold](service-share-dashboards.md).

## <a name="licensing-and-administering"></a>Licensering og administration

### <a name="licenses"></a>Licenser
Hvis et af de nye arbejdsområder er i en delt kapacitet, skal alle, du føjer til det, have en Power BI Pro-licens. Disse brugere kan samarbejde om dashboards og rapporter i det nye arbejdsområde. Hvis du vil distribuere indhold til andre i din organisation, kan du enten tildele Power BI Pro-licenser til disse brugere eller anbringe arbejdsområdet i en Power BI Premium-kapacitet.

Når det nye arbejdsområde er i en Power BI Premium-kapacitet, kan brugere med rollen som læser få adgang til arbejdsområdet, også selvom de ikke har en Power BI Pro-licens. Men hvis du tildeler disse brugere en rolle på et højere niveau som f.eks. administrator, medlem eller bidragyder, vil de blive bedt om at starte en Pro-prøveversion, når de forsøger at få adgang til arbejdsområdet. Hvis du vil have brugere uden Pro-licenser til at bruge læserrollen, skal du sørge for, at de ikke også har andre arbejdsområderoller, enten som enkeltperson eller som en del af en brugergruppe.

Publicering af rapporter til den nye arbejdsområdeoplevelse har strengere håndhævelse af eksisterende licensregler. Hvis du forsøger at udgive fra Power BI Desktop eller andre klientværktøjer uden en Pro-licens, får du vist fejlmeddelelsen "Kun brugere med Power BI Pro-licenser kan publicere til dette arbejdsområde".

> [!NOTE]
> Power BI US Government er ikke tilgængelig som en gratis licens. Du finder licensoplysninger under [Power BI til US Government-kunder](../admin/service-govus-overview.md).

### <a name="guest-users"></a>Gæstebrugere

[Azure AD B2B-gæstebrugere](../admin/service-admin-azure-ad-b2b.md) kan som standard ikke få adgang til arbejdsområder. Power BI-administratorer kan [tillade, at eksterne brugere kan redigere og administrere indhold i organisationen](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Brugere, der er gæstebrugere, kan få adgang til de arbejdsområder, de har tilladelse til.

### <a name="administering-new-workspace-experience-workspaces"></a>Administration af arbejdsområder i den nye arbejdsområdeoplevelse

Arbejdsområder til administration af nye arbejdsområder er på plads i Power BI-administrationsportalen. Power BI-administratorer bestemmer, hvem i en organisation der kan oprette arbejdsområder og distribuere apps. Læs om [administration af brugernes mulighed for at oprette arbejdsområder](../admin/service-admin-portal.md#create-the-new-workspaces) i artiklen "Administrationsportal". 

Administratorer kan også se status for alle arbejdsområder i deres organisation. De kan administrere, genoprette og endda slette arbejdsområder. Læs mere om [brugernes egen administration af arbejdsområder](../admin/service-admin-portal.md#workspaces) i artiklen "Administrationsportal".

### <a name="auditing"></a>Overvågning

Følgende aktiviteter overvåges af Power BI for arbejdsområder i den nye arbejdsområdeoplevelse.

| Brugervenligt navn | Handlingsnavn |
|---|---|
| Power BI-mappe er oprettet | CreateFolder |
| Power BI-mappe er slettet | DeleteFolder |
| Power BI-mappe er opdateret | UpdateFolder |
| Adgang til Power BI-mappe er opdateret| UpdateFolderAccess |

Læs mere om [overvågning i Power BI](../admin/service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Begrænsninger, du skal være opmærksom på:

- Arbejdsområder kan indeholde op til 1.000 datasæt eller 1.000 rapporter pr. datasæt. 
- En person med en Power BI Pro-licens kan være medlem af maks. 1.000 arbejdsområder.
- Power BI Publisher til Excel understøttes ikke.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Påvirkes links til eksisterende indhold af den offentligt tilgængelige version af den nye arbejdsområdeoplevelse?**

Nej. Links til eksisterende elementer i de klassiske arbejdsområder påvirkes ikke af den nye arbejdsområdeoplevelse. Den generelle tilgængelighed af den nye arbejdsområdeoplevelse ændrer det standardarbejdsområde, som du opretter, men ikke eksisterende arbejdsområder. 

**Opgraderes eksisterende arbejdsområder til den nye arbejdsområdeoplevelse i forbindelse med, at den bliver generelt tilgængelig?**

Nej. Den nye generelt tilgængelige arbejdsområdeoplevelse ændrer kun standardtypen for arbejdsområder til den nye arbejdsområdeoplevelse. Eksisterende klassiske arbejdsområder, der er baseret på Microsoft 365-grupper, forbliver uændrede.

**Oprettes der stadig automatisk arbejdsområder for Microsoft 365 Grupper?**

Ja. Da vi understøtter begge typer arbejdsområder samtidig, fortsætter vi med at vise alle de Microsoft 365-grupper, som du har adgang til, på listen over arbejdsområder.

## <a name="next-steps"></a>Næste trin

* [Opret nye arbejdsområder i Power BI](service-create-the-new-workspaces.md)
* [Opret klassiske arbejdsområder](service-create-workspaces.md)
* [Installér og brug apps i Power BI](service-create-distribute-apps.md)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

