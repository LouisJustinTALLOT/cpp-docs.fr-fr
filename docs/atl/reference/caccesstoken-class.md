---
description: 'En savoir plus sur : classe Caccesstoken,'
title: Caccesstoken,, classe
ms.date: 07/02/2019
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: fdcef40948a19c5ffb69aa32b18566280d048697
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158541"
---
# <a name="caccesstoken-class"></a>Caccesstoken,, classe

Cette classe est un wrapper pour un jeton d’accès.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAccessToken
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Caccesstoken, :: ~ Caccesstoken,](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Caccesstoken, :: Attach](#attach)|Appelez cette méthode pour prendre possession du handle de jeton d’accès donné.|
|[Caccesstoken, :: CheckTokenMembership](#checktokenmembership)|Appelez cette méthode pour déterminer si un SID spécifié est activé dans l' `CAccessToken` objet.|
|[Caccesstoken, :: CreateImpersonationToken](#createimpersonationtoken)|Appelez cette méthode pour créer un nouveau jeton d’accès d’emprunt d’identité.|
|[Caccesstoken, :: CreatePrimaryToken](#createprimarytoken)|Appelez cette méthode pour créer un jeton principal.|
|[Caccesstoken, :: CreateProcessAsUser](#createprocessasuser)|Appelez cette méthode pour créer un nouveau processus qui s’exécute dans le contexte de sécurité de l’utilisateur représenté par l' `CAccessToken` objet.|
|[Caccesstoken, :: CreateRestrictedToken](#createrestrictedtoken)|Appelez cette méthode pour créer un nouvel objet restreint `CAccessToken` .|
|[Caccesstoken, ::D Etach](#detach)|Appelez cette méthode pour révoquer la propriété du jeton d’accès.|
|[Caccesstoken, ::D isablePrivilege](#disableprivilege)|Appelez cette méthode pour désactiver un privilège dans l' `CAccessToken` objet.|
|[Caccesstoken, ::D isablePrivileges](#disableprivileges)|Appelez cette méthode pour désactiver un ou plusieurs privilèges dans l' `CAccessToken` objet.|
|[Caccesstoken, :: EnablePrivilege](#enableprivilege)|Appelez cette méthode pour activer un privilège dans l' `CAccessToken` objet.|
|[Caccesstoken, :: EnablePrivileges](#enableprivileges)|Appelez cette méthode pour activer un ou plusieurs privilèges dans l' `CAccessToken` objet.|
|[Caccesstoken, :: GetDefaultDacl](#getdefaultdacl)|Appelez cette méthode pour retourner la `CAccessToken` liste DACL par défaut de l’objet.|
|[Caccesstoken, :: GetEffectiveToken](#geteffectivetoken)|Appelez cette méthode pour obtenir l' `CAccessToken` objet égal au jeton d’accès en vigueur pour le thread actuel.|
|[Caccesstoken, :: GetGroups](#getgroups)|Appelez cette méthode pour retourner les `CAccessToken` groupes de jetons de l’objet.|
|[Caccesstoken, :: GetHandle](#gethandle)|Appelez cette méthode pour récupérer un handle du jeton d’accès.|
|[Caccesstoken, :: GetImpersonationLevel](#getimpersonationlevel)|Appelez cette méthode pour récupérer le niveau d’emprunt d’identité à partir du jeton d’accès.|
|[Caccesstoken, :: GetLogonSessionId](#getlogonsessionid)|Appelez cette méthode pour récupérer l’ID de session d’ouverture de session associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetLogonSid](#getlogonsid)|Appelez cette méthode pour récupérer le SID d’ouverture de session associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetOwner](#getowner)|Appelez cette méthode pour que le propriétaire soit associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetPrimaryGroup](#getprimarygroup)|Appelez cette méthode pour récupérer le groupe principal associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetPrivileges](#getprivileges)|Appelez cette méthode pour récupérer les privilèges associés à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetProcessToken](#getprocesstoken)|Appelez cette méthode pour initialiser `CAccessToken` avec le jeton d’accès à partir du processus donné.|
|[Caccesstoken, :: GetProfile](#getprofile)|Appelez cette méthode pour faire en sorte que le handle pointe vers le profil utilisateur associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetSource](#getsource)|Appelez cette méthode pour récupérer la source de l' `CAccessToken` objet.|
|[Caccesstoken, :: GetStatistics](#getstatistics)|Appelez cette méthode pour récupérer les informations associées à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetTerminalServicesSessionId](#getterminalservicessessionid)|Appelez cette méthode pour récupérer l’ID de session des services Terminal Server associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetThreadToken](#getthreadtoken)|Appelez cette méthode pour initialiser `CAccessToken` avec le jeton à partir du thread donné.|
|[Caccesstoken, :: GetTokenId](#gettokenid)|Appelez cette méthode pour récupérer l’ID de jeton associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: GetType](#gettype)|Appelez cette méthode pour récupérer le type de jeton de l' `CAccessToken` objet.|
|[Caccesstoken, :: GetUser](#getuser)|Appelez cette méthode pour identifier l’utilisateur associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: HKeyCurrentUser](#hkeycurrentuser)|Appelez cette méthode pour faire en sorte que le handle pointe vers le profil utilisateur associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: Impersonate](#impersonate)|Appelez cette méthode pour assigner un emprunt `CAccessToken` d’identité à un thread.|
|[Caccesstoken, :: ImpersonateLoggedOnUser](#impersonateloggedonuser)|Appelez cette méthode pour autoriser le thread appelant à emprunter l’identité du contexte de sécurité d’un utilisateur connecté.|
|[Caccesstoken, :: IsTokenRestricted](#istokenrestricted)|Appelez cette méthode pour vérifier si l' `CAccessToken` objet contient une liste de sid restreints.|
|[Caccesstoken, :: LoadUserProfile](#loaduserprofile)|Appelez cette méthode pour charger le profil utilisateur associé à l' `CAccessToken` objet.|
|[Caccesstoken, :: LogonUser](#logonuser)|Appelez cette méthode pour créer une session d’ouverture de session pour l’utilisateur associé aux informations d’identification données.|
|[Caccesstoken, :: OpenCOMClientToken](#opencomclienttoken)|Appelez cette méthode à partir d’un serveur COM qui gère un appel d’un client pour initialiser `CAccessToken` avec le jeton d’accès à partir du client com.|
|[Caccesstoken, :: OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Appelez cette méthode à partir d’un serveur effectuant des requêtes sur un canal nommé pour initialiser le `CAccessToken` avec le jeton d’accès du client.|
|[Caccesstoken, :: OpenRPCClientToken](#openrpcclienttoken)|Appelez cette méthode à partir d’un serveur qui gère un appel d’un client RPC pour initialiser `CAccessToken` avec le jeton d’accès à partir du client.|
|[Caccesstoken, :: OpenThreadToken](#openthreadtoken)|Appelez cette méthode pour définir le niveau d’emprunt d’identité, puis initialisez `CAccessToken` avec le jeton à partir du thread donné.|
|[Caccesstoken, ::P rivilegeCheck](#privilegecheck)|Appelez cette méthode pour déterminer si un jeu de privilèges spécifié est activé dans l' `CAccessToken` objet.|
|[Caccesstoken, :: Revert](#revert)|Appelez cette méthode pour arrêter un thread qui utilise un jeton d’emprunt d’identité.|
|[Caccesstoken, :: SetDefaultDacl](#setdefaultdacl)|Appelez cette méthode pour définir la DACL par défaut de l' `CAccessToken` objet.|
|[Caccesstoken, :: SetOwner](#setowner)|Appelez cette méthode pour définir le propriétaire de l' `CAccessToken` objet.|
|[Caccesstoken, :: SetPrimaryGroup](#setprimarygroup)|Appelez cette méthode pour définir le groupe principal de l' `CAccessToken` objet.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/win32/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou d’un thread et qui est alloué à chaque utilisateur connecté à un système Windows.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="caccesstokenattach"></a><a name="attach"></a> Caccesstoken, :: Attach

Appelez cette méthode pour prendre possession du handle de jeton d’accès donné.

```cpp
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Paramètres

*hToken*<br/>
Handle du jeton d’accès.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si l' `CAccessToken` objet a déjà la propriété d’un jeton d’accès.

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a> Caccesstoken, :: ~ Caccesstoken,

Destructeur.

```cpp
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a> Caccesstoken, :: CheckTokenMembership

Appelez cette méthode pour déterminer si un SID spécifié est activé dans l' `CAccessToken` objet.

```cpp
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Référence à un objet de [classe CSID](../../atl/reference/csid-class.md) .

*pbIsMember*<br/>
Pointeur vers une variable qui reçoit les résultats de la vérification.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

La `CheckTokenMembership` méthode vérifie la présence du SID dans les SID de groupe et d’utilisateur du jeton d’accès. Si le SID est présent et qu’il a l’attribut SE_GROUP_ENABLED, *pbIsMember* a la valeur true ; dans le cas contraire, il est défini sur FALSe.

Dans les versions Debug, une erreur d’assertion se produit si *pbIsMember* n’est pas un pointeur valide.

> [!NOTE]
> L' `CAccessToken` objet doit être un jeton d’emprunt d’identité et non un jeton principal.

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a> Caccesstoken, :: CreateImpersonationToken

Appelez cette méthode pour créer un jeton d’accès d’emprunt d’identité.

```cpp
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Paramètres

*Améliorez*<br/>
Pointeur vers le nouvel `CAccessToken` objet.

*SIL*<br/>
Spécifie un [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) type énuméré qui fournit le niveau d’emprunt d’identité du nouveau jeton.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

`CreateImpersonationToken` appelle [DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) pour créer un jeton d’emprunt d’identité.

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a> Caccesstoken, :: CreatePrimaryToken

Appelez cette méthode pour créer un jeton principal.

```cpp
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPri*<br/>
Pointeur vers le nouvel `CAccessToken` objet.

*dwDesiredAccess*<br/>
Spécifie les droits d’accès demandés pour le nouveau jeton. La valeur par défaut, MAXIMUM_ALLOWED, demande tous les droits d’accès qui sont valides pour l’appelant. Pour plus d’informations sur les droits d’accès, consultez droits d’accès [et masques d’accès](/windows/win32/SecAuthZ/access-rights-and-access-masks) .

*pTokenAttributes*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie un descripteur de sécurité pour le nouveau jeton et détermine si les processus enfants peuvent hériter du jeton. Si *pTokenAttributes* a la valeur null, le jeton obtient un descripteur de sécurité par défaut et le descripteur ne peut pas être hérité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

`CreatePrimaryToken` appelle [DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) pour créer un jeton principal.

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a> Caccesstoken, :: CreateProcessAsUser

Appelez cette méthode pour créer un nouveau processus qui s’exécute dans le contexte de sécurité de l’utilisateur représenté par l' `CAccessToken` objet.

```cpp
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*pApplicationName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le module à exécuter. Ce paramètre ne peut pas être NULL.

*pCommandLine*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie la ligne de commande à exécuter.

*pProcessInformation*<br/>
Pointeur vers une [structure PROCESS_INFORMATION](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) qui reçoit des informations d’identification sur le nouveau processus.

*pStartupInfo*<br/>
Pointeur vers une structure [STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) qui spécifie comment la fenêtre principale pour le nouveau processus doit apparaître.

*dwCreationFlags*<br/>
Spécifie des indicateurs supplémentaires qui contrôlent la classe de priorité et la création du processus. Consultez la fonction Win32 [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) pour obtenir la liste des indicateurs.

*bLoadProfile*<br/>
Si la valeur est TRUE, le profil de l’utilisateur est chargé avec [LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew).

*pProcessAttributes*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie un descripteur de sécurité pour le nouveau processus et détermine si les processus enfants peuvent hériter du handle retourné. Si *pProcessAttributes* a la valeur null, le processus obtient un descripteur de sécurité par défaut et le descripteur ne peut pas être hérité.

*pThreadAttributes*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie un descripteur de sécurité pour le nouveau thread et détermine si les processus enfants peuvent hériter du handle retourné. Si *pThreadAttributes* a la valeur null, le thread obtient un descripteur de sécurité par défaut et le descripteur ne peut pas être hérité.

*bInherit*<br/>
Indique si le nouveau processus hérite des handles du processus appelant. Si la valeur est TRUE, chaque descripteur ouvert pouvant être hérité dans le processus appelant est hérité par le nouveau processus. Les handles hérités ont la même valeur et les mêmes privilèges d’accès que les handles d’origine.

*pCurrentDirectory*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le lecteur et le répertoire actifs pour le nouveau processus. La chaîne doit être un chemin d’accès complet qui comprend une lettre de lecteur. Si ce paramètre a la valeur NULL, le nouveau processus aura le même lecteur et le même répertoire en cours que le processus appelant.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

`CreateProcessAsUser` utilise la `CreateProcessAsUser` fonction Win32 pour créer un nouveau processus qui s’exécute dans le contexte de sécurité de l’utilisateur représenté par l' `CAccessToken` objet. Consultez la description de la fonction [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) pour une discussion complète sur les paramètres requis.

Pour que cette méthode aboutisse, l' `CAccessToken` objet doit contenir AssignPrimaryToken (sauf s’il s’agit d’un jeton restreint) et des privilèges IncreaseQuota.

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a> Caccesstoken, :: CreateRestrictedToken

Appelez cette méthode pour créer un nouvel objet restreint `CAccessToken` .

```cpp
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pRestrictedToken*<br/>
Nouvel `CAccessToken` objet restreint.

*SidsToDisable*<br/>
`CTokenGroups`Objet qui spécifie les SID en refus seul.

*SidsToRestrict*<br/>
`CTokenGroups`Objet qui spécifie les SID de restriction.

*PrivilegesToDelete*<br/>
`CTokenPrivileges`Objet qui spécifie les privilèges à supprimer dans le jeton restreint. La valeur par défaut crée un objet vide.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

`CreateRestrictedToken` utilise la fonction Win32 [CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) pour créer un nouvel `CAccessToken` objet, avec des restrictions.

> [!IMPORTANT]
> Lors de l’utilisation `CreateRestrictedToken` de, vérifiez les points suivants : le jeton existant est valide (et n’est pas entré par l’utilisateur) et *SidsToDisable* et *PrivilegesToDelete* sont tous les deux valides (et ne sont pas entrés par l’utilisateur). Si la méthode retourne la valeur FALSe, refuser la fonctionnalité.

## <a name="caccesstokendetach"></a><a name="detach"></a> Caccesstoken, ::D Etach

Appelez cette méthode pour révoquer la propriété du jeton d’accès.

```cpp
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le handle vers le `CAccessToken` qui a été détaché.

### <a name="remarks"></a>Notes

Cette méthode révoque la `CAccessToken` propriété du jeton d’accès.

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a> Caccesstoken, ::D isablePrivilege

Appelez cette méthode pour désactiver un privilège dans l' `CAccessToken` objet.

```cpp
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne contenant le privilège à désactiver dans l' `CAccessToken` objet.

*pPreviousState*<br/>
Pointeur vers un `CTokenPrivileges` objet qui va contenir l’état précédent des privilèges.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a> Caccesstoken, ::D isablePrivileges

Appelez cette méthode pour désactiver un ou plusieurs privilèges dans l' `CAccessToken` objet.

```cpp
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*<br/>
Pointeur vers un tableau de chaînes contenant les privilèges à désactiver dans l' `CAccessToken` objet.

*pPreviousState*<br/>
Pointeur vers un `CTokenPrivileges` objet qui va contenir l’état précédent des privilèges.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a> Caccesstoken, :: EnablePrivilege

Appelez cette méthode pour activer un privilège dans l' `CAccessToken` objet.

```cpp
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne contenant le privilège à activer dans l' `CAccessToken` objet.

*pPreviousState*<br/>
Pointeur vers un `CTokenPrivileges` objet qui va contenir l’état précédent des privilèges.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a> Caccesstoken, :: EnablePrivileges

Appelez cette méthode pour activer un ou plusieurs privilèges dans l' `CAccessToken` objet.

```cpp
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*<br/>
Pointeur vers un tableau de chaînes contenant les privilèges à activer dans l' `CAccessToken` objet.

*pPreviousState*<br/>
Pointeur vers un `CTokenPrivileges` objet qui va contenir l’état précédent des privilèges.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a> Caccesstoken, :: GetDefaultDacl

Appelez cette méthode pour retourner la `CAccessToken` liste DACL par défaut de l’objet.

```cpp
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pDacl*<br/>
Pointeur vers l’objet de [classe CDacl](../../atl/reference/cdacl-class.md) qui recevra la `CAccessToken` liste DACL par défaut de l’objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la DACL par défaut a été récupérée ; sinon, FALSe.

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a> Caccesstoken, :: GetEffectiveToken

Appelez cette méthode pour obtenir l' `CAccessToken` objet égal au jeton d’accès en vigueur pour le thread actuel.

```cpp
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés à la liste DACL du jeton pour déterminer quels accès sont accordés ou refusés.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a> Caccesstoken, :: GetGroups

Appelez cette méthode pour retourner les `CAccessToken` groupes de jetons de l’objet.

```cpp
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pGroups*<br/>
Pointeur vers l’objet de [classe CTokenGroups](../../atl/reference/ctokengroups-class.md) qui recevra les informations de groupe.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengethandle"></a><a name="gethandle"></a> Caccesstoken, :: GetHandle

Appelez cette méthode pour récupérer un handle du jeton d’accès.

```cpp
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle pour le `CAccessToken` jeton d’accès de l’objet.

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a> Caccesstoken, :: GetImpersonationLevel

Appelez cette méthode pour récupérer le niveau d’emprunt d’identité à partir du jeton d’accès.

```cpp
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pImpersonationLevel*<br/>
Pointeur vers un type d’énumération [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) qui recevra les informations de niveau d’emprunt d’identité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a> Caccesstoken, :: GetLogonSessionId

Appelez cette méthode pour récupérer l’ID de session d’ouverture de session associé à l' `CAccessToken` objet.

```cpp
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pluid*<br/>
Pointeur vers un [LUID](/windows/win32/api/winnt/ns-winnt-luid) qui recevra l’ID de session de connexion.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si *pluid* est une valeur non valide.

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a> Caccesstoken, :: GetLogonSid

Appelez cette méthode pour récupérer le SID d’ouverture de session associé à l' `CAccessToken` objet.

```cpp
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un objet de [classe CSID](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si *pSid* est une valeur non valide.

## <a name="caccesstokengetowner"></a><a name="getowner"></a> Caccesstoken, :: GetOwner

Appelez cette méthode pour que le propriétaire soit associé à l' `CAccessToken` objet.

```cpp
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un objet de [classe CSID](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le propriétaire est défini par défaut sur tous les objets créés pendant que ce jeton d’accès est en vigueur.

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a> Caccesstoken, :: GetPrimaryGroup

Appelez cette méthode pour récupérer le groupe principal associé à l' `CAccessToken` objet.

```cpp
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un objet de [classe CSID](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le groupe est défini par défaut sur tous les objets créés pendant que ce jeton d’accès est en vigueur.

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a> Caccesstoken, :: GetPrivileges

Appelez cette méthode pour récupérer les privilèges associés à l' `CAccessToken` objet.

```cpp
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPrivileges*<br/>
Pointeur vers un objet de [classe CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md) qui recevra les privilèges.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a> Caccesstoken, :: GetProcessToken

Appelez cette méthode pour initialiser `CAccessToken` avec le jeton d’accès à partir du processus donné.

```cpp
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés à la liste DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*hProcess*<br/>
Handle vers le processus dont le jeton d’accès est ouvert. Si la valeur par défaut NULL est utilisée, le processus actuel est utilisé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Appelle la fonction Win32 [OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) .

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a> Caccesstoken, :: GetProfile

Appelez cette méthode pour faire en sorte que le handle pointe vers le profil utilisateur associé à l' `CAccessToken` objet.

```cpp
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle pointant vers le profil utilisateur, ou NULL s’il n’existe aucun profil.

## <a name="caccesstokengetsource"></a><a name="getsource"></a> Caccesstoken, :: GetSource

Appelez cette méthode pour récupérer la source de l' `CAccessToken` objet.

```cpp
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSource*<br/>
Pointeur vers une structure [TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a> Caccesstoken, :: GetStatistics

Appelez cette méthode pour récupérer les informations associées à l' `CAccessToken` objet.

```cpp
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pStatistics*<br/>
Pointeur vers une structure [TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a> Caccesstoken, :: GetTerminalServicesSessionId

Appelez cette méthode pour récupérer l’ID de session des services Terminal Server associé à l' `CAccessToken` objet.

```cpp
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pdwSessionId*<br/>
ID de session des services Terminal Server.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a> Caccesstoken, :: GetThreadToken

Appelez cette méthode pour initialiser `CAccessToken` avec le jeton à partir du thread donné.

```cpp
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés à la liste DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*hThread*<br/>
Handle vers le thread dont le jeton d’accès est ouvert.

*bOpenAsSelf*<br/>
Indique si la vérification de l’accès doit être effectuée par rapport au contexte de sécurité du thread appelant la `GetThreadToken` méthode ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre a la valeur FALSe, le contrôle d’accès est effectué à l’aide du contexte de sécurité du thread appelant. Si le thread emprunte l’identité d’un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre a la valeur TRUE, le contrôle d’accès est effectué à l’aide du contexte de sécurité du processus pour le thread appelant.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a> Caccesstoken, :: GetTokenId

Appelez cette méthode pour récupérer l’ID de jeton associé à l' `CAccessToken` objet.

```cpp
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pluid*<br/>
Pointeur vers un [LUID](/windows/win32/api/winnt/ns-winnt-luid) qui recevra l’ID de jeton.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokengettype"></a><a name="gettype"></a> Caccesstoken, :: GetType

Appelez cette méthode pour récupérer le type de jeton de l' `CAccessToken` objet.

```cpp
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pType*<br/>
Adresse de la variable [TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type) qui, en cas de réussite, reçoit le type du jeton.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le type d’énumération TOKEN_TYPE contient des valeurs qui différencient un jeton principal et un jeton d’emprunt d’identité.

## <a name="caccesstokengetuser"></a><a name="getuser"></a> Caccesstoken, :: GetUser

Appelez cette méthode pour identifier l’utilisateur associé à l' `CAccessToken` objet.

```cpp
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un objet de [classe CSID](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a> Caccesstoken, :: HKeyCurrentUser

Appelez cette méthode pour faire en sorte que le handle pointe vers le profil utilisateur associé à l' `CAccessToken` objet.

```cpp
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle pointant vers le profil utilisateur, ou NULL s’il n’existe aucun profil.

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a> Caccesstoken, :: Impersonate

Appelez cette méthode pour assigner un emprunt `CAccessToken` d’identité à un thread.

```cpp
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*hThread*<br/>
Handle vers le thread auquel assigner le jeton d’emprunt d’identité. Ce descripteur doit avoir été ouvert avec les droits d’accès TOKEN_IMPERSONATE. Si *hThread* a la valeur null, la méthode provoque l’arrêt du thread à l’aide d’un jeton d’emprunt d’identité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si `CAccessToken` le n’a pas de pointeur valide vers un jeton.

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour rétablir automatiquement les jetons d’accès empruntés.

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a> Caccesstoken, :: ImpersonateLoggedOnUser

Appelez cette méthode pour autoriser le thread appelant à emprunter l’identité du contexte de sécurité d’un utilisateur connecté.

```cpp
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

> [!IMPORTANT]
> Si un appel à une fonction d’emprunt d’identité échoue pour une raison quelconque, le client n’est pas emprunté et la demande du client est effectuée dans le contexte de sécurité du processus à partir duquel l’appel a été effectué. Si le processus s’exécute en tant que compte à privilèges élevés, ou en tant que membre d’un groupe d’administration, l’utilisateur peut être en mesure d’effectuer des actions qui, sinon, seraient rejetées. Par conséquent, la valeur de retour de cette fonction doit toujours être confirmée.

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a> Caccesstoken, :: IsTokenRestricted

Appelez cette méthode pour vérifier si l' `CAccessToken` objet contient une liste de sid restreints.

```cpp
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’objet contient une liste de SID de restriction, FALSe s’il n’y a pas de sid restreints ou si la méthode échoue.

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a> Caccesstoken, :: LoadUserProfile

Appelez cette méthode pour charger le profil utilisateur associé à l' `CAccessToken` objet.

```cpp
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si `CAccessToken` ne contient pas de jeton valide, ou si un profil utilisateur existe déjà.

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a> Caccesstoken, :: LogonUser

Appelez cette méthode pour créer une session d’ouverture de session pour l’utilisateur associé aux informations d’identification données.

```cpp
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>Paramètres

*pszUserName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom d’utilisateur. Il s’agit du nom du compte d’utilisateur auquel se connecter.

*pszDomain*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom du domaine ou du serveur dont la base de données du compte contient le compte *pszUserName* .

*pszPassword*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le mot de passe en texte clair pour le compte d’utilisateur spécifié par *pszUserName*.

*dwLogonType*<br/>
Spécifie le type d’opération d’ouverture de session à effectuer. Pour plus d’informations, consultez [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) .

*dwLogonProvider*<br/>
Spécifie le fournisseur d’ouverture de session. Pour plus d’informations, consultez [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le jeton d’accès résultant de l’ouverture de session est associé à `CAccessToken` . Pour que cette méthode aboutisse, l' `CAccessToken` objet doit contenir SE_TCB_NAME privilèges, identifiant le détenteur dans le cadre de la base de l’ordinateur approuvé. Pour plus d’informations sur les privilèges requis, consultez [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) .

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a> Caccesstoken, :: OpenCOMClientToken

Appelez cette méthode à partir d’un serveur COM qui gère un appel d’un client pour initialiser `CAccessToken` avec le jeton d’accès à partir du client com.

```cpp
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés à la liste DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*bImpersonate*<br/>
Si la valeur est TRUE, le thread actuel empruntera l’identité du client COM appelant si cet appel se termine correctement. Si la valeur est FALSe, le jeton d’accès est ouvert, mais le thread n’a pas de jeton d’emprunt d’identité lorsque cet appel se termine.

*bOpenAsSelf*<br/>
Indique si la vérification de l’accès doit être effectuée par rapport au contexte de sécurité du thread appelant la méthode [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre a la valeur FALSe, le contrôle d’accès est effectué à l’aide du contexte de sécurité du thread appelant. Si le thread emprunte l’identité d’un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre a la valeur TRUE, le contrôle d’accès est effectué à l’aide du contexte de sécurité du processus pour le thread appelant.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour rétablir automatiquement les jetons d’accès empruntés créés en affectant à l’indicateur *bImpersonate* la valeur true.

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a> Caccesstoken, :: OpenNamedPipeClientToken

Appelez cette méthode à partir d’un serveur effectuant des requêtes sur un canal nommé pour initialiser le `CAccessToken` avec le jeton d’accès du client.

```cpp
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*hPipe*<br/>
Handle vers un canal nommé.

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés à la liste DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*bImpersonate*<br/>
Si la valeur est TRUE, le thread actuel empruntera l’identité du client du canal appelant si cet appel se termine correctement. Si la valeur est FALSe, le jeton d’accès est ouvert, mais le thread n’a pas de jeton d’emprunt d’identité lorsque cet appel se termine.

*bOpenAsSelf*<br/>
Indique si la vérification de l’accès doit être effectuée par rapport au contexte de sécurité du thread appelant la méthode [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre a la valeur FALSe, le contrôle d’accès est effectué à l’aide du contexte de sécurité du thread appelant. Si le thread emprunte l’identité d’un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre a la valeur TRUE, le contrôle d’accès est effectué à l’aide du contexte de sécurité du processus pour le thread appelant.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour rétablir automatiquement les jetons d’accès empruntés créés en affectant à l’indicateur *bImpersonate* la valeur true.

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a> Caccesstoken, :: OpenRPCClientToken

Appelez cette méthode à partir d’un serveur qui gère un appel d’un client RPC pour initialiser `CAccessToken` avec le jeton d’accès à partir du client.

```cpp
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*BindingHandle*<br/>
Handle de liaison sur le serveur qui représente une liaison à un client.

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés à la liste DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*bImpersonate*<br/>
Si la valeur est TRUE, le thread actuel empruntera l’identité du client RPC appelant si cet appel se termine correctement. Si la valeur est FALSe, le jeton d’accès est ouvert, mais le thread n’a pas de jeton d’emprunt d’identité lorsque cet appel se termine.

*bOpenAsSelf*<br/>
Indique si la vérification de l’accès doit être effectuée par rapport au contexte de sécurité du thread appelant la méthode [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre a la valeur FALSe, le contrôle d’accès est effectué à l’aide du contexte de sécurité du thread appelant. Si le thread emprunte l’identité d’un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre a la valeur TRUE, le contrôle d’accès est effectué à l’aide du contexte de sécurité du processus pour le thread appelant.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour rétablir automatiquement les jetons d’accès empruntés créés en affectant à l’indicateur *bImpersonate* la valeur true.

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a> Caccesstoken, :: OpenThreadToken

Appelez cette méthode pour définir le niveau d’emprunt d’identité, puis initialisez `CAccessToken` avec le jeton à partir du thread donné.

```cpp
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés à la liste DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*bImpersonate*<br/>
Si la valeur est TRUE, le thread reste au niveau d’emprunt d’identité demandé à l’issue de cette méthode. Si la valeur est FALSe, le thread revient à son niveau d’emprunt d’identité d’origine.

*bOpenAsSelf*<br/>
Indique si la vérification de l’accès doit être effectuée par rapport au contexte de sécurité du thread appelant la méthode [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre a la valeur FALSe, le contrôle d’accès est effectué à l’aide du contexte de sécurité du thread appelant. Si le thread emprunte l’identité d’un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre a la valeur TRUE, le contrôle d’accès est effectué à l’aide du contexte de sécurité du processus pour le thread appelant.

*SIL*<br/>
Spécifie un [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) type énuméré qui fournit le niveau d’emprunt d’identité du jeton.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

`OpenThreadToken` est semblable à [caccesstoken, :: GetThreadToken](#getthreadtoken), mais définit le niveau d’emprunt d’identité avant d’initialiser le `CAccessToken` à partir du jeton d’accès du thread.

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour rétablir automatiquement les jetons d’accès empruntés créés en affectant à l’indicateur *bImpersonate* la valeur true.

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a> Caccesstoken, ::P rivilegeCheck

Appelez cette méthode pour déterminer si un jeu de privilèges spécifié est activé dans l' `CAccessToken` objet.

```cpp
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Paramètres

*RequiredPrivileges*<br/>
Pointeur vers une structure [PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set) .

*pbResult*<br/>
Pointeur vers une valeur que la méthode définit pour indiquer si l’un ou l’ensemble des privilèges spécifiés sont activés dans l' `CAccessToken` objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Lorsque `PrivilegeCheck` retourne, le `Attributes` membre de chaque structure de [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) est défini sur SE_PRIVILEGE_USED_FOR_ACCESS si le privilège correspondant est activé. Cette méthode appelle la fonction Win32 [PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) .

## <a name="caccesstokenrevert"></a><a name="revert"></a> Caccesstoken, :: Revert

Appelez cette méthode pour empêcher un thread d’utiliser un jeton d’emprunt d’identité.

```cpp
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*hThread*<br/>
Handle vers le thread pour rétablir l’emprunt d’identité. Si *hThread* a la valeur null, le thread actuel est utilisé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

La Reversion des jetons d’emprunt d’identité peut être effectuée automatiquement avec la [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md).

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a> Caccesstoken, :: SetDefaultDacl

Appelez cette méthode pour définir la DACL par défaut de l' `CAccessToken` objet.

```cpp
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Paramètres

*rDacl*<br/>
Nouvelles informations de la [classe CDacl](../../atl/reference/cdacl-class.md) par défaut.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

La liste DACL par défaut est la liste DACL qui est utilisée par défaut lorsque de nouveaux objets sont créés avec ce jeton d’accès en vigueur.

## <a name="caccesstokensetowner"></a><a name="setowner"></a> Caccesstoken, :: SetOwner

Appelez cette méthode pour définir le propriétaire de l' `CAccessToken` objet.

```cpp
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Objet de [classe CSID](../../atl/reference/csid-class.md) contenant les informations de propriétaire.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le propriétaire est le propriétaire par défaut qui est utilisé pour les nouveaux objets créés alors que ce jeton d’accès est en vigueur.

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a> Caccesstoken, :: SetPrimaryGroup

Appelez cette méthode pour définir le groupe principal de l' `CAccessToken` objet.

```cpp
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Objet de [classe CSID](../../atl/reference/csid-class.md) contenant les informations de groupe principal.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le groupe principal est le groupe par défaut pour les nouveaux objets créés alors que ce jeton d’accès est en vigueur.

## <a name="see-also"></a>Voir aussi

[ATLSecurity, exemple](../../overview/visual-cpp-samples.md)<br/>
[Jetons d’accès](/windows/win32/SecAuthZ/access-tokens)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
