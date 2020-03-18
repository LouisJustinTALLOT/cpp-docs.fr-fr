---
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
ms.openlocfilehash: 5d03154597f800042846e82d0a0cf5e7c46b613f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418145"
---
# <a name="cacl-class"></a>CAcl, classe

Cette classe est un wrapper pour une structure de `ACL` (liste de contrôle d’accès).

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAcl
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Tableau de ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Tableau d’octets.|
|[CAcl::CAceTypeArray](#cacetypearray)|Tableau d’octets.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Constructeur.|
|[CAcl :: ~ CAcl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Retourne le nombre d’objets d’entrée de contrôle d’accès (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Récupère les entrées de la liste de contrôle d’accès (ACL) de l’objet `CAcl`.|
|[CAcl::GetAclEntry](#getaclentry)|Récupère toutes les informations relatives à une entrée dans un objet `CAcl`.|
|[CAcl :: GetLength](#getlength)|Retourne la longueur de la liste de contrôle d’accès.|
|[CAcl::GetPACL](#getpacl)|Retourne un du (pointeur vers une liste de contrôle d’accès).|
|[CAcl :: IsEmpty](#isempty)|Teste l’objet `CAcl` pour les entrées.|
|[CAcl :: IsNull](#isnull)|Retourne l’état de l’objet `CAcl`.|
|[CAcl::RemoveAce](#removeace)|Supprime une entrée du contrôle d’accès (ACE) spécifique de l’objet `CAcl`.|
|[CAcl::RemoveAces](#removeaces)|Supprime toutes les entrées du contrôle d’accès (ACE) des `CAcl` qui s’appliquent au `CSid`donné.|
|[CAcl :: setentanty](#setempty)|Marque l’objet `CAcl` comme vide.|
|[CAcl :: SetNull](#setnull)|Marque l’objet `CAcl` comme NULL.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|----------|-----------------|
|[CAcl :: Operator const ACL *](#operator_const_acl__star)|Effectue un cast d’un objet `CAcl` en une structure `ACL`.|
|[CAcl :: Operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

La structure `ACL` est l’en-tête d’une liste de contrôle d’accès (ACL). Une liste de contrôle d’accès comprend une liste séquentielle de zéro ou plusieurs entrées de contrôle d’accès ( [ACE](/windows/win32/SecAuthZ/access-control-entries) ). Les ACE individuelles d’une liste de contrôle d’accès sont numérotées de 0 à *n-1*, où *n* est le nombre d’entrées du contrôle d’accès dans la liste de contrôle d’accès. Lors de la modification d’une liste de contrôle d’accès, une application fait référence à une entrée de contrôle d’accès (ACE) dans la liste ACL par son index.

Il existe deux types de listes de contrôle d’accès :

- Discrétionnaire

- Système

Une liste de contrôle d’accès discrétionnaire est contrôlée par le propriétaire d’un objet ou toute personne disposant d’un accès WRITE_DAC à l’objet. Il spécifie l’accès que les utilisateurs et les groupes particuliers peuvent avoir à un objet. Par exemple, le propriétaire d’un fichier peut utiliser une liste de contrôle d’accès discrétionnaire pour contrôler les utilisateurs et les groupes qui peuvent et ne peuvent pas accéder au fichier.

Un objet peut également être associé à des informations de sécurité au niveau du système, sous la forme d’une liste de contrôle d’accès système contrôlée par un administrateur système. Une liste de contrôle d’accès système peut permettre à l’administrateur système d’effectuer un audit des tentatives d’accès à un objet.

Pour plus d’informations, consultez la discussion sur les [listes de contrôle d’accès](/windows/win32/SecAuthZ/access-control-lists) dans la SDK Windows.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

##  <a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

Tableau d’objets ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Notes

Ce typedef spécifie le type de tableau qui peut être utilisé pour stocker les droits d’accès utilisés dans les entrées de contrôle d’accès (ACE).

##  <a name="caceflagarray"></a>CAcl::CAceFlagArray

Tableau d’octets.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Notes

Ce typedef spécifie le type de tableau utilisé pour définir les indicateurs de contrôle spécifiques au type d’entrée de contrôle d’accès (ACE). Consultez la définition de [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour obtenir la liste complète des indicateurs possibles.

##  <a name="cacetypearray"></a>CAcl::CAceTypeArray

Tableau d’octets.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Notes

Ce typedef spécifie le type de tableau utilisé pour définir la nature des objets d’entrée de contrôle d’accès (ACE), tels que ACCESS_ALLOWED_ACE_TYPE ou ACCESS_DENIED_ACE_TYPE. Consultez la définition de [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour obtenir la liste complète des types possibles.

##  <a name="cacl"></a>CAcl::CAcl

Constructeur.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Objet `CAcl` existant.

### <a name="remarks"></a>Notes

L’objet `CAcl` peut éventuellement être créé à l’aide d’un objet `CAcl` existant.

##  <a name="dtor"></a>CAcl :: ~ CAcl

Destructeur.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet.

##  <a name="getacecount"></a>CAcl::GetAceCount

Retourne le nombre d’objets d’entrée de contrôle d’accès (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’entrées d’entrée du contrôle d’accès dans l’objet `CAcl`.

##  <a name="getaclentries"></a>CAcl::GetAclEntries

Récupère les entrées de la liste de contrôle d’accès (ACL) de l’objet `CAcl`.

```
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

Cette méthode remplit les paramètres de tableau avec les détails de chaque objet ACE contenu dans l’objet `CAcl`. Utilisez NULL lorsque les détails de ce tableau particulier ne sont pas requis.

Le contenu de chaque tableau correspond à l’un de l’autre, autrement dit, le premier élément du tableau `CAccessMaskArray` correspond au premier élément du tableau `CSidArray`, et ainsi de suite.

Pour plus d’informations sur les types et les indicateurs ACE, consultez [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

##  <a name="getaclentry"></a>CAcl::GetAclEntry

Récupère toutes les informations relatives à une entrée dans une liste de contrôle d’accès (ACL).

```
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

##  <a name="getlength"></a>CAcl :: GetLength

Retourne la longueur de la liste de contrôle d’accès (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur requise en octets nécessaire pour contenir la structure `ACL`.

##  <a name="getpacl"></a>CAcl::GetPACL

Retourne un pointeur désignant une liste de contrôle d’accès (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la structure `ACL`.

##  <a name="isempty"></a>CAcl :: IsEmpty

Teste l’objet `CAcl` pour les entrées.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur TRUE si l’objet `CAcl` n’est pas NULL et ne contient aucune entrée. Retourne la valeur FALSe si l’objet `CAcl` a la valeur NULL ou contient au moins une entrée.

##  <a name="isnull"></a>CAcl :: IsNull

Retourne l’état de l’objet `CAcl`.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’objet `CAcl` est NULL ; sinon, FALSe.

##  <a name="operator_const_acl__star"></a>CAcl :: Operator const ACL *

Effectue un cast d’un objet `CAcl` en une structure `ACL` (liste de contrôle d’accès).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Notes

Retourne l’adresse de la structure `ACL`.

##  <a name="operator_eq"></a>CAcl :: Operator =

Opérateur d'assignation.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`CAcl` à assigner à l’objet existant.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l’objet `CAcl` mis à jour.

##  <a name="removeace"></a>CAcl::RemoveAce

Supprime une entrée du contrôle d’accès (ACE) spécifique de l’objet `CAcl`.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray :: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeaces"></a>CAcl::RemoveAces

Supprime les ACE alls (entrées de contrôle d’accès) de la `CAcl` qui s’appliquent au `CSid`donné.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Référence à un objet `CSid`.

##  <a name="setempty"></a>CAcl :: setentanty

Marque l’objet `CAcl` comme vide.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Notes

Le `CAcl` peut être défini sur vide ou sur NULL : les deux États sont distincts.

##  <a name="setnull"></a>CAcl :: SetNull

Marque l’objet `CAcl` comme NULL.

```
void SetNull() throw();
```

### <a name="remarks"></a>Notes

Le `CAcl` peut être défini sur vide ou sur NULL : les deux États sont distincts.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
