---
description: 'En savoir plus sur : classe CAcl'
title: CAcl, classe
ms.date: 11/04/2016
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
ms.openlocfilehash: 60c498336f1bfb5358dd8e5b2eb771456a84ce17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165067"
---
# <a name="cacl-class"></a>CAcl, classe

Cette classe est un wrapper pour une `ACL` structure (liste de contrôle d’accès).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAcl
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Tableau de ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Tableau d’octets.|
|[CAcl::CAceTypeArray](#cacetypearray)|Tableau d’octets.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Constructeur.|
|[CAcl :: ~ CAcl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Retourne le nombre d’objets d’entrée de contrôle d’accès (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Récupère les entrées de liste de contrôle d’accès (ACL) de l' `CAcl` objet.|
|[CAcl::GetAclEntry](#getaclentry)|Récupère toutes les informations relatives à une entrée dans un `CAcl` objet.|
|[CAcl :: GetLength](#getlength)|Retourne la longueur de la liste de contrôle d’accès.|
|[CAcl::GetPACL](#getpacl)|Retourne un du (pointeur vers une liste de contrôle d’accès).|
|[CAcl :: IsEmpty](#isempty)|Teste l' `CAcl` objet pour les entrées.|
|[CAcl :: IsNull](#isnull)|Retourne l’état de l' `CAcl` objet.|
|[CAcl::RemoveAce](#removeace)|Supprime une entrée du contrôle d’accès spécifique de l' `CAcl` objet.|
|[CAcl::RemoveAces](#removeaces)|Supprime toutes les entrées du contrôle d’accès (ACE) de la `CAcl` qui s’appliquent au donné `CSid` .|
|[CAcl :: setentanty](#setempty)|Marque l' `CAcl` objet comme vide.|
|[CAcl :: SetNull](#setnull)|Marque l' `CAcl` objet comme null.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAcl :: Operator const ACL *](#operator_const_acl__star)|Effectue un cast d’un `CAcl` objet en une `ACL` structure.|
|[CAcl :: Operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

La `ACL` structure est l’en-tête d’une liste de contrôle d’accès (ACL). Une liste de contrôle d’accès comprend une liste séquentielle de zéro ou plusieurs entrées de contrôle d’accès ( [ACE](/windows/win32/SecAuthZ/access-control-entries) ). Les ACE individuelles d’une liste de contrôle d’accès sont numérotées de 0 à *n-1*, où *n* est le nombre d’entrées du contrôle d’accès dans la liste de contrôle d’accès. Lors de la modification d’une liste de contrôle d’accès, une application fait référence à une entrée de contrôle d’accès (ACE) dans la liste ACL par son index.

Il existe deux types de listes de contrôle d’accès :

- Discrétionnaire

- Système

Une liste de contrôle d’accès discrétionnaire est contrôlée par le propriétaire d’un objet ou toute personne disposant d’un accès WRITE_DAC à l’objet. Il spécifie l’accès que les utilisateurs et les groupes particuliers peuvent avoir à un objet. Par exemple, le propriétaire d’un fichier peut utiliser une liste de contrôle d’accès discrétionnaire pour contrôler les utilisateurs et les groupes qui peuvent et ne peuvent pas accéder au fichier.

Un objet peut également être associé à des informations de sécurité au niveau du système, sous la forme d’une liste de contrôle d’accès système contrôlée par un administrateur système. Une liste de contrôle d’accès système peut permettre à l’administrateur système d’effectuer un audit des tentatives d’accès à un objet.

Pour plus d’informations, consultez la discussion sur les [listes de contrôle d’accès](/windows/win32/SecAuthZ/access-control-lists) dans la SDK Windows.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a> CAcl::CAccessMaskArray

Tableau d’objets ACCESS_MASK.

```cpp
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Notes

Ce typedef spécifie le type de tableau qui peut être utilisé pour stocker les droits d’accès utilisés dans les entrées de contrôle d’accès (ACE).

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a> CAcl::CAceFlagArray

Tableau d’octets.

```cpp
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Notes

Ce typedef spécifie le type de tableau utilisé pour définir les indicateurs de contrôle spécifiques au type d’entrée de contrôle d’accès (ACE). Consultez la définition de [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour obtenir la liste complète des indicateurs possibles.

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a> CAcl::CAceTypeArray

Tableau d’octets.

```cpp
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Notes

Ce typedef spécifie le type de tableau utilisé pour définir la nature des objets d’entrée de contrôle d’accès (ACE), tels que ACCESS_ALLOWED_ACE_TYPE ou ACCESS_DENIED_ACE_TYPE. Consultez la définition de [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour obtenir la liste complète des types possibles.

## <a name="caclcacl"></a><a name="cacl"></a> CAcl::CAcl

Constructeur.

```cpp
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Objet `CAcl` existant.

### <a name="remarks"></a>Notes

L' `CAcl` objet peut éventuellement être créé à l’aide d’un `CAcl` objet existant.

## <a name="caclcacl"></a><a name="dtor"></a> CAcl :: ~ CAcl

Destructeur.

```cpp
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet.

## <a name="caclgetacecount"></a><a name="getacecount"></a> CAcl::GetAceCount

Retourne le nombre d’objets d’entrée de contrôle d’accès (ACE).

```cpp
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’entrées d’entrée du contrôle d’accès dans l' `CAcl` objet.

## <a name="caclgetaclentries"></a><a name="getaclentries"></a> CAcl::GetAclEntries

Récupère les entrées de liste de contrôle d’accès (ACL) de l' `CAcl` objet.

```cpp
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSids*<br/>
Pointeur vers un tableau d’objets [CSID](../../atl/reference/csid-class.md) .

*pAccessMasks*<br/>
Masques d’accès.

*pAceTypes*<br/>
Types d’entrée de contrôle d’accès (ACE).

*pAceFlags*<br/>
Indicateurs d’entrée du contrôle d’accès.

### <a name="remarks"></a>Notes

Cette méthode remplit les paramètres de tableau avec les détails de chaque objet ACE contenu dans l' `CAcl` objet. Utilisez NULL lorsque les détails de ce tableau particulier ne sont pas requis.

Le contenu de chaque tableau correspond l’un à l’autre, autrement dit, le premier élément du `CAccessMaskArray` tableau correspond au premier élément du `CSidArray` tableau, et ainsi de suite.

Pour plus d’informations sur les types et les indicateurs ACE, consultez [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

## <a name="caclgetaclentry"></a><a name="getaclentry"></a> CAcl::GetAclEntry

Récupère toutes les informations relatives à une entrée dans une liste de contrôle d’accès (ACL).

```cpp
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’entrée de liste de contrôle d’accès à récupérer.

*pSid*<br/>
Objet [CSID](../../atl/reference/csid-class.md) auquel l’entrée de la liste de contrôle d’accès s’applique.

*pMask*<br/>
Masque spécifiant les autorisations d’accorder ou de refuser l’accès.

*pType*<br/>
Type d’entrée du contrôle d’accès.

*pFlags*<br/>
Indicateurs d’entrée du contrôle d’accès.

*pObjectType*<br/>
Type d'objet. Cette valeur est définie sur GUID_NULL si le type d’objet n’est pas spécifié dans l’entrée du contrôle d’accès ou si l’entrée du contrôle d’accès n’est pas un ACE d’objet.

*pInheritedObjectType*<br/>
Type d’objet hérité. Cette valeur est définie sur GUID_NULL si le type d’objet hérité n’est pas spécifié dans l’entrée du contrôle d’accès ou si l’entrée du contrôle d’accès n’est pas un ACE d’objet.

### <a name="remarks"></a>Notes

Cette méthode récupère toutes les informations relatives à une entrée de contrôle d’accès, en fournissant plus d’informations que [CaCl :: GetAclEntries](#getaclentries) seul rend disponible.

Pour plus d’informations sur les types et les indicateurs ACE, consultez [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

## <a name="caclgetlength"></a><a name="getlength"></a> CAcl :: GetLength

Retourne la longueur de la liste de contrôle d’accès (ACL).

```cpp
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur requise en octets nécessaire pour contenir la `ACL` structure.

## <a name="caclgetpacl"></a><a name="getpacl"></a> CAcl::GetPACL

Retourne un pointeur désignant une liste de contrôle d’accès (ACL).

```cpp
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la `ACL` structure.

## <a name="caclisempty"></a><a name="isempty"></a> CAcl :: IsEmpty

Teste l' `CAcl` objet pour les entrées.

```cpp
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur TRUE si l' `CAcl` objet n’est pas null et ne contient aucune entrée. Retourne la valeur FALSe si l' `CAcl` objet a une valeur null ou contient au moins une entrée.

## <a name="caclisnull"></a><a name="isnull"></a> CAcl :: IsNull

Retourne l’état de l' `CAcl` objet.

```cpp
bool IsNull() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l' `CAcl` objet est NULL ; sinon, false.

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a> CAcl :: Operator const ACL *

Effectue un cast d’un `CAcl` objet en une `ACL` structure (liste de contrôle d’accès).

```cpp
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Notes

Retourne l’adresse de la `ACL` structure.

## <a name="cacloperator-"></a><a name="operator_eq"></a> CAcl :: Operator =

Opérateur d'assignation.

```cpp
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`CAcl`À assigner à l’objet existant.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à l’objet mis à jour `CAcl` .

## <a name="caclremoveace"></a><a name="removeace"></a> CAcl::RemoveAce

Supprime une entrée du contrôle d’accès spécifique de l' `CAcl` objet.

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray :: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="caclremoveaces"></a><a name="removeaces"></a> CAcl::RemoveAces

Supprime les ACE alls (entrées de contrôle d’accès) de `CAcl` qui s’appliquent au donné `CSid` .

```cpp
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Référence à un objet `CSid`.

## <a name="caclsetempty"></a><a name="setempty"></a> CAcl :: setentanty

Marque l' `CAcl` objet comme vide.

```cpp
void SetEmpty() throw();
```

### <a name="remarks"></a>Notes

`CAcl`Peut avoir la valeur Empty ou NULL : les deux États sont distincts.

## <a name="caclsetnull"></a><a name="setnull"></a> CAcl :: SetNull

Marque l' `CAcl` objet comme null.

```cpp
void SetNull() throw();
```

### <a name="remarks"></a>Notes

`CAcl`Peut avoir la valeur Empty ou NULL : les deux États sont distincts.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
