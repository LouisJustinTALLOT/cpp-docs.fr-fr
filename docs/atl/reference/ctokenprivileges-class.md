---
title: CTokenPrivileges, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98fb1c50b6bdd46cc6cf0efe7739e8ada60f3274
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762633"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges, classe

Cette classe est un wrapper pour le `TOKEN_PRIVILEGES` structure.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CTokenPrivileges::Add](#add)|Ajoute un ou plusieurs privilèges à le `CTokenPrivileges` objet.|
|[CTokenPrivileges::Delete](#delete)|Supprime un privilège à partir de la `CTokenPrivileges` objet.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Supprime tous les privilèges à partir de la `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetCount](#getcount)|Retourne le nombre d’entrées de privilège dans le `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Récupère noms complets pour les privilèges contenus dans le `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetLength](#getlength)|Retourne la taille du tampon en octets requis pour conserver le `TOKEN_PRIVILEGES` structure représentée par le `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Récupère les identificateurs uniques local (LUID) et les indicateurs d’attribut à partir de la `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Récupère les noms de privilège et les indicateurs d’attribut à partir de la `CTokenPrivileges` objet.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Retourne un pointeur vers le `TOKEN_PRIVILEGES` structure.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Récupère l’attribut associé à un nom de privilège.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[TOKEN_PRIVILEGES const CTokenPrivileges::operator *](#operator_const_token_privileges__star)|Convertit une valeur en un pointeur vers le `TOKEN_PRIVILEGES` structure.|
|[CTokenPrivileges::operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/desktop/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou un thread et est alloué à chaque utilisateur connecté à un système Windows.

Le jeton d’accès est utilisé pour décrire les différents privilèges de sécurité accordés à chaque utilisateur. Un privilège se compose d’un nombre 64 bits appelé identificateur unique local ( [LUID](/windows/desktop/api/winnt/ns-winnt-_luid)) et une chaîne de descripteur.

Le `CTokenPrivileges` classe est un wrapper pour le [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) structurer et contient 0 ou plus de privilèges. Privilèges peuvent être ajoutés, supprimés ou interrogées à l’aide des méthodes de la classe fournie.

Pour une présentation du modèle de contrôle d’accès dans Windows, consultez [contrôle d’accès](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h

##  <a name="add"></a>  CTokenPrivileges::Add

Ajoute un ou plusieurs privilèges à le `CTokenPrivileges` objet de jeton d’accès.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*  
Pointeur vers une chaîne se terminant par null qui spécifie le nom du privilège, tel que défini dans le WINNT. Fichier d’en-tête H.

*bActivez*  
Si la valeur est true, le privilège est activé. Si la valeur est false, le privilège est désactivé.

*rPrivileges*  
Référence à un [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) structure. Les privilèges et les attributs sont copiés à partir de cette structure et ajoutés à la `CTokenPrivileges` objet.

### <a name="return-value"></a>Valeur de retour

La première forme de cette méthode retourne la valeur true si les privilèges sont correctement ajoutés, false sinon.

##  <a name="ctokenprivileges"></a>  CTokenPrivileges::CTokenPrivileges

Constructeur.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Paramètres

*terme de droite*  
Le `CTokenPrivileges` objet à attribuer au nouvel objet.

*rPrivileges*  
Le [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) structure à assigner au nouveau `CTokenPrivileges` objet.

### <a name="remarks"></a>Notes

Le `CTokenPrivileges` objet peut éventuellement être créé à l’aide un `TOKEN_PRIVILEGES` précédemment définie ou structure `CTokenPrivileges` objet.

##  <a name="dtor"></a>  CTokenPrivileges :: ~ CTokenPrivileges

Destructeur.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées.

##  <a name="delete"></a>  CTokenPrivileges::Delete

Supprime un privilège à partir de la `CTokenPrivileges` objet de jeton d’accès.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*  
Pointeur vers une chaîne se terminant par null qui spécifie le nom du privilège, tel que défini dans le WINNT. Fichier d’en-tête H. Par exemple, ce paramètre peut spécifier la constante SE_SECURITY_NAME, ou sa chaîne correspondante, « SeSecurityPrivilege ».

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si le privilège a été supprimé.

### <a name="remarks"></a>Notes

Cette méthode est utile en tant qu’outil pour créer des jetons restreints.

##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll

Supprime tous les privilèges à partir de la `CTokenPrivileges` objet de jeton d’accès.

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Notes

Supprime tous les privilèges contenus dans le `CTokenPrivileges` objet de jeton d’accès.

##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames

Récupère noms complets pour les privilèges contenus dans le `CTokenPrivileges` objet de jeton d’accès.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pDisplayNames*  
Pointeur vers un tableau d'objets `CString`. `CNames` est défini comme un typedef : `CTokenPrivileges::CAtlArray<CString>`.

### <a name="remarks"></a>Notes

Le paramètre `pDisplayNames` est un pointeur vers un tableau de `CString` objets qui recevront les noms d’affichage correspondant aux privilèges contenus dans le `CTokenPrivileges` objet. Cette méthode récupère les noms d’affichage uniquement pour les privilèges spécifiés dans la section de privilèges défini de WINNT. H.

Cette méthode récupère un nom affichable : par exemple, si le nom d’attribut est SE_REMOTE_SHUTDOWN_NAME, le nom peut être affichée est « Forcer l’arrêt à partir d’un système distant ». Pour obtenir le nom du système, utilisez [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

##  <a name="getcount"></a>  CTokenPrivileges::GetCount

Retourne le nombre d’entrées de privilège dans le `CTokenPrivileges` objet.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de privilèges contenus dans le `CTokenPrivileges` objet.

##  <a name="getlength"></a>  CTokenPrivileges::GetLength

Retourne la longueur de la `CTokenPrivileges` objet.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’octets requis pour conserver un `TOKEN_PRIVILEGES` structure représentée par le `CTokenPrivileges` objet, y compris toutes les entrées de privilèges qu’il contient.

##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes

Récupère les identificateurs uniques local (LUID) et les indicateurs d’attribut à partir de la `CTokenPrivileges` objet.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pPrivileges*  
Pointeur vers un tableau de [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) objets. `CLUIDArray` est un typedef défini comme `CAtlArray<LUID> CLUIDArray`.

*pAttributes*  
Pointeur vers un tableau d’objets de valeur DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérées. `CAttributes` est un typedef défini comme `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Notes

Cette méthode énumérera tous les privilèges contenus dans le `CTokenPrivileges` objet du jeton d’accès et de placer la liste des LUID individuels et (éventuellement) les indicateurs d’attribut en objets du tableau.

##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes

Récupère les indicateurs de nom et l’attribut à partir de la `CTokenPrivileges` objet.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pNames*  
Pointeur vers un tableau de `CString` objets. `CNames` est un typedef défini comme `CAtlArray <CString> CNames`.

*pAttributes*  
Pointeur vers un tableau d’objets de valeur DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérées. `CAttributes` est un typedef défini comme `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Notes

Cette méthode énumérera tous les privilèges contenus dans le `CTokenPrivileges` objet, en plaçant le nom et (éventuellement) les indicateurs d’attribut en objets du tableau.

Cette méthode récupère le nom d’attribut, plutôt que le nom affichable : par exemple, si le nom d’attribut est SE_REMOTE_SHUTDOWN_NAME, le nom du système est « SeRemoteShutdownPrivilege. » Pour obtenir le nom affichable, utilisez la méthode [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES

Retourne un pointeur vers le `TOKEN_PRIVILEGES` structure.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) structure.

##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege

Récupère l’attribut associé à un nom de privilège.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pszPrivilege*  
Pointeur vers une chaîne se terminant par null qui spécifie le nom du privilège, tel que défini dans le WINNT. Fichier d’en-tête H. Par exemple, ce paramètre peut spécifier la constante SE_SECURITY_NAME, ou sa chaîne correspondante, « SeSecurityPrivilege ».

*pdwAttributes*  
Pointeur vers une variable qui reçoit les attributs.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’attribut est récupérée avec succès, false sinon.

##  <a name="operator_eq"></a>  CTokenPrivileges::operator =

Opérateur d'assignation.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rPrivileges*  
Le [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) structure à affecter à la `CTokenPrivileges` objet.

*terme de droite*  
Le `CTokenPrivileges` objet à assigner à l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la mise à jour `CTokenPrivileges` objet.

##  <a name="operator_const_token_privileges__star"></a>  TOKEN_PRIVILEGES const CTokenPrivileges::operator \*

Convertit une valeur en un pointeur vers le `TOKEN_PRIVILEGES` structure.

```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Notes

Convertit une valeur en un pointeur vers le [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) structure.

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../visual-cpp-samples.md)   
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges)   
[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)   
[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
