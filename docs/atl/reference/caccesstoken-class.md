---
title: Classe CAccessToken
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
ms.openlocfilehash: 9ae63946dfa6244e97c376f9eccd9bab93586990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319040"
---
# <a name="caccesstoken-class"></a>Classe CAccessToken

Cette classe est un emballage pour un jeton d’accès.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAccessToken
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAccessToken: :CAccessToken](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAccessToken::Attach](#attach)|Appelez cette méthode pour prendre possession de la poignée de jet d’accès donnée.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Appelez cette méthode pour déterminer si un `CAccessToken` PEID spécifié est activé dans l’objet.|
|[CAccessToken::CréerImpersonationToken](#createimpersonationtoken)|Appelez cette méthode pour créer un nouveau jeton d’accès à l’imitation.|
|[CAccessToken::CréerPrimaryToken](#createprimarytoken)|Appelez cette méthode pour créer un nouveau jeton primaire.|
|[CAccessToken::CréerProcessAsUser](#createprocessasuser)|Appelez cette méthode pour créer un nouveau processus en cours `CAccessToken` d’exécution dans le contexte de sécurité de l’utilisateur représenté par l’objet.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Appelez cette méthode pour créer `CAccessToken` un nouvel objet restreint.|
|[CAccessToken::Detach](#detach)|Appelez cette méthode pour révoquer la propriété du jeton d’accès.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Appelez cette méthode pour désactiver `CAccessToken` un privilège dans l’objet.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Appelez cette méthode pour désactiver un ou `CAccessToken` plusieurs privilèges dans l’objet.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Appelez cette méthode pour permettre `CAccessToken` un privilège dans l’objet.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Appelez cette méthode pour activer un `CAccessToken` ou plusieurs privilèges dans l’objet.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Appelez cette méthode `CAccessToken` pour retourner le DACL par défaut de l’objet.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Appelez cette méthode `CAccessToken` pour obtenir l’objet égal au jeton d’accès en vigueur pour le thread actuel.|
|[CAccessToken::GetGroups](#getgroups)|Appelez cette méthode `CAccessToken` pour retourner les groupes symboliques de l’objet.|
|[CAccessToken::GetHandle](#gethandle)|Appelez cette méthode pour récupérer une poignée au jeton d’accès.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Appelez cette méthode pour obtenir le niveau d’usurpation d’identité à partir du jeton d’accès.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Appelez cette méthode pour obtenir l’ID `CAccessToken` de session Logon associé à l’objet.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Appelez cette méthode pour obtenir le `CAccessToken` site d’évitement Logon associé à l’objet.|
|[CAccessToken::GetOwner](#getowner)|Appelez cette méthode pour obtenir `CAccessToken` le propriétaire associé à l’objet.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Appelez cette méthode pour obtenir le `CAccessToken` groupe principal associé à l’objet.|
|[CAccessToken::GetPrivileges](#getprivileges)|Appelez cette méthode pour obtenir les `CAccessToken` privilèges associés à l’objet.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Appelez cette méthode pour `CAccessToken` initialiser le jeton d’accès du processus donné.|
|[CAccessToken::GetProfile](#getprofile)|Appelez cette méthode pour obtenir la poignée pointant vers le profil utilisateur associé à l’objet. `CAccessToken`|
|[CAccessToken::GetSource](#getsource)|Appelez cette méthode pour obtenir `CAccessToken` la source de l’objet.|
|[CAccessToken::GetStatistics](#getstatistics)|Appelez cette méthode pour obtenir `CAccessToken` des informations associées à l’objet.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Appelez cette méthode pour obtenir l’ID `CAccessToken` de session de services terminaux associé à l’objet.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Appelez cette méthode pour `CAccessToken` initialiser le jeton à partir du fil donné.|
|[CAccessToken::GetTokenId](#gettokenid)|Appelez cette méthode pour obtenir l’ID jeton associé à l’objet. `CAccessToken`|
|[CAccessToken::GetType](#gettype)|Appelez cette méthode pour obtenir le `CAccessToken` type symbolique de l’objet.|
|[CAccessToken::GetUser](#getuser)|Appelez cette méthode pour identifier `CAccessToken` l’utilisateur associé à l’objet.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Appelez cette méthode pour obtenir la poignée pointant vers le profil utilisateur associé à l’objet. `CAccessToken`|
|[CAccessToken::Impersonate](#impersonate)|Appelez cette méthode pour `CAccessToken` attribuer une usurpation d’identité à un thread.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Appelez cette méthode pour permettre au thread d’appel d’usurper l’identité du contexte de sécurité d’un utilisateur connecté.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Appelez cette méthode pour `CAccessToken` tester si l’objet contient une liste de SID restreints.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Appelez cette méthode pour charger le `CAccessToken` profil utilisateur associé à l’objet.|
|[CAccessToken::LogonUser](#logonuser)|Appelez cette méthode pour créer une session logon pour l’utilisateur associé aux informations d’identification données.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Appelez cette méthode à partir d’un serveur COM `CAccessToken` traitant un appel d’un client pour initialiser le jeton d’accès du client COM.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Appelez cette méthode à l’intérieur d’un serveur `CAccessToken` en prenant des demandes sur un tuyau nommé pour initialiser le jeton d’accès du client.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Appelez cette méthode à partir d’un serveur traitant un `CAccessToken` appel d’un client RPC pour initialiser le avec le jeton d’accès du client.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Appelez cette méthode pour définir le niveau `CAccessToken` d’usurpation d’identité, puis initialiser le jeton à partir du fil donné.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Appelez cette méthode pour déterminer si un ensemble `CAccessToken` précis de privilèges sont activés dans l’objet.|
|[CAccessToken::Revert](#revert)|Appelez cette méthode pour arrêter un thread qui utilise un jeton d’imitation.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Appelez cette méthode pour définir le `CAccessToken` DACL par défaut de l’objet.|
|[CAccessToken::SetOwner](#setowner)|Appelez cette méthode pour définir `CAccessToken` le propriétaire de l’objet.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Appelez cette méthode pour définir `CAccessToken` le groupe principal de l’objet.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/win32/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou d’un thread et qui est attribué à chaque utilisateur connecté à un système Windows.

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken::Attach

Appelez cette méthode pour prendre possession de la poignée de jet d’accès donnée.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Paramètres

*hToken*<br/>
Une poignée au jeton d’accès.

### <a name="remarks"></a>Notes

Dans les constructions de débog, `CAccessToken` une erreur d’affirmation se produira si l’objet a déjà la propriété d’un jeton d’accès.

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken: :CAccessToken

Destructeur.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership

Appelez cette méthode pour déterminer si un `CAccessToken` PEID spécifié est activé dans l’objet.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Référence à un objet [de classe CSid.](../../atl/reference/csid-class.md)

*pbIsMember*<br/>
Pointeur vers une variable qui reçoit les résultats de la vérification.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

La `CheckTokenMembership` méthode vérifie la présence du SID dans les SID de l’utilisateur et du groupe du jeton d’accès. Si le SID est présent et a l’attribut SE_GROUP_ENABLED, *pbIsMember* est réglé sur TRUE; autrement, il est réglé sur FALSE.

Dans les constructions de débog, une erreur d’affirmation se produira si *pbIsMember n’est* pas un pointeur valide.

> [!NOTE]
> L’objet `CAccessToken` doit être un jeton d’imitation et non un jeton primaire.

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken::CréerImpersonationToken

Appelez cette méthode pour créer un jeton d’accès à l’imitation.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Paramètres

*Pimp*<br/>
Pointeur vers `CAccessToken` le nouvel objet.

*Sil*<br/>
Spécifie un [type SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) énuméré qui fournit le niveau d’usurpation d’identité du nouveau jeton.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

`CreateImpersonationToken`appelle [DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) pour créer un nouveau jeton d’imitation.

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken::CréerPrimaryToken

Appelez cette méthode pour créer un nouveau jeton primaire.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPri (en)*<br/>
Pointeur vers `CAccessToken` le nouvel objet.

*dwDesiredAccess*<br/>
Spécifie les droits d’accès demandés pour le nouveau jeton. Le défaut, MAXIMUM_ALLOWED, demande tous les droits d’accès qui sont valables pour l’appelant. Voir [les droits d’accès et les masques d’accès](/windows/win32/SecAuthZ/access-rights-and-access-masks) pour en savoir plus sur les droits d’accès.

*pTokenAttributes*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie un descripteur de sécurité pour le nouveau jeton et détermine si les processus de l’enfant peuvent hériter du jeton. Si *pTokenAttributes* est NULL, le jeton obtient un descripteur de sécurité par défaut et la poignée ne peut pas être héritée.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

`CreatePrimaryToken`appelle [DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) pour créer un nouveau jeton primaire.

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken::CréerProcessAsUser

Appelez cette méthode pour créer un nouveau processus en cours `CAccessToken` d’exécution dans le contexte de sécurité de l’utilisateur représenté par l’objet.

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
Pointeur vers une chaîne non terminée qui spécifie le module à exécuter. Ce paramètre peut ne pas être NULL.

*pCommandLine (en)*<br/>
Pointeur vers une chaîne non terminée qui spécifie la ligne de commande à exécuter.

*pProcessInformation*<br/>
Pointeur vers une [structure PROCESS_INFORMATION](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) qui reçoit des informations d’identification sur le nouveau processus.

*pStartupInfo (en anglais)*<br/>
Pointeur vers une structure [STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) qui spécifie comment la fenêtre principale du nouveau processus devrait apparaître.

*dwCreationFlags dwCreationFlags dwCreationFlags*<br/>
Spécifie des drapeaux supplémentaires qui contrôlent la classe prioritaire et la création du processus. Consultez la fonction Win32 [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) pour une liste de drapeaux.

*bLoadProfile (en)*<br/>
Si VRAI, le profil de l’utilisateur est chargé de [LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew).

*pProcessAttributes*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie un descripteur de sécurité pour le nouveau processus et détermine si les processus de l’enfant peuvent hériter de la poignée retournée. Si *pProcessAttributes* est NULL, le processus obtient un descripteur de sécurité par défaut et la poignée ne peut pas être héritée.

*pThreadAttributes*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui spécifie un descripteur de sécurité pour le nouveau thread et détermine si les processus de l’enfant peuvent hériter de la poignée retournée. Si *pThreadAttributes* est NULL, le thread obtient un descripteur de sécurité par défaut et la poignée ne peut pas être héritée.

*bInherit*<br/>
Indique si le nouveau processus hérite des poignées du processus d’appel. Si VRAI, chaque poignée ouverte héréditaire dans le processus d’appel est héritée par le nouveau processus. Les poignées héritées ont la même valeur et les mêmes privilèges d’accès que les poignées d’origine.

*pCurrentDirectory (en)*<br/>
Pointeur vers une chaîne non terminée qui spécifie le lecteur actuel et l’annuaire pour le nouveau processus. La chaîne doit être un chemin complet qui comprend une lettre d’entraînement. Si ce paramètre est NULL, le nouveau processus aura le même lecteur actuel et répertoire que le processus d’appel.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

`CreateProcessAsUser`utilise `CreateProcessAsUser` la fonction Win32 pour créer un nouveau processus qui s’exécute dans le contexte de sécurité de l’utilisateur représenté par l’objet. `CAccessToken` Voir la description de la fonction [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) pour une discussion complète des paramètres requis.

Pour que cette méthode `CAccessToken` réussisse, l’objet doit détenir AssignPrimaryToken (sauf s’il s’agit d’un jeton restreint) et des privilèges IncreaseQuota.

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken

Appelez cette méthode pour créer `CAccessToken` un nouvel objet restreint.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pRestrictedToken*<br/>
Le nouvel `CAccessToken` objet restreint.

*SidsToDisable*<br/>
Un `CTokenGroups` objet qui spécifie les SID sans-seulement.

*SidsToRestrict*<br/>
Un `CTokenGroups` objet qui spécifie les SID restrictifs.

*PrivilègesToDelete*<br/>
Un `CTokenPrivileges` objet qui spécifie les privilèges à supprimer dans le jeton restreint. La valeur par défaut crée un objet vide.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

`CreateRestrictedToken`utilise la fonction [CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 `CAccessToken` pour créer un nouvel objet, avec des restrictions.

> [!IMPORTANT]
> Lors `CreateRestrictedToken`de l’utilisation, assurez-vous que le jeton existant est valide (et non entré par l’utilisateur) et *SidsToDisable* et *PrivilegesToDelete* sont tous deux valides (et non entrés par l’utilisateur). Si la méthode renvoie FALSE, niez la fonctionnalité.

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken::Detach

Appelez cette méthode pour révoquer la propriété du jeton d’accès.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la poignée `CAccessToken` à ce qui a été détaché.

### <a name="remarks"></a>Notes

Cette méthode révoque la `CAccessToken`propriété du jeton d’accès.

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken::DisablePrivilege

Appelez cette méthode pour désactiver `CAccessToken` un privilège dans l’objet.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur à une chaîne contenant le `CAccessToken` privilège de désactiver dans l’objet.

*pPreviousState (en)*<br/>
Pointeur `CTokenPrivileges` vers un objet qui contiendra l’état précédent des privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken::DisablePrivileges

Appelez cette méthode pour désactiver un ou `CAccessToken` plusieurs privilèges dans l’objet.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*<br/>
Pointeur vers un tableau de cordes contenant les `CAccessToken` privilèges de désactiver dans l’objet.

*pPreviousState (en)*<br/>
Pointeur `CTokenPrivileges` vers un objet qui contiendra l’état précédent des privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken::EnablePrivilege

Appelez cette méthode pour permettre `CAccessToken` un privilège dans l’objet.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne contenant `CAccessToken` le privilège d’activer dans l’objet.

*pPreviousState (en)*<br/>
Pointeur `CTokenPrivileges` vers un objet qui contiendra l’état précédent des privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken::EnablePrivileges

Appelez cette méthode pour activer un `CAccessToken` ou plusieurs privilèges dans l’objet.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*<br/>
Pointeur vers un tableau de cordes contenant `CAccessToken` les privilèges à activer dans l’objet.

*pPreviousState (en)*<br/>
Pointeur `CTokenPrivileges` vers un objet qui contiendra l’état précédent des privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl

Appelez cette méthode `CAccessToken` pour retourner le DACL par défaut de l’objet.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pDacl (en)*<br/>
Pointeur vers l’objet de classe `CAccessToken` [CDacl](../../atl/reference/cdacl-class.md) qui recevra le DACL par défaut de l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le DACL par défaut a été récupéré, FALSE autrement.

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken

Appelez cette méthode `CAccessToken` pour obtenir l’objet égal au jeton d’accès en vigueur pour le thread actuel.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés au DACL du jeton pour déterminer quels accès sont accordés ou refusés.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken::GetGroups

Appelez cette méthode `CAccessToken` pour retourner les groupes symboliques de l’objet.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pGroups (en anglais)*<br/>
Pointeur vers l’objet [de classe CTokenGroups](../../atl/reference/ctokengroups-class.md) qui recevra les informations de groupe.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken::GetHandle

Appelez cette méthode pour récupérer une poignée au jeton d’accès.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une poignée `CAccessToken` au jeton d’accès de l’objet.

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel

Appelez cette méthode pour obtenir le niveau d’usurpation d’identité à partir du jeton d’accès.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pImpersonationLevel (en)*<br/>
Pointeur vers un type d’énumération [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) qui recevra les informations de niveau d’usurpation d’identité.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId

Appelez cette méthode pour obtenir l’ID `CAccessToken` de session Logon associé à l’objet.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pluid*<br/>
Pointeur vers un [LUID](/windows/win32/api/winnt/ns-winnt-luid) qui recevra l’ID de session Logon.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Dans les constructions de débogé, une erreur d’affirmation se produira si *pluid* est une valeur invalide.

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken::GetLogonSid

Appelez cette méthode pour obtenir le `CAccessToken` site d’évitement Logon associé à l’objet.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un objet [de classe CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une erreur d’affirmation se produira si *pSid* est une valeur invalide.

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken::GetOwner

Appelez cette méthode pour obtenir `CAccessToken` le propriétaire associé à l’objet.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un objet [de classe CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Le propriétaire est défini par défaut sur tous les objets créés pendant que ce jeton d’accès est en vigueur.

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup

Appelez cette méthode pour obtenir le `CAccessToken` groupe principal associé à l’objet.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un objet [de classe CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Le groupe est défini par défaut sur tous les objets créés pendant que ce jeton d’accès est en vigueur.

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken::GetPrivileges

Appelez cette méthode pour obtenir les `CAccessToken` privilèges associés à l’objet.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPrivileges*<br/>
Pointeur vers un objet [de classe CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md) qui recevra les privilèges.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken::GetProcessToken

Appelez cette méthode pour `CAccessToken` initialiser le jeton d’accès du processus donné.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés au DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*hProcess (en)*<br/>
Gérer le processus dont le jeton d’accès est ouvert. Si la valeur par défaut de NULL est utilisée, le processus actuel est utilisé.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Appelle la fonction [OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32.

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken::GetProfile

Appelez cette méthode pour obtenir la poignée pointant vers le profil utilisateur associé à l’objet. `CAccessToken`

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie une poignée pointant vers le profil utilisateur, ou NULL si aucun profil n’existe.

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken::GetSource

Appelez cette méthode pour obtenir `CAccessToken` la source de l’objet.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSource (en)*<br/>
Pointeur vers une structure [TOKEN_SOURCE.](/windows/win32/api/winnt/ns-winnt-token_source)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken::GetStatistics

Appelez cette méthode pour obtenir `CAccessToken` des informations associées à l’objet.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pStatistique*<br/>
Pointeur vers une structure [TOKEN_STATISTICS.](/windows/win32/api/winnt/ns-winnt-token_statistics)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId

Appelez cette méthode pour obtenir l’ID `CAccessToken` de session de services terminaux associé à l’objet.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pdwSessionId*<br/>
L’ID de session de services terminaux.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken::GetThreadToken

Appelez cette méthode pour `CAccessToken` initialiser le jeton à partir du fil donné.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés au DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*hThread (en)*<br/>
Gérer le fil dont le jeton d’accès est ouvert.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée `GetThreadToken` dans le contexte de sécurité du thread appelant la méthode ou contre le contexte de sécurité du processus pour le thread d’appel.

Si ce paramètre est FALSE, la vérification d’accès est effectuée en utilisant le contexte de sécurité du thread d’appel. Si le thread se fait passer pour un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est VRAI, la vérification d’accès est effectuée en utilisant le contexte de sécurité du processus pour le thread d’appel.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken::GetTokenId

Appelez cette méthode pour obtenir l’ID jeton associé à l’objet. `CAccessToken`

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pluid*<br/>
Pointeur vers un [LUID](/windows/win32/api/winnt/ns-winnt-luid) qui recevra l’ID Jeton.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken::GetType

Appelez cette méthode pour obtenir le `CAccessToken` type symbolique de l’objet.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pType (en)*<br/>
Adresse de la [variable TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type) qui, sur le succès, reçoit le type de jeton.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Le type d’énumération TOKEN_TYPE contient des valeurs qui différencient entre un jeton primaire et un jeton d’imitation.

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken::GetUser

Appelez cette méthode pour identifier `CAccessToken` l’utilisateur associé à l’objet.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un objet [de classe CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser

Appelez cette méthode pour obtenir la poignée pointant vers le profil utilisateur associé à l’objet. `CAccessToken`

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie une poignée pointant vers le profil utilisateur, ou NULL si aucun profil n’existe.

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken::Impersonate

Appelez cette méthode pour `CAccessToken` attribuer une usurpation d’identité à un thread.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*hThread (en)*<br/>
Gérer le fil pour attribuer le jeton d’imitation à. Cette poignée doit avoir été ouverte avec TOKEN_IMPERSONATE droits d’accès. Si *hThread* est NULL, la méthode provoque le thread d’arrêter à l’aide d’un jeton d’imitation.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Dans les constructions de débog, `CAccessToken` une erreur d’affirmation se produira si n’a pas un pointeur valide à un jeton.

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour revenir automatiquement aux jetons d’accès imités.

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser

Appelez cette méthode pour permettre au thread d’appel d’usurper l’identité du contexte de sécurité d’un utilisateur connecté.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

> [!IMPORTANT]
> Si un appel à une fonction d’usurpation d’identité échoue pour quelque raison que ce soit, le client n’est pas usurpé l’identité et la demande du client est faite dans le contexte de sécurité du processus à partir duquel l’appel a été effectué. Si le processus fonctionne comme un compte très privilégié, ou en tant que membre d’un groupe administratif, l’utilisateur pourrait être en mesure d’effectuer des actions qu’il ou elle serait autrement refusé. Par conséquent, la valeur de retour pour cette fonction doit toujours être confirmée.

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted

Appelez cette méthode pour `CAccessToken` tester si l’objet contient une liste de SID restreints.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’objet contient une liste de SIDs restrictifs, FALSE s’il n’y a pas de SID restrictif ou si la méthode échoue.

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken::LoadUserProfile

Appelez cette méthode pour charger le `CAccessToken` profil utilisateur associé à l’objet.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Dans les versions de débog, `CAccessToken` une erreur d’affirmation se produira si le ne contient pas un jeton valide, ou si un profil d’utilisateur existe déjà.

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken::LogonUser

Appelez cette méthode pour créer une session logon pour l’utilisateur associé aux informations d’identification données.

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
Pointeur vers une chaîne non terminée qui spécifie le nom d’utilisateur. C’est le nom du compte utilisateur à connecter.

*pszDomain*<br/>
Pointeur vers une chaîne non terminée qui spécifie le nom du domaine ou du serveur dont la base de données de compte contient le compte *pszUserName.*

*pszPassword*<br/>
Pointeur vers une chaîne non terminée qui spécifie le mot de passe à texte clair pour le compte utilisateur spécifié par *pszUserName*.

*dwLogonType*<br/>
Spécifie le type d’opération logon à effectuer. Voir [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) pour plus de détails.

*dwLogonProvider*<br/>
Spécifie le fournisseur de logon. Voir [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) pour plus de détails.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Le jeton d’accès résultant du logon sera associé à la `CAccessToken`. Pour que cette méthode `CAccessToken` réussisse, l’objet doit détenir SE_TCB_NAME privilèges, identifiant le titulaire comme faisant partie de la base informatique de confiance. Consultez [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) pour plus d’informations sur les privilèges requis.

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken

Appelez cette méthode à partir d’un serveur COM `CAccessToken` traitant un appel d’un client pour initialiser le jeton d’accès du client COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés au DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*bImpersonate (en)*<br/>
Si TRUE, le thread actuel se fera passer pour le client COM d’appel si cet appel se termine avec succès. Si FALSE, le jeton d’accès sera ouvert, mais le thread n’aura pas de jeton d’imitation lorsque cet appel se termine.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée dans le contexte de sécurité du thread appelant la méthode [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) ou contre le contexte de sécurité du processus pour le thread d’appel.

Si ce paramètre est FALSE, la vérification d’accès est effectuée en utilisant le contexte de sécurité du thread d’appel. Si le thread se fait passer pour un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est VRAI, la vérification d’accès est effectuée en utilisant le contexte de sécurité du processus pour le thread d’appel.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour revenir automatiquement les jetons d’accès imités créés en définissant le drapeau *bImpersonate* à TRUE.

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken

Appelez cette méthode à l’intérieur d’un serveur `CAccessToken` en prenant des demandes sur un tuyau nommé pour initialiser le jeton d’accès du client.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*hPipe (en)*<br/>
Manipulez un tuyau nommé.

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés au DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*bImpersonate (en)*<br/>
Si TRUE, le thread actuel se fera passer pour le client de tuyau d’appel si cet appel se termine avec succès. Si FALSE, le jeton d’accès sera ouvert, mais le thread n’aura pas de jeton d’imitation lorsque cet appel se termine.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée dans le contexte de sécurité du thread appelant la méthode [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) ou contre le contexte de sécurité du processus pour le thread d’appel.

Si ce paramètre est FALSE, la vérification d’accès est effectuée en utilisant le contexte de sécurité du thread d’appel. Si le thread se fait passer pour un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est VRAI, la vérification d’accès est effectuée en utilisant le contexte de sécurité du processus pour le thread d’appel.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour revenir automatiquement les jetons d’accès imités créés en définissant le drapeau *bImpersonate* à TRUE.

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken

Appelez cette méthode à partir d’un serveur traitant un `CAccessToken` appel d’un client RPC pour initialiser le avec le jeton d’accès du client.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*BindingHandle (bindingHandle)*<br/>
Gérer de liaison sur le serveur qui représente une liaison pour un client.

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés au DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*bImpersonate (en)*<br/>
Si TRUE, le thread actuel se fera passer pour le client D’appel RPC si cet appel se termine avec succès. Si FALSE, le jeton d’accès sera ouvert, mais le thread n’aura pas de jeton d’imitation lorsque cet appel se termine.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée dans le contexte de sécurité du thread appelant la méthode [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) ou contre le contexte de sécurité du processus pour le thread d’appel.

Si ce paramètre est FALSE, la vérification d’accès est effectuée en utilisant le contexte de sécurité du thread d’appel. Si le thread se fait passer pour un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est VRAI, la vérification d’accès est effectuée en utilisant le contexte de sécurité du processus pour le thread d’appel.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour revenir automatiquement les jetons d’accès imités créés en définissant le drapeau *bImpersonate* à TRUE.

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken::OpenThreadToken

Appelez cette méthode pour définir le niveau `CAccessToken` d’usurpation d’identité, puis initialiser le jeton à partir du fil donné.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Paramètres

*dwDesiredAccess*<br/>
Spécifie un masque d’accès qui spécifie les types d’accès demandés au jeton d’accès. Ces types d’accès demandés sont comparés au DACL du jeton pour déterminer quels accès sont accordés ou refusés.

*bImpersonate (en)*<br/>
Si VRAI, le thread sera laissé au niveau d’usurpation d’identité demandée après la fin de cette méthode. Si FALSE, le thread reviendra à son niveau d’usurpation d’identité d’origine.

*bOpenAsSelf*<br/>
Indique si la vérification d’accès doit être effectuée dans le contexte de sécurité du thread appelant la méthode [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) ou contre le contexte de sécurité du processus pour le thread d’appel.

Si ce paramètre est FALSE, la vérification d’accès est effectuée en utilisant le contexte de sécurité du thread d’appel. Si le thread se fait passer pour un client, ce contexte de sécurité peut être celui d’un processus client. Si ce paramètre est VRAI, la vérification d’accès est effectuée en utilisant le contexte de sécurité du processus pour le thread d’appel.

*Sil*<br/>
Spécifie un [type SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) énuméré qui fournit le niveau d’usurpation d’identité du jeton.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

`OpenThreadToken`est similaire à [CAccessToken::GetThreadToken](#getthreadtoken), mais définit le `CAccessToken` niveau d’imitation avant d’initialiser le jeton d’accès du fil.

La [classe CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) peut être utilisée pour revenir automatiquement les jetons d’accès imités créés en définissant le drapeau *bImpersonate* à TRUE.

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken::PrivilegeCheck

Appelez cette méthode pour déterminer si un ensemble `CAccessToken` précis de privilèges sont activés dans l’objet.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Paramètres

*Priorités requises*<br/>
Pointeur vers une structure [PRIVILEGE_SET.](/windows/win32/api/winnt/ns-winnt-privilege_set)

*pbResult*<br/>
Pointeur à une valeur que la méthode définit pour indiquer `CAccessToken` si l’un ou l’autre du privilège spécifié est activé dans l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Au `PrivilegeCheck` retour, `Attributes` le membre de chaque structure [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) est configuré pour SE_PRIVILEGE_USED_FOR_ACCESS si le privilège correspondant est activé. Cette méthode appelle la fonction [PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32.

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken::Revert

Appelez cette méthode pour empêcher un thread d’utiliser un jeton d’imitation.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*hThread (en)*<br/>
Poignée au fil pour revenir de l’usurpation d’identité. Si *hThread* est NULL, le fil actuel est supposé.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Le retour des jetons d’usurpation d’identité peut être effectué automatiquement avec la [classe CAutoRevertImpersonation .](../../atl/reference/cautorevertimpersonation-class.md)

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl

Appelez cette méthode pour définir le `CAccessToken` DACL par défaut de l’objet.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Paramètres

*rDacl rDacl*<br/>
Les nouvelles informations par défaut [de la classe CDacl.](../../atl/reference/cdacl-class.md)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Le DACL par défaut est le DACL qui est utilisé par défaut lorsque de nouveaux objets sont créés avec ce jeton d’accès en vigueur.

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken::SetOwner

Appelez cette méthode pour définir `CAccessToken` le propriétaire de l’objet.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
[L’objet de la classe CSid](../../atl/reference/csid-class.md) contenant les informations du propriétaire.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Le propriétaire est le propriétaire par défaut qui est utilisé pour les nouveaux objets créés pendant que ce jeton d’accès est en vigueur.

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup

Appelez cette méthode pour définir `CAccessToken` le groupe principal de l’objet.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
[L’objet de classe CSid](../../atl/reference/csid-class.md) contenant les informations du groupe principal.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Le groupe principal est le groupe par défaut pour les nouveaux objets créés pendant que ce jeton d’accès est en vigueur.

## <a name="see-also"></a>Voir aussi

[Échantillon d’ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Jetons d’accès](/windows/win32/SecAuthZ/access-tokens)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
