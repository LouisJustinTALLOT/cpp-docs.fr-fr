---
title: location, classe
ms.date: 11/04/2016
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
ms.openlocfilehash: 7f45ff6d3092bd7c27e81adddca72c9411f752d1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139823"
---
# <a name="location-class"></a>location, classe

Abstraction d'un emplacement physique sur du matériel.

## <a name="syntax"></a>Syntaxe

```cpp
class location;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[location](#ctor)|Surchargé. Construit un objet `location`.|
|[~ emplacement, destructeur](#dtor)|Détruit un objet `location`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[actif](#current)|Retourne un objet `location` représentant l’emplacement le plus spécifique que le thread appelant exécute.|
|[from_numa_node](#from_numa_node)|Retourne un objet `location` qui représente un nœud NUMA donné.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator!=](#operator_neq)|Détermine si deux objets `location` représentent un emplacement différent.|
|[operator=](#operator_eq)|Assigne le contenu d’un objet `location` différent à celui-ci.|
|[operator==](#operator_eq_eq)|Détermine si deux objets `location` représentent le même emplacement.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`location`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="dtor"></a>emplacement ~

Détruit un objet `location`.

```cpp
~location();
```

## <a name="current"></a>actif

Retourne un objet `location` représentant l’emplacement le plus spécifique que le thread appelant exécute.

```cpp
static location __cdecl current();
```

### <a name="return-value"></a>Valeur de retour

Emplacement représentant l’emplacement le plus spécifique que le thread appelant exécute.

## <a name="from_numa_node"></a>from_numa_node

Retourne un objet `location` qui représente un nœud NUMA donné.

```cpp
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>Paramètres

*_NumaNodeNumber*<br/>
Numéro de nœud NUMA pour lequel créer un emplacement.

### <a name="return-value"></a>Valeur de retour

Emplacement représentant le nœud NUMA spécifié par le paramètre `_NumaNodeNumber`.

## <a name="ctor"></a>emplacement

Construit un objet `location`.

```cpp
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>

*_LocationType*<br/>

*_Id*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
Facultatif Pointeur de liaison.

### <a name="remarks"></a>Notes

Un emplacement construit par défaut représente le système dans son ensemble.

## <a name="operator_neq"></a>opérateur ! =

Détermine si deux objets `location` représentent un emplacement différent.

```cpp
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
`location`d’opérande.

### <a name="return-value"></a>Valeur de retour

**true** si les deux emplacements sont différents ; sinon, **false** .

## <a name="operator_eq"></a>opérateur =

Assigne le contenu d’un objet `location` différent à celui-ci.

```cpp
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
Objet `location` source.

### <a name="return-value"></a>Valeur de retour

## <a name="operator_eq_eq"></a>opérateur = =

Détermine si deux objets `location` représentent le même emplacement.

```cpp
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
`location`d’opérande.

### <a name="return-value"></a>Valeur de retour

**true** si les deux emplacements sont identiques, et **false** dans le cas contraire.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
