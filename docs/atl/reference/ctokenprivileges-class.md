---
title: Classe CTokenPrivileges
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
ms.openlocfilehash: ceb9aeca6b99e7fc9d08625e11cbdb182fb3dc9e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330541"
---
# <a name="ctokenprivileges-class"></a>Classe CTokenPrivileges

Cette classe est un `TOKEN_PRIVILEGES` emballage pour la structure.

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
|[CTokenPrivileges::CTokenPrivileges](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTokenPrivileges::Ajouter](#add)|Ajoute un ou plusieurs `CTokenPrivileges` privilèges à l’objet.|
|[CTokenPrivileges::Delete](#delete)|Supprime un privilège `CTokenPrivileges` de l’objet.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Supprime tous les privilèges de l’objet. `CTokenPrivileges`|
|[CTokenPrivileges::GetCount](#getcount)|Retourne le nombre d’entrées de privilège dans l’objet. `CTokenPrivileges`|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Récupère les noms d’affichage pour `CTokenPrivileges` les privilèges contenus dans l’objet.|
|[CTokenPrivileges::GetLength](#getlength)|Retourne la taille du tampon dans `TOKEN_PRIVILEGES` les octets `CTokenPrivileges` requis pour tenir la structure représentée par l’objet.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Récupère les identificateurs locaux uniques (LUID) `CTokenPrivileges` et attribue les drapeaux de l’objet.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Récupère les noms de privilège `CTokenPrivileges` et attribue les drapeaux de l’objet.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Retourne un pointeur à la `TOKEN_PRIVILEGES` structure.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Récupère l’attribut associé à un nom de privilège donné.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTokenPrivileges::l’opérateur const TOKEN_PRIVILEGES](#operator_const_token_privileges__star)|Jette une valeur à un `TOKEN_PRIVILEGES` pointeur de la structure.|
|[CTokenPrivileges::opérateur](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/win32/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou d’un thread et qui est attribué à chaque utilisateur connecté à un système Windows.

Le jeton d’accès est utilisé pour décrire les différents privilèges de sécurité accordés à chaque utilisateur. Un privilège se compose d’un numéro 64 bits appelé un identifiant local unique ( [LUID](/windows/win32/api/winnt/ns-winnt-luid)) et une chaîne descripteur.

La `CTokenPrivileges` classe est un emballage pour la structure [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) et contient 0 privilèges ou plus. Les privilèges peuvent être ajoutés, supprimés ou interrogés à l’aide des méthodes de classe fournies.

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="ctokenprivilegesadd"></a><a name="add"></a>CTokenPrivileges::Ajouter

Ajoute un ou plusieurs `CTokenPrivileges` privilèges à l’objet symbolique d’accès.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne non terminée qui spécifie le nom du privilège, tel que défini dans le WINNT. Fichier d’en-tête H.

*bEnable*<br/>
Si c’est vrai, le privilège est activé. Si elle est fausse, le privilège est désactivé.

*rPrivileges*<br/>
Référence à une structure [TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges) Les privilèges et les attributs sont copiés `CTokenPrivileges` à partir de cette structure et ajoutés à l’objet.

### <a name="return-value"></a>Valeur de retour

La première forme de cette méthode revient vrai si les privilèges sont ajoutés avec succès, faux autrement.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges

Constructeur.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
L’objet `CTokenPrivileges` à attribuer au nouvel objet.

*rPrivileges*<br/>
La [structure TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) à attribuer `CTokenPrivileges` au nouvel objet.

### <a name="remarks"></a>Notes

L’objet `CTokenPrivileges` peut être créé `TOKEN_PRIVILEGES` en option `CTokenPrivileges` à l’aide d’une structure ou d’un objet précédemment défini.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="dtor"></a>CTokenPrivileges::CTokenPrivileges

Destructeur.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées.

## <a name="ctokenprivilegesdelete"></a><a name="delete"></a>CTokenPrivileges::Delete

Supprime un privilège `CTokenPrivileges` de l’objet symbolique d’accès.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne non terminée qui spécifie le nom du privilège, tel que défini dans le WINNT. Fichier d’en-tête H. Par exemple, ce paramètre pourrait spécifier la SE_SECURITY_NAME constante, ou sa chaîne correspondante, "SeSecurityPrivilege."

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le privilège a été supprimé avec succès, faux autrement.

### <a name="remarks"></a>Notes

Cette méthode est utile comme outil pour créer des jetons restreints.

## <a name="ctokenprivilegesdeleteall"></a><a name="deleteall"></a>CTokenPrivileges::DeleteAll

Supprime tous les privilèges de l’objet symbolique d’accès. `CTokenPrivileges`

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Notes

Supprime tous les privilèges `CTokenPrivileges` contenus dans l’objet symbolique d’accès.

## <a name="ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames

Récupère les noms d’affichage pour `CTokenPrivileges` les privilèges contenus dans l’objet symbolique d’accès.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pDisplayNames (en)*<br/>
Pointeur vers un tableau d'objets `CString`. `CNames`est défini comme un `CTokenPrivileges::CAtlArray<CString>`tapdef: .

### <a name="remarks"></a>Notes

Le `pDisplayNames` paramètre est un `CString` pointeur vers une gamme d’objets qui `CTokenPrivileges` recevront les noms d’affichage correspondant aux privilèges contenus dans l’objet. Cette méthode ne récupère les noms d’affichage que pour les privilèges spécifiés dans la section Privilèges Définis de WINNT. H.

Cette méthode récupère un nom displayable : par exemple, si le nom d’attribut est SE_REMOTE_SHUTDOWN_NAME, le nom displayable est « Arrêt de force à partir d’un système distant ». Pour obtenir le nom du système, utilisez [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

## <a name="ctokenprivilegesgetcount"></a><a name="getcount"></a>CTokenPrivileges::GetCount

Retourne le nombre d’entrées de privilège dans l’objet. `CTokenPrivileges`

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de privilèges contenus dans l’objet. `CTokenPrivileges`

## <a name="ctokenprivilegesgetlength"></a><a name="getlength"></a>CTokenPrivileges::GetLength

Retourne la longueur `CTokenPrivileges` de l’objet.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’octets `TOKEN_PRIVILEGES` requis pour `CTokenPrivileges` tenir une structure représentée par l’objet, y compris toutes les entrées de privilège qu’il contient.

## <a name="ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes

Récupère les identificateurs locaux uniques (LUID) `CTokenPrivileges` et attribue les drapeaux de l’objet.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPrivileges*<br/>
Pointeur vers un tableau d’objets [LUID.](/windows/win32/api/winnt/ns-winnt-luid) `CLUIDArray`est un typéfacteur défini comme `CAtlArray<LUID> CLUIDArray`.

*pAttributes*<br/>
Pointeur vers une gamme d’objets DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérés. `CAttributes`est un typéfacteur défini comme `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Notes

Cette méthode énumérera tous les privilèges `CTokenPrivileges` contenus dans l’objet symbolique d’accès et placera les DIFFÉRENTS LUID et (optionnellement) les drapeaux d’attribut dans les objets de tableau.

## <a name="ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes

Récupère le nom et attribue `CTokenPrivileges` les drapeaux de l’objet.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pNames (en)*<br/>
Pointeur vers `CString` un tableau d’objets. `CNames`est un typéfacteur défini comme `CAtlArray <CString> CNames`.

*pAttributes*<br/>
Pointeur vers une gamme d’objets DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérés. `CAttributes`est un typéfacteur défini comme `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Notes

Cette méthode énumérera tous les privilèges `CTokenPrivileges` contenus dans l’objet, en plaçant le nom et (optionnellement) les drapeaux d’attribut dans les objets de tableau.

Cette méthode récupère le nom d’attribut, plutôt que le nom displayable: par exemple, si le nom d’attribut est SE_REMOTE_SHUTDOWN_NAME, le nom du système est "SeRemoteShutdownPrivilege." Pour obtenir le nom displayable, utilisez la méthode [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

## <a name="ctokenprivilegesgetptoken_privileges"></a><a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES

Retourne un pointeur à la `TOKEN_PRIVILEGES` structure.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la structure [TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges)

## <a name="ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege

Récupère l’attribut associé à un nom de privilège donné.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*<br/>
Pointeur vers une chaîne non terminée qui spécifie le nom du privilège, tel que défini dans le WINNT. Fichier d’en-tête H. Par exemple, ce paramètre pourrait spécifier la SE_SECURITY_NAME constante, ou sa chaîne correspondante, "SeSecurityPrivilege."

*pdwAttributes*<br/>
Pointeur vers une variable qui reçoit les attributs.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si l’attribut est récupéré avec succès, faux autrement.

## <a name="ctokenprivilegesoperator-"></a><a name="operator_eq"></a>CTokenPrivileges::opérateur

Opérateur d'assignation.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*<br/>
La [structure TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) à attribuer `CTokenPrivileges` à l’objet.

*rhs*<br/>
L’objet `CTokenPrivileges` à attribuer à l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet mis à jour. `CTokenPrivileges`

## <a name="ctokenprivilegesoperator-const-token_privileges-"></a><a name="operator_const_token_privileges__star"></a>CTokenPrivileges::l’opérateur const TOKEN_PRIVILEGES\*

Jette une valeur à un `TOKEN_PRIVILEGES` pointeur de la structure.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Notes

Lance une valeur à un pointeur de la structure [TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges)

## <a name="see-also"></a>Voir aussi

[Échantillon de sécurité](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[LUID](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
