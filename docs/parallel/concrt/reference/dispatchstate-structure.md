---
title: DispatchState, structure
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: c755675a69ce86bc03a3fdb59fa7d43a20676495
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295914"
---
# <a name="dispatchstate-structure"></a>DispatchState, structure

La structure `DispatchState` est utilisée pour transférer l'état à la méthode `IExecutionContext::Dispatch`. Elle décrit les circonstances dans lesquelles la méthode `Dispatch` est appelée sur une interface `IExecutionContext`.

## <a name="syntax"></a>Syntaxe

```
struct DispatchState;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[DispatchState::DispatchState](#ctor)|Construit un nouvel `DispatchState` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Taille de cette structure, qui est utilisée pour le contrôle de version.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Indique si ce contexte a entré le `Dispatch` (méthode), car le contexte précédent bloqué de façon asynchrone. Cela est utilisé uniquement sur le contexte de planification UMS et est défini sur la valeur `0` pour tous les autres contextes d’exécution.|
|[DispatchState::m_reserved](#m_reserved)|Bits réservés pour le passage de futures informations.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DispatchState`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrtrm.h

**Espace de noms :** concurrency

##  <a name="ctor"></a>  DispatchState::DispatchState Constructor

Construit un nouvel `DispatchState` objet.

```
DispatchState();
```

##  <a name="m_dispatchstatesize"></a>  Données membres DispatchState::m_dispatchStateSize

Taille de cette structure, qui est utilisée pour le contrôle de version.

```
unsigned long m_dispatchStateSize;
```

##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>  DispatchState::m_fIsPreviousContextAsynchronouslyBlocked Data Member

Indique si ce contexte a entré le `Dispatch` (méthode), car le contexte précédent bloqué de façon asynchrone. Cela est utilisé uniquement sur le contexte de planification UMS et est défini sur la valeur `0` pour tous les autres contextes d’exécution.

```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

##  <a name="m_reserved"></a>  Données membres DispatchState::m_reserved

Bits réservés pour le passage de futures informations.

```
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
