---
title: Classe CAcl
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
ms.openlocfilehash: 87bf903220a584798ea59c5f1c701fc35049e901
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321656"
---
# <a name="cacl-class"></a>Classe CAcl

Cette classe est un `ACL` emballage pour une structure (liste d’accès).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAcl
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Un éventail de ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Un éventail de BYTE.|
|[CAcl::CAceTypeArray](#cacetypearray)|Un éventail de BYTE.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Constructeur.|
|[CAcl: : CAcl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Retourne le nombre d’objets d’entrée de contrôle d’accès (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Récupère les entrées de la liste de `CAcl` contrôle d’accès (ACL) de l’objet.|
|[CAcl::GetAclEntry](#getaclentry)|Récupère toutes les informations sur une `CAcl` entrée dans un objet.|
|[CAcl::GetLength](#getlength)|Retourne la longueur de l’ACL.|
|[CAcl::GetPACL](#getpacl)|Retourne un PACL (pointeur à un ACL).|
|[CAcl::IsEmpty](#isempty)|Teste `CAcl` l’objet pour les entrées.|
|[CAcl::IsNull](#isnull)|Retourne l’état `CAcl` de l’objet.|
|[CAcl::RemoveAce](#removeace)|Supprime un ACE spécifique (entrée de `CAcl` contrôle d’accès) de l’objet.|
|[CAcl::RemoveAces](#removeaces)|Supprime toutes les AE (entrées de `CAcl` contrôle d’accès) de ce qui s’applique à la donnée `CSid`.|
|[CAcl::SetEmpty](#setempty)|Marque `CAcl` l’objet comme vide.|
|[CAcl::SetNull](#setnull)|Marque `CAcl` l’objet comme NULL.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAcl::opérateur const ACL](#operator_const_acl__star)|Jette un `CAcl` objet `ACL` à une structure.|
|[CAcl::opérateur](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

La `ACL` structure est l’en-tête d’un ACL (liste de contrôle d’accès). Un ACL comprend une liste séquentielle de [NCP](/windows/win32/SecAuthZ/access-control-entries) nuls ou plus (entrées de contrôle d’accès). Les ACA individuels dans un ACL sont numérotés de 0 à *n-1*, où *n* est le nombre d’ACE dans le LCA. Lors de l’édition d’un ACL, une application se réfère à une entrée de contrôle d’accès (ACE) au sein de l’ACL par son index.

Il existe deux types ACL :

- Discrétionnaire

- Système

Un ACL discrétionnaire est contrôlé par le propriétaire d’un objet ou toute personne WRITE_DAC accès à l’objet. Il spécifie l’accès que certains utilisateurs et groupes peuvent avoir à un objet. Par exemple, le propriétaire d’un fichier peut utiliser un ACL discrétionnaire pour contrôler quels utilisateurs et groupes peuvent et ne peuvent pas avoir accès au fichier.

Un objet peut également avoir des informations de sécurité au niveau du système qui lui sont associées, sous la forme d’un système ACL contrôlé par un administrateur système. Un système ACL peut permettre à l’administrateur du système de vérifier toute tentative d’accès à un objet.

Pour plus de détails, voir la discussion [ACL](/windows/win32/SecAuthZ/access-control-lists) dans le SDK Windows.

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

Une gamme d’objets ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Notes

Ce type de réseau précise le type de tableau qui peut être utilisé pour stocker les droits d’accès utilisés dans les entrées de contrôle d’accès (ACE).

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>CAcl::CAceFlagArray

Un éventail de BYTE.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Notes

Ce type de réseau spécifie le type de tableau utilisé pour définir les indicateurs de contrôle spécifiques à l’entrée de contrôle d’accès (ACE). Voir la définition [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour la liste complète des drapeaux possibles.

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>CAcl::CAceTypeArray

Un éventail de BYTE.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Notes

Ce type précise le type de tableau utilisé pour définir la nature des objets d’entrée de contrôle d’accès (ACE), tels que ACCESS_ALLOWED_ACE_TYPE ou ACCESS_DENIED_ACE_TYPE. Consultez la définition [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour la liste complète des types possibles.

## <a name="caclcacl"></a><a name="cacl"></a>CAcl::CAcl

Constructeur.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Objet `CAcl` existant.

### <a name="remarks"></a>Notes

L’objet `CAcl` peut être créé `CAcl` en option à l’aide d’un objet existant.

## <a name="caclcacl"></a><a name="dtor"></a>CAcl: : CAcl

Destructeur.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet.

## <a name="caclgetacecount"></a><a name="getacecount"></a>CAcl::GetAceCount

Retourne le nombre d’objets d’entrée de contrôle d’accès (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’entrées ACE dans l’objet. `CAcl`

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>CAcl::GetAclEntries

Récupère les entrées de la liste de `CAcl` contrôle d’accès (ACL) de l’objet.

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSids*<br/>
Un pointeur à un tableau d’objets [CSid.](../../atl/reference/csid-class.md)

*pAccessMasks*<br/>
Les masques d’accès.

*pAceTypes*<br/>
Les types d’entrée de contrôle d’accès (ACE).

*pAceFlags*<br/>
Les drapeaux de l’ACE.

### <a name="remarks"></a>Notes

Cette méthode remplit les paramètres de tableau avec les `CAcl` détails de chaque objet ACE contenu dans l’objet. Utilisez NULL lorsque les détails de ce tableau particulier ne sont pas requis.

Le contenu de chaque tableau correspond les uns aux `CAccessMaskArray` autres, c’est-à-dire que le premier élément du tableau correspond au premier élément du `CSidArray` tableau, etc.

Consultez [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour plus de détails sur les types et les drapeaux ACE.

## <a name="caclgetaclentry"></a><a name="getaclentry"></a>CAcl::GetAclEntry

Récupère toutes les informations sur une entrée dans une liste de contrôle d’accès (ACL).

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
Index à l’entrée ACL à récupérer.

*pSid*<br/>
[L’objet CSid](../../atl/reference/csid-class.md) auquel s’applique l’entrée ACL.

*pMask (pMask)*<br/>
Le masque spécifiant les autorisations d’accorder ou de refuser l’accès.

*pType (en)*<br/>
Le type ACE.

*pFlags*<br/>
Les drapeaux de l’ACE.

*pObjectType*<br/>
Type d'objet. Cela sera réglé pour GUID_NULL si le type d’objet n’est pas spécifié dans l’ACE, ou si l’ACE n’est pas un ACE OBJECT.

*pInheritedObjectType*<br/>
Le type d’objet hérité. Cela sera réglé pour GUID_NULL si le type d’objet hérité n’est pas spécifié dans l’ACE, ou si l’ACE n’est pas un ACE OBJECT.

### <a name="remarks"></a>Notes

Cette méthode récupérera toutes les informations sur un ACE individuel, fournissant plus d’informations que [CAcl::GetAclEntries](#getaclentries) seul met à disposition.

Consultez [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour plus de détails sur les types et les drapeaux ACE.

## <a name="caclgetlength"></a><a name="getlength"></a>CAcl::GetLength

Retourne la longueur de la liste de contrôle d’accès (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur requise dans les `ACL` octets nécessaires pour tenir la structure.

## <a name="caclgetpacl"></a><a name="getpacl"></a>CAcl::GetPACL

Renvoie un pointeur à une liste de contrôle d’accès (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la `ACL` structure.

## <a name="caclisempty"></a><a name="isempty"></a>CAcl::IsEmpty

Teste `CAcl` l’objet pour les entrées.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Notes

Retourne VRAI `CAcl` si l’objet n’est pas NULL, et ne contient pas d’entrées. Renvoie FALSE `CAcl` si l’objet est SOIT NULL, ou contient au moins une entrée.

## <a name="caclisnull"></a><a name="isnull"></a>CAcl::IsNull

Retourne l’état `CAcl` de l’objet.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI `CAcl` si l’objet est NULL, FALSE autrement.

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>CAcl::opérateur const ACL

Jette un `CAcl` objet `ACL` à une structure (liste d’accès-contrôle).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Notes

Retourne l’adresse `ACL` de la structure.

## <a name="cacloperator-"></a><a name="operator_eq"></a>CAcl::opérateur

Opérateur d'assignation.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
L’assignation `CAcl` à l’objet existant.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence `CAcl` à l’objet mis à jour.

## <a name="caclremoveace"></a><a name="removeace"></a>CAcl::RemoveAce

Supprime un ACE spécifique (entrée de `CAcl` contrôle d’accès) de l’objet.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index à l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="caclremoveaces"></a><a name="removeaces"></a>CAcl::RemoveAces

Supprime tous les CCE (entrées de `CAcl` contrôle d’accès) de ce qui s’applique à la donnée `CSid`.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Référence à un objet `CSid`.

## <a name="caclsetempty"></a><a name="setempty"></a>CAcl::SetEmpty

Marque `CAcl` l’objet comme vide.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Notes

Le `CAcl` peut être réglé pour vider ou à NULL: les deux états sont distincts.

## <a name="caclsetnull"></a><a name="setnull"></a>CAcl::SetNull

Marque `CAcl` l’objet comme NULL.

```
void SetNull() throw();
```

### <a name="remarks"></a>Notes

Le `CAcl` peut être réglé pour vider ou à NULL: les deux états sont distincts.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
