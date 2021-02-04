---
title: Kapacitet og SKU'er i en integreret Power BI-analyse, der giver bedre integreret BI-indsigt
description: Om kapacitet og SKU'er i integrerede Power BI-analyser. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/14/2021
ms.openlocfilehash: b37182cbdf030e8b32fdfe307d0a652fef678b9b
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2021
ms.locfileid: "99533021"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Kapacitet og SKU'er i integrerede Power BI-analyser

Når du går videre til produktion, kræver integreret analyse i Power BI en kapacitet (*A*, *EM* eller *P* SKU) til udgivelse af integreret Power BI-indhold.

Kapacitet er et dedikeret sæt af ressourcer, som er reserveret til eksklusiv brug. Det gør det muligt for dig at publicere dashboards, rapporter og datasæt til brugere uden at være nødt til at købe licenser til hver enkelt bruger. Det garanterer også pålidelig, ensartet ydeevne for dit indhold.

>[!NOTE]
>Hvis du vil publicere, skal du bruge én Power BI Pro-konto.

## <a name="what-is-embedded-analytics"></a>Hvad er integreret analyse?

Integreret analyse i Power BI omfatter to løsninger:

* *Power BI Embedded* – Azure-tilbud

* Integration af Power BI som en del af *Power BI Premium* – Microsoft Office-tilbud

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded er til ISV'er og udviklere, der vil integrere visualiseringer i deres programmer.

Programmer, der bruger Power BI Embedded, gør det muligt for brugerne at forbruge indhold, der er lagret på en Power BI Embedded-kapacitet.

>[!NOTE]
>Power BI Embedded har for nylig udgivet en ny version med navnet **Embedded Gen2**. Embedded Gen2 forenkler administrationen af integrerede kapaciteter og forbedrer Power BI Embedded-oplevelsen. Se [Power BI Embedded Generation 2](power-bi-embedded-generation-2.md) for at få flere oplysninger.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../../admin/service-premium-what-is.md) er kapacitetsmæssigt gearet mod virksomheder, som vil have en komplet BI-løsning, der giver adgang til en enkelt visning af virksomheden, kunderne og leverandørerne.

Power BI Premium er et SaaS-produkt, der giver mulighed for brugere at forbruge indhold gennem mobilapps, internt udviklede apps eller i Power BI-portalen (Power BI-tjeneste). Dette gør det muligt for Power BI Premium at levere en løsning til både interne og eksterne kundeorienterede programmer.

## <a name="capacity-and-skus"></a>Kapacitet og SKU'er

Hver enkelt kapacitet tilbyder en række SKU'er, og hver enkelt SKU indeholder forskellige ressourceniveauer til hukommelses- og computerkraft. Den type SKU, du har brug for, afhænger af den løsningstype, du vil udrulle.

Hvis du vil vide, hvilke arbejdsbelastninger der understøttes for hvert enkelt niveau, kan du se i artiklen [Konfigurer arbejdsbelastninger i en Premium-kapacitet](../../admin/service-admin-premium-workloads.md)

