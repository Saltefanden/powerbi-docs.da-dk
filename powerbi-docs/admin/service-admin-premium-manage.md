---
title: Konfigurer og administrer kapaciteter i Power BI Premium
description: Få mere at vide om, hvordan du kan administrere Power BI Premium og give adgang til indhold for hele organisationen.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 2eb1c5bd685cedabd96483867546c7578124af45
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2021
ms.locfileid: "99532837"
---
# <a name="configure-and-manage-capacities-in-power-bi-premium"></a>Konfigurer og administrer kapaciteter i Power BI Premium

Administration af Power BI Premium omfatter oprettelse, administration og overvågning af Premium-kapaciteter. Denne artikel indeholder en trinvis vejledning. Hvis du vil have en oversigt over kapaciteter, skal du se [Administration af Premium-kapaciteter](service-premium-capacity-manage.md).

Få mere at vide om, hvordan du administrerer Power BI Premium- og Power BI Embedded-kapaciteter, som leverer dedikerede ressourcer til dit indhold.

![Indstillingsskærm for Power BI-kapacitet](media/service-admin-premium-manage/premium-capacity-management.png)

*Kapaciteten* er i hjertet af Power BI Premium og [Power bi Embedded](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md) tilbud. Det er en række ressourcer, som er reserveret udelukkende til din organisation. Adgang til en kapacitet giver dig mulighed for at publicere dashboards, rapporter og datasæt til brugere i hele organisationen uden at være nødt til at købe licenser til dem. Det garanterer også pålidelig, ensartet ydeevne for det indhold, der hostes i kapacitet. Du kan finde flere oplysninger i [Hvad er Power BI Premium?](service-premium-what-is.md).

