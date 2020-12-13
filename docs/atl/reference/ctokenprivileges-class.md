---
description: 'En savoir plus sur : classe CTokenPrivileges'
title: CTokenPrivileges, classe
ms.date: 11/04/2016
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
ms.openlocfilehash: 22953c0d2aa8c4fa7dd0b79b001e46797bd3ca25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140307"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges, classe

Cette classe est un wrapper pour la `TOKEN_PRIVILEGES` structure.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CTokenPrivileges
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|Constructeur.|
|[CTokenPrivileges :: ~ CTokenPrivileges](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTokenPrivileges :: Add](#add)|Ajoute un ou plusieurs privilèges à l' `CTokenPrivileges` objet.|
|[CTokenPrivileges ::D supprim](#delete)|Supprime un privilège de l' `CTokenPrivileges` objet.|
|[CTokenPrivileges ::D eleteAll](#deleteall)|Supprime tous les privilèges de l' `CTokenPrivileges` objet.|
|[CTokenPrivileges :: GetCount](#getcount)|Retourne le nombre d’entrées de privilège dans l' `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Récupère les noms d’affichage des privilèges contenus dans l' `CTokenPrivileges` objet.|
|[CTokenPrivileges :: GetLength](#getlength)|Retourne la taille de la mémoire tampon en octets requis pour contenir la `TOKEN_PRIVILEGES` structure représentée par l' `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Récupère les identificateurs uniques locaux (LUID) et les indicateurs d’attribut à partir de l' `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Récupère les noms de privilèges et les indicateurs d’attribut de l' `CTokenPrivileges` objet.|
|[CTokenPrivileges :: GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Retourne un pointeur vers la `TOKEN_PRIVILEGES` structure.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Récupère l’attribut associé à un nom de privilège donné.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTokenPrivileges :: Operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Convertit une valeur en pointeur vers la `TOKEN_PRIVILEGES` structure.|
|[CTokenPrivileges :: Operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/win32/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou d’un thread et qui est alloué à chaque utilisateur connecté à un système Windows.

Le jeton d’accès est utilisé pour décrire les différents privilèges de sécurité accordés à chaque utilisateur. Un privilège se compose d’un nombre 64 bits appelé identificateur unique local ( [LUID](/windows/win32/api/winnt/ns-winnt-luid)) et d’une chaîne de descripteur.

La `CTokenPrivileges` classe est un wrapper pour la structure [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) et contient 0 ou plusieurs privilèges. Des privilèges peuvent être ajoutés, supprimés ou interrogés à l’aide des méthodes de classe fournies.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="ctokenprivilegesadd"></a><a name="add"></a> CTokenPrivileges :: Add

Ajoute un ou plusieurs privilèges à l' `CTokenPrivileges` objet de jeton d’accès.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom du privilège, tel que défini dans WINNt. Fichier d’en-tête H.

*bEnable*<br/>
Si la valeur est true, le privilège est activé. Si la valeur est false, le privilège est désactivé.

*rPrivileges*<br/>
Référence à une structure de [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) . Les privilèges et les attributs sont copiés à partir de cette structure et ajoutés à l' `CTokenPrivileges` objet.

### <a name="return-value"></a>Valeur renvoyée

La première forme de cette méthode retourne la valeur true si les privilèges ont été ajoutés avec succès ; sinon, false.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a> CTokenPrivileges::CTokenPrivileges

Constructeur.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`CTokenPrivileges`Objet à assigner au nouvel objet.

*rPrivileges*<br/>
Structure [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) à assigner au nouvel `CTokenPrivileges` objet.

### <a name="remarks"></a>Notes

L' `CTokenPrivileges` objet peut éventuellement être créé à l’aide d’une `TOKEN_PRIVILEGES` structure ou d’un objet défini précédemment `CTokenPrivileges` .

## <a name="ctokenprivilegesctokenprivileges"></a><a name="dtor"></a> CTokenPrivileges :: ~ CTokenPrivileges

Destructeur.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées.

## <a name="ctokenprivilegesdelete"></a><a name="delete"></a> CTokenPrivileges ::D supprim

Supprime un privilège de l' `CTokenPrivileges` objet de jeton d’accès.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom du privilège, tel que défini dans WINNt. Fichier d’en-tête H. Par exemple, ce paramètre peut spécifier la constante SE_SECURITY_NAME, ou la chaîne correspondante, « SeSecurityPrivilege ».

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le privilège a été correctement supprimé ; sinon, false.

### <a name="remarks"></a>Notes

Cette méthode est utile en tant qu’outil pour la création de jetons restreints.

## <a name="ctokenprivilegesdeleteall"></a><a name="deleteall"></a> CTokenPrivileges ::D eleteAll

Supprime tous les privilèges de l' `CTokenPrivileges` objet de jeton d’accès.

```cpp
void DeleteAll() throw();
```

### <a name="remarks"></a>Notes

Supprime tous les privilèges contenus dans l' `CTokenPrivileges` objet de jeton d’accès.

## <a name="ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a> CTokenPrivileges::GetDisplayNames

Récupère les noms complets des privilèges contenus dans l' `CTokenPrivileges` objet de jeton d’accès.

```cpp
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pDisplayNames*<br/>
Pointeur vers un tableau d'objets `CString`. `CNames` est défini en tant que typedef : `CTokenPrivileges::CAtlArray<CString>` .

### <a name="remarks"></a>Notes

Le paramètre `pDisplayNames` est un pointeur vers un tableau d' `CString` objets qui recevra les noms d’affichage correspondant aux privilèges contenus dans l' `CTokenPrivileges` objet. Cette méthode récupère les noms d’affichage uniquement pour les privilèges spécifiés dans la section des privilèges définis de WINNt. H.

Cette méthode récupère un nom affichable : par exemple, si le nom de l’attribut est SE_REMOTE_SHUTDOWN_NAME, le nom affichable est « forcer l’arrêt à partir d’un système distant ». Pour obtenir le nom du système, utilisez [CTokenPrivileges :: GetNamesAndAttributes](#getnamesandattributes).

## <a name="ctokenprivilegesgetcount"></a><a name="getcount"></a> CTokenPrivileges :: GetCount

Retourne le nombre d’entrées de privilège dans l' `CTokenPrivileges` objet.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de privilèges contenus dans l' `CTokenPrivileges` objet.

## <a name="ctokenprivilegesgetlength"></a><a name="getlength"></a> CTokenPrivileges :: GetLength

Retourne la longueur de l' `CTokenPrivileges` objet.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’octets requis pour contenir une `TOKEN_PRIVILEGES` structure représentée par l' `CTokenPrivileges` objet, y compris toutes les entrées de privilège qu’il contient.

## <a name="ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a> CTokenPrivileges::GetLuidsAndAttributes

Récupère les identificateurs uniques locaux (LUID) et les indicateurs d’attribut à partir de l' `CTokenPrivileges` objet.

```cpp
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPrivileges*<br/>
Pointeur vers un tableau d’objets [LUID](/windows/win32/api/winnt/ns-winnt-luid) . `CLUIDArray` est un typedef défini en tant que `CAtlArray<LUID> CLUIDArray` .

*pAttributes*<br/>
Pointeur vers un tableau d’objets DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérés. `CAttributes` est un typedef défini en tant que `CAtlArray <DWORD> CAttributes` .

### <a name="remarks"></a>Notes

Cette méthode énumère tous les privilèges contenus dans l' `CTokenPrivileges` objet de jeton d’accès et place le LUID individuel et (éventuellement) les indicateurs d’attribut dans des objets de tableau.

## <a name="ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a> CTokenPrivileges::GetNamesAndAttributes

Récupère le nom et les indicateurs d’attribut de l' `CTokenPrivileges` objet.

```cpp
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pNames*<br/>
Pointeur vers un tableau d' `CString` objets. `CNames` est un typedef défini en tant que `CAtlArray <CString> CNames` .

*pAttributes*<br/>
Pointeur vers un tableau d’objets DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérés. `CAttributes` est un typedef défini en tant que `CAtlArray <DWORD> CAttributes` .

### <a name="remarks"></a>Notes

Cette méthode énumère tous les privilèges contenus dans l' `CTokenPrivileges` objet, en plaçant le nom et (éventuellement) les indicateurs d’attribut dans des objets de tableau.

Cette méthode récupère le nom de l’attribut, plutôt que le nom affichable : par exemple, si le nom de l’attribut est SE_REMOTE_SHUTDOWN_NAME, le nom du système est « SeRemoteShutdownPrivilege ». Pour obtenir le nom affichable, utilisez la méthode [CTokenPrivileges :: GetDisplayNames](#getdisplaynames).

## <a name="ctokenprivilegesgetptoken_privileges"></a><a name="getptoken_privileges"></a> CTokenPrivileges :: GetPTOKEN_PRIVILEGES

Retourne un pointeur vers la `TOKEN_PRIVILEGES` structure.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la structure [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) .

## <a name="ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a> CTokenPrivileges::LookupPrivilege

Récupère l’attribut associé à un nom de privilège donné.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom du privilège, tel que défini dans WINNt. Fichier d’en-tête H. Par exemple, ce paramètre peut spécifier la constante SE_SECURITY_NAME, ou la chaîne correspondante, « SeSecurityPrivilege ».

*pdwAttributes*<br/>
Pointeur vers une variable qui reçoit les attributs.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si l’attribut a été récupéré avec succès ; sinon, false.

## <a name="ctokenprivilegesoperator-"></a><a name="operator_eq"></a> CTokenPrivileges :: Operator =

Opérateur d'assignation.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*<br/>
Structure [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) à assigner à l' `CTokenPrivileges` objet.

*rhs*<br/>
`CTokenPrivileges`Objet à assigner à l’objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CTokenPrivileges` .

## <a name="ctokenprivilegesoperator-const-token_privileges-"></a><a name="operator_const_token_privileges__star"></a> CTokenPrivileges :: Operator const TOKEN_PRIVILEGES \*

Convertit une valeur en pointeur vers la `TOKEN_PRIVILEGES` structure.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Notes

Convertit une valeur en pointeur vers la structure [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) .

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[LUID](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
