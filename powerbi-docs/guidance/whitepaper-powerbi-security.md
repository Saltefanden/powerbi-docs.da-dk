---
title: Whitepaper om Power BI-sikkerhedsrapport
description: Et whitepaper, der beskriver og beskriver sikkerhedsarkitektur og implementering af Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/11/2021
LocalizationGroup: Conceptual
ms.openlocfilehash: 9752eddb82fa8f612b9d740cf010c0649ba5b3f8
ms.sourcegitcommit: 803653e8aa79ed38ec555c27c13b3b6835f98a5d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/17/2021
ms.locfileid: "100569746"
---
# <a name="power-bi-security-white-paper"></a>Whitepaper om Power BI-sikkerhedsrapport

**Oversigt:** Power BI er et tilbud via online software service (*SaaS* eller software som en service) fra Microsoft, der gør det muligt for dig nemt og hurtigt at oprette dashboards til Business Intelligence, rapporter, datasæt og visualiseringer, der er selvbetjenings baseret. Med Power BI kan du oprette forbindelse til mange forskellige datakilder, kombinere og forme data fra disse forbindelser og derefter oprette rapporter og dashboards, som kan deles med andre.

**Skrivere:** Yitzhak Kesselman, uafskallet Osborne, Matt Neely, Tony Bencic, Srinivasan Turuvekere, Cristian Petculescu, ADI Regev, Naveen Sivaraj, Benjamin Glastein, Evgeny Tshiorny, Arthi Ramasubramanian Iyer, SID Jayadevan, Ronald Chang, ori Eduar, Anton Fritz, Idan Sheinberg, Ron Gilad, Sagiv Hadaya, Inbar Igor, Uzhviev Roth, Tarquino Gennady, Pats Orion, Yury Berezansky, Maya Shenhav Romit Chattopadhyay, Yariv Maimon

**Tekniske reviewere:** Cristian Petculescu, Amir Netz, Sergei Gundorov

**Gælder for:** Power BI SaaS, Power BI Desktop, Power BI Premium, Power BI Embedded analyse, Power BI-Mobil

> [!NOTE]
> Du kan gemme eller udskrive dette whitepaper ved at vælge **Udskriv** i din browser og derefter vælge **Gem som PDF**.

## <a name="introduction"></a>Introduktion

Power BI er en onlinesoftwaretjeneste (*SaaS* eller Software as a Service) fra Microsoft, der gør det nemt og hurtigt for dig at oprette dashboards, rapporter, datasæt og visualiseringer i forbindelse med selvbetjenings-business intelligence. Med Power BI kan du oprette forbindelse til mange forskellige datakilder, kombinere og forme data fra disse forbindelser og derefter oprette rapporter og dashboards, som kan deles med andre.

Verden ændrer sig hurtigt. organisationer gennemgår en accelereret digital transformation, og vi får vist en omfattende stigning i Fjern arbejdet, øget kundebehov for onlinetjenester og øget brug af avancerede teknologier i drift og forretningsmæssige beslutninger. Og det hele er baseret på clouden.

I takt med at overgangen til clouden er ændret fra et Trickle til et oversvømmelse, og med det nye, eksponerede overflade område, der følger med det, kan du bruge flere og flere virksomheder, *hvor sikkerheden er mine data i clouden?* og *hvilken end-to-end-beskyttelse der er tilgængelig for at forhindre, at mine følsomme data* er ved at blive utæt? Og på BI-platforme, der ofte håndterer nogle af de mest strategiske oplysninger i virksomheden, er disse spørgsmål lidt vigtige.

Det gamle funda mente BI-sikkerhedsmodel – sikkerhed på objektniveau og sikkerhed på rækkeniveau – mens den stadig er vigtig, er ikke længere tilstrækkelig til at kunne vise den type sikkerhed, der kræves i clouden. Organisationer skal i stedet søge efter en skybaseret sikkerhedsløsning med flere niveauer, som er baseret på flere niveauer, til deres business intelligence data.

Power BI blev bygget til at levere branchens førende komplette og hermetisk beskyttelse af data. Produktet har opnået de højeste sikkerheds klassifikationer, der er tilgængelige i branchen, og i dag mange nationale sikkerhedsmyndigheder, finansielle institutioner og sundhedspleje udbydere overdrager det de mest følsomme oplysninger.

Det alle starter med fundamentet. Efter en grov periode i de tidlige 2000 har Microsoft skabt store investeringer til at udbedre sikkerhedssvagheder, og i de følgende årtier bygger en meget stærk sikkerheds stak, som er lige så dyb som maskinens BIOS-kerne på chip. der er en udvidelse af hele vejen op til slutbruger oplevelser. Disse omfattende investeringer fortsætter, og i 3.500 dag er Microsoft-teknikere i gang med at bygge og forbedre Microsofts sikkerheds stakke og ved proaktivt at adressere den stadigt mere robuste trussel. Med milliarder af computere, lokale virksomheder og utallige zettabytes af oplysninger, der overdrages til Microsofts beskyttelse, er virksomheden nu den mest avancerede sikkerheds stak i den tekniske branche og vises bredt som global leder i kampen mod skadelige agenter.

Power BI bygger på dette meget stærke fundament. Den bruger samme sikkerheds stak, der optjente Azure til at håndtere og beskytte verdens mest følsomme data, og den integreres med de mest avancerede oplysninger om beskyttelse og overholdelse af Microsoft 365. Oven på disse leverer den sikkerhed ved hjælp af sikkerhedsforanstaltninger med flere lag, hvilket resulterer i end-to-end-beskyttelse, der er designet til at håndtere de unikke udfordringer, der er forbundet med cloudens ERA.

Hvis du vil levere en end-to-end-løsning til beskyttelse af følsomme aktiver, skal du bruge det produktteam, der er nødvendigt for at håndtere potentielle kunde bekymringer, på flere samtidige forkanter:
* *Hvordan styrer vi, hvem der kan oprette forbindelse, hvor de opretter forbindelse fra, og hvordan de opretter forbindelse?* *Hvordan kan vi kontrollere forbindelserne?*
* *Hvordan gemmes dataene?* *Hvordan krypteres den?* *Hvilke kontrolelementer har jeg på mine data?*
* *Hvordan gør jeg du kontrollere og beskytte følsomme data?* *Hvordan gør jeg sikrer du, at disse data ikke kan være i et uden for organisationen?*
* *Vil du Hvordan gør jeg overvåge, hvem der foretager handlinger?* *Hvordan gør jeg reagere hurtigt, hvis der er mistænkelig aktivitet i tjenesten?*

I denne artikel får du et omfattende svar på alle disse spørgsmål. Det starter med en oversigt over tjenestens arkitektur og forklarer, hvordan systemets hoved flows fungerer. Derefter flyttes den til for at beskrive, hvordan brugerne kan godkende Power BI, hvordan dataforbindelser oprettes, og hvordan Power BI lagrer og flytter data gennem tjenesten. I det sidste afsnit beskrives de sikkerhedsfunktioner, der gør det muligt for dig som tjenesteadministrator at beskytte dine mest værdifulde aktiver.

