---
title: CAcl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db7903dccfd851bb4bf76f1990424f887686d344
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070104"
---
# <a name="cacl-class"></a>CAcl, classe

Cette classe est un wrapper pour un `ACL` structure (liste de contrôle d’accès).

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAcl
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Tableau de ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Un tableau d’octets.|
|[CAcl::CAceTypeArray](#cacetypearray)|Un tableau d’octets.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Constructeur.|
|[CAcl :: ~ CAcl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Retourne le nombre de contrôle d’accès objets d’entrée (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Récupère les entrées de liste (ACL) de contrôle d’accès à partir de la `CAcl` objet.|
|[CAcl::GetAclEntry](#getaclentry)|Récupère toutes les informations sur une entrée dans un `CAcl` objet.|
|[CAcl::GetLength](#getlength)|Retourne la longueur de la liste ACL.|
|[CAcl::GetPACL](#getpacl)|Retourne un PACL (pointeur vers une liste ACL).|
|[CAcl::IsEmpty](#isempty)|Tests du `CAcl` objet pour les entrées.|
|[CAcl::IsNull](#isnull)|Retourne l’état de la `CAcl` objet.|
|[CAcl::RemoveAce](#removeace)|Supprime un ACE spécifique (entrée de contrôle d’accès) de la `CAcl` objet.|
|[CAcl::RemoveAces](#removeaces)|Supprime tous les ACE (entrées de contrôle d’accès) de la `CAcl` qui s’appliquent à la donnée `CSid`.|
|[CAcl::SetEmpty](#setempty)|Marque le `CAcl` de l’objet comme vide.|
|[CAcl::SetNull](#setnull)|Marque le `CAcl` objet en tant que valeur NULL.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[ACL const CAcl::operator *](#operator_const_acl__star)|Les casts un `CAcl` de l’objet à un `ACL` structure.|
|[CAcl::operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Le `ACL` structure est l’en-tête d’une liste ACL (liste de contrôle d’accès). Une ACL inclut une liste séquentielle de zéro ou plusieurs [ACE](/windows/desktop/SecAuthZ/access-control-entries) (entrées de contrôle d’accès). Les ACE individuelles dans une liste ACL sont numérotés de 0 à *n-1*, où *n* est le nombre d’entrées dans la liste ACL. Lorsque vous modifiez une liste ACL, une application fait référence à une entrée de contrôle d’accès (ACE) dans la liste ACL par son index.

Il existe deux types d’ACL :

- Discrétionnaire

- Système

Une ACL est contrôlée par le propriétaire d’un objet ou tout le monde accès WRITE_DAC à l’objet. Il spécifie que les groupes et utilisateurs particulier d’accès peuvent avoir à un objet. Par exemple, le propriétaire d’un fichier peut utiliser une ACL pour contrôler quels utilisateurs et groupes permettre et ne peut pas avoir accès au fichier.

Un objet peut avoir également des informations de sécurité au niveau du système associées, sous la forme d’un système ACL contrôlée par un administrateur système. Un système ACL peut permettre à l’administrateur système auditer les tentatives d’accès à un objet.

Pour plus d’informations, consultez le [ACL](/windows/desktop/SecAuthZ/access-control-lists) discussion dans le SDK Windows.

Pour une présentation du modèle de contrôle d’accès dans Windows, consultez [contrôle d’accès](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h

##  <a name="caccessmaskarray"></a>  CAcl::CAccessMaskArray

Un tableau d’objets ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Notes

Ce typedef Spécifie le type de tableau qui peut être utilisé pour stocker des droits d’accès utilisés dans les entrées de contrôle d’accès (ACE).

##  <a name="caceflagarray"></a>  CAcl::CAceFlagArray

Un tableau d’octets.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Notes

Ce typedef Spécifie le type de tableau utilisé pour définir les indicateurs de contrôle spécifiques au type de contrôle d’accès (ACE) d’entrée. Consultez le [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) définition pour obtenir la liste complète des indicateurs possibles.

##  <a name="cacetypearray"></a>  CAcl::CAceTypeArray

Un tableau d’octets.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Notes

Ce typedef Spécifie le type de tableau permet de définir la nature des objets entrée du contrôle d’accès, telles que ACCESS_ALLOWED_ACE_TYPE ou ACCESS_DENIED_ACE_TYPE. Consultez le [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) définition pour obtenir la liste complète des types possibles.

##  <a name="cacl"></a>  CAcl::CAcl

Constructeur.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*terme de droite*<br/>
Objet `CAcl` existant.

### <a name="remarks"></a>Notes

Le `CAcl` objet peut être éventuellement créé à l’aide d’un existant `CAcl` objet.

##  <a name="dtor"></a>  CAcl :: ~ CAcl

Destructeur.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère les ressources acquises par l’objet.

##  <a name="getacecount"></a>  CAcl::GetAceCount

Retourne le nombre de contrôle d’accès objets d’entrée (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’entrées ACE dans le `CAcl` objet.

##  <a name="getaclentries"></a>  CAcl::GetAclEntries

Récupère les entrées de liste (ACL) de contrôle d’accès à partir de la `CAcl` objet.

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSids*<br/>
Un pointeur vers un tableau de [CSid](../../atl/reference/csid-class.md) objets.

*pAccessMasks*<br/>
Les masques d’accès.

*pAceTypes*<br/>
Les types d’entrée de contrôle d’accès.

*pAceFlags*<br/>
Les indicateurs ACE.

### <a name="remarks"></a>Notes

Cette méthode remplit des paramètres de tableau avec les détails de chaque objet ACE contenues dans le `CAcl` objet. Utilisez la valeur NULL lorsque les détails de ce tableau particulier ne sont pas requises.

Le contenu de chaque tableau correspondre à l’autre, autrement dit, le premier élément de la `CAccessMaskArray` tableau correspond au premier élément dans le `CSidArray` tableau et ainsi de suite.

Consultez [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) pour plus d’informations sur les types d’ACE et les indicateurs.

##  <a name="getaclentry"></a>  CAcl::GetAclEntry

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
Index de l’entrée ACL à récupérer.

*pSid*<br/>
Le [CSid](../../atl/reference/csid-class.md) de l’objet auquel l’entrée ACL s’applique.

*pMask*<br/>
Masque spécifiant des autorisations pour accorder ou refuser l’accès.

*PTapez*<br/>
Le type d’ACE.

*pFlags*<br/>
Les indicateurs ACE.

*pObjectType*<br/>
Type d'objet. Il sera configuré à la valeur GUID_NULL si le type d’objet n’est pas spécifié dans l’entrée du contrôle, ou si l’entrée du contrôle n’est pas un ACE d’objet.

*pInheritedObjectType*<br/>
Le type d’objet hérité. Il sera configuré à la valeur GUID_NULL si le type d’objet hérité n’est pas spécifié dans l’entrée du contrôle, ou si l’entrée du contrôle n’est pas un ACE d’objet.

### <a name="remarks"></a>Notes

Cette méthode récupère toutes les informations à propos d’un ACE individuel, en fournissant plus d’informations que [CAcl::GetAclEntries](#getaclentries) seul rend disponibles.

Consultez [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) pour plus d’informations sur les types d’ACE et les indicateurs.

##  <a name="getlength"></a>  CAcl::GetLength

Retourne la longueur de la liste de contrôle d’accès (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur en octets nécessaire pour contenir le `ACL` structure.

##  <a name="getpacl"></a>  CAcl::GetPACL

Retourne un pointeur vers une liste de contrôle d’accès (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le `ACL` structure.

##  <a name="isempty"></a>  CAcl::IsEmpty

Tests du `CAcl` objet pour les entrées.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur TRUE si le `CAcl` objet n’est pas NULL et ne contient aucune entrée. Retourne FALSE si le `CAcl` objet est NULL, ou contient au moins une entrée.

##  <a name="isnull"></a>  CAcl::IsNull

Retourne l’état de la `CAcl` objet.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le `CAcl` objet est NULL, sinon FALSE.

##  <a name="operator_const_acl__star"></a>  ACL const CAcl::operator *

Les casts un `CAcl` de l’objet à un `ACL` structure (liste de contrôle d’accès).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Notes

Retourne l’adresse de la `ACL` structure.

##  <a name="operator_eq"></a>  CAcl::operator =

Opérateur d'assignation.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*terme de droite*<br/>
Le `CAcl` à affecter à l’objet existant.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la mise à jour `CAcl` objet.

##  <a name="removeace"></a>  CAcl::RemoveAce

Supprime un ACE spécifique (entrée de contrôle d’accès) de la `CAcl` objet.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeaces"></a>  CAcl::RemoveAces

Supprime interdits (entrées du contrôle d’accès) de la `CAcl` qui s’appliquent à la donnée `CSid`.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Référence à un objet `CSid`.

##  <a name="setempty"></a>  CAcl::SetEmpty

Marque le `CAcl` de l’objet comme vide.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Notes

Le `CAcl` peut être définie sur une valeur vide ou une valeur NULL : les deux États sont distincts.

##  <a name="setnull"></a>  CAcl::SetNull

Marque le `CAcl` objet en tant que valeur NULL.

```
void SetNull() throw();
```

### <a name="remarks"></a>Notes

Le `CAcl` peut être définie sur une valeur vide ou une valeur NULL : les deux États sont distincts.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
