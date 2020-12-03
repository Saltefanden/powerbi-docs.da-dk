---
title: Betinget formatering af tabeller i Power BI Desktop
description: Anvend brugerdefineret formatering på tabeller
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 421ccbe08435e03fe43cf6f0e7f2b71c99ec6901
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414386"
---
# <a name="use-conditional-formatting-in-tables"></a>Brug betinget formatering på tabeller 

Med betinget formatering af tabeller i Power BI Desktop kan du angive brugerdefinerede cellefarver, herunder farvegradueringer, på baggrund af feltværdier. Du kan også repræsentere celleværdier med datalinjer eller KPI-ikoner eller som aktive weblinks. Du kan anvende betinget formatering på ethvert tekst- eller datafelt, så længe du baserer formateringen på et felt, der har numerisk værdi, farvenavn eller hex-kode eller URL-værdier. 

Hvis du vil anvende betinget formatering, skal du vælge en visualisering af typen **Tabel** eller **Matrix** i Power BI Desktop. I afsnittet **Felter** i ruden **Visualiseringer** skal du højreklikke eller vælge pil ned ud for feltet i de **værdier**, du vil formatere. Vælg **Betinget formatering**, og vælg derefter den formattype, der skal anvendes.

![Menuen Betinget formatering](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

> [!NOTE]
> Betinget formatering tilsidesætter en brugerdefineret baggrund eller skriftfarve, som du anvender på den celle, der har betinget formatering.

Hvis du vil fjerne betinget formatering fra en visualisering, skal du vælge **Fjern betinget formatering** fra feltets rullemenu og derefter vælge den type formatering, du vil fjerne.

![Menuen Fjern betinget formatering](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

I de følgende afsnit beskrives hver indstilling for betinget formatering. Du kan kombinere mere end én indstilling i en enkelt tabelkolonne.

## <a name="format-background-or-font-color"></a>Formatér baggrund eller skriftfarve

Hvis du vil formatere cellebaggrunden eller skriftfarven, skal du vælge **Betinget formatering** for et felt og derefter vælge enten **Baggrundsfarve** eller **Skriftfarve** i rullemenuen. 

![Vælg Baggrundsfarve eller Skriftfarve](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

Dialogboksen **Baggrundsfarve** eller **Skriftfarve** åbnes med navnet på det felt, du formaterer, i titlen. Når du har valgt indstillinger for betinget formatering, skal du vælge **OK**. 

![Dialogboksene Baggrundsfarve og Skriftfarve](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

Indstillingerne **Baggrundsfarve** og **Skriftfarve** er de samme, men påvirker henholdsvis cellens baggrundsfarve og skriftfarve. Du kan anvende den samme eller en anden betinget formatering på et felts skriftfarve og baggrundsfarve. Hvis du gør et felts skrifttype og baggrund til den samme farve, blandes skrifttypen med baggrunden, så tabelkolonnen kun viser farverne.

## <a name="color-by-color-scale"></a>Farve efter farveskala

Hvis du vil formatere cellens baggrund eller skriftfarve efter farveskala, skal du i feltet **Formatér efter** i dialogboksen **Baggrundsfarve** eller **Skriftfarve** vælge **Farveskala**. Under **feltet Baseret på** skal du vælge det felt, som formateringen skal baseres på. Du kan basere formateringen på det aktuelle felt eller på et hvilket som helst felt i din model, der indeholder numeriske data eller farvedata. 

Under **Opsummering** skal du angive den sammenlægningstype, du vil bruge til det valgte felt. Vælg den formatering, der skal anvendes på tomme værdier, under **Standardformatering**. 

Under **Minimum** og **Maksimum** skal du vælge, om du vil anvende farveskemaet baseret på de laveste og højeste feltværdier eller på de brugerdefinerede værdier, du angiver. På rullelisten skal du vælge de farveprøver, der skal anvendes på minimum- og maksimumværdierne. Markér afkrydsningsfeltet **Divergerende** for også at angive en **Mellemste** værdi og farve. 

![Angiv cellens baggrund med farveskala](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

Et eksempel på en tabel med baggrundsformatering af farveskalaer på kolonnen **Prisbillighed** ser sådan ud:

![Eksempel på en tabel med divergerende baggrundsfarveskala](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

Et eksempel på en tabel med skriftformatering af farveskalaer på kolonnen **Prisbillighed** ser sådan ud:

![Eksempel på en tabel med divergerende skriftfarveskala](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="color-by-rules"></a>Farve efter regler

Hvis du vil formatere cellens baggrund eller skriftfarve efter regler, skal du i feltet **Formatér efter** i dialogboksen **Baggrundsfarve** eller **Skriftfarve** vælge **Regler**. **Feltet Baseret på** viser igen det felt, som formateringen skal baseres på, og **Opsummering** viser sammenlægningstypen for feltet. 

Under **Regler** skal du angive et eller flere værdiområder og angive en farve for hver enkelt. Hvert værdiområde har en *Hvis værdi*-betingelse, en *og*-betingelse og en farve. Cellens baggrunde eller skrifttyper i hvert værdiområde er farvet med den angivne farve. Det følgende eksempel har tre regler:

![Farve efter regler](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Et eksempel på en tabel med regelbaseret baggrundsformatering af farver på kolonnen **Prisbillighed** ser sådan ud:

![Eksempeltabel med Farve efter regler](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)

## <a name="color-by-color-values"></a>Farve efter farveværdier

Hvis du har et felt eller en måling med farvenavn eller hex-værdidata, kan du bruge betinget formatering til automatisk at anvende disse farver på en kolonnes baggrund eller skriftfarve. Du kan også bruge brugerdefineret logik til at anvende farver på skrifttypen eller baggrunden.

Feltet kan bruge de farveværdier, der er angivet i specifikationen for CSS-farve på [https://www.w3.org/TR/css-color-3/](https://www.w3.org/TR/css-color-3/). Disse farveværdier kan omfatte:
- 3-, 6- eller 8-cifrede hex-koder, f.eks #3E4AFF. Sørg for at inkludere #-tegnet i starten af koden. 
- RGB- eller RGBA-værdier, som f.eks. RGBA (234, 234, 234, 0,5)
- HSL- eller HSLA-værdier, som f.eks. HSLA (123, 75 %, 75 %, 0,5)
- Farvenavne, f.eks. grøn, SkyBlue eller PeachPuff. 

Følgende tabel indeholder et farvenavn, der er knyttet til hver delstat: 

![Tabel over delstater med farvenavne](media/desktop-conditional-table-formatting/conditional-table-formatting_01.png)

Hvis du vil formatere kolonnen **Farve** på baggrund af feltværdier, skal du vælge **Betinget formatering** for feltet **Farve** og derefter vælge **Baggrundsfarve** eller **Skriftfarve**. 

I dialogboksen **Baggrundsfarve** eller **Skriftfarve** skal du vælge **Feltværdi** på rullelisten **Formatér efter**.

![Formatér efter feltværdi](media/desktop-conditional-table-formatting/conditional-table-formatting_02.png)

Et eksempel på en tabel med værdibaseret farvefelt formatering **Baggrundsfarve** på feltet **Farve** ser sådan ud:

![Eksempel på tabel med baggrundsformatering efter feltværdi](media/desktop-conditional-table-formatting/conditional-table-formatting_03.png)

Hvis du også bruger **Feltværdi** til at formatere kolonnens **Skriftfarve**, er resultatet en dækkende farve i kolonnen **Farve**:

![Formatér baggrund og skrifttype efter feltværdi](media/desktop-conditional-table-formatting/conditional-table-formatting_04.png)

## <a name="color-based-on-a-calculation"></a>Farve baseret på en beregning

Du kan oprette en beregning, som giver forskellige værdier baseret på de betingelser for forretningslogik, du vælger. Det er normalt hurtigere at oprette en formel end at oprette flere regler i dialogboksen Betinget formatering. 

Følgende formel anvender f.eks. hex-farveværdier i en ny kolonne for **Rangering efter prisbillighed**, baseret på eksisterende kolonneværdier for **Prisbillighed**:

![Formelberegning](media/desktop-conditional-table-formatting/conditional-table-formatting_05.png)

Hvis du vil anvende farverne, skal du vælge **Baggrundsfarve** eller **Skriftfarve** betinget formatering for kolonnen **Prisbillighed** og basere formateringen på **Feltværdi** af kolonnen **Rangering efter prisbillighed**. 

![Grundlæggende baggrundsfarve på en beregnet kolonne](media/desktop-conditional-table-formatting/conditional-table-formatting_06.png)

Eksempel på tabel med baggrundsfarve for **Prisbillighed** baseret på beregnet **Rangering af prisbillighed** ser sådan ud:

![Eksempel på tabel med en beregnet værdibaseret farve](media/desktop-conditional-table-formatting/conditional-table-formatting_07.png)

Med lidt fantasi og nogle beregninger kan du oprette mange flere variationer.

## <a name="add-data-bars"></a>Tilføj datalinjer

Hvis du vil have vist datalinjer, der er baseret på celleværdier, skal du vælge **Betinget formatering** til feltet **Prisbillighed** og derefter vælge **Datalinjer** i rullemenuen. 

I dialogboksen **Datalinjer** er indstillingen **Vis kun søjle** som standard ikke markeret, så der vises både linjerne og de faktiske værdier i tabelcellerne. Hvis du kun vil have vist datalinjerne, skal du markere afkrydsningsfeltet **Vis kun søjle**.

Du kan angive værdierne **Minimum** og **Maksimum**, farver på datasøjler og retning samt aksens farve. 

![Dialogboksen Datalinjer](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

Med datalinjer, der er anvendt på kolonnen **Prisbillighed**, ser eksempeltabellen sådan ud:

![Eksempel på tabel kun med datalinjer](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)

## <a name="add-icons"></a>Tilføj ikoner

Hvis du vil have vist ikoner, der er baseret på celleværdier, skal du vælge **Betinget formatering** til feltet og derefter vælge **Ikoner** i rullemenuen. 

I dialogboksen **Ikoner** under **Formatér efter** skal du vælge enten **Regler** eller **Feltværdi**. 

Hvis du vil formatere efter regler, skal du vælge **feltet Baseret på**, metoden **Opsummering**, **Ikonets layout**, **Ikonets justering**, ikonets **Typografi** og en eller flere **Regler**. Under **Regler** skal du angive en eller flere regler med en betingelse af typen *Hvis værdi* og en *og*-værdi og vælge et ikon, der skal anvendes på hver enkelt regel. 

Hvis du vil formatere efter feltværdier, skal du vælge **feltet Baseret på**, metoden **Opsummering**, **Ikonets layout** og **Ikonets justering**.

Følgende eksempel tilføjer ikoner, der er baseret på tre regler:

![Dialogboksen Ikoner](media/desktop-conditional-table-formatting/table-formatting-1-default-table.png)

Vælg **OK**. Med ikoner anvendt på kolonnen **Prisbillighed** efter regler ser eksempeltabellen sådan ud:

![Eksempel på tabel med ikoner](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

## <a name="format-as-web-urls"></a>Formatér som webadresser

Hvis du har en kolonne eller måling, der indeholder webadresser, kan du bruge betinget formatering til at anvende disse URL-adresser til felter som aktive links. Følgende tabel har f.eks. en kolonne af typen **Websted** med URL-adresser til websteder for hver tilstand:

![Tabel med kolonne til webadresse](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

Hvis du vil have vist hver enkelt delstats navn som et dynamisk link til webstedet, skal du vælge **Betinget formatering** for feltet **State** og derefter vælge **URL-adresse til websted**. I dialogboksen **URL-adresse til websted** skal du under **feltet Baseret på** vælge **Websted** og derefter vælge **OK**. 

Med formatering for **URL-adresse til websted** anvendt på feltet **State** er hvert navn på en delstat et aktivt link til sit websted. Følgende eksempeltabel har formatering for **URL-adresse til websted** anvendt på kolonnen **State** og betingede **Datalinjer** og **Baggrundsformatering** anvendt på kolonnen **Prisbillighed**. 

![Tabel med URL-adresse til websted, datalinjer og baggrundsfarve](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

## <a name="totals-and-subtotals"></a>Totaler og subtotaler

Fra og med versionen fra april 2020 kan du anvende regler for betinget formatering på totaler og subtotaler for både tabel- og matrixvisualiseringer. 

Du anvender reglerne for betinget formatering ved at bruge rullelisten **Anvend på** i betinget formatering, som vist på følgende billede.

![Formatér totaler og subtotaler](media/desktop-conditional-table-formatting/table-formatting-4.png)

Du skal manuelt angive tærskler og intervaller for regler for betinget formatering. I forbindelse med matrixer refererer **værdier** til det laveste synlige niveau i matrixhierarkiet.


## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger
Der er et par overvejelser, du skal gøre, når du arbejder med betinget formatering af tabeller:

- Betinget formatering anvendes kun på værdier i visualiseringer for Tabel eller Matrix og anvendes ikke på nogen subtotaler, samlede totaler eller rækken **Total**. 
- Alle tabeller, der ikke har en gruppering, vises som en enkelt række, der ikke understøtter betinget formatering.
- Du kan ikke anvende gradueringsformat med automatiske værdier for maksimum/minimum eller regelbaseret formatering med procentregler, hvis dine data indeholder *NaN*-værdier. NaN står for "Not a number" (ikke et tal) og skyldes ofte en fejl med division med nul. Du kan bruge [funktionen DIVIDE() DAX](/dax/divide-function-dax) til at undgå disse fejl.
- Betinget formatering skal have en sammenlægning eller en måling for at blive anvendt på værdien. Det er derfor, at du får vist 'Først' eller 'Sidst' i eksemplet **Farve efter værdi**. Hvis du opretter din rapport i en flerdimensionel Analysis Service-kube, kan du ikke bruge en attribut til betinget formatering, medmindre kubeejeren har oprettet en måling, der giver værdien.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om farveformatering under [Tip og tricks til farveformatering i Power BI](../visuals/service-tips-and-tricks-for-color-formatting.md)