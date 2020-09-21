---
title: Administrer din datakilde – Analysis Services
description: Sådan administrerer du en datagateway i det lokale miljø samt de datakilder, der hører til denne gateway. Dette omhandler Analysis Services i både flerdimensionel og tabellarisk tilstand.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: c97a303a5b3241f49e82aac41d9ed7984c3a5af1
ms.sourcegitcommit: 002c140d0eae3137a137e9a855486af6c55ad957
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/10/2020
ms.locfileid: "89642298"
---
# <a name="manage-your-data-source---analysis-services"></a>Administrer din datakilde – Analysis Services

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Når du har [installeret datagatewayen i det lokale miljø](/data-integration/gateway/service-gateway-install), skal du [tilføje datakilder](service-gateway-data-sources.md#add-a-data-source), der kan bruges sammen med gateway'en. Denne artikel indeholder oplysninger om, hvordan du arbejder med gateways og SQL Server Analysis Services-datakilder (SSAS), der enten bruges til planlagte opdateringer eller til direkte forbindelser.

Hvis du vil have mere at vide om, hvordan du konfigurerer en direkte forbindelse til Analysis Services, skal du [se denne video](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be).

> [!NOTE]
> Hvis du har en Analysis Services-datakilde, skal du installere gatewayen på en computer, der er tilsluttet det samme område/domæne som din Analysis Services-server.

## <a name="add-a-data-source"></a>Tilføj en datakilde

Du kan finde oplysninger om, hvordan du tilføjer en datakilde i [Tilføj en datakilde](service-gateway-data-sources.md#add-a-data-source). Vælg **Analysis Services** som **Datakildetype**, hvis du opretter forbindelse til enten en flerdimensionel server eller en tabellarisk server.

![Tilføj Analysis Services-datakilden](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Udfyld oplysningerne om datakilden, herunder **Server** og **Database**. De oplysninger, du indtastede for **Brugernavn** og **Adgangskode**, bruges af gateway'en til at oprette forbindelse til Analysis Services-instansen.

> [!NOTE]
> Den Windows-konto, du angiver, skal være medlem af rollen Serveradministrator på den Analysis Services-forekomst, du opretter forbindelse til. Hvis adgangskoden til kontoen er angivet til at udløbe, kan brugerne få en forbindelsesfejl, hvis adgangskoden ikke er opdateret for datakilden. Hvis du vil have mere at vide om, hvor legitimationsoplysningerne gemmes, skal du se [Lagring af krypterede legitimationsoplysninger i cloudmiljøet](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Angivelse af indstillinger for datakilden](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Når du har udfyldt alt, skal du vælge **Tilføj**. Du kan nu bruge denne datakilde til planlagt opdatering eller direkte forbindelser op mod en Analysis-server, der er i det lokale miljø. Du får vist *Forbindelsen blev oprettet*, hvis det lykkes.

![Visning af forbindelsesstatus](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Avancerede indstillinger

Du kan eventuelt konfigurere niveauet for beskyttelse af personlige oplysninger for datakilden. Denne indstilling styrer, hvordan data kan kombineres. Det bruges kun for planlagte opdateringer. Indstillingen for beskyttelsesniveau gælder ikke for direkte forbindelser. Hvis du vil vide mere om niveauer for beskyttelse af personlige oplysninger, skal du se [Niveauer for beskyttelse af personlige oplysninger (Power-forespørgsel)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Angivelse af niveauet for beskyttelse af personlige oplysninger](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="user-names-with-analysis-services"></a>Brugernavne med Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Hver gang en bruger interagerer med en rapport, der har forbindelse til Analysis Services, overføres det effektive brugernavn til gatewayen og derefter til den lokale Analysis Services-server. Den mailadresse, du bruger til at logge på Power BI med, sendes til Analysis Services som den effektive bruger. Den overføres i forbindelsesegenskaben [EffectiveUserName](/analysis-services/instances/connection-string-properties-analysis-services#bkmk_auth). 

Denne mailadresse skal matche et defineret UPN (brugerens hovednavn) på det lokale Active Directory-domæne. UPN'et er en egenskab for en Active Directory-konto. Windows-kontoen skal være til stede i en Analysis Services-rolle. Hvis der ikke findes et match i Active Directory, logges der ikke på. Hvis du vil vide mere om Active Directory og brugernavngivelse, skal du se [Attributter for brugernavngivning](/windows/win32/ad/naming-properties).

Du kan også [knytte dit Power BI-logonnavn til et UPN for en lokal mappe](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="map-user-names-for-analysis-services-data-sources"></a>Tilknyt brugernavne for Analysis Services-datakilder

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

I Power BI kan brugernavne tilknyttes for Analysis Services-datakilder. Du kan konfigurere regler for at knytte et brugernavn, der er logget på med Power BI, til et navn, der er sendt for EffectiveUserName på Analysis Services-forbindelsen. Funktionen til tilknytning af brugernavne er god måde at løse problemet på, når dit brugernavn i Azure Active Directory (Azure AD) ikke stemmer overens med et UPN i din lokale Active Directory-instans. Hvis din mailadresse for eksempel er nancy@contoso.onmicrsoft.com, kan du knytte den til nancy@contoso.com, og denne værdi overføres til gateway'en.

Du kan knytte navne til Analysis Services på to forskellige måder:

* Manuel brugertilknytning igen
* Active Directory-egenskabsopslag for at gentilknytte Azure AD UPN'er til Active Directory-brugere (Active Directory-opslagstilknytning)

Det er muligt at udføre manuel tilknytning ved hjælp af den anden metode, men det er meget tidskrævende og svært at vedligeholde. Det er især vanskeligt, når det mønster, der matcher, ikke er tilstrækkeligt. Som eksempler kan nævnes, når der er forskelle mellem domænenavne i Azure AD og Active Directory i det lokale miljø, eller når der er forskelle mellem brugerkontonavne i Azure AD og Active Directory. Derfor anbefales det ikke at foretage manuel tilknytning med den anden metode.

Vi beskriver disse to metoder i rækkefølge i de følgende to afsnit.

### <a name="manual-user-name-remapping"></a>Manuel tilknytning af brugernavn igen

Du kan konfigurere brugerdefinerede UPN-regler for Analysis Services-datakilder. Brugerdefinerede regler hjælper dig, hvis dine logon-navne til Power BI-tjenesten ikke stemmer overens med dit lokale mappe-UPN. Hvis du f.eks. logger på Power BI med john@contoso.com, men din lokale mappe-UPN er john@contoso.local, kan du konfigurere en tilknytningsregel for at få john@contoso.local overført til Analysis Services.

Følg disse trin for at komme til UPN-tilknytningsskærmen.

1. Gå til tandhjulsikonet, og vælg **Administrer gateways**.
2. Udvid den gateway, der indeholder Analysis Services-datakilden. Eller hvis du ikke har oprettet Analysis Services-datakilden, kan du gøre det på nuværende tidspunkt.
3. Vælg datakilden, og vælg derefter fanen **Brugere**.
4. Vælg **Tilknyt brugernavne**.

    ![Skærm med tilknytning af UPN](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Du får vist indstillinger til at tilføje regler og foretage test for en given bruger.

> [!NOTE]
> Du kan komme til at foretage ændringer af en bruger ved en fejl. Hvis **Erstat (oprindelig værdi)** f.eks. er contoso.com, og **Med (Nyt navn)** er @contoso.local, erstattes alle brugere med et login, der indeholder @contoso.com, med @contoso.local. Hvis **Erstat (Oprindeligt navn)** er dave@contoso.com, og **Med (Nyt navn)** er dave@contoso.local, sendes en bruger med logonnet v-dave@contoso.com som v-dave@contoso.local.

### <a name="active-directory-lookup-mapping"></a>Active Directory-opslagstilknytning

Hvis du vil udføre Active Directory-opslag i det lokale miljø for at tilknytte Azure AD UPN'er til Active Directory-brugere igen, skal du benytte fremgangsmåden i dette afsnit. Lad os se, hvordan det fungerer.

Der sker følgende i Power BI-tjenesten:

* For hver forespørgsel fra en Power BI Azure AD-bruger til en SSAS-server i det lokale miljø overføres en UPN-streng, f.eks.      firstName.lastName@contoso.com.

> [!NOTE]
> Manuelle UPN-brugertilknytninger, der er defineret i konfigurationen af Power BI-datakilden, anvendes stadig, *før* brugernavnestrengen sendes til datagateway'en i det lokale miljø.

I datagatewayen i det lokale miljø med konfigurerbar brugerdefineret brugertilknytning skal du følge denne fremgangsmåde.

1. Find det Active Directory, der skal søges i. Du kan bruge automatisk eller konfigurerbar.
2. Slå attributten på den Active Directory-person (f.eks. mail) op, fra Power BI-tjenesten. Attributten er baseret på en indgående UPN-streng som firstName.lastName@contoso.com.
3. Hvis Active Directory-opslaget mislykkes, forsøger den at bruge det UPN, der blev overført som EffectiveUser til SSAS.
4. Hvis Active Directory-opslaget lykkes, hentes UserPrincipalName for den pågældende Active Directory-person.
5. Mailadressen for UserPrincipalName overføres som EffectiveUser til SSAS, f.eks. Alias@corp.on-prem.contoso.

Sådan konfigurerer du gateway'en til at udføre Active Directory-opslaget:

1. [Download og installér den nyeste gateway](/data-integration/gateway/service-gateway-install).

2. I gatewayen skal du ændre datagatewaytjenesten i det lokale miljø, så den kører med en domænekonto i stedet for en lokal tjenestekonto. Ellers fungerer Active Directory-opslaget ikke korrekt på kørselstidspunktet. Gå til [programmet for datagateway i det lokale miljø](/data-integration/gateway/service-gateway-app) på din maskine, og gå derefter til **Tjenesteindstillinger** > **Skift tjenestekonto**. Kontrollér, at du har genoprettelsesnøglen til denne gateway, da du skal gendanne den på den samme maskine, medmindre du vil oprette en ny gateway i stedet. Genstart gatewaytjenesten, så ændringerne kan træde i kraft.

3. Gå til installationsmappen for gatewayen, *C:\Program Files\On-premises data gateway* som administrator for at sikre, at du har skriverettigheder. Åbn filen *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

4. Rediger følgende to konfigurationsværdier i henhold til *dine* Active Directory-attributkonfigurationer til dine Active Directory-brugere. Følgende konfigurationsværdier er eksempler. Angiv værdierne på baggrund af din Active Directory-konfiguration. Der skelnes mellem store og små bogstaver i disse konfigurationer, så sørg for, at de matcher værdierne i Active Directory.

    ![Indstillinger for Azure AD](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    Hvis der ikke er angivet en værdi for ADServerPath-konfigurationen, bruger gatewayen det globale standardkatalog. Du kan også angive flere værdier for ADServerPath. Værdierne skal adskilles med et semikolon som vist i følgende eksempel:

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    Gatewayen analyserer værdierne for ADServerPath fra venstre mod højre, indtil den finder et match. Hvis der ikke blev fundet et match, bruges den oprindelige UPN. Kontrollér, at den konto, der kører gatewaytjenesten (PBIEgwService), har forespørgselstilladelser til alle Active Directory-servere, som du angiver i ADServerPath.

    Gateway'en understøtter to typer ADServerPath som vist i følgende eksempler:

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. Genstart datagatewaytjenesten i det lokale miljø, for at konfigurationsændringen kan træde i kraft.

### <a name="work-with-mapping-rules"></a>Arbejd med tilknytningsregler

Hvis du vil oprette en tilknytningsregel, skal du angive en værdi for **Oprindeligt navn** og **Nyt navn** og derefter vælge **Tilføj**.

| Felt | Beskrivelse |
| --- | --- |
| Erstat (Oprindeligt navn) |Den mailadresse, du brugte til at logge på Power BI. |
| Med (Nyt navn) |Den værdi, du vil erstatte mailadressen med. Resultatet af erstatningen er det, der overføres til egenskaben EffectiveUserName for Analysis Services-forbindelsen. |

![Oprettelse af en tilknytningsregel](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

Når du markerer et element på listen, kan du vælge at omarrangere listen ved hjælp af pileikonerne. Du kan desuden slette posten.

![Omrokering af et element på listen](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="use-a-wildcard"></a>Brug et jokertegn

Du kan bruge et jokertegn (*) i strengen **Erstat (Oprindeligt navn)** . Det kan kun bruges alene og ikke sammen med andre strengdele. Brug et jokertegn, hvis du vil tage alle brugere og overføre en enkelt værdi til datakilden. Denne metode er nyttig, når du gerne vil have, at alle brugere i organisationen benytter den samme bruger i det lokale miljø.

### <a name="test-a-mapping-rule"></a>Test en tilknytningsregel

Angiv en værdi for **Oprindeligt navn** for at validere det oprindelige navn, det erstattes af. Vælg **Test regel**.

![Test af en tilknytningsregel](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> Det tager nogle få minutter for tjenesten at bruge de regler, der er blevet gemt. Reglen fungerer med det samme i browseren.

### <a name="limitations-for-mapping-rules"></a>Begrænsninger for tilknytningsregler

Tilknytning gælder den bestemte datakilde, der konfigureres. Det er ikke en global indstilling. Hvis du har flere Analysis Services-datakilder, skal du knytte brugerne til hver enkelt datakilde.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Godkendelse til en live Analysis Services-datakilde

Hver gang en bruger interagerer med Analysis Services, overføres det effektive brugernavn til gateway'en og derefter til den lokale Analysis Services-server. Den UPN, som typisk er den mailadresse, du bruger til at logge på clouden med, sendes til Analysis Services som den effektive bruger. UPN'et overføres i forbindelsesegenskaben EffectiveUserName. 

Denne mailadresse skal svare til et UPN, der er defineret i det lokale Active Directory-domæne. UPN'et er en egenskab for en Active Directory-konto. Den pågældende Windows-konto skal være til stede i en Analysis Services-rolle for at have adgang til serveren. Hvis der ikke findes et match i Active Directory, kan der ikke logges på.

Analysis Services kan også levere filtrering baseret på denne konto. Filtreringen kan finde sted med rollebaseret sikkerhed eller sikkerhed på rækkeniveau.

## <a name="role-based-security"></a>Rollebaseret sikkerhed

Modeller giver sikkerhed, som er baseret på brugerroller. Roller er defineret for et bestemt modelprojekt under oprettelse i SQL Server Data Tools – Business Intelligence, eller når en model er installeret, ved hjælp af SQL Server Management Studio. Roller indeholder medlemmer efter Windows-brugernavn eller efter Windows-gruppe. Roller definerer de tilladelser, som en bruger har til at forespørge på eller udføre handlinger på modellen. De fleste brugere tilhører en rolle med læsetilladelser. Andre roller er beregnet til administratorer med tilladelser til at behandle elementer, administrere databasefunktioner og administrere andre roller.

## <a name="row-level-security"></a>Sikkerhed på rækkeniveau

Sikkerhed på rækkeniveau er specifik for Analysis Services-sikkerhed på rækkeniveau. Modeller kan levere dynamisk sikkerhed på rækkeniveau. I modsætning til at have mindst én rolle, som brugere tilhører, er dynamisk sikkerhed ikke påkrævet for en tabelmodel. På et højt niveau definerer dynamisk sikkerhed en brugers læseadgang til data helt ned til en bestemt række i en bestemt tabel. I lighed med roller er dynamisk sikkerhed på rækkeniveau afhængig af en brugers Windows-brugernavn.

En brugers mulighed for at forespørge på og få vist modeldata bestemmes af:

- De roller, som deres Windows-brugerkonto tilhører, som medlem.
- Dynamisk sikkerhed på rækkeniveau, hvis den er konfigureret.

Det er uden for denne artikels omfang at drøfte implementering af roller og dynamisk sikkerhed på rækkeniveau i modeller. Få yderligere oplysninger i [Roller (SSAS-tabel)](/analysis-services/tabular-models/roles-ssas-tabular) og [Sikkerhedsroller (Analysis Services – flerdimensionelle data)](/analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data) på MSDN. Hvis du vil have den mest detaljerede forståelse af sikkerhed med en tabellarisk model, skal du downloade og læse [dette whitepaper om sikring af den tabellariske, semantiske BI-model](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

## <a name="what-about-azure-ad"></a>Hvad med Azure AD?

Microsoft-cloudtjenester bruger [Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) til at godkende brugere. Azure AD er lejeren, der indeholder brugernavne og sikkerhedsgrupper. Typisk er den mailadresse, som en bruger logger på med, den samme som kontoens UPN.

## <a name="what-is-the-role-of-my-local-active-directory-instance"></a>Hvad er rollen for min lokale forekomst af Active Directory?

For at Analysis Services kan bestemme, om en bruger, der opretter forbindelse til den, tilhører en rolle med tilladelser til at læse data, skal serveren konvertere det effektive brugernavn, der sendes fra Azure AD til gateway'en og videre til Analysis Services-serveren. Analysis Services-serveren overfører det effektive brugernavn til en Windows Active Directory-domænecontroller (DC). Active Directory DC bekræfter derefter, at det effektive brugernavn er et gyldigt UPN på en lokal konto. Det returnerer brugerens Windows-brugernavn til Analysis Services-serveren.

EffectiveUserName kan ikke bruges på en Analysis Services-server, der ikke er tilsluttet et domæne. Analysis Services-serveren skal tilsluttes et domæne for at undgå eventuelle logonfejl.

## <a name="how-do-i-tell-what-my-upn-is"></a>Hvordan kan jeg se, hvad mit UPN er?

Du ved måske ikke, hvad dit UPN er, og du er muligvis ikke domæneadministrator. Du kan bruge følgende kommando fra din arbejdsstation for at finde ud af, hvad UPN'et for din konto er.

    whoami /upn

Resultatet ligner en mailadresse, men det er det UPN, der er på din domænekonto. Hvis du bruger en Analysis Services-datakilde til direkte forbindelser, og hvis denne UPN ikke matcher den mailadresse, du bruger til at logge på Power BI, kan du se, hvordan du [tilknytter brugernavne](#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-ad"></a>Synkroniser en lokal Active Directory med Azure AD

Hvis du vil bruge Analysis Services Live forbindelser, skal dine lokale Active Directory-konti stemme overens med Azure AD. UPN'en skal matche mellem kontiene.

Cloudtjenesterne kender kun til konti på Azure AD. Det har ingen betydning, hvis du har tilføjet en konto i dit lokale Active Directory. Hvis kontoen ikke findes i Azure AD, kan den ikke bruges. Du kan matche dine lokale Active Directory-konti med Azure AD på forskellige måder:

- Du kan føje konti manuelt til Azure AD.

   Du kan oprette en konto på Azure Portal eller i Microsoft 365 Administration, og så matcher kontonavnet UPN for den lokale Active Directory-konto.

- Du kan bruge værktøjet [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) til at synkronisere lokale konti med din Azure AD-lejer.

   Værktøjet Azure AD Connect indeholder muligheder for synkronisering og konfiguration af godkendelse. Mulighederne omfatter synkronisering af adgangskode-hash, videregivelse til godkendelse og samling. Hvis du ikke er administrator af lejeren eller lokal domæneadministrator, skal du kontakte it-administratoren for at få hjælp til konfigurationen.

   Ved at bruge Azure AD Connect sikrer du, at UPN'et matcher mellem Azure AD og din lokale Active Directory-instans.

> [!NOTE]
> Når konti synkroniseres med værktøjet Azure AD Connect, oprettes der nye konti i din Azure AD-lejer.

## <a name="use-the-data-source"></a>Brug datakilden

Når du opretter datakilden, er den tilgængelig til brug med enten direkte forbindelser eller via en planlagt opdatering.

> [!NOTE]
> Servernavnet og databasenavnet skal matche mellem Power BI Desktop og datakilden i datagatewayen i det lokale miljø.

Forbindelsen mellem dit datasæt og datakilden i gatewayen er baseret på dit servernavn og databasenavn. Disse navne skal være ens. Hvis du f.eks. angiver en IP-adresse for servernavnet i Power BI Desktop, skal du bruge IP-adressen for datakilden i konfigurationen af gatewayen. Hvis du bruger *SERVER\INSTANCE* i Power BI Desktop, skal du også bruge det i den datakilde, der er konfigureret for gateway'en.

Dette krav gælder for både direkte forbindelser og planlagt opdatering.

### <a name="use-the-data-source-with-live-connections"></a>Brug datakilden med direkte forbindelser

Sørg for, at servernavnet og databasenavnet matcher mellem Power BI Desktop og den konfigurerede datakilde for gateway'en. Du skal også sikre, at din bruger er angivet under fanen **Brugere** i datakilden for at kunne publicere datasæt med direkte forbindelse. Valget til direkte forbindelser sker i Power BI Desktop, når du importerer data første gang.

Når du publicerer fra enten Power BI Desktop eller **Hent Data**, bør dine rapporter begynde at fungere. Det kan tage flere minutter, efter du har oprettet datakilden i gateway'en, før forbindelsen kan bruges.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Brug datakilden med planlagt opdatering

Hvis du er angivet under fanen **Brugere** i den datakilde, der er konfigureret i gatewayen, og server- og databasenavnet stemmer overens, får du vist gatewayen som en mulighed, der kan bruges sammen med en planlagt opdatering.

![Visning af brugerne](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Begrænsninger for Analysis Services-liveforbindelser

Du kan bruge en liveforbindelse til tabellariske eller flerdimensionelle forekomster.

| **Serverversion** | **Påkrævet SKU** |
| --- | --- |
| 2012 SP1 CU4 eller nyere |Business Intelligence- og Enterprise-SKU |
| 2014 |Business Intelligence- og Enterprise-SKU |
| 2016 |Standard-SKU eller nyere |

* Funktionen til formatering på celleniveau og oversættelse understøttes ikke.
* Handlinger og navngivne sæt vises ikke for Power BI. Du kan stadig oprette forbindelse til flerdimensionelle kuber, der også indeholder handlinger eller navngivne sæt, og oprette visuelle elementer og rapporter.

## <a name="next-steps"></a>De næste trin

* [Fejlfinding af datagateway i lokalt miljø](/data-integration/gateway/service-gateway-tshoot)
* [Foretag fejlfinding af gateways – Power BI](service-gateway-onprem-tshoot.md)

Har du flere spørgsmål? Prøv at spørge [Power BI-community'et](https://community.powerbi.com/).