Brug disse link til at planlægge og teste din kapacitet:
* [Kapacitetsplanlægning](embedded-capacity-planning.md)
* [Testmetoder](../../admin/service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>Power BI Embedded-SKU'er

Power BI Embedded leveres med en [*a*-SKU](../../admin/service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios).

### <a name="power-bi-premium-skus"></a>Power BI Premium-SKU'er

Power BI Premium tilbyder to SKU'er, *P* og *EM*.
* [Forstå forskellene mellem *P*- og *EM*-SKU'er](../../admin/service-premium-what-is.md#subscriptions-and-licensing)
* [Køb en Premium-SKU](../../admin/service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Hvilken SKU skal jeg bruge?

I nedenstående tabel finder du en oversigt over funktioner, den nødvendige kapacitet og det specifikke varenummer, der kræves til hver enkelt.

I denne tabel refererer en brugerdefineret app til en webapp, der er oprettet ved hjælp af integreret analyse. Når du integrerer til en brugerdefineret webapp som udvikler (ved hjælp af JavaScript, .NET SDK'er eller REST API'er), har du mulighed for at styre og tilpasse UX. Denne mulighed er ikke tilgængelig, når du bruger andre indstillinger for integrering, f.eks. Power BI-tjeneste og Power BI – Mobil.

| Scenarie | Azure   | Office          |
|----------|---------|-----------------|
|          | (A-varenummer) | (P- og EM-varenumre) |
|[Integrer indhold for dine kunder](embed-sample-for-customers.md)</br>(appen ejer data)     |✔        |✔        |
|[Integrer til din organisation](embed-sample-for-your-organization.md)</br>(brugeren ejer data)     |✖        |✔         |
|Microsoft 365-apps</br>(tidligere kaldet Office 365-apps)<ul><li>[Integrer i Teams](../../collaborate-share/service-embed-report-microsoft-teams.md)</li><li>[Integrer i SharePoint](../../collaborate-share/service-embed-report-spo.md)</li></ul>     |✖        |✔        |
|[Sikker URL-integrering](../../collaborate-share/service-embed-secure.md)</br>(integrer fra Power BI-tjenesten)     |✖        |✔        |

>[!NOTE]
>* Publicering af indhold til arbejdsområdet i en Power BI-app kræver en [Power BI Pro-licens](../../admin/service-admin-purchasing-power-bi-pro.md).
>* Kun **P-varenummer** tillader gratis Power BI-brugere at bruge Power BI-apps og delt indhold i en Power BI-tjeneste.

### <a name="capacity-considerations"></a>Kapacitetsovervejelser

I nedenstående tabel vises betalings- og forbrugsovervejelser pr. kapacitet.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Tilbud</strong></p></td>
<td style="text-align: center"><p>Azure</p></td>
<td style="text-align: center" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center"><p>A</p></td>
<td style="text-align: center"><p>EM</p></td>
<td style="text-align: center"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Fakturering</strong></td>
<td style="text-align: center">Pr. time</td>
<td style="text-align: center">Månedligt</td>
<td style="text-align: center">Månedligt</td>
</tr>
<tr>
<td><p><strong>Forpligtelse</strong></td>
<td style="text-align: center">Ingen</td>
<td style="text-align: center">Årligt</td>
<td style="text-align: center">Månedligt eller årligt</td>
</tr>
<tr>
<td valign="top"><p><strong>Forbrug</strong></td>
<td style="text-align: center">Azure-ressourcer kan:<li><a href="azure-pbie-scale-capacity.md">skaleres op eller ned</a></li><li><a href="azure-pbie-pause-start.md">afbrydes midlertidigt og genoptages</a>
</td></li>
<td style="text-align: center">Integrer i apps og i</br> Microsoft-programmer</td>
<td style="text-align: center">Integrer i apps og</br> i Power BI-tjenesten</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>SKU-hukommelses- og computerkraft

I nedenstående tabel beskrives ressourcerne og begrænsningerne for hver SKU.

| Kapacitetsnoder | V-kerner i alt | Backend-v-kerner | RAM (GB) | Frontend-v-kerner | DirectQuery/direkte forbindelser (pr. sek.) | Parallel opdatering af modeller |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

#### <a name="embedded-gen-2-memory-enhancements-preview"></a>Forbedret hukommelse i op til 2 (eksempelvisning)

Med [Power bi Embedded generation 2](power-bi-embedded-generation-2.md) (også kaldet Embedded gen 2) er den mængde hukommelse, der er tilgængelig på hver node størrelse, angivet til grænsen for hukommelsesforbrug for et enkelt Power bi element (f. eks. en rapport eller et dashboard) og ikke det akkumulerede forbrug af hukommelse. I en integreret Gen2 A4-kapacitet er det f. eks. begrænset til 25 GB i forhold til den oprindelige Power BI Embedded kapacitet, hvor det samlede hukommelsesforbrug for de datasæt, der håndteres på samme tid, begrænset til 25 GB.

## <a name="next-steps"></a>Næste trin

> [!div class="nextstepaction"]
>[Integrer indhold for dine kunder](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Integrer til din organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Integrer fra apps](./index.yml)