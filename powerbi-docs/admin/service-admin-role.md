---
title: Om roller som administrator af Power BI-tjenesten
description: I denne artikel beskrives rollen som administrator af Power BI-tjenesten og de specifikke roller, der giver administratorrettigheder.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/02/2020
LocalizationGroup: Administration
ms.openlocfilehash: 8ba05d9a7dd39df91cd7313038129f69e9b8d70b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408038"
---
# <a name="understanding-power-bi-service-administrator-roles"></a>Om roller som administrator af Power BI-tjenesten

Hvis du vil administrere en Power BI-lejer, skal du have en af følgende roller: Power BI-administrator, Power Platform-administrator eller Global administrator i Microsoft 365. Administratorer af Microsoft 365-brugeradministration tildeler brugere til rollerne Power BI-administrator eller Power Platform-administrator i Microsoft 365 Administration eller ved hjælp af et PowerShell-script. Du kan finde flere oplysninger under [Tildel roller til brugerkonti med PowerShell](/office365/enterprise/powershell/assign-roles-to-user-accounts-with-office-365-powershell).

Brugere med rollerne Power BI-administrator eller Power Platform-administrator har fuld kontrol over en Power BI-lejer og de tilhørende administrative funktioner (undtagen licensering). Når en bruger er tildelt, har vedkommende adgang til [Power BI-administrationsportalen](service-admin-portal.md). Her har vedkommende adgang til lejerbaserede forbrugsdata og kan kontrollere lejerbaseret forbrug af Power BI-funktioner. Disse administratorroller er ideelle til brugere, som skal have adgang til Power BI-administrationsportalen, men ikke skal have tildelt anden administrativ adgang i Microsoft 365.

> [!NOTE]
> I Power BI dokumentationen henviser "Power BI administrator" til brugere med rollen Power BI-administrator eller Power Platform-administrator. Dokumentationen angiver, hvornår rollen Global administrator i Microsoft 365 kræves til en opgave.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Rollerne som administrator af Power BI-tjenesten og Power Platform giver ikke følgende muligheder:

* Mulighed for at ændre brugere og licenser i Microsoft 365 Administration.

* Adgang til overvågningslogge. Du kan finde flere oplysninger under [Spor brugeraktiviteter i Power BI](service-admin-auditing.md).

Disse funktioner kræver rollen Global administrator i Microsoft 365.

## <a name="assign-users-to-an-admin-role-in-the-microsoft-365-admin-center"></a>Tildel brugere til en administratorrolle i Microsoft 365 Administration

Følg disse trin for at tildele brugere til en administratorrolle i Microsoft 365 Administration.

1. I [Microsoft 365 Administration](https://portal.office.com/adminportal/home#/homepage) skal du vælge **Brugere** > **Aktive brugere**.

    ![Microsoft 365 Administration](media/service-admin-role/powerbi-admin-users.png)

1. Vælg den bruger, du vil tildele rollen.

1. Vælg **Administrer roller** under **Roller**.

    ![Administrer roller](media/service-admin-role/powerbi-admin-edit-roles.png)

1. Udvid **Vis alle efter kategori**, og vælg derefter **Power BI-administrator** eller **Power Platform-administrator**.

    ![Vælg administratorrollen](media/service-admin-role/powerbi-admin-role.png)

1. Vælg **Gem ændringer**.

## <a name="assign-users-to-the-admin-role-with-powershell"></a>Tildel brugere administratorrollen via PowerShell

Du kan også tildele brugere roller ved hjælp af PowerShell. Brugere administreres i Azure Active Directory (Azure AD). Hvis du ikke allerede har Azure AD PowerShell-modulet, skal du [downloade og installere den nyeste version](https://www.powershellgallery.com/packages/AzureAD/).

1. Først skal du oprette forbindelse til Azure AD:
   ```
   PS C:\Windows\system32> Connect-AzureAD
   ```

1. Derefter skal du hente **ObjectId** for rollen som **administrator af Power BI-tjenesten**. Du kan køre [Get-AzureADDirectoryRole](/powershell/module/azuread/get-azureaddirectoryrole) for at hente **ObjectId**

    ```
    PS C:\Windows\system32> Get-AzureADDirectoryRole

    ObjectId                             DisplayName                        Description
    --------                             -----------                        -----------
    00f79122-c45d-436d-8d4a-2c0c6ca246bf Power BI Service Administrator     Full access in the Power BI Service.
    250d1222-4bc0-4b4b-8466-5d5765d14af9 Helpdesk Administrator             Helpdesk Administrator has access to perform..
    3ddec257-efdc-423d-9d24-b7cf29e0c86b Directory Synchronization Accounts Directory Synchronization Accounts
    50daa576-896c-4bf3-a84e-1d9d1875c7a7 Company Administrator              Company Administrator role has full access t..
    6a452384-6eb9-4793-8782-f4e7313b4dfd Device Administrators              Device Administrators
    9900b7db-35d9-4e56-a8e3-c5026cac3a11 AdHoc License Administrator        Allows access manage AdHoc license.
    a3631cce-16ce-47a3-bbe1-79b9774a0570 Directory Readers                  Allows access to various read only tasks in ..
    f727e2f3-0829-41a7-8c5c-5af83c37f57b Email Verified User Creator        Allows creation of new email verified users.
    ```

    I dette tilfælde er rollen **ObjectId** 00f79122-c45d-436d-8d4a-2c0c6ca246bf.

1. Hent derefter brugerens **ObjectId**. Det finder du ved at køre [Get-AzureADUser](/powershell/module/azuread/get-azureaduser).

    ```
    PS C:\Windows\system32> Get-AzureADUser -ObjectId 'tim@contoso.com'

    ObjectId                             DisplayName UserPrincipalName      UserType
    --------                             ----------- -----------------      --------
    6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c Tim         tim@contoso.com        Member
    ```

1. For at føje medlemmet til rollen skal du køre [Add-AzureADDirectoryRoleMember](/powershell/module/azuread/add-azureaddirectoryrolemember).

    | Parameter | Beskrivelse |
    | --- | --- |
    | ObjectId |Rollen ObjectId. |
    | RefObjectId |Medlemmernes ObjectId. |

    ```powershell
    Add-AzureADDirectoryRoleMember -ObjectId 00f79122-c45d-436d-8d4a-2c0c6ca246bf -RefObjectId 6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c
    ```

## <a name="next-steps"></a>Næste trin

[Administrer Power BI i din organisation](service-admin-administering-power-bi-in-your-organization.md)  
[Power BI-administrationsportal](service-admin-portal.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)