Power BI-tjenesten er underlagt [servicebetingelserne for Microsoft Online](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31) og [erklæringen om beskyttelse af personlige oplysninger for Microsoft Enterprise](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx). Du kan finde placeringen af databehandling ved at referere til placeringen af databehandlings vilkårene i [vilkår for Microsoft-online tjenester](http://www.microsoftvolumelicensing.com/Downloader.aspx?DocumentId=9555) og til [tillægget om databeskyttelse](https://www.microsoft.com/download/details.aspx?id=101581). Hvis du vil have flere oplysninger om overholdelse af angivne standarder, skal du gå til [Microsoft Trust Center](https://www.microsoft.com/trustcenter), som er den primære ressource for Power BI. Power BI-teamet arbejder hårdt på at give kunderne de nyeste innovationer og produktivitet. Få mere at vide om overholdelse af [Microsofts overholdelses tilbud](/compliance/regulatory/offering-home).

Power BI-tjeneste følger SDL (Security Development Lifecycle), strenge sikkerhedsmetoder, der understøtter kravene til sikkerhed og overensstemmelse. SDL hjælper udviklere med at skabe mere sikker software ved at reducere antallet og alvorsgraden af sårbarheder i software, samtidig med at vi reducerer udviklingsomkostningerne. Få mere at vide på [Microsofts praksis for Security Development Lifecycle](https://www.microsoft.com/securityengineering/sdl/practices).

## <a name="power-bi-architecture"></a>Power BI arkitektur

Power BI-tjeneste er bygget på Azure, som er Microsofts [skybaseret computerplatform](https://azure.microsoft.com/overview/what-is-azure/). Power BI er i øjeblikket udrullet i mange datacentre overalt i verden. Der er mange aktive udrulninger tilgængelige for kunder i de områder, der betjenes af disse datacentre, og et lige antal så stort antal passive udrulninger, der fungerer som sikkerhedskopier for hver aktiv udrulning.

![WFE og Back End](media/whitepaper-powerbi-security/powerbi-security-whitepaper_01.png)

### <a name="web-front-end-cluster-wfe"></a>Web front-end-klynge (WFE)

WFE-klyngen giver brugerens browser med indholdet i den oprindelige HTML-side, når du indlæser webstedet, og administrerer den indledende forbindelse og godkendelsesprocessen for Power BI ved hjælp af Azure Active Directory (Azure AD) til at godkende klienter og angive tokens for efterfølgende klientforbindelser til den Power BI back-end-tjeneste.

![WFE-klyngen](media/whitepaper-powerbi-security/powerbi-security-whitepaper_02.png)

En WFE-klynge består af et ASP.NET-websted, der kører i det [Azure app service miljø](/azure/app-service/environment/intro). Når brugerne forsøger at oprette forbindelse til Power BI-tjeneste, kan klientens DNS-tjeneste kommunikere med Azure-Traffic Manager for at finde det mest relevante (normalt nærmeste) datacenter med en Power BI-installation. Du kan finde flere oplysninger om denne proces under [routing Traffic-routingmetode til Azure Traffic Manager](/azure/traffic-manager/traffic-manager-routing-methods#performance-traffic-routing-method).

Den WFE-klynge, der er tildelt til brugeren, administrerer logon-og godkendelses sekvensen (beskrevet senere i denne artikel) og henter et Azure AD-adgangstoken, når godkendelsen er gennemført. Komponenten ASP.NET i WFE-klyngen analyserer tokenet for at afgøre, hvilken organisation brugeren tilhører, og derefter hører den Power BI globale tjeneste. Egenskaben WFE angiver den browser, hvor back-end-klynge huser organisationens lejer. Når en bruger er godkendt, sker der efterfølgende kundeinteraktioner for kundedata med back-end-eller Premium-klyngen direkte, uden at WFE er en interaktionsgruppe for disse anmodninger.

Statiske ressourcer, f. eks *. *. js*, **. css* og billedfiler, gemmes hovedsageligt på Azure Content Delivery Network (CDN) og hentes direkte af browseren. Bemærk, at de amerikanske myndigheders klynge udrulninger er en undtagelse til denne regel, og med hensyn til overholdelse vil overholdelse af standarder udelukke CDN og i stedet bruge en WFE-klynge fra en kompatibel region til hosting af statisk indhold.

### <a name="power-bi-back-end-cluster-be"></a>Power BI back-end Cluster (være)

Back-end-klyngen er den grund sten, der findes i Power BI. Det består af flere tjeneste slutpunkter, der bruges af web frontend-og API-klienter samt Baggrundstjenester, databaser, cachelagre og forskellige andre komponenter.

Backend er tilgængelig i de fleste Azure-områder, og den udrulles i nye områder, efterhånden som de bliver tilgængelige. Et enkelt Azure-område er vært for en eller flere back-end-klynger, der tillader ubegrænset vandret skalering af Power BI-tjeneste, når de lodrette og vandrette skalerings grænser for en enkelt klynge er opbrugt.

Hver back-end-klynge er i stand til at være vært for alle dataene for alle de lejere, der er tildelt til den pågældende klynge. En klynge, der indeholder dataene fra en bestemt lejer, kaldes lejerens hjemme klynge. En godkendt brugers oplysninger om hjemme klynger leveres af den globale tjeneste og bruges af webfrontend til at dirigere anmodninger til lejerens hjemme klynge.

Hver back-end-klynge består af flere virtuelle maskiner, som er samlet i flere sæt, der kan tilpasses, og som er justeret til udførelse af bestemte opgaver, ressourcer med høj sikkerhed, f. eks. SQL-databaser, lagerkonti, tjeneste busser, cacher og andre nødvendige Cloud-komponenter.

Lejerens metadata og data lagres i klynge grænser, undtagen til data replikering, til en sekundær back-end-klynge i et parret Azure-område i det samme Azure-geografiske område. Den sekundære back-end-klynge fungerer som en failover-klynge i tilfælde af regional afbrydelse og er passiv på ethvert andet tidspunkt.

Back-end-funktionaliteten betjenes af Micro Services, der kører på forskellige maskiner i klyngens virtuelle netværk, som ikke er tilgængeligt fra ydersiden, med undtagelse af to komponenter, der kan opnås adgang til fra det offentlige Internet:
* Gateway tjeneste
* Azure API Management

![Back-end-klyngen](media/whitepaper-powerbi-security/powerbi-security-whitepaper_03.png)

### <a name="power-bi-premium-infrastructure"></a>Power BI Premium infrastruktur

Power BI Premium tilbyder en tjeneste til abonnenter, der kræver Premium Power BI-funktioner, f. eks. dataflows, sideinddelte rapporter, AI osv. Når en kunde tilmelder sig et Power BI Premium abonnement, oprettes Premium-kapaciteten via Azure Resource Manager.

Power BI Premium kapaciteter hostes i back-end-klynger, der er uafhængige af den almindelige Power BI-back-end – se ovenfor). Det giver bedre isolering, ressourceallokering, support, sikkerheds isolation og skalerbarhed i Premium-tilbuddet.

Følgende diagram illustrerer arkitekturen i Power BI Premium infrastruktur:

![Power BI Premium](media/whitepaper-powerbi-security/powerbi-security-whitepaper_05.png)

Forbindelsen til Power BI Premium infrastruktur kan udføres på flere forskellige måder, afhængigt af Brugerscenariet. Power BI Premium-klienter kan være en brugers browser, en regulær Power BI back-end, direkte forbindelser via XMLA-klienter, ARM-API'er osv.

Den Power BI Premium infrastruktur i et Azure-område består af flere Power BI Premium klynger (minimum er en). Størstedelen af Premium-ressourcerne er indkapslet i en klynge (f. eks. en forekomst, beregning), og der er nogle almindelige regionale ressourcer (f. eks. metadatalager). Premium-infrastruktur giver mulighed for at opnå vandret skalerbarhed i et område ved at gøre det muligt at øge ressourcer i klynger og/eller tilføje flere klynger efter behov efter behov (hvis klyngeressourcer nærmer sig deres grænser).

Backbonen for hver klynge er beregnings ressourcer, der administreres af [Virtual Machine Scale Sets (VMSS)](/azure/virtual-machine-scale-sets/overview) og [Azure-service Fabric](/azure/service-fabric/service-fabric-overview). VMSS og Service Fabric muliggør hurtig og problemfri forøgelse af beregnings noder, efterhånden som forbruget vokser og arrangerer udrulningen, administrationen og overvågningen af Power BI Premium tjenester og programmer.

Der er mange omgivende ressourcer, som sikrer en sikker og pålidelig infrastruktur: belastnings balancer, virtuelle netværk, netværks sikkerhedsgrupper, service bus, lager osv. Alle hemmelige oplysninger, nøgler og certifikater, der kræves til Power BI Premium, administreres af [Azure Key Vault](/azure/key-vault/general/basic-concepts) eksklusivt. Enhver godkendelse foretages via integration med Azure AD eksklusivt.

Alle anmodninger, der sendes til Power BI Premium-infrastruktur, går først til front-end-noder først – de er de eneste noder, der er tilgængelige for eksterne forbindelser. Resten af ressourcerne er skjulte bag Virtual Networks. Front-end-noderne godkender anmodningen, håndterer den eller videresender den til de relevante ressourcer (f. eks. back-end-noder).

Back-end-noder indeholder de fleste af de Power BI Premium funktioner og funktioner.

### <a name="power-bi-mobile"></a>Power BI Mobile

Power BI-Mobil er en samling af apps, der er udviklet til de tre primære mobil platforme: Android, iOS og Windows (UWP). Overvejelser i forbindelse med sikkerhed i forbindelse med Power BI-Mobil apps, der er placeret i to kategorier:
* Enhedskommunikation
* Appen og dataene på enheden

I forbindelse med enheds kommunikation kommunikerer alle Power BI-Mobil programmer med Power BI-tjeneste og bruger den samme forbindelses-og godkendelses sekvens, der bruges af browsere, som er beskrevet detaljeret tidligere i dette whitepaper. Power BI Mobile Applications til iOS og Android viser en browsersession i selve programmet, mens Windows-mobilappen viser en mægler for at oprette kommunikations kanalen med Power BI (til logonprocessen).

I følgende tabel vises understøttelse af certifikatbaseret godkendelse (CBA) for Power BI-Mobil, baseret på platform til mobilenheder:


|CBA-support  |iOS  |Android  |Windows  |
|---------|---------|---------|---------|
|Power BI (log på tjenesten)    |Understøttet         |Understøttet         |Ikke understøttet         |
|SSRS ADFS on-Prem (Opret forbindelse til SSRS-server)     |Ikke understøttet         |Understøttet         |Ikke understøttet         |
|SSRS-app-proxy     |Understøttet         |Understøttet         |Ikke understøttet         |

Apps til Power BI – Mobil kommunikerer aktivt med Power BI-tjenesten. Telemetri bruges til at indsamle statistik om brug af mobilapps og lignende data, som sendes til tjenester, der bruges til at overvåge brug og aktivitet. der sendes ikke kundedata med telemetri.

Power BI-programmet gemmer data på enheden, der gør det nemmere at bruge appen:
* Tokens i Azure AD og refresh lagres i en sikker mekanisme på enheden ved hjælp af sikkerhedsforanstaltninger, der er standard i branchen.
* Data og indstillinger (nøgleværdipar til Brugerkonfiguration) cachelagres i lager på enheden og kan krypteres af operativsystemet. I iOS udføres dette automatisk, når brugeren angiver en adgangskode. I Android kan dette konfigureres i indstillingerne. I Windows udføres den ved hjælp af BitLocker.
* I forbindelse med Android-og iOS-apps cachelagres data og indstillinger (nøgleværdipar til Brugerkonfiguration) på lager på enheden i en sandkasse og et internt lager, der kun er tilgængeligt for appen. For Windows-appen kan du kun få adgang til dataene fra brugeren (og systemadministrator).
* Geoplacering er aktiveret eller deaktiveret eksplicit af brugeren. Hvis indstillingen er aktiveret, gemmes geografiske data ikke på enheden, og de deles ikke med Microsoft.
* Meddelelser aktiveres eller deaktiveres eksplicit af brugeren. Hvis den er aktiveret, understøtter Android og iOS ikke geografiske dataopbevaring krav til meddelelser.

Data kryptering kan forbedres ved at anvende kryptering på filniveau via Microsoft Intune, som er en softwaretjeneste, der giver mulighed for administration af mobilenheder og-programmer. Alle tre platforme, hvor Power BI-Mobil er tilgængelig, understøtter Intune. Når Intune er aktiveret og konfigureret, krypteres data på mobilenheden, og selve Power BI-programmet kan ikke installeres på et SD-kort. [Få mere at vide om Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

Windows-appen understøtter også [windows information Protection (via)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).

Hvis du vil implementere SSO, er nogle af de sikre lagerværdier, der er relateret til den token baserede godkendelse, tilgængelige for andre Microsoft-apps fra den ADAL (f. eks. Microsoft Authenticator) og administreres af-SDK (Azure Active Directory Authentication Library).  

Power BI-Mobil cachelagrede data slettes, når appen fjernes, når brugeren logger af Power BI-Mobil, eller når brugeren ikke logger på (f. eks. efter en udløbs hændelse for token eller ændring af adgangskode). Datacachen omfatter dashboards og rapporter, der tidligere blev tilgået fra appen Power BI – Mobil.

Power BI-Mobil har ikke adgang til andre programmapper eller filer på enheden.

Power BI-apps til iOS og Android giver dig mulighed for at beskytte dine data ved at konfigurere yderligere identifikation, f. eks. levering af ansigts-ID, touch ID eller en adgangskode til iOS og biometriske data (fingeraftryks-ID) til Android. [Få mere at vide om yderligere identifikation](../consumer/mobile/mobile-native-secure-access.md).

## <a name="authentication-to-the-power-bi-service"></a>Godkendelse til Power BI-tjeneste

Godkendelse af brugeren til Power BI-tjenesten består af en række anmodninger, svar og omdirigeringer mellem brugerens browser og Power BI-tjenesten eller de Azure-tjenester, som bruges af Power BI. Denne sekvens beskriver processen til brugergodkendelse i Power BI, som følger [Azure Active Directory Rens flow for godkendelse af godkendelseskode](/azure/active-directory/develop/v2-oauth2-auth-code-flow). Du kan finde flere oplysninger om mulighederne for en organisations bruger godkendelses modeller (Sign-in-modeller) under [valg af logon model til Microsoft 365](https://www.microsoft.com/en-us/microsoft-365/blog/2014/05/13/choosing-a-sign-in-model-for-office-365/).

### <a name="authentication-sequence"></a>Godkendelsessekvens

Bruger godkendelses sekvensen for Power BI-tjeneste indtræffer som beskrevet i følgende trin, som illustreres i det billede, der følger efter.

1. En bruger starter en forbindelse til Power BI-tjeneste fra en browser, enten ved at skrive Power BI adressen på adresselinjen eller ved at vælge *Log på* fra landingssiden Power bi ( https://powerbi.microsoft.com) . Forbindelsen oprettes ved hjælp af TLS 1.2 og HTTPS, og HTTPS bruges til al efterfølgende kommunikation mellem browseren og Power BI-tjenesten.

1. Azure Traffic Manager kontrollerer brugerens DNS-post for at se det mest relevante (normalt nærmeste) datacenter, hvor Power BI er installeret, og svarer på DNS med IP-adressen på den WFE-klynge, som brugeren skal sendes til.

1. WFE omdirigerer derefter brugeren til logonsiden for Microsoft Online Services.

1. Når brugeren er blevet godkendt, omdirigerer logonsiden til brugeren til den tidligere belagte nærmeste Power BI-tjeneste WFE-klynge med en godkendelseskode.

1. WFE-klyngen kontrollerer Azure AD-tjenesten for at få et Azure AD-sikkerheds-token ved hjælp af godkendelseskoden. Når Azure AD returnerer en vellykket godkendelse af brugeren og returnerer et Azure AD-sikkerhedstoken, hører WFE-klyngen Power BI globale tjeneste, der vedligeholder en liste over lejere og deres Power BI back-end-klynge placeringer og bestemmer, hvilken Power BI back-end-tjeneste klynge der indeholder brugerens lejer. WFE-klyngen returnerer derefter en programside til brugerens browser med de Sessions-, adgangs-og routingoplysninger, der kræves for at udføre handlingen.

1. Når klientens browser f. eks. kræver kundedata, sendes der nu anmodninger til back-end-klynge adressen med Azure AD-adgangs tokenet i Authorization-headeren. Den Power BI back-end-klynge læser Azure AD-adgangs tokenet og validerer signaturen for at sikre, at identiteten af anmodningen er gyldig. Det pågældende [Azure ad-adgangstoken har en standardlevetid på 1 time](/azure/active-directory/develop/active-directory-configurable-token-lifetimes#configurable-token-lifetime-properties-after-the-retirement)og for at bevare den aktuelle session, hvor brugerens browser vil foretage regelmæssige anmodninger om at forny adgangs tokenet, før det udløber.

![Godkendelsessekvens](media/whitepaper-powerbi-security/powerbi-security-whitepaper_08.png)

## <a name="data-residency"></a>Data opbevaring

Medmindre andet er angivet i dokumentation, gemmer Power BI kundedata i et Azure-geografisk område, der tildeles, når en [Azure ad-lejer](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings) tilmelder sig Power bi Services for første gang. En Azure AD-lejer er omfattet af bruger-og program identiteter, grupper og andre relevante oplysninger, der vedrører en organisation og dens sikkerhed. 

Tildelingen af en Azure-geografi til lejer datalagring sker ved at tilknytte det land eller område, der er valgt som en del af Azure AD-lejer konfigurationen, til den mest relevante Azure-geografi, hvor der findes en Power BI-installation. Når dette er sket, gemmes alle Power BI kundedata i dette valgte Azure-geografiske område (også kaldet det *private geografiske* område), bortset fra de tilfælde, hvor organisationer anvender fler geografiske installationer.

### <a name="multiple-geographies-multi-geo"></a>Flere geografiske områder (flere områder)

Nogle organisationer har en global tilstedeværelse og kan kræve Power BI tjenester i flere Azure-geografiske områder. En virksomhed kan f. eks. have sit hoved i USA men kan også gøre forretninger i andre geografiske områder, f. eks. Australien. I sådanne tilfælde kan virksomheden kræve, at visse Power BI data forbliver lagret i Fjern området for at overholde lokale regler. Denne funktion i Power BI-tjeneste kaldes *flere geografiske* områder.

Det forespørgsels udførelses lag, de forespørgsels cacher og De artefakt data, der er tildelt et arbejdsområde med flere områder, er hostet og forbliver i Azure-geografi med Fjern kapacitet. Nogle artefakt metadata, f. eks. rapport struktur, kan dog forblive lagret i lejerens geografiske område. Derudover kan nogle data transit og behandling stadig ske i lejerens geografiske geografiske område, selv for arbejdsområder, der er hostet i en Premium-kapacitet med flere områder.

Du kan finde flere oplysninger om, hvordan du opretter og administrerer Power BI udrulninger, der spænder over flere Azure-geografiske områder, under [Konfigurer understøttelse af flere områder til Power bi Premium](../admin/service-admin-premium-multi-geo.md) .

### <a name="regions-and-datacenters"></a>Områder og datacentre

Power BI-tjenester er tilgængelige i bestemte Azure-geografiske områder som beskrevet i [Microsoft Center for sikkerhed](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)og rettigheder. Du kan finde flere oplysninger om, hvor dine data er gemt, og hvordan de bruges, i [Microsofts center for sikkerhed](https://www.microsoft.com/TrustCenter/Transparency/default.aspx#_You_know_where)og rettigheder. Forpligtelser vedrørende placeringen af kundedata i rest er angivet i vilkårene for behandling af [Microsoft Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31).

Microsoft leverer også datacentre til suveræne enheder. Du kan finde flere oplysninger om tilgængeligheden af Power BI-tjenesten i nationale cloudmiljøer i [Power BI i nationale cloudmiljøer](https://powerbi.microsoft.com/clouds/). 

## <a name="data-handling"></a>Data håndtering

I dette afsnit beskrives Power BI praksis for datahåndtering, når det drejer sig om lagring, behandling og overførsel af kundedata.

### <a name="data-at-rest"></a>Inaktive data

Power BI bruger to primære datalager ressourcetyper:
* Azure Storage
* Azure SQL Databases

I de fleste scenarier bruges Azure Storage til at bevare dataene for Power BI artefakter, mens Azure SQL databases bruges til at bevare artefaktens metadata. 

Alle data, der bevares af Power BI, krypteres som standard ved hjælp af Microsoft-administrerede nøgler. Kundedata, der er gemt i Azure SQL-databaser, er fuldt krypteret med [Azure sqls TDE-teknologi (transparent Data Encryption)](/azure/sql-database/transparent-data-encryption-azure-sql) . Kundedata, der er gemt i Azure blob Storage, er krypteret ved hjælp af [Azure Storage kryptering](/azure/storage/common/storage-service-encryption).

Det kan også være, at organisationer bruger Power BI Premium til at bruge deres egne nøgler til at kryptere data, der importeres til et datasæt. Denne fremgangsmåde beskrives ofte som BYOK (Bring Your Own Key – medbring din egen nøgle). Brug af BYOK hjælper med at sikre, at der ikke er adgang til kundedata, selvom der er fejl i tilfælde af en service operatør, at der ikke kan opnås adgang til dem ved hjælp af transparent kryptering på tjenestesiden. Se Brug [dine egne krypteringsnøgler til Power bi](../admin/service-encryption-byok.md) for at få flere oplysninger.

Power BI datasæt giver mulighed for en række forbindelses tilstande for datakilder, der bestemmer, om datakilde dataene er permanent i tjenesten eller ej.

|DataSet-tilstand (type)   |Data bevares i Power BI |
|----------------------|---------------------------|
|Importér                |Yes |
|Direct Query          |No |
|Live Connect          |No |
|Sammensat             |Hvis indeholder en Importér datakilde |
|Streaming             |Hvis det er konfigureret til at blive vedvarende |

Uanset hvilken datatype der anvendes, kan Power BI midlertidigt cachelagre data, der er hentet, for at optimere forespørgsler og rapportere belastnings ydeevne.

### <a name="data-in-processing"></a>Data til behandling

Dataene behandles, når de bruges af en eller flere brugere som en del af et interaktivt scenarie, eller når en baggrundsproces, som f. eks. opdatering, berører disse data. Power BI indlæser aktivt behandlede data i hukommelsen i en eller flere tjeneste arbejdsprocesser. For at lette den funktionalitet, der kræves af arbejdsbelastningen, er de behandlede data i hukommelsen ikke krypteret.

### <a name="data-in-transit"></a>Data under overførsel
Power BI kræver, at al indgående HTTP-trafik krypteres ved hjælp af TLS 1,2 eller nyere. Anmodninger, der forsøger at bruge tjenesten med TLS 1,1 eller lavere, afvises.

## <a name="authentication-to-data-sources"></a>Godkendelse til datakilder

Når en bruger opretter forbindelse til en datakilde, kan den vælge at importere en kopi af dataene til Power BI eller til at oprette forbindelse direkte til datakilden. 

I tilfælde af import opretter en bruger en forbindelse, der er baseret på brugerens logon, og der opnås adgang til dataene med legitimationsoplysningerne. Når datasættet er publiceret i Power BI-tjeneste, bruger Power BI altid denne brugers legitimationsoplysninger til at importere data. Når dataene er importeret, kan du ikke få adgang til den underliggende datakilde, når du får vist dataene i rapporter og dashboards. Power BI understøtter godkendelse med enkeltlogon for udvalgte datakilder. Hvis forbindelsen er konfigureret til at bruge Single Sign-on, bruges legitimationsoplysningerne for datasættet til at oprette forbindelse til datakilden.

Hvis en datakilde er forbundet direkte ved hjælp af forudkonfigurerede legitimationsoplysninger, bruges forudkonfigurerede legitimationsoplysninger til at oprette forbindelse til datakilden, når en bruger får vist dataene. Hvis en datakilde er forbundet direkte ved hjælp af enkeltlogon, bruges den aktuelle brugers legitimationsoplysninger til at oprette forbindelse til datakilden, når en bruger får vist dataene. Når det bruges med enkeltlogon, kan sikkerhed på rækkeniveau (RLS) implementeres på datakilden. Dette gør det muligt for brugere kun at få vist data, de har adgang til. Når forbindelsen er til datakilder i clouden, bruges Azure AD-godkendelse til enkeltlogon. i forbindelse med datakilder i Prem understøttes Kerberos, SAML Markup Language (Security Assertion Markup Language) og Azure AD.

Hvis datakilden er Azure Analysis Services eller i det lokale miljø Analysis Services og RLS er konfigureret, vil Power BI-tjeneste anvende sikkerhed på rækkeniveau, og brugere, der ikke har tilstrækkelige legitimationsoplysninger til at få adgang til de underliggende data (som kan være en forespørgsel, der bruges i et dashboard, en rapport eller en anden data artefakt), kan ikke se de data, de ikke har tilstrækkelige rettigheder til.

## <a name="premium-features"></a>Premium-funktioner

### <a name="dataflows-architecture"></a>Dataflows-arkitektur

Dataflows gør det muligt for brugerne at konfigurere back-end-databehandlings handlinger, der udtrækker data fra polyformede datakilder, udfører Transformations logik i forhold til dataene og derefter uddeler dem i en destinationsmodel, så de kan bruges på tværs af forskellige rapporterings præsentations teknologier. Alle brugere, der har rollen som medlem, bidragyder eller administrator i et arbejdsområde, kan oprette en data flow. Brugere i Viewer-rollen kan få vist data, der behandles af data flow, men som ikke foretager ændringer af dens komposition. Når en data flow er blevet oprettet, kan alle medlemmer, bidragydere eller administratorer af arbejdsområdet planlægge opdateringer, og du kan også få vist og redigere data flow ved at overtage ejerskabet af det.

Hver af de konfigurerede datakilder er bundet til en klient teknologi for at få adgang til den pågældende datakilde. Strukturen af de legitimationsoplysninger, der kræves for at få adgang til dem, er udformet, så de stemmer overens med de krævede Implementeringsoplysninger Transformerings logikken anvendes af Power-forespørgsel tjenester, mens dataene er i Flight. Til Premium dataflows er Power-forespørgsel Services-udførelse i back-end-noder. Data kan trækkes direkte fra Cloud-kilderne eller via en gateway, der er installeret i det lokale miljø. Når den trækkes direkte fra en skybaseret kilde til tjenesten eller til gatewayen, anvender transporten den beskyttelsesmetode, der er specifik for klient teknologien, hvis det er relevant. Når data overføres fra gatewayen til Cloud service, krypteres den. Se afsnittet om [data i behandling](#data-in-processing) ovenfor.

Når kundens angivne datakilder kræver legitimationsoplysninger for at få adgang, vil ejeren/forfatteren af data flow give dem under oprettelse. De lagres i standard-lageret med legitimationsoplysninger i hele produktet. Se afsnittet [godkendelse til data kilder](#authentication-to-data-sources) ovenfor. Der er forskellige måder, som brugerne kan konfigurere til at optimere data fastholdelse og-adgang. Som standard placeres dataene i en Power BI ejet og beskyttet Lagerkonto. Lager kryptering er aktiveret på blob Storage-objektbeholdere for at beskytte dataene, mens de er i rest. Se afsnittet om [resterende data](#data-at-rest) nedenfor. Brugerne kan dog konfigurere deres egen Lagerkonto, der er knyttet til deres eget Azure-abonnement. Når du gør det, tildeles en Power BI-tjeneste Principal adgang til den pågældende Lagerkonto, så den kan skrive dataene der under opdateringen. I dette tilfælde er ejeren af lager ressourcen ansvarlig for at konfigurere kryptering på den konfigurerede ADLS Storage-konto. Data sendes altid til blob-lager ved hjælp af kryptering.

Da ydeevnen i forbindelse med adgang til lagerkonti muligvis er under optimale for nogle data, har brugerne også mulighed for at bruge en Power BI værtsmaskine til at øge ydeevnen. I dette tilfælde er data redundant lagret i en SQL-database, der er tilgængelig for DirectQuery via adgang fra back-end-Power BI systemet. Data er altid krypteret på filsystemet. Hvis brugeren angiver en nøgle til kryptering af de data, der er gemt i SQL-databasen, vil den nøgle blive brugt til at kryptere den.

Når der foretages en forespørgsel ved hjælp af DirectQuery, bruges den krypterede transportprotokol HTTPS til at få adgang til API'EN. Al sekundær eller indirekte brug af DirectQuery styres af de samme adgangskontrol elementer, der tidligere er beskrevet. Da dataflows altid er bundet til et arbejdsområde, er adgangen til dataene altid gated af brugerens rolle i det pågældende arbejdsområde. En bruger skal mindst have læseadgang for at kunne sende forespørgsler til dataene via en eller anden måde.

Når Power BI Desktop bruges til at få adgang til data i en data flow, skal den først godkende brugeren ved hjælp af Azure AD for at afgøre, om brugeren har tilstrækkelige rettigheder til at få vist dataene. Hvis det er tilfældet, hentes og bruges der en SaS-nøgle til at få direkte adgang til storage ved hjælp af den krypterede transportprotokol HTTPS.

Behandling af data i pipelinen udsender Office 365-overvågningshændelser. Nogle af disse hændelser registrerer handlinger, der er relateret til sikkerhed og beskyttelse af personlige oplysninger.

### <a name="paginated-reports"></a>Sideinddelte rapporter

Sideinddelte rapporter er designet til at skulle udskrives eller deles. De kaldes sideinddelte, fordi de er formateret til at passe godt på en side. De viser alle data i en tabel, selvom tabellen strækker sig over flere sider. De kaldes også perfekt pixel, fordi du kan styre layoutet af rapportsiderne helt præcist.

Sideinddelte rapporter understøtter omfattende og effektive udtryk, der er skrevet i Microsoft Visual Basic .NET. Udtryk bruges i stor udstrækning overalt i sideinddelte rapporter i Power BI Report Builder til at hente, beregne, vise, gruppere, sortere, filtrere, parameterisere og formatere data.

Udtryk oprettes af forfatteren af rapporten med adgang til den brede række funktioner i .NET Framework. Behandling og udførelse af sideinddelte rapporter udføres i en sandkasse.

Sideinddelte rapportdefinitioner (. rdl) lagres i Power BI og for at udgive og/eller gengive en sideinddelt rapport, som en bruger skal godkende og godkende på samme måde som beskrevet i [godkendelsen til den pågældende Power bi service](#authentication-to-the-power-bi-service) -sektion.

Det Azure AD-token, der er opnået under godkendelsen, bruges til at kommunikere direkte fra browseren til Power BI Premium-klyngen.

For Premium Gen1 findes der en enkelt sandkasse pr. hver af lejerens kapaciteter, og den deles af de arbejdsområder, der er knyttet til kapaciteten.

![Sideinddelte rapporter gen 1](media/whitepaper-powerbi-security/powerbi-security-whitepaper-paginated-reports-gen1.png)

I forbindelse med Premium Gen2 (i prøveversion) oprettes der en individuel og eksklusiv, kortvarig Sandbox for hver af de gengivne i en rapport, hvilket giver et højere isolationsniveau mellem brugerne.

![Sideinddelte rapporter gen 2](media/whitepaper-powerbi-security/powerbi-security-whitepaper-paginated-reports-gen2.png)

En sideinddelt rapport kan få adgang til en lang række datakilder som en del af rapportens gengivelse. Sandkassen kommunikerer ikke direkte med nogen af datakilderne, men i stedet for at kommunikere med den proces, der er tillid til, til at anmode om data, og den nøgle, der er tillid til, føjer de påkrævede legitimationsoplysninger til forbindelsen. På denne måde har sandkassen aldrig adgang til legitimationsoplysninger eller hemmelighed. 

For at kunne understøtte funktioner som Bing Maps eller kald til Azure Functions, har sandkassen adgang til internettet.

### <a name="power-bi-embedded-analytics"></a>Power BI integreret analyse

Uafhængige softwareleverandører og løsningsudbydere har to primære måder at integrere Power BI artefakter på i deres webprogrammer og-portaler: [Integrer til din organisation](../developer/embedded/embed-sample-for-your-organization.md) , og [Integrer til dine kunder](../developer/embedded/embed-sample-for-customers.md). Artefakten er integreret i en iframe i programmet eller på portalen. En iframe har ikke tilladelse til at læse eller skrive data fra det eksterne webprogram eller portalen, og kommunikationen med iframe udføres ved hjælp af Power BI klient-SDK, der bruger POST-meddelelser.

I en [integrering til dit organisations](../developer/embedded/embed-sample-for-your-organization.md) scenarie har Azure ad-brugere adgang til deres egne Power bi indhold via portaler, der er tilpasset af deres virksomheder og dets. Alle Power BI politikker og egenskaber, der er beskrevet i dette dokument, f. eks. sikkerhed på rækkeniveau (RLS), anvendes automatisk på alle brugere uafhængigt af, om de har adgang til Power BI via [Power bi-portalen](https://app.powerbi.com/) eller gennem tilpassede portaler.

I en [integrering til dit kunders](../developer/embedded/embed-sample-for-customers.md) scenarie ejer isv'er typisk Power bi lejere og Power bi artefakter (dashboards, rapporter, datasæt osv.). Det er ansvaret for en ISV-back-end-tjeneste til at godkende sine slutbrugere og afgøre, hvilke artefakter og hvilket adgangsniveau der passer til den pågældende slutbruger. ISV-politik beslutningerne er krypteret i et [indlejre token](/rest/api/power-bi/embedtoken) , der er genereret af Power bi og videresendes til ISV-back-end til videredistribution til slutbrugerne i henhold til softwarens forretningslogik. Slutbrugere, der bruger en browser eller andre klientprogrammer, kan ikke dekryptere eller redigere integrerede tokens. SDK'er på klientsiden, f. eks. [Power bi Client API'er](/javascript/api/overview/powerbi/) , tilføjer automatisk det krypterede embeds token for at Power bi anmodninger som en *autorisation: EmbedToken* -header. På baggrund af denne header vil Power BI gennemtvinge alle politikker (f. eks. adgang eller RLS) nøjagtigt, som det blev angivet af ISV under oprettelsen.

Hvis du vil aktivere integration og automatisering og oprette de integrerede tokens, der er beskrevet ovenfor, så Power BI udviser en lang række [rest API'er](/rest/api/power-bi/embedtoken). Disse Power BI REST-API'er understøtter både bruger [uddelegerede](/azure/active-directory/develop/v2-permissions-and-consent) og [tjeneste principale](../admin/service-premium-service-principal.md) Azure ad-metoder til godkendelse og autorisation.

Power BI integrerede analyser og REST-API'er understøtter alle Power BI netværks isolations funktioner, der er beskrevet i denne artikel: f. eks. [service koder](#service-tags) og [private links](#private-link-integration).

### <a name="ai-features"></a>AI-funktioner

Power BI understøtter i øjeblikket to brede kategorier af AI-funktioner i produktet i dag: AI-visualiseringer og AI-forbedringer. AI-funktionerne på det visuelle niveau omfatter funktioner som f. eks. nøgle indflydelse, opdelingstræ, smart-fortælling, uregelmæssig registrering, R-visualisering, Python – visualisering, klynger, udarbejdelse af prognoser, spørgsmål&A, Quick-Insights osv. AI-forbedrings mulighederne omfatter funktioner som AutoML, AzureML, CognitiveServices, R/Python transformeringer osv. 

De fleste af ovennævnte funktioner understøttes i både delte og Premium-arbejdsområder i dag. Men AutoML og CognitiveServices understøttes kun i Premium-arbejdsområder på grund af IP-begrænsninger. I dag med AutoML-integrationen i Power BI kan en bruger bygge og træne en brugerdefineret ML-model (f. eks. forudsigelse, klassificering, regression osv.) og anvende den til at få forudsigelser, mens du indlæser data i en data flow, der er defineret i et Premium-arbejdsområde. Derudover kan Power BI brugere anvende flere CognitiveServices-API'er, f. eks. TextAnalytics og ImageTagging, til at transformere data, før de indlæser dem i et data flow/datasæt, der er defineret i et Premium-arbejdsområde. 

Premium-forbedrings funktionerne i Premium kan ses bedst som en samling af ikke-Trans formeres stabile AI-funktioner, der kan bruges af Power BI brugere i deres data integrations pipelines, der bruges af et Power BI datasæt eller data flow. Bemærk, at disse funktioner også kan åbnes fra det aktuelle data flow/DataSets oprettelses miljøer i Power BI tjeneste og Power BI Desktop. Disse AI-funktioner/transformeringer kører altid i et Premium-arbejdsområde/-kapacitet. Disse funktioner er over fladt i Power BI som en datakilde, der kræver et Azure AD-token for den Power BI bruger, der bruger AI-funktionen. Disse AI-datakilder er specielle, fordi de ikke overholder nogen af deres egne data, og de kun leverer disse funktioner/transformationer. Under udførelsen foretager disse funktioner ikke udgående opkald til andre tjenester for at sende kundens data. Lad os se på de førsteklasses scenarier for at forstå kommunikations mønstrene og relevante sikkerhedsrelaterede oplysninger om dem. 

For at under oplære og anvende en AutoML-model bruger Power BI Azure AutoML SDK og kører al træning i kundens Power BI kapacitet. Under oplærings gentagelser kalder Power BI en AzureML-tjeneste for at vælge en passende model og flere parametre for den aktuelle gentagelse. I dette udgående kald er det kun relevante eksperimentelle metadata (f. eks. nøjagtighed, ml algoritme, algoritmeparametre osv.), der sendes fra den forrige gentagelse. AutoML-oplæringen producerer en ONNX model og undervisnings rapportdata, som derefter gemmes i data flow. På et senere tidspunkt kan Power BI brugere derefter anvende den oplærte ML-model som transformation for at Operational Isere ML-modellen på et tidspunkt. For TextAnalytics-og ImageTagging-API'er kalder Power BI ikke direkte tjeneste-API'erne, men i stedet bruger en intern SDK til at køre API'erne i Power BI Premium kapacitet. I dag understøttes disse API'er både i Power BI dataflows og datasæt. Når du opretter et datasæt i Power BI Desktop, kan brugerne kun få adgang til denne funktionalitet, hvis de har adgang til et Premium Power BI-arbejdsområde. Kunder bliver derfor bedt om at angive deres Azure AD-legitimationsoplysninger. 

## <a name="network-isolation"></a>Netværks isolation

I dette afsnit beskrives avancerede sikkerhedsfunktioner i Power BI. Nogle af funktionerne har specifikke licenskrav. Du kan finde flere oplysninger i afsnittene nedenfor.

### <a name="service-tags"></a>Service Tags

En servicekode repræsenterer en gruppe IP-adressepræfikser fra en given Azure-tjeneste. Det er med til at minimere kompleksiteten ved hyppige opdateringer til netværks sikkerhedsregler. Kunder kan bruge service Tags til at definere kontrolelementer til netværksadgang på [netværks sikkerhedsgrupper](/azure/virtual-network/security-overview#security-rules) eller [Azure firewall](/azure/firewall/service-tags). Kunder kan bruge service Tags i stedet for bestemte IP-adresser, når de opretter sikkerhedsregler. Når du angiver service tag Name (f. eks. PowerBI) i det relevante kilde-eller destinationsfelt (for API'er) i en regel, kan kunderne tillade eller afvise trafikken for den tilsvarende tjeneste. Microsoft administrerer de adressepræfikser, der er omfattet af servicekoden, og opdaterer automatisk servicekoden som adresse ændringer.

### <a name="private-link-integration"></a>Integration af privat link

Azure networking indeholder den Azure private link-funktion, der gør det muligt for Power BI at give sikker adgang via private slutpunkter i Azure networking. Med Azure private link og private slutpunkter sendes datatrafik privat ved hjælp af Microsofts basis netværksinfrastruktur, og derfor gennemløber dataene ikke for internettet.

Privat link sikrer, at Power BI brugere bruger det private backbone Microsoft private netværk, når de går til ressourcer i Power BI-tjeneste.

Brug af privat link med Power BI giver følgende fordele:
* Privat link sikrer, at trafikken overfører Azure-basis til et privat slutpunkt for Azure cloud-baserede ressourcer.
* Isolering af netværkstrafik fra ikke-Azure-baseret infrastruktur, f. eks. adgang i det lokale miljø, kræver, at kunderne har Express Route eller et VPN-konfigureret (virtuelt privat netværk).

Se [private links for at få adgang til Power bi for at få](../admin/service-security-private-links.md) flere oplysninger.

### <a name="vnet-connectivity-preview---coming-soon"></a>VNet-forbindelse (eksempel komme snart)

Selvom funktionen til integration af personlige links giver sikre indgående forbindelser til Power BI, muliggør VNet-forbindelses funktionen en sikker udgående forbindelse fra Power BI til datakilder i en VNet. 

VNet gateways (Microsoft-Managed) eliminerer den belastning, der er forbundet med at installere og overvåge data gateways i det lokale miljø, for at oprette forbindelse til datakilder, der er knyttet til en VNet. De vil dog stadig følge den velkendte proces til administration af sikkerheds-og datakilder som med en data gateway i det lokale miljø.

Følgende er en oversigt over, hvad der sker, når du interagerer med en Power BI rapport, der er forbundet til en datakilde i en VNet ved hjælp af VNet gateways:

1. Den Power BI Cloud service (eller en af de andre understøttede Cloud Services) udsætter en forespørgsel og sender forespørgslen, oplysninger om datakilder og legitimationsoplysninger til VNet-tjenesten Power platform (PP VNet).

1. PP VNet-tjenesten indsætter derefter en objektbeholder, der kører en VNet gateway, i undernettet på sikker vis. Denne beholder kan nu oprette forbindelse til datatjenester, der er tilgængelige i dette undernet.

1. The PP VNet-tjenesten sender derefter forespørgslen, oplysninger om datakilder og legitimationsoplysninger til VNet gateway. 

1. VNet gateway henter forespørgslen og opretter forbindelse til datakilderne med disse legitimationsoplysninger.

1. Forespørgslen sendes derefter til datakilden til udførelse.

1. Efter udførelsen sendes resultaterne til VNet gateway, og PP VNet-tjenesten sender sikkert dataene fra objektbeholderen til Power BI Cloud service.

Denne funktion er snart tilgængelig som offentlig prøveversion.

### <a name="service-principals"></a>Tjenesteprincipaler

Power BI understøtter brugen af tjeneste principaler. Gem alle de legitimationsoplysninger, der bruges til at kryptere eller få adgang til Power BI i en Key Vault, Tildel de rette adgangs politikker til samlingen, og kontrollér adgangstilladelser regelmæssigt.

Se [Automatiser Premium-arbejdsområde og DataSet-opgaver med tjeneste principaler](../admin/service-premium-service-principal.md) for at få flere oplysninger.

## <a name="data-loss-prevention-dlp"></a>Forebyggelse af datatab (DLP)

### <a name="microsoft-365-sensitivity-labels"></a>Navne på Microsoft 365 følsomhed

Power BI har en detaljeret integration med Microsoft-Information Protection (MIP) følsomheds etiketter, der gør det muligt for organisationer at have en enkelt integreret løsning til administration af DLP-politikker, overvågning og overholdelse af angivne standarder på tværs af Office-pakken.

Når følsomheds etiketter er aktiveret i Power BI:
* Følsomme data, både i Power BI-tjeneste (GA) og i Power BI Desktop (prøveversion), kan klassificeres og mærkes ved hjælp af de samme velkendte Microsoft Information Protection følsomheds etiketter, der bruges i Office og i Azure Purview. 
* Politikker for styring kan gennemtvinges, selv når Power BI indhold eksporteres til Excel-, PowerPoint-, PDF-eller *. pbix* -filer for at sikre, at data er beskyttet, selvom de forlader Power bi.
* *. pbix* -filer kan krypteres i henhold til MIP-navne politikker, når der anvendes en MIP-etiket i *. pbix* -filen i desktop, hvilket sikrer, at det kun er godkendte brugere, der kan redigere denne fil.
* Det er nemt at klassificere og beskytte *. pbix* -filer, ligesom de er færdige med Excel-, Word-og PowerPoint-filer. Med blot to klik kan en fil mærkes i henhold til dens følsomhed, og den skal også være krypteret, hvis den indeholder forretnings fortrolige data.
* Excel-projektmapper arver automatisk følsomheds etiketter, når de opretter forbindelse til Power BI (prøveversion), hvilket gør det muligt at vedligeholde end-to-end-klassificering og anvende beskyttelse, når det Power BI DataSet analyseres i Excel.
* Følsomheds etiketter, der er anvendt på Power BI-rapporter og-dashboards, er synlige i Power BI iOS-og Android-mobilapps.
* Følsomheds etiketter bevares, når en Power BI rapport er integreret i teams, SharePoint eller et sikkert websted (prøveversion). Det hjælper organisationer med at vedligeholde klassificering og beskyttelse efter eksport, når de integrerer Power BI indhold.
* Nedarvning af etiketter ved oprettelse af nyt indhold i Power BI-tjeneste sikres det, at den etiket, der anvendes på et datasæt i Power BI-tjeneste, vil blive anvendt på nyt indhold, der oprettes oven på datasættet. 
* [Power bi admin-scannings-API'er](/rest/api/power-bi/admin/workspaceinfo_getscanresult) kan udtrække en Power bi artefakts følsomheds etiket, aktivere Power bi og INFOSEC-administratorer til at overvåge etiketter i Power bi-tjeneste og oprette overordnede rapporter. 
* Power BI sikrer, at det kun er godkendte brugere, der kan ændre eller fjerne etiketter med beskyttelsesindstillinger i Power BI-tjeneste. 
* Kommer snart
    * Power BI administrator-API'er til anvendelse af MIP-etiketter for at gøre det muligt for centrale Team at mærke indholdet i Power BI-tjeneste.  
    * Administratorer kan gennemtvinge anvendelse af etiketter på nyt eller redigeret indhold med en obligatorisk etiket politik i Power BI-tjeneste (prøveversion).
    * Automatisk artefakt-artefakt etikettering i Power BI-tjeneste. Når en etiket på et datasæt anvendes eller ændres, anvendes etiketten automatisk på alt downstream-indhold, der er knyttet til dette artefakt.

Du kan finde flere oplysninger [i dokumentationen til Microsoft information Protection følsomheds etiketten i Power bi](../admin/service-security-sensitivity-label-overview.md) .

### <a name="microsoft-cloud-app-security-mcas-for-power-bi"></a>Microsoft Cloud App Security (MCAS) til Power BI

Microsoft Cloud App Security er en af verdens førende sikkerheds mæglere for clouden, der er navngivet som førende i Gartners Magic kvadrant til CASB-markedet (Cloud Access Security Broker). Cloud app Security bruges til at sikre brugen af Cloud apps. Det giver organisationer mulighed for at overvåge og styre i realtid, risiko Power BI sessioner, f. eks. bruger adgang fra ikke-administrerede enheder. Sikkerhedsadministratorer kan definere politikker til at styre brugerhandlinger, f. eks. at hente rapporter med følsomme oplysninger.

Med Cloud App Security kan organisationer få følgende DLP-egenskaber: 
* Angiv kontrolelementer i realtid for at gennemtvinge risikable brugersessioner i Power BI. Hvis en bruger f. eks. opretter forbindelse til Power BI uden for deres land, kan sessionen overvåges ved hjælp af Cloud App Securitys kontrolelementer i realtid, f. eks. at hente data, der er mærket med et "stærkt fortroligt" følsomheds navn, kan blokeres med det samme.
* Undersøg Power BI brugeraktivitet med Cloud App Security aktivitets logfil. Cloud App Security aktivitets loggen indeholder Power BI aktivitet, der er registreret i Office 365-overvågningslogfilen, som indeholder oplysninger om alle bruger-og administrator aktiviteter samt oplysninger om følsomheds oplysninger for relevante aktiviteter, som f. eks. Anvend, Rediger og Fjern etiket. Administratorer kan udnytte Cloud App Security Rens avancerede filtre og hurtige handlinger for at få en effektiv problem undersøgelse. 
* Opret brugerdefinerede politikker for at advare om mistænkelig brugeraktivitet i Power BI. Cloud App Security Rens aktivitets politikfunktion kan bruges til at definere dine egne brugerdefinerede regler for at hjælpe dig med at registrere brugeradfærd, der afviger fra normen, og endda muligvis reagere på den automatisk, hvis den tilsyneladende er for risikabel.
* Arbejd med Cloud App Security indbyggede registrering af uregelmæssigheder. Cloud App Securitys politikker for registrering af uregelmæssigheder leverer bruger adfærds analyse og maskinel indlæring, der er klar til brug, så du er klar til at køre avanceret trussels registrering på tværs af dit skybaserede miljø. Når en politik for registrering af uregelmæssigheder identificerer en mistænkelig funktionsmåde, udløser den en sikkerhedsadvarsel. 
* Rollen Power BI administrator i Cloud App Security-portalen. Cloud App Security indeholder en app-specifik administratorrolle, der kan bruges til at give Power BI administratorer kun de tilladelser, de har brug for til at få adgang til Power BI relevante data på portalen, f. eks. beskeder, brugere i risiko, aktivitets logge og andre Power BI relaterede oplysninger.

Du kan finde flere oplysninger under [brug af Microsoft Cloud app Securitys kontrolelementer i Power bi](../admin/service-security-using-microsoft-cloud-app-security-controls.md) .

## <a name="preview-security-features"></a>Funktioner til eksempelvisning af sikkerhed

Dette emne indeholder en liste over de funktioner, der er planlagt til udgivelse frem til og med marts 2021. Da dette emne indeholder en liste over funktioner, der muligvis ikke er frigivet endnu, **kan leverings tidslinjerne blive ændret, og den projekterede funktionalitet kan blive frigivet senere end 2021, eller de frigives måske ikke**. Hvis du vil have flere oplysninger om prøveversioner, skal du gennemse [vilkårene for Online Services](https://www.microsoft.com/licensing/product-licensing/products).

### <a name="bring-your-own-log-analytics-byola"></a>Hent dine egne Log Analytics (BYOLA)

Få dine egne Log Analytics muliggør integration mellem Power BI og Azure-Log Analytics. Denne integration omfatter Azure Log Analytics Advanced Analytics Engine, Interactive Query Language og indbyggede Machine Learning-strukturer.

## <a name="power-bi-security-questions-and-answers"></a>Power BI sikkerhedsspørgsmål og-svar

Følgende spørgsmål er almindelige spørgsmål og svar om sikkerhed i Power BI. Disse er organiseret, afhængigt af hvornår de blev føjet til dette whitepaper, for at gøre det nemmere for dig hurtigt at finde nye spørgsmål og svar, når dette dokument opdateres. De nyeste spørgsmål føjes til slutningen af denne liste.

**Hvordan opretter brugere forbindelse og får adgang til datakilder under brug af Power BI?**

* Power BI administrerer legitimationsoplysninger til datakilder for hver bruger i forbindelse med legitimationsoplysninger til skyen eller til forbindelser via en personlig gateway. Datakilder, der administreres af en data gateway i det lokale miljø, kan deles på tværs af virksomheden, og tilladelserne til disse datakilder kan administreres af Gatewayadministratoren. Når du konfigurerer et datasæt, kan brugeren vælge et sæt legitimationsoplysninger fra deres personlige lager eller bruge en data gateway i det lokale miljø til at bruge et delt sæt legitimationsoplysninger.

    I import tilfælde opretter en bruger en forbindelse på baggrund af brugerens logon og får adgang til dataene med legitimationsoplysningerne. Når datasættet er publiceret til Power BI-tjeneste, bruger Power BI altid denne brugers legitimationsoplysninger til at importere data. Når dataene er importeret, kan du ikke få adgang til den underliggende datakilde, når dataene vises i rapporter og Dashboard. Power BI understøtter godkendelse med enkeltlogon for udvalgte datakilder. Hvis forbindelsen er konfigureret til at bruge Single Sign-on, bruges legitimationsoplysningerne for datasættet til at oprette forbindelse til datakilden.

    For rapporter, der er forbundet med DirectQuery, er datakilden forbundet direkte ved hjælp af forudkonfigurerede legitimationsoplysninger, og de forudkonfigurerede legitimationsoplysninger bruges til at oprette forbindelse til datakilden, når en bruger får vist dataene. Hvis en datakilde er forbundet direkte ved hjælp af enkeltlogon, bruges legitimationsoplysningerne for den aktuelle bruger til at oprette forbindelse til datakilden, når brugeren får vist dataene. Når du bruger med enkeltlogon, kan sikkerhed på rækkeniveau (RLS) implementeres i datakilden, og det gør det muligt for brugere at se de data, de har tilladelse til at få adgang til. Når forbindelsen er til datakilder i clouden, bruges Azure AD-godkendelse til enkeltlogon. for datakilder i Prem understøttes Kerberos, SAML og Azure AD.  

    Når der oprettes forbindelse til Kerberos, sendes brugerens UPN til gatewayen, og hvis du bruger Kerberos-begrænset delegering, repræsenteres brugeren, og der oprettes forbindelse til de respektive datakilder. SAML understøttes også på gatewayen for SAP HANA data source. Du kan finde flere oplysninger i [oversigten over enkeltlogon for gateways](../connect-data/service-gateway-sso-overview.md).

    Hvis datakilden er Azure Analysis Services eller i det lokale miljø Analysis Services og sikkerhed på rækkeniveau (RLS) er konfigureret, vil Power BI-tjeneste anvende sikkerhed på rækkeniveau, og brugere, der ikke har tilstrækkelige legitimationsoplysninger til at få adgang til de underliggende data (som kan være en forespørgsel, der bruges i et dashboard, en rapport eller en anden data artefakt), kan ikke se de data, som brugeren ikke

    [Sikkerhed på rækkeniveau med Power bi](../admin/service-admin-rls.md) kan bruges til at begrænse adgang til data for bestemte brugere. Filtre begrænser adgangen til data på rækkeniveau, og du kan definere filtre i rollen.  

**Hvordan overføres data til Power BI?**

* Alle data, der anmodes om og sendes af Power BI, krypteres i transit ved hjælp af HTTPS (undtagen når den datakilde, der er valgt af kunden, ikke understøtter HTTPS), så der kan oprettes forbindelse fra datakilden til Power BI-tjeneste. Der etableres en sikker forbindelse med dataprovideren, og det er først, når der er etableret en sikker forbindelse, at data krydser netværket.

**Hvordan cachelagrer Power BI rapport-, dashboard- eller modeldata, og er det sikkert?**

* Når der opnås adgang til en datakilde, følger Power BI-tjeneste den proces, der er beskrevet i afsnittet [godkendelse til datakilder](#authentication-to-data-sources) tidligere i dette dokument.

**Cachelagrer klienter data for websiden lokalt?**

* Når browserklienter tilgår Power BI, angiver Power BI-webserverne direktivet *Cache-Control* til *no-store*. Direktivet *no-store* instruerer browsere til ikke at cachelagre den webside, som brugeren får vist, og til ikke at gemme websiden i klientens cachemappe.

**Hvad med rollebaseret sikkerhed, deling af rapporter eller dashboards og dataforbindelser? Hvordan fungerer det sammen med dataadgang, Dashboard visning, rapport adgang eller opdatering?**

* Hvis et dashboard, en rapport eller en datamodel deles med andre brugere via Power BI i forbindelse med datakilder, der **ikke understøtter sikkerhed på rolleniveau**, bliver dataene tilgængelige for brugerne, som de deles med, og brugerne kan få dem vist og interagere med dem. Power BI godkender *ikke* brugerne igen i forhold til den oprindelige datakilde. Når data uploades til Power BI, er den bruger, som blev godkendt i forhold til kildedataene, ansvarlig for at administrere, hvilke andre brugere og grupper der kan få vist dataene.

  Når der oprettes dataforbindelser til en datakilde, der er i **RLS**, f. eks. en Analysis Services datakilde, cachelagres kun Dashboard data i Power bi. Hver gang en rapport eller et datasæt vises eller tilgås i Power BI, som bruger data fra en datakilde, der understøtter sikkerhed på rolleniveau, tilgår Power BI-tjenesten datakilden for at hente data på baggrund af brugerens legitimationsoplysninger. Hvis der er tilstrækkelige tilladelser, indlæses dataene i rapporten eller datamodellen for den pågældende bruger. Hvis godkendelse mislykkes, får brugeren vist en fejl.

  Du kan finde flere oplysninger i afsnittet [godkendelse til data kilder](#authentication-to-data-sources) tidligere i dette dokument.

**Vores brugere opretter forbindelse til de samme datakilder hele tiden, hvoraf nogle kræver legitimationsoplysninger, der adskiller sig fra deres legitimationsoplysninger til domænet. Hvordan kan de undgå at angive disse legitimationsoplysninger, hver gang de opretter en dataforbindelse?**

* Power BI tilbyder [Power BI Personal Gateway](../connect-data/service-gateway-personal-mode.md), som er en funktion, der giver brugerne mulighed for at oprette legitimationsoplysninger til flere forskellige datakilder og derefter bruge disse legitimationsoplysninger automatisk, når hver af disse datakilder efterfølgende tilgås. Du kan finde flere oplysninger under [Power BI Personal Gateway](../connect-data/service-gateway-personal-mode.md).

**Hvilke porte bruges af data gatewayen i det lokale miljø og den personlige gateway? Er der nogle domænenavne, der skal tillades til forbindelses formål?**

* Det detaljerede svar på dette spørgsmål er tilgængelig på følgende link: [gateway porte](/data-integration/gateway/service-gateway-communication#ports)

**Hvordan bruges genoprettelses nøgler, når der arbejdes med data gatewayen i det lokale miljø, og hvor gemmes de? Hvad med sikker administration af legitimationsoplysninger?**

* Under installationen og konfigurationen af gatewayen skriver administratoren en **genoprettelsesnøgle** til gatewayen. Denne **genoprettelsesnøgle** bruges til at generere en stærk AES symmetrisk nøgle. Der oprettes også en asymmetrisk RSA-nøgle på samme tid.

    Disse genererede nøgler (RSA og AES) gemmes i en fil, der er placeret på den lokale computer. Denne fil er også krypteret. Indholdet af filen kan kun dekrypteres af denne specifikke Windows-computer og kun af denne specifikke konto for gatewaytjenesten.

    Når en bruger angiver legitimationsoplysninger for datakilden i brugergrænsefladen i Power BI-tjenesten, krypteres legitimationsoplysningerne med den offentlige nøgle i browseren. Gatewayen dekrypterer legitimationsoplysningerne ved hjælp af den private RSA-nøgle og krypterer dem igen med en AES symmetrisk nøgle, før dataene gemmes i Power BI-tjeneste. Denne proces sikrer, at Power BI-tjenesten aldrig har adgang til ukrypterede data.

**Hvilke kommunikationsprotokoller bruges af datagatewayen i det lokale miljø, og hvordan sikres de?**

* Gatewayen understøtter følgende to kommunikationsprotokoller:

  - AMQP 1,0 – TCP + TLS: denne protokol kræver, at Ports 443, 5671-5672 og 9350-9354 er åbne for udgående kommunikation. Denne protokol foretrækkes, da den har lavere kommunikationsspild.

  - HTTPS – WebSockets over HTTPS + TLS: denne protokol bruger kun port 443. WebSocket startes af en enkelt HTTP CONNECT-meddelelse. Når kanalen er etableret, er kommunikationen i bund og grund TCP + TLS. Du kan tvinge gatewayen til at bruge denne protokol ved at ændre en indstilling, der er beskrevet i [artiklen gateway i det lokale miljø](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

**Hvilke rolle spiller Azure CDN i Power BI?**

* Som tidligere nævnt bruger Power BI Azure Content Delivery Network (CDN) til effektivt at distribuere det nødvendige statiske indhold og de nødvendige statiske filer til brugerne på baggrund af geografisk landestandard. Sagt mere detaljeret, så bruger Power BI-tjenesten flere CDN'er til effektivt at distribuere det nødvendige statiske indhold og de nødvendige statiske filer til brugerne via det offentlige internet. Disse statiske filer omfatter produktdownloads (f.eks. Power BI Desktop, datagatewayen i det lokale miljø eller Power BI-apps fra forskellige uafhængige tjenesteudbydere), browserkonfigurationsfiler, der bruges til at starte og etablere relevante efterfølgende forbindelser med Power BI-tjenesten, samt den indledende sikre Power BI-logonside.

  På baggrund af de oplysninger, der angives under den indledende forbindelse til Power BI-tjenesten, kontakter en brugers browser det angivne Azure CDN (eller for nogle filer den angivne WFE) for at downloade samlingen af angivne fælles filer, som er nødvendige for at muliggøre browserens interaktion med Power BI-tjenesten. Browsersiden inkluderer derefter Azure AD-tokenet, Sessionsoplysningerne, placeringen af den tilknyttede back-end-klynge og den samling af filer, der er hentet fra Azure CDN-og WFE-klyngen, for varigheden af Power BI-tjeneste browsersessionen.

**I forbindelse med Power BI visuelle elementer udfører Microsoft enhver sikkerheds-eller beskyttelses vurdering af den brugerdefinerede visuelle kode, før de udgiver elementer til galleriet?**

* Nej. Det er kundens ansvar at gennemse og afgøre, om der kan være tillid til koden for den brugerdefinerede visualisering. Alle koder for brugerdefinerede visualiseringer håndteres i et sandkassemiljø, så en evt. fejlbehæftet kode i en brugerdefineret visualisering ikke påvirker resten af Power BI-tjenesten.

**Er der andre Power BI-visualiseringer, som sender oplysninger uden for kundens netværk?**

* Ja. Bing Kort og ESRI-visualiseringer overfører data ud af Power BI-tjenesten for visualiseringer, der bruger disse tjenester.

**I forbindelse med skabelon apps udfører Microsoft enhver sikkerheds-eller beskyttelses vurdering af skabelon-appen, før der publiceres elementer i galleriet?**
* Nej. App-udgiveren er ansvarlig for indholdet, mens det er kundens ansvar at gennemgå og finde ud af, om du har tillid til udgiveren af skabelon appen. 

**Er der skabelon apps, der kan sende oplysninger uden for kunde netværket?**
* Ja. Det er kundens ansvar at gennemgå udgiverens politik til beskyttelse af personlige oplysninger og finde ud af, om du skal installere skabelon programmet på lejeren. Udgiveren er ansvarlig for at undersøge kunden om appens funktionsmåde og funktioner.

**Hvad med data højhedsområde? Kan vi klargøre lejere i datacentre, der er placeret i bestemte geografiske områder, for at sikre, at dataene ikke efterlader landegrænserne?**

* Nogle kunder i visse geografiske områder har mulighed for at oprette en lejer i et nationalt cloudmiljø, hvor datalagring og -behandling er isoleret fra alle andre datacentre. Nationale cloudmiljøer har en lidt anderledes type sikkerhed, da en separat dataforvalter driver det nationale cloudmiljø i Power BI-tjenesten på vegne af Microsoft.

  Alternativt kan kunder også konfigurere en lejer i et bestemt område. Disse lejere har dog ikke en separat data uafhængig person fra Microsoft. Priserne på nationale cloudmiljøer er forskellig fra den offentligt tilgængelige kommercielle Power BI-tjeneste. Du kan finde flere oplysninger om tilgængeligheden af Power BI-tjenesten i nationale cloudmiljøer i [Power BI i nationale cloudmiljøer](https://powerbi.microsoft.com/clouds/).

**Hvordan behandler Microsoft forbindelser til kunder, der har Power BI Premium abonnementer? Er disse forbindelser forskellige fra dem, der er oprettet for de ikke-Premium-Power BI-tjeneste?**

* De forbindelser, der er oprettet for kunder med Power BI Premium abonnementer, implementerer en [Azure business-to-business](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) -autorisations proces (B2B) ved hjælp af Azure ad for at aktivere adgangskontrol og godkendelse. Power BI håndterer forbindelser fra Power BI Premium-abonnenter til Power BI Premium-ressourcer på samme måde som for alle andre Azure AD-brugere.

## <a name="feedback-and-suggestions"></a>Feedback og forslag

Vi sætter pris på din feedback. Vi er interesseret i at høre om de forslag, du har til at forbedre, Tilføjelser til eller tydeliggøre dette whitepaper, eller andet indhold, der er relateret til Power BI. Send dine forslag til [pbiss@microsoft.com](mailto:pbiss@microsoft.com) .

## <a name="additional-resources"></a>Yderligere ressourcer

Du kan finde flere oplysninger om Power BI i følgende ressourcer.

* [Introduktion til Power BI Desktop](../fundamentals/desktop-getting-started.md)
* [REST API til Power BI – oversigt](/rest/api/power-bi/)
* [Reference til Power BI-API](/rest/api/power-bi/)
* [On-premises data gateway (Datagateway i det lokale miljø)](../connect-data/service-gateway-onprem.md)
* [Nationale Power BI-cloudmiljøer](https://powerbi.microsoft.com/clouds/)
* [Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
* [Oversigt over enkeltlogon (SSO) til gateways i Power BI](../connect-data/service-gateway-sso-overview.md)