> [!NOTE]
> Power BI Premium har for nylig udgivet en ny version af Premium med navnet **Premium Gen2**, der i øjeblikket er tilgængelig som prøveversion. Premium Gen2 forenkler administrationen af Premium-kapaciteter og reducerer administrationsomkostningerne. Du kan finde flere oplysninger under [Power BI Premium – Generation 2 (prøveversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="manage-capacity"></a>Administrer kapacitet

Når du har købt kapacitetsnoder i Microsoft 365, konfigurerer du kapaciteten på Power BI-administrationsportalen. Du kan administrere Power BI Premium-kapaciteter i afsnittet med **kapacitetsindstillinger** i portalen.

![Kapacitetsindstillinger i administrationsportalen](media/service-admin-premium-manage/admin-portal-premium.png)

Du kan administrere en kapacitet ved at vælge navnet på kapaciteten. Herefter kommer du til skærmbilledet med kapacitetsadministration.

![Vælg kapacitetsnavn for at åbne skærmbilledet med kapacitetstildeling](media/service-admin-premium-manage/capacity-assignment.png)

Hvis der ikke er blevet tildelt nogen arbejdsområder til kapaciteten, får du vist en meddelelse om [tildeling af et arbejdsområde til en kapacitet](#assign-a-workspace-to-a-capacity).

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>Konfiguration af en ny kapacitet (Power BI Premium)

Administrationsportalen viser antallet af *virtuelle kerner* (v-kerner), som du har brugt, og som stadigvæk er tilgængelige. Det samlede antal virtuelle kerner er baseret på de Premium-varenumre, du har købt. Køb af en P3 og en P2 resulterer f.eks. i 48 tilgængelige kerner – 32 fra P3 og 16 fra P2.

![Brugte og tilgængelige v-kerner for Power BI Premium](media/service-admin-premium-manage/admin-portal-v-cores.png)

Hvis du har tilgængelige v-kerner, skal du konfigurere en ny kapacitet på følgende måde.

1. Vælg **Konfigurer ny kapacitet**.

1. Giv din kapacitet et navn.

1. Definer, hvem administratoren er for denne kapacitet.

1. Vælg kapacitetstørrelsen. Hvilke indstillinger, der er tilgængelige, afhænger af, hvor mange tilgængelige v-kerner du har. Du kan ikke vælge en indstilling, der er større end den, du har adgang til.

    ![Tilgængelige Premium-kapacitetsstørrelser](media/service-admin-premium-manage/premium-capacity-size.png)

1. Vælg **Konfigurer**.

    ![Konfigurer en ny kapacitet](media/service-admin-premium-manage/set-up-capacity.png)

Kapacitetsadministratorer såvel som Power BI-administratorer og globale administratorer kan derefter se kapaciteten i oversigten på administratorportalen.

### <a name="capacity-settings"></a>Kapacitetsindstillinger

1. Vælg **tandhjulsikonet** under **Handlinger** på skærmbilledet til administration af Premium-kapaciteter for at gennemse og opdatere indstillinger. 

    ![Kapacitetshandlinger i området for kapacitetsadministration](media/service-admin-premium-manage/capacity-actions.png)

1. Du kan se, hvem administratorer af tjenesten er, kapacitetens varenummer/størrelse, og hvilket område kapaciteten er i.

    ![Kapacitetsindstillinger](media/service-admin-premium-manage/capacity-settings.png)

1. Du kan også omdøbe eller slette en kapacitet.

    ![Slet og anvend knapper til kapacitetsindstillinger i Power BI Premium](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> Power BI Embedded-kapacitetsindstillinger administreres i Microsoft Azure-portalen.

### <a name="change-capacity-size"></a>Skift kapacitetsstørrelse

Power BI-administratorer og globale administratorer kan ændre Power BI Premium-kapacitet. Kapacitetsadministratorer, der ikke er en Power BI-administrator eller global administrator, har ikke adgang til denne indstilling.

1. Vælg **Skift kapacitetsstørrelse**.

    ![Tilpas Power BI Premium-kapacitetsstørrelse](media/service-admin-premium-manage/change-capacity-size.png)

1. Opgrader eller nedgrader din kapacitet efter behov på skærmen **Skift kapacitetsstørrelse**.

    ![Rullemenu til tilpasning af Power BI Premium-kapacitetsstørrelse](media/service-admin-premium-manage/change-capacity-size2.png)

    Administratorer kan frit oprette, tilpasse størrelsen af og slette noder, så længe de har de fornødne antal v-kerner.

    P-varenumre kan ikke nedgraderes til EM-varenumre. Du kan placere markøren over deaktiverede indstillinger for at få vist en forklaring.



> [!IMPORTANT]
> Hvis der er et højt forbrug af ressourcer i din Power BI Premium-kapacitet, hvilket medfører problemer med ydeevne eller pålidelighed, kan du modtage notifikationer via mail for at identificere og løse problemet. Se [notifikationer om kapacitet og pålidelighed](service-interruption-notifications.md#capacity-and-reliability-notifications) for at få flere oplysninger.


### <a name="manage-user-permissions"></a>Administrer brugertilladelser

Du kan tildele yderligere kapacitetsadministratorer, og du kan tildele brugere, der har tilladelse til at *tildele kapacitet*. Brugere, der har tildelingstilladelser, kan tildele et arbejdsområde til en kapacitet, hvis de er administratorer af det pågældende arbejdsområde. De kan også tildele deres personlige *Mit arbejdsområde* til kapaciteten. Brugere med tildelingstilladelser har ikke adgang til administrationsportalen.

> [!NOTE]
> Kapacitetsadministratorer til Power BI Embedded er defineret inden for Microsoft Azure-portalen.

Udvid **Brugere med tildelingstilladelser** under **Brugertilladelser**, og tilføj derefter brugere eller grupper efter behov.

![Kapacitetsbrugertilladelser](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="assign-a-workspace-to-a-capacity"></a>Tildel et arbejdsområde til en kapacitet

Der er to måder at tildele et arbejdsområde til en kapacitet på: via administrationsportalen og fra et arbejdsområde.

### <a name="assign-from-the-admin-portal"></a>Tildel fra administrationsportalen

Ud over Power BI-administratorer og globale administratorer kan kapacitetsadministratorer massetildele arbejdsområder i afsnittet til administration af Premium-kapacitet på administrationsportalen. Når du administrerer en kapacitet, får du vist et afsnit med **arbejdsområder**, hvor du kan tildele arbejdsområder.

![Afsnit for tildeling af arbejdsområde i kapacitetsadministration](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. Vælg **Tildel arbejdsområder**. Denne indstilling er tilgængelig flere steder.

1. Vælg en indstilling for **Anvend for**.

    ![Tildel arbejdsområder](media/service-admin-premium-manage/assign-workspaces.png)

   | Markering | Beskrivelse |
   | --- | --- |
   | **Arbejdsområder efter brugere** | Når du tildeler arbejdsområder efter bruger eller gruppe, så tildeles alle arbejdsområder, der ejes af de pågældende brugere, Premium-kapacitet, herunder brugerens personlige arbejdsområde. Disse brugere får automatisk tilladelser til arbejdsområdetildeling.<br>Dette omfatter arbejdsområder, der allerede er tildelt en anden kapacitet. |
   | **Specifikke arbejdsområder** | Angiv navnet på et bestemt arbejdsområde, der skal tildeles til den valgte kapacitet. |
   | **Arbejdsområder til hele organisationen** | Hvis du tildeler Premium-kapacitet til alle organisationens arbejdsområder, tildeles alle arbejdsområder og Mine arbejdsområder i organisationen til den pågældende Premium-kapacitet. Desuden får alle aktuelle og fremtidige brugere tilladelse til at gentildele individuelle arbejdsområder til denne kapacitet. |
   | | |

1. Vælg **Anvend**.

### <a name="assign-from-workspace-settings"></a>Tildel fra indstillinger for arbejdsområde

Du kan også tildele et arbejdsområde til en Premium-kapacitet fra det pågældende arbejdsområdes indstillinger. Hvis du vil flytte en kapacitet til et arbejdsområde, skal du have administratortilladelser til det pågældende arbejdsområde og desuden have tilladelser til kapacitetstildeling for den pågældende kapacitet. Bemærk, at arbejdsområdeadministratorer altid kan fjerne et arbejdsområde fra Premium-kapacitet.

1. Rediger et arbejdsområde ved at vælge **(...)** og derefter vælge **Rediger arbejdsområde**.

    ![Rediger arbejdsområde via ellipsegenvejsmenuen](media/service-admin-premium-manage/edit-app-workspace.png)

1. Under **Rediger arbejdsområde** skal du udvide **Avanceret**.

1. Vælg den kapacitet, du vil tildele dette arbejdsområde til.

    ![Rullemenu til valg af kapacitet](media/service-admin-premium-manage/app-workspace-advanced.png)

1. Vælg **Gem**.

Når arbejdsområdet er gemt, flyttes det og al dets indhold til Premium-kapacitet, uden at slutbrugerne oplever nogen tjenesteafbrydelser.

## <a name="power-bi-report-server-product-key"></a>Produktnøgle til Power BI-rapportserver

På fanen **Kapacitetsindstillinger** i Power BI-administratorportalen kan du få adgang til produktnøglen til Power BI-rapportserver. Den kan kun tilgås af globale administratorer eller brugere tildelt rollen som administrator af Power BI-tjenesten, og hvis man har erhvervet et Power BI Premium-varenummer.

![Power BI Report Server-nøgle i kapacitetsindstillinger](media/service-admin-premium-manage/pbirs-product-key.png)

Når du vælger **Power BI Report Server-nøgle** vises en dialogboks med din produktnøgle. Du kan kopiere den og bruge den med installationen.

![Power BI Report Server-produktnøgle](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

Du kan finde flere oplysninger under [Installér Power BI-rapportserveren](../report-server/install-report-server.md).

## <a name="next-steps"></a>Næste trin

[Administration af Premium-kapaciteter](service-premium-capacity-manage.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

Power BI har introduceret Power BI Premium Gen2 som et prøveversionstilbud, der forbedrer Power BI Premium-oplevelsen på følgende områder:
* Ydeevne
* Licens pr. bruger
* Større skalering
* Forbedrede målepunkter
* Automatisk skalering
* Reducerede administrationsomkostninger

Du kan finde flere oplysninger om Power BI Premium Gen2 under [Power BI-Premium – Generation 2 (prøveversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).