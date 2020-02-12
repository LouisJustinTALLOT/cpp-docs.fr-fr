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
ms.openlocfilehash: 69e00893373ccca6e2ed676fbb7f5a109c49efdf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143042"
---
# <a name="dispatchstate-structure"></a>DispatchState, structure

La structure `DispatchState` est utilisée pour transférer l'état à la méthode `IExecutionContext::Dispatch`. Elle décrit les circonstances dans lesquelles la méthode `Dispatch` est appelée sur une interface `IExecutionContext`.

## <a name="syntax"></a>Syntaxe

```cpp
struct DispatchState;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[DispatchState ::D ispatchState](#ctor)|Construit un nouvel objet `DispatchState`.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[DispatchState :: m_dispatchStateSize](#m_dispatchstatesize)|Taille de cette structure, utilisée pour le contrôle de version.|
|[DispatchState :: m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Indique si ce contexte est entré dans la méthode `Dispatch`, car le contexte précédent a été bloqué de manière asynchrone. Elle est utilisée uniquement dans le contexte de planification UMS et est définie sur la valeur `0` pour tous les autres contextes d’exécution.|
|[DispatchState :: m_reserved](#m_reserved)|Bits réservés pour le passage d’informations futures.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DispatchState`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="ctor"></a>DispatchState ::D constructeur ispatchState

Construit un nouvel objet `DispatchState`.

```cpp
DispatchState();
```

## <a name="m_dispatchstatesize"></a>DispatchState :: m_dispatchStateSize données de membre

Taille de cette structure, utilisée pour le contrôle de version.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="m_fispreviouscontextasynchronouslyblocked"></a>DispatchState :: m_fIsPreviousContextAsynchronouslyBlocked données de membre

Indique si ce contexte est entré dans la méthode `Dispatch`, car le contexte précédent a été bloqué de manière asynchrone. Elle est utilisée uniquement dans le contexte de planification UMS et est définie sur la valeur `0` pour tous les autres contextes d’exécution.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="m_reserved"></a>DispatchState :: m_reserved données de membre

Bits réservés pour le passage d’informations futures.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
