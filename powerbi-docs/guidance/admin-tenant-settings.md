---
title: Vejledning til indstillinger for lejer
description: Vejledning til indstillinger for Power BI-lejer.
author: paulinbar
ms.author: painbar
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/10/2020
ms.openlocfilehash: 39357ec461ae96ef566719739aa76a61c7e7c539
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969782"
---
# <a name="tenant-settings-guidance"></a>Vejledning til indstillinger for lejer

Denne artikel er målrettet Power BI-administratorer, der er ansvarlige for at konfigurere Power BI-miljøet i deres organisation.

Vi yder vejledning om bestemte lejerindstillinger, der hjælper med at forbedre Power BI-oplevelsen, eller som kan udsætte din organisation for risiko. Vi anbefaler, at du altid konfigurerer din lejer i henhold til din organisations politikker og processer.

[Lejerindstillinger](../admin/service-admin-portal.md#tenant-settings) administreres på [administrationsportalen](https://app.powerbi.com/admin-portal/tenantSettings) og kan konfigureres af en [Power BI-tjenesteadministrator](../admin/service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi). Mange lejerindstillinger kan begrænse egenskaber og funktioner til et begrænset antal brugere. Derfor anbefaler vi, at du først får kendskab til indstillingerne for at planlægge de sikkerhedsgrupper, du har brug for. Det kan måske være, at du kan anvende den samme sikkerhedsgruppe for flere indstillinger.

## <a name="improve-power-bi-experience"></a>Opnå en bedre Power BI-oplevelse

### <a name="publish-get-help-information"></a>Publicer "Få hjælp"-oplysninger

Vi opfordrer dig til at konfigurere interne Power BI-relaterede websteder ved hjælp af [Microsoft Teams](/microsoftteams) eller en anden samarbejdsplatform. Disse websteder kan bruges til at gemme træningsdokumentation, værtsdiskussioner, foretage anmodninger om licenser eller reagere på hjælp.

Hvis du har gjort det, anbefaler vi, at du derefter aktiverer indstillingen **Publicer "Hent hjælp"-oplysninger** _for hele organisationen_. Den finder du i gruppen **Indstillinger for hjælp og support**. Du kan angive URL-adresser til:

- træningsdokumentation
- diskussionsforum
- licensanmodninger
- Helpdesk

Disse URL-adresser bliver tilgængelige som links i menuen Hjælp i Power BI.

> [!NOTE]
> Hvis du angiver URL-adressen for **licensanmodninger**, kan enkeltbrugere ikke købe en Power BI Pro-licens. De henvises i stedet til dit interne websted med oplysninger om, hvordan de anskaffer sig en licens. Indstillingen **Tillad brugere at prøve Power BI Pro** er aktiveret som standard og adskiller købs-og prøveversionsoplevelsen. Hvis du vil vide mere om, hvordan disse indstillinger fungerer sammen, skal du se [Tillad brugere at prøve Power BI Pro](../admin/service-admin-portal.md#allow-users-to-try-power-bi-paid-features).
>
>

![Skærmbillede af Power BI Desktop, der viser indstillinger for Hjælp og Support.](media/admin-tenant-settings/publish-get-help-information.png)

Du kan finde flere oplysninger under [Indstillinger for Hjælp og support](../admin/service-admin-portal.md#help-and-support-settings).

## <a name="manage-risk"></a>Administrer risiko
Indstillingerne til at administrere risici kan hjælpe dig med at oprette politikker for styring af politikker i din Power BI-lejer. Vær dog opmærksom på, at styringsindstillingerne ikke er en sikkerhedsmåling. Hvis du f.eks. deaktiverer indstillingen **Eksportér data**, fjernes funktionen fra Power BI-brugergrænsefladen og hjælper på denne måde Power BI-brugere med at overholde organisationens styringspolitikker, men den forhindrer ikke brugerne i at eksportere data ved hjælp af andre indstillinger. Set fra et sikkerhedsmæssigt synspunkt har en Power BI-bruger med læseadgang til et datasæt tilladelse til at forespørge dette datasæt og kan bevare resultaterne, uanset hvilke funktioner der er tilgængelige i Power BI-brugergrænsefladen.
### <a name="receive-email-notification-service-outages-or-incidents"></a>Modtag mails i forbindelse med tjenesteudfald eller hændelser

Du kan få besked via mail, hvis lejeren påvirkes af et tjenesteudfald eller en hændelse. På denne måde kan du proaktivt reagere på hændelser.

Vi anbefaler, at du aktiverer indstillingen **Modtag mails ved tjenesteudfald eller hændelser**. Den finder du i gruppen **Indstillinger for hjælp og support**. Tildel en eller flere _mailaktiverede_ sikkerhedsgrupper.

![Skærmbillede af Power B I Desktop, der viser indstillingen "Modtag mails ved tjenesteudfald eller hændelser".](media/admin-tenant-settings/receive-email-notifications-for-service-outages-or-incidents.png)

### <a name="information-protection"></a>Information Protection

Information Protection gør det muligt at gennemtvinge indstillinger for beskyttelse – f.eks. kryptering eller vandmærker – når der eksporteres data fra Power BI-tjenesten.

Der er to lejerindstillinger i relation til beskyttelse af oplysninger. Som standard er begge indstillinger deaktiveret for hele organisationen.

Vi anbefaler, at du aktiverer disse indstillinger, når du skal håndtere og beskytte følsomme data. Du kan finde flere oplysninger under [Databeskyttelse i Power BI](../admin/service-security-data-protection-overview.md).

### <a name="create-workspaces"></a>Opret arbejdsområder

Du kan begrænse brugerne i at oprette arbejdsområder. På den måde kan du styre, hvad der oprettes i din organisation.

> [!NOTE]
> I øjeblikket er der en overgangsperiode mellem det gamle arbejdsområde og det nye. Denne lejerindstilling gælder kun for den nye oplevelse.

Indstillingen **Opret arbejdsområder** er som standard aktiveret for hele organisationen. Du finder den i gruppen **Indstillinger for arbejdsområde**.

Vi anbefaler, at du tildeler én eller flere sikkerhedsgrupper. Tilladelse til at oprette arbejdsområder kan blive tildelt _eller afvist_ for disse grupper.

Sørg for at inkludere instruktioner i din dokumentation, så brugerne (der ikke har tilladelse til at oprette arbejdsområder) ved, hvordan de kan anmode om et nyt arbejdsområde.

![Skærmbillede af Power BI Desktop, der viser indstillingen "Opret arbejdsområder".](media/admin-tenant-settings/create-workspaces.png)

### <a name="share-content-with-external-users"></a>Del indhold med eksterne brugere

Brugerne kan dele rapporter og dashboards med personer uden for organisationen.

Indstillingen **Del indhold med eksterne brugere** er som standard aktiveret for hele organisationen. Du finder den i gruppen **Indstillinger for eksport og deling**.

Vi anbefaler, at du tildeler én eller flere sikkerhedsgrupper. Tilladelse til at dele indhold med eksterne brugere kan tildeles _eller afvises_ for disse grupper.

![Skærmbillede af Power BI Desktop, der viser indstillingen "Del indhold med eksterne brugere".](media/admin-tenant-settings/share-content-with-external-users.png)

### <a name="publish-to-web"></a>Publicer på internettet

Funktionen [Publicer på internettet](../collaborate-share/service-publish-to-web.md) gør det muligt at publicere offentlige rapporter på internettet. Hvis funktionen ikke anvendes korrekt, er der en risiko for, at fortrolige oplysninger bliver tilgængelige live på internettet.

Indstillingen **Publicer på internettet** er som standard aktiveret for hele organisationen, men den begrænser muligheden for at oprette integreringskoder for brugere, der ikke er administratorer. Du finder den i gruppen **Indstillinger for eksport og deling**.

Hvis indstillingen er aktiveret, anbefaler vi, at du tildeler én eller flere sikkerhedsgrupper. Tilladelse til at publicere rapporter kan blive tildelt _eller afvist_ for disse grupper.

Desuden er der mulighed for at vælge, hvordan dine integreringskoder fungerer. Den er som standard angivet til **Tillad kun eksisterende koder**. Det betyder, at brugerne bliver bedt om at kontakte en Power BI-administrator for at oprette en integreringskode.

![Skærmbillede af Power BI Desktop, der viser indstillingen "Udgiv på web".](media/admin-tenant-settings/publish-to-web.png)

Vi anbefaler også, at du gennemgår [Publicer integreringskoder på internettet](https://app.powerbi.com/admin-portal/embedCodes) jævnligt. Fjern koder, hvis de medfører publicering af private eller fortrolige oplysninger.

### <a name="export-data"></a>Eksportér data

Du kan begrænse brugernes eksport af data fra dashboardfelter eller rapportvisualiseringer.

Indstillingen **Eksportér data** er som standard aktiveret for hele organisationen. Du finder den i gruppen **Indstillinger for eksport og deling**.

Vi anbefaler, at du tildeler én eller flere sikkerhedsgrupper. Tilladelse til at publicere rapporter kan blive tildelt _eller afvist_ for disse grupper.

> [!IMPORTANT]
> Deaktivering af denne indstilling begrænser også brugen af funktionerne [Analysér i Excel](../collaborate-share/service-analyze-in-excel.md) og [liveforbindelse](../connect-data/desktop-report-lifecycle-datasets.md#using-a-power-bi-service-live-connection-for-report-lifecycle-management) i Power BI-tjenesten.

![Skærmbillede af Power BI Desktop, der viser indstillingen "Eksportér data".](media/admin-tenant-settings/export-data.png)

> [!NOTE]
> Hvis brugerne tillader andre brugere at eksportere data, kan du tilføje et beskyttelseslag ved at gennemtvinge [databeskyttelse](../admin/service-security-data-protection-overview.md). Når det er konfigureret, blokeres eksport af indhold der er markeret som følsomt for ikke-godkendte brugere.

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Tillad, at eksterne brugere kan redigere og administrere indhold i organisationen

Det er muligt, at eksterne gæstebrugere kan redigere og administrere Power BI-indhold. Se flere oplysninger under [Distribuer Power BI-indhold til eksterne gæstebrugere med Azure AD B2B](../admin/service-admin-azure-ad-b2b.md).

Indstillingen **Tillad, at eksterne gæstebrugere kan redigere og administrere indhold i organisationen** er som standard deaktiveret for hele organisationen. Du finder den i gruppen **Indstillinger for eksport og deling**.

Hvis du skal godkende, at eksterne brugere kan redigere og administrere indhold, anbefaler vi, at du tildeler én eller flere sikkerhedsgrupper. Tilladelse til at publicere rapporter kan blive tildelt _eller afvist_ for disse grupper.

![Skærmbillede af Power BI Desktop, der viser indstillingen "Tillad, at eksterne brugere kan redigere og administrere indhold i organisationen".](media/admin-tenant-settings/allow-external-guest-users.png)

### <a name="developer-settings"></a>Indstillinger for udviklere

Der er to lejerindstillinger i forbindelse med [integration af Power BI-indhold](../developer/embedded/embedding.md). De er:

- Integrer indhold i apps (aktiveret som standard)
- Tillad, at tjenesteprincipaler bruger Power BI-API'er (deaktiveret som standard)

Hvis du ikke vil bruge udvikler-API'erne til at integrere indhold, anbefaler vi, at du deaktiverer dem. Du kan også konfigurere specifikke sikkerhedsgrupper, der udfører dette arbejde.

![Skærmbillede af Power BI Desktop, der viser indstillingerne for udviklere.](media/admin-tenant-settings/developer-settings.png)

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Hvad er Power BI-administration?](../admin/service-admin-administering-power-bi-in-your-organization.md)
- [Administrer Power BI på administrationsportalen](../admin/service-admin-portal.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)