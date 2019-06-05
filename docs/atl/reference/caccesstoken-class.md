---
title: Caccesstoken, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: ce5c29c2399fd47bdb1ad0135257b41617094aa9
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503383"
---
# <a name="caccesstoken-class"></a>Caccesstoken, classe

Cette classe est un wrapper pour un jeton d’accès.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAccessToken
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAccessToken :: ~ CAccessToken](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAccessToken::Attach](#attach)|Appelez cette méthode pour s’approprier le handle de jeton d’accès donné.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Appelez cette méthode pour déterminer si un SID spécifique est activé dans le `CAccessToken` objet.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Appelez cette méthode pour créer un nouveau jeton d’accès de l’emprunt d’identité.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Appelez cette méthode pour créer un jeton principal.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Appelez cette méthode pour créer un nouveau processus en cours d’exécution dans le contexte de sécurité de l’utilisateur représenté par le `CAccessToken` objet.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Appelez cette méthode pour créer un nouveau restreint `CAccessToken` objet.|
|[CAccessToken::Detach](#detach)|Appelez cette méthode pour révoquer la propriété du jeton d’accès.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Appelez cette méthode pour désactiver un privilège dans le `CAccessToken` objet.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Appelez cette méthode pour désactiver un ou plusieurs privilèges dans le `CAccessToken` objet.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Appelez cette méthode pour activer un privilège dans le `CAccessToken` objet.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Appelez cette méthode pour activer un ou plusieurs privilèges dans le `CAccessToken` objet.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Appelez cette méthode pour retourner le `CAccessToken` l’objet par défaut DACL.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Appelez cette méthode pour obtenir le `CAccessToken` objet égale au jeton d’accès en vigueur pour le thread actuel.|
|[CAccessToken::GetGroups](#getgroups)|Appelez cette méthode pour retourner le `CAccessToken` groupes de jeton de l’objet.|
|[CAccessToken::GetHandle](#gethandle)|Appelez cette méthode pour récupérer un handle vers le jeton d’accès.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Appelez cette méthode pour obtenir le niveau d’emprunt d’identité dans le jeton d’accès.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Appelez cette méthode pour obtenir l’ID de Session d’ouverture de session associé à la `CAccessToken` objet.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Appelez cette méthode pour obtenir le SID d’ouverture de session associé à la `CAccessToken` objet.|
|[CAccessToken::GetOwner](#getowner)|Appelez cette méthode pour obtenir le propriétaire associé à la `CAccessToken` objet.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Appelez cette méthode pour obtenir le groupe principal associé à la `CAccessToken` objet.|
|[CAccessToken::GetPrivileges](#getprivileges)|Appelez cette méthode pour obtenir les privilèges associés le `CAccessToken` objet.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Appelez cette méthode pour initialiser le `CAccessToken` avec le jeton d’accès à partir du processus donné.|
|[CAccessToken::GetProfile](#getprofile)|Appelez cette méthode pour obtenir le handle pointant vers le profil utilisateur associé à la `CAccessToken` objet.|
|[CAccessToken::GetSource](#getsource)|Appelez cette méthode pour obtenir la source de la `CAccessToken` objet.|
|[CAccessToken::GetStatistics](#getstatistics)|Appelez cette méthode pour obtenir des informations associées à la `CAccessToken` objet.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Appelez cette méthode pour obtenir l’ID de Session des Services Terminal Server associé à la `CAccessToken` objet.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Appelez cette méthode pour initialiser le `CAccessToken` avec le jeton à partir du thread donné.|
|[CAccessToken::GetTokenId](#gettokenid)|Appelez cette méthode pour obtenir l’ID de jeton associé à le `CAccessToken` objet.|
|[CAccessToken::GetType](#gettype)|Appelez cette méthode pour obtenir le type de jeton de la `CAccessToken` objet.|
|[CAccessToken::GetUser](#getuser)|Appelez cette méthode pour identifier l’utilisateur associé à la `CAccessToken` objet.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Appelez cette méthode pour obtenir le handle pointant vers le profil utilisateur associé à la `CAccessToken` objet.|
|[CAccessToken::Impersonate](#impersonate)|Appelez cette méthode pour affecter un emprunt d’identité `CAccessToken` à un thread.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Appelez cette méthode pour permettre au thread appelant de l’identité du contexte de sécurité d’un utilisateur connecté.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Appelez cette méthode pour tester si le `CAccessToken` objet contient une liste de SID restreint.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Appelez cette méthode pour charger le profil utilisateur associé à la `CAccessToken` objet.|
|[CAccessToken::LogonUser](#logonuser)|Appelez cette méthode pour créer une ouverture de session pour l’utilisateur associé les informations d’identification fournies.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Appelez cette méthode à partir d’un serveur COM traite un appel à partir d’un client pour initialiser le `CAccessToken` avec le jeton d’accès à partir du client COM.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Appelez cette méthode à partir d’un serveur prise de demandes via un canal nommé pour initialiser le `CAccessToken` avec le jeton d’accès à partir du client.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Appelez cette méthode à partir d’un serveur qui traite un appel à partir d’un client RPC pour initialiser le `CAccessToken` avec le jeton d’accès à partir du client.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Appelez cette méthode pour définir le niveau d’emprunt d’identité, puis initialisez le `CAccessToken` avec le jeton à partir du thread donné.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Appelez cette méthode pour déterminer si un jeu défini de privilèges sont activés dans le `CAccessToken` objet.|
|[CAccessToken::Revert](#revert)|Appelez cette méthode pour arrêter un thread qui utilise un jeton d’emprunt d’identité.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Appelez cette méthode pour définir la valeur par défaut DACL de le `CAccessToken` objet.|
|[CAccessToken::SetOwner](#setowner)|Appelez cette méthode pour définir le propriétaire de la `CAccessToken` objet.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Appelez cette méthode pour définir le groupe principal de le `CAccessToken` objet.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/desktop/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou un thread et est alloué à chaque utilisateur connecté à un système Windows.

Pour une présentation du modèle de contrôle d’accès dans Windows, consultez [contrôle d’accès](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h

##  <a name="attach"></a>  CAccessToken::Attach

Appelez cette méthode pour s’approprier le handle de jeton d’accès donné.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Paramètres

*hToken*<br/>
Handle vers le jeton d’accès.

### <a name="remarks"></a>Notes

Dans les versions debug, une erreur d’assertion se produit si le `CAccessToken` objet dispose déjà de la propriété d’un jeton d’accès.

##  <a name="dtor"></a>  CAccessToken::~CAccessToken

Destructeur.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="checktokenmembership"></a>  CAccessToken::CheckTokenMembership

Appelez cette méthode pour déterminer si un SID spécifique est activé dans le `CAccessToken` objet.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Référence à un [CSid, classe](../../atl/reference/csid-class.md) objet.

*pbIsMember*<br/>
Pointeur vers une variable qui reçoit les résultats de la vérification.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le `CheckTokenMembership` méthode vérifie la présence du SID de l’utilisateur et le SID de groupe du jeton d’accès. Si le SID est présent et a l’attribut SE_GROUP_ENABLED, *pbIsMember* est définie sur TRUE ; sinon, elle est définie sur FALSE.

Dans les versions debug, une erreur d’assertion se produit si *pbIsMember* n’est pas un pointeur valide.

> [!NOTE]
>  Le `CAccessToken` objet doit être un jeton d’emprunt d’identité et pas un jeton principal.

##  <a name="createimpersonationtoken"></a>  CAccessToken::CreateImpersonationToken

Appelez cette méthode pour créer un jeton d’accès de l’emprunt d’identité.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pImp*<br/>
Pointeur vers le nouveau `CAccessToken` objet.

*sil*<br/>
Spécifie un [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) type énuméré qui fournit le niveau d’emprunt d’identité du nouveau jeton.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

`CreateImpersonationToken` appels [DuplicateToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) pour créer un nouveau jeton d’emprunt d’identité.

##  <a name="createprimarytoken"></a>  CAccessToken::CreatePrimaryToken

Appelez cette méthode pour créer un jeton principal.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPri*<br/>
Pointeur vers le nouveau `CAccessToken` objet.

*dwDesiredAccess*<br/>
Spécifie les droits d’accès demandé pour le nouveau jeton. La valeur par défaut, MAXIMUM_ALLOWED, demande tous les droits d’accès qui sont valides pour l’appelant. Consultez [droits d’accès et des masques d’accès](/windows/desktop/SecAuthZ/access-rights-and-access-masks) plus on droits d’accès.

*pTokenAttributes*<br/>
Pointeur vers un [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) structure qui spécifie un descripteur de sécurité pour le nouveau jeton et détermine si les processus enfants peuvent hériter du jeton. Si *pTokenAttributes* est NULL, le jeton Obtient un descripteur de sécurité par défaut et le handle ne peut pas être hérité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

`CreatePrimaryToken` appels [DuplicateTokenEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) pour créer un nouveau jeton principal.

##  <a name="createprocessasuser"></a>  CAccessToken::CreateProcessAsUser

Appelez cette méthode pour créer un nouveau processus en cours d’exécution dans le contexte de sécurité de l’utilisateur représenté par le `CAccessToken` objet.

```
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
Pointeur vers une chaîne se terminant par null qui spécifie le module à exécuter. Ce paramètre ne peut pas être NULL.

*pCommandLine*<br/>
Pointeur vers une chaîne se terminant par null qui spécifie la ligne de commande à exécuter.

*pProcessInformation*<br/>
Pointeur vers un [PROCESS_INFORMATION](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_process_information) structure qui reçoit les informations d’identification sur le nouveau processus.

*pStartupInfo*<br/>
Pointeur vers un [STARTUPINFO](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_startupinfoa) structure qui spécifie la manière dont la fenêtre principale du nouveau processus doit apparaître.

*dwCreationFlags*<br/>
Spécifie des indicateurs supplémentaires qui contrôlent la classe de priorité et de la création du processus. Consultez la fonction Win32 [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera) pour obtenir la liste d’indicateurs.

*bLoadProfile*<br/>
Si la valeur est TRUE, le profil utilisateur est chargé avec [LoadUserProfile](/windows/desktop/api/userenv/nf-userenv-loaduserprofilea).

*pProcessAttributes*<br/>
Pointeur vers un [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) structure qui spécifie un descripteur de sécurité pour le nouveau processus et détermine si les processus enfants peuvent hériter le handle retourné. Si *pProcessAttributes* est NULL, le processus obtient un descripteur de sécurité par défaut et le handle ne peut pas être hérité.

*pThreadAttributes*<br/>
Pointeur vers un [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) structure qui spécifie un descripteur de sécurité pour le nouveau thread et détermine si les processus enfants peuvent hériter le handle retourné. Si *pThreadAttributes* est NULL, le thread obtient un descripteur de sécurité par défaut et le handle ne peut pas être hérité.

*bInherit*<br/>
Indique si le nouveau processus hérite des handles du processus appelant. Si la valeur est TRUE, chaque handle ouvert peut être hérité dans le processus appelant est héritée par le nouveau processus. Handles hérités ont les mêmes privilèges d’accès et la valeur en tant que les handles d’origine.

*pCurrentDirectory*<br/>
Pointeur vers une chaîne se terminant par null qui spécifie le lecteur actuel et le répertoire du nouveau processus. La chaîne doit être un chemin d’accès complet qui inclut une lettre de lecteur. Si ce paramètre est NULL, le nouveau processus aura le même lecteur actuel et le répertoire en tant que le processus appelant.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

`CreateProcessAsUser` utilise le `CreateProcessAsUser` fonction Win32 pour créer un nouveau processus qui s’exécute dans le contexte de sécurité de l’utilisateur représenté par le `CAccessToken` objet. Consultez la description de la [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera) fonction pour obtenir une présentation complète des paramètres requis.

Pour que cette méthode réussisse, le `CAccessToken` objet doit contenir AssignPrimaryToken (sauf s’il s’agit d’un jeton restreint) et les privilèges de IncreaseQuota.

##  <a name="createrestrictedtoken"></a>  CAccessToken::CreateRestrictedToken

Appelez cette méthode pour créer un nouveau restreint `CAccessToken` objet.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pRestrictedToken*<br/>
Restreint la nouvelle `CAccessToken` objet.

*SidsToDisable*<br/>
Un `CTokenGroups` objet qui spécifie le SID en refus seul.

*SidsToRestrict*<br/>
Un `CTokenGroups` objet qui spécifie le SID restreints.

*PrivilegesToDelete*<br/>
Un `CTokenPrivileges` objet qui spécifie les privilèges à supprimer dans le jeton restreint. La valeur par défaut crée un objet vide.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

`CreateRestrictedToken` utilise le [CreateRestrictedToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) fonction Win32 pour créer un nouveau `CAccessToken` objet, avec des restrictions.

> [!IMPORTANT]
>  Lorsque vous utilisez `CreateRestrictedToken`, vérifiez les éléments suivants : le jeton existant est valide (et non entré par l’utilisateur) et *SidsToDisable* et *PrivilegesToDelete* sont valides (et non entré par l’utilisateur). Si la méthode retourne FALSE, refuser les fonctionnalités.

##  <a name="detach"></a>  CAccessToken::Detach

Appelez cette méthode pour révoquer la propriété du jeton d’accès.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le handle pour le `CAccessToken` qui a été détaché.

### <a name="remarks"></a>Notes

Cette méthode révoque le `CAccessToken`de la propriété du jeton d’accès.

##  <a name="disableprivilege"></a>  CAccessToken::DisablePrivilege

Appelez cette méthode pour désactiver un privilège dans le `CAccessToken` objet.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne contenant le privilège à désactiver dans le `CAccessToken` objet.

*pPreviousState*<br/>
Pointeur vers un `CTokenPrivileges` objet qui contient l’état précédent des privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="disableprivileges"></a>  CAccessToken::DisablePrivileges

Appelez cette méthode pour désactiver un ou plusieurs privilèges dans le `CAccessToken` objet.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*<br/>
Pointeur vers un tableau de chaînes contenant les privilèges à désactiver dans le `CAccessToken` objet.

*pPreviousState*<br/>
Pointeur vers un `CTokenPrivileges` objet qui contient l’état précédent des privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="enableprivilege"></a>  CAccessToken::EnablePrivilege

Appelez cette méthode pour activer un privilège dans le `CAccessToken` objet.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne contenant le privilège d’activer dans le `CAccessToken` objet.

*pPreviousState*<br/>
Pointeur vers un `CTokenPrivileges` objet qui contient l’état précédent des privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="enableprivileges"></a>  CAccessToken::EnablePrivileges

Appelez cette méthode pour activer un ou plusieurs privilèges dans le `CAccessToken` objet.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*<br/>
Pointeur vers un tableau de chaînes contenant les privilèges pour activer dans le `CAccessToken` objet.

*pPreviousState*<br/>
Pointeur vers un `CTokenPrivileges` objet qui contient l’état précédent des privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="getdefaultdacl"></a>  CAccessToken::GetDefaultDacl

Appelez cette méthode pour retourner le `CAccessToken` l’objet par défaut DACL.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pDacl*<br/>
Pointeur vers le [CDacl, classe](../../atl/reference/cdacl-class.md) objet qui reçoit le `CAccessToken` l’objet par défaut DACL.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la liste DACL par défaut a été récupérée, FALSE sinon.

##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken

Appelez cette méthode pour obtenir le `CAccessToken` objet égale au jeton d’accès en vigueur pour le thread actuel.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès au jeton d’accès demandés. Ces types d’accès demandés sont comparées aux DACL du jeton pour déterminer qui accède aux est accordées ou refusées.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="getgroups"></a>  CAccessToken::GetGroups

Appelez cette méthode pour retourner le `CAccessToken` groupes de jeton de l’objet.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pGroups*<br/>
Pointeur vers le [CTokenGroups, classe](../../atl/reference/ctokengroups-class.md) objet qui reçoit les informations de groupe.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="gethandle"></a>  CAccessToken::GetHandle

Appelez cette méthode pour récupérer un handle vers le jeton d’accès.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un handle vers la `CAccessToken` jeton d’accès de l’objet.

##  <a name="getimpersonationlevel"></a>  CAccessToken::GetImpersonationLevel

Appelez cette méthode pour obtenir le niveau d’emprunt d’identité dans le jeton d’accès.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pImpersonationLevel*<br/>
Pointeur vers un [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) type d’énumération qui recevront les informations au niveau d’emprunt d’identité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="getlogonsessionid"></a>  CAccessToken::GetLogonSessionId

Appelez cette méthode pour obtenir l’ID de Session d’ouverture de session associé à la `CAccessToken` objet.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pluid*<br/>
Pointeur vers un [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) qui reçoit l’ID de Session d’ouverture de session.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions debug, une erreur d’assertion se produit si *pluid* est une valeur non valide.

##  <a name="getlogonsid"></a>  CAccessToken::GetLogonSid

Appelez cette méthode pour obtenir le SID d’ouverture de session associé à la `CAccessToken` objet.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un [CSid, classe](../../atl/reference/csid-class.md) objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions debug, une erreur d’assertion se produit si *pSid* est une valeur non valide.

##  <a name="getowner"></a>  CAccessToken::GetOwner

Appelez cette méthode pour obtenir le propriétaire associé à la `CAccessToken` objet.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un [CSid, classe](../../atl/reference/csid-class.md) objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le propriétaire est défini par défaut sur tous les objets créés alors que ce jeton d’accès est en vigueur.

##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup

Appelez cette méthode pour obtenir le groupe principal associé à la `CAccessToken` objet.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un [CSid, classe](../../atl/reference/csid-class.md) objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le groupe est défini par défaut sur tous les objets créés alors que ce jeton d’accès est en vigueur.

##  <a name="getprivileges"></a>  CAccessToken::GetPrivileges

Appelez cette méthode pour obtenir les privilèges associés le `CAccessToken` objet.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPrivileges*<br/>
Pointeur vers un [CTokenPrivileges, classe](../../atl/reference/ctokenprivileges-class.md) objet qui recevra les privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="getprocesstoken"></a>  CAccessToken::GetProcessToken

Appelez cette méthode pour initialiser le `CAccessToken` avec le jeton d’accès à partir du processus donné.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès au jeton d’accès demandés. Ces types d’accès demandés sont comparées aux DACL du jeton pour déterminer qui accède aux est accordées ou refusées.

*hProcess*<br/>
Handle vers le processus dont le jeton d’accès est ouvert. Si la valeur NULL comme valeur par défaut est utilisée, le processus en cours est utilisé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Appelle le [OpenProcessToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) fonction Win32.

##  <a name="getprofile"></a>  CAccessToken::GetProfile

Appelez cette méthode pour obtenir le handle pointant vers le profil utilisateur associé à la `CAccessToken` objet.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un handle pointant vers le profil utilisateur, ou NULL si aucun profil n’existe.

##  <a name="getsource"></a>  CAccessToken::GetSource

Appelez cette méthode pour obtenir la source de la `CAccessToken` objet.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSource*<br/>
Pointeur vers un [TOKEN_SOURCE](/windows/desktop/api/winnt/ns-winnt-_token_source) structure.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="getstatistics"></a>  CAccessToken::GetStatistics

Appelez cette méthode pour obtenir des informations associées à la `CAccessToken` objet.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pStatistics*<br/>
Pointeur vers un [TOKEN_STATISTICS](/windows/desktop/api/winnt/ns-winnt-_token_statistics) structure.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId

Appelez cette méthode pour obtenir l’ID de Session des Services Terminal Server associé à la `CAccessToken` objet.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pdwSessionId*<br/>
L’ID de Session des Services Terminal Server.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="getthreadtoken"></a>  CAccessToken::GetThreadToken

Appelez cette méthode pour initialiser le `CAccessToken` avec le jeton à partir du thread donné.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès au jeton d’accès demandés. Ces types d’accès demandés sont comparées aux DACL du jeton pour déterminer qui accède aux est accordées ou refusées.

*hThread*<br/>
Handle vers le thread dont le jeton d’accès est ouvert.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée par rapport au contexte de sécurité de l’appel de thread la `GetThreadToken` méthode ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre est FALSE, la vérification d’accès est effectuée à l’aide du contexte de sécurité pour le thread appelant. Si le thread emprunte un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est TRUE, la vérification d’accès est effectuée à l’aide du contexte de sécurité du processus pour le thread appelant.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="gettokenid"></a>  CAccessToken::GetTokenId

Appelez cette méthode pour obtenir l’ID de jeton associé à le `CAccessToken` objet.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pluid*<br/>
Pointeur vers un [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) qui recevra le jeton ID.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="gettype"></a>  CAccessToken::GetType

Appelez cette méthode pour obtenir le type de jeton de la `CAccessToken` objet.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pType*<br/>
Adresse de la [TOKEN_TYPE](/windows/desktop/api/winnt/ne-winnt-_token_type) variable qui, en cas de réussite, reçoit le type du jeton.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le type d’énumération TOKEN_TYPE contient des valeurs qui faire la distinction entre un jeton principal et un jeton d’emprunt d’identité.

##  <a name="getuser"></a>  CAccessToken::GetUser

Appelez cette méthode pour identifier l’utilisateur associé à la `CAccessToken` objet.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un [CSid, classe](../../atl/reference/csid-class.md) objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="hkeycurrentuser"></a>  CAccessToken::HKeyCurrentUser

Appelez cette méthode pour obtenir le handle pointant vers le profil utilisateur associé à la `CAccessToken` objet.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un handle pointant vers le profil utilisateur, ou NULL si aucun profil n’existe.

##  <a name="impersonate"></a>  CAccessToken::Impersonate

Appelez cette méthode pour affecter un emprunt d’identité `CAccessToken` à un thread.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*hThread*<br/>
Pointeur vers le thread pour affecter le jeton d’emprunt d’identité. Ce handle doit avoir été ouvert avec des droits d’accès TOKEN_IMPERSONATE. Si *hThread* est NULL, la méthode provoque le thread pour arrêter à l’aide d’un jeton d’emprunt d’identité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions debug, une erreur d’assertion se produit si `CAccessToken` n’a pas un pointeur valide vers un jeton.

Le [cautorevertimpersonation, classe](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisé pour rétablir automatiquement les jetons d’accès avec emprunt d’identité.

##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser

Appelez cette méthode pour permettre au thread appelant de l’identité du contexte de sécurité d’un utilisateur connecté.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

> [!IMPORTANT]
>  Si un appel à une fonction de l’emprunt d’identité échoue pour une raison quelconque, le client n’est pas empruntée et la demande du client est effectuée dans le contexte de sécurité du processus à partir de laquelle l’appel a été effectué. Si le processus s’exécute sous un compte disposant de privilèges élevés, ou en tant que membre d’un groupe d’administration, l’utilisateur peut être en mesure d’effectuer des actions qu’il est sinon interdite. Par conséquent, la valeur de retour pour cette fonction doit toujours être confirmée.

##  <a name="istokenrestricted"></a>  CAccessToken::IsTokenRestricted

Appelez cette méthode pour tester si le `CAccessToken` objet contient une liste de SID restreint.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE si l’objet contient une liste de restriction des SID, FALSE s’il en existe aucun SID restreints ou si la méthode échoue.

##  <a name="loaduserprofile"></a>  CAccessToken::LoadUserProfile

Appelez cette méthode pour charger le profil utilisateur associé à la `CAccessToken` objet.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions debug, une erreur d’assertion se produit si le `CAccessToken` ne contient pas un jeton valide, ou si un utilisateur de profil déjà existe.

##  <a name="logonuser"></a>  CAccessToken::LogonUser

Appelez cette méthode pour créer une ouverture de session pour l’utilisateur associé les informations d’identification fournies.

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>Paramètres

*pszUserName*<br/>
Pointeur vers une chaîne se terminant par null qui spécifie le nom d’utilisateur. Il s’agit du nom du compte d’utilisateur pour vous connecter au.

*pszDomain*<br/>
Pointeur vers une chaîne se terminant par null qui spécifie le nom de domaine ou du serveur de base de données dont compte contient le *pszUserName* compte.

*pszPassword*<br/>
Pointeur vers une chaîne se terminant par null qui spécifie le mot de passe en texte clair pour le compte d’utilisateur spécifié par *pszUserName*.

*dwLogonType*<br/>
Spécifie le type d’opération d’ouverture de session à effectuer. Consultez [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) pour plus d’informations.

*dwLogonProvider*<br/>
Spécifie le fournisseur d’ouverture de session. Consultez [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) pour plus d’informations.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

L’accès au jeton résultant de l’ouverture de session sera associé le `CAccessToken`. Pour que cette méthode réussisse, le `CAccessToken` objet détenir des privilèges SE_TCB_NAME, identifiant le détenteur du cadre de l’ordinateur approuvé base. Consultez [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) pour plus d’informations sur les privilèges requis.

##  <a name="opencomclienttoken"></a>  CAccessToken::OpenCOMClientToken

Appelez cette méthode à partir d’un serveur COM traite un appel à partir d’un client pour initialiser le `CAccessToken` avec le jeton d’accès à partir du client COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès au jeton d’accès demandés. Ces types d’accès demandés sont comparées aux DACL du jeton pour déterminer qui accède aux est accordées ou refusées.

*bImpersonate*<br/>
Si la valeur est TRUE, le thread actuel emprunte l’identité du client COM appelant si cet appel se termine correctement. Si la valeur est FALSE, le jeton d’accès doit être ouvert, mais le thread n’aura pas un jeton d’emprunt d’identité à l’issue de cet appel.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée par rapport au contexte de sécurité de l’appel de thread la [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) (méthode) ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre est FALSE, la vérification d’accès est effectuée à l’aide du contexte de sécurité pour le thread appelant. Si le thread emprunte un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est TRUE, la vérification d’accès est effectuée à l’aide du contexte de sécurité du processus pour le thread appelant.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le [cautorevertimpersonation, classe](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisé pour rétablir automatiquement les jetons d’accès avec emprunt d’identité créés en définissant le *bImpersonate* indicateur sur TRUE.

##  <a name="opennamedpipeclienttoken"></a>  CAccessToken::OpenNamedPipeClientToken

Appelez cette méthode à partir d’un serveur prise de demandes via un canal nommé pour initialiser le `CAccessToken` avec le jeton d’accès à partir du client.

```
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
Spécifie un masque d’accès qui spécifie les types d’accès au jeton d’accès demandés. Ces types d’accès demandés sont comparées aux DACL du jeton pour déterminer qui accède aux est accordées ou refusées.

*bImpersonate*<br/>
Si la valeur est TRUE, le thread actuel emprunte l’identité du client appelant de canal si cet appel se termine correctement. Si la valeur est FALSE, le jeton d’accès doit être ouvert, mais le thread n’aura pas un jeton d’emprunt d’identité à l’issue de cet appel.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée par rapport au contexte de sécurité de l’appel de thread la [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) (méthode) ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre est FALSE, la vérification d’accès est effectuée à l’aide du contexte de sécurité pour le thread appelant. Si le thread emprunte un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est TRUE, la vérification d’accès est effectuée à l’aide du contexte de sécurité du processus pour le thread appelant.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le [cautorevertimpersonation, classe](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisé pour rétablir automatiquement les jetons d’accès avec emprunt d’identité créés en définissant le *bImpersonate* indicateur sur TRUE.

##  <a name="openrpcclienttoken"></a>  CAccessToken::OpenRPCClientToken

Appelez cette méthode à partir d’un serveur qui traite un appel à partir d’un client RPC pour initialiser le `CAccessToken` avec le jeton d’accès à partir du client.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*BindingHandle*<br/>
Handle de la liaison sur le serveur qui représente une liaison à un client.

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès au jeton d’accès demandés. Ces types d’accès demandés sont comparées aux DACL du jeton pour déterminer qui accède aux est accordées ou refusées.

*bImpersonate*<br/>
Si la valeur est TRUE, le thread actuel emprunte l’identité du client RPC si cet appel se termine correctement. Si la valeur est FALSE, le jeton d’accès doit être ouvert, mais le thread n’aura pas un jeton d’emprunt d’identité à l’issue de cet appel.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée par rapport au contexte de sécurité de l’appel de thread la [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) (méthode) ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre est FALSE, la vérification d’accès est effectuée à l’aide du contexte de sécurité pour le thread appelant. Si le thread emprunte un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est TRUE, la vérification d’accès est effectuée à l’aide du contexte de sécurité du processus pour le thread appelant.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le [cautorevertimpersonation, classe](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisé pour rétablir automatiquement les jetons d’accès avec emprunt d’identité créés en définissant le *bImpersonate* indicateur sur TRUE.

##  <a name="openthreadtoken"></a>  CAccessToken::OpenThreadToken

Appelez cette méthode pour définir le niveau d’emprunt d’identité, puis initialisez le `CAccessToken` avec le jeton à partir du thread donné.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès au jeton d’accès demandés. Ces types d’accès demandés sont comparées aux DACL du jeton pour déterminer qui accède aux est accordées ou refusées.

*bImpersonate*<br/>
Si la valeur est TRUE, le thread sera conservé au niveau d’emprunt d’identité demandé une fois que cette méthode se termine. Si la valeur est FALSE, le thread reviendra à son niveau d’emprunt d’identité d’origine.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée par rapport au contexte de sécurité de l’appel de thread la [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) (méthode) ou par rapport au contexte de sécurité du processus pour le thread appelant.

Si ce paramètre est FALSE, la vérification d’accès est effectuée à l’aide du contexte de sécurité pour le thread appelant. Si le thread emprunte un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est TRUE, la vérification d’accès est effectuée à l’aide du contexte de sécurité du processus pour le thread appelant.

*sil*<br/>
Spécifie un [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) type énuméré qui fournit le niveau d’emprunt d’identité du jeton.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

`OpenThreadToken` est similaire à [CAccessToken::GetThreadToken](#getthreadtoken), mais définit le niveau d’emprunt d’identité avant d’initialiser le `CAccessToken` à partir du jeton d’accès du thread.

Le [cautorevertimpersonation, classe](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisé pour rétablir automatiquement les jetons d’accès avec emprunt d’identité créés en définissant le *bImpersonate* indicateur sur TRUE.

##  <a name="privilegecheck"></a>  CAccessToken::PrivilegeCheck

Appelez cette méthode pour déterminer si un jeu défini de privilèges sont activés dans le `CAccessToken` objet.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Paramètres

*RequiredPrivileges*<br/>
Pointeur vers un [PRIVILEGE_SET](/windows/desktop/api/winnt/ns-winnt-_privilege_set) structure.

*pbResult*<br/>
Pointeur vers une valeur de la méthode définit pour indiquer si tout ou partie du privilège spécifié sont activés dans le `CAccessToken` objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Lorsque `PrivilegeCheck` retourne, le `Attributes` membre de chaque [LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes) structure est définie à SE_PRIVILEGE_USED_FOR_ACCESS si le privilège correspondant est activé. Cette méthode appelle la [PrivilegeCheck](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-privilegecheck) fonction Win32.

##  <a name="revert"></a>  CAccessToken::Revert

Appelez cette méthode pour arrêter un thread à l’aide d’un jeton d’emprunt d’identité.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*hThread*<br/>
Handle du thread pour restaurer à partir de l’emprunt d’identité. Si *hThread* est NULL, le thread actuel est supposé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le rétablissement de jetons de l’emprunt d’identité peut être effectué automatiquement avec le [cautorevertimpersonation, classe](../../atl/reference/cautorevertimpersonation-class.md).

##  <a name="setdefaultdacl"></a>  CAccessToken::SetDefaultDacl

Appelez cette méthode pour définir la valeur par défaut DACL de le `CAccessToken` objet.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Paramètres

*rDacl*<br/>
La nouvelle valeur par défaut [CDacl, classe](../../atl/reference/cdacl-class.md) plus d’informations.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

La DACL est la liste DACL qui est utilisée par défaut lorsque de nouveaux objets sont créés avec ce jeton d’accès en vigueur.

##  <a name="setowner"></a>  CAccessToken::SetOwner

Appelez cette méthode pour définir le propriétaire de la `CAccessToken` objet.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Le [CSid, classe](../../atl/reference/csid-class.md) objet contenant les informations de propriétaire.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le propriétaire est le propriétaire par défaut qui est utilisé pour les nouveaux objets créés alors que ce jeton d’accès est en vigueur.

##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup

Appelez cette méthode pour définir le groupe principal de le `CAccessToken` objet.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Le [CSid, classe](../../atl/reference/csid-class.md) objet contenant les informations de groupe principal.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le groupe principal est le groupe par défaut pour les nouveaux objets créés alors que ce jeton d’accès est en vigueur.

## <a name="see-also"></a>Voir aussi

[Exemple ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Jetons d’accès](/windows/desktop/SecAuthZ/access-tokens)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
