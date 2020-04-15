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
ms.openlocfilehash: 2c4103f89f7fc74c5368bafac3c82685ff9b6e03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372696"
---
# <a name="dispatchstate-structure"></a>DispatchState, structure

La structure `DispatchState` est utilisée pour transférer l'état à la méthode `IExecutionContext::Dispatch`. Elle décrit les circonstances dans lesquelles la méthode `Dispatch` est appelée sur une interface `IExecutionContext`.

## <a name="syntax"></a>Syntaxe

```cpp
struct DispatchState;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[DispatchState::DispatchState](#ctor)|Construit un nouvel objet `DispatchState`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Taille de cette structure, qui est utilisé pour la version.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Indique si ce contexte `Dispatch` est entré dans la méthode parce que le contexte précédent a bloqué asynchronement. Ceci n’est utilisé que dans le contexte de `0` la planification UMS, et est défini à la valeur pour tous les autres contextes d’exécution.|
|[DispatchState::m_reserved](#m_reserved)|Bits réservés à la transmission d’informations futures.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DispatchState`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="dispatchstatedispatchstate-constructor"></a><a name="ctor"></a>DispatchState::DispatchState Constructor

Construit un nouvel objet `DispatchState`.

```cpp
DispatchState();
```

## <a name="dispatchstatem_dispatchstatesize-data-member"></a><a name="m_dispatchstatesize"></a>DispatchState::m_dispatchStateSize Membre des données

Taille de cette structure, qui est utilisé pour la version.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="dispatchstatem_fispreviouscontextasynchronouslyblocked-data-member"></a><a name="m_fispreviouscontextasynchronouslyblocked"></a>DispatchState::m_fIsPreviousContextAsynchronouslyBlocked Membre des données

Indique si ce contexte `Dispatch` est entré dans la méthode parce que le contexte précédent a bloqué asynchronement. Ceci n’est utilisé que dans le contexte de `0` la planification UMS, et est défini à la valeur pour tous les autres contextes d’exécution.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="dispatchstatem_reserved-data-member"></a><a name="m_reserved"></a>DispatchState::m_reserved Membre des données

Bits réservés à la transmission d’informations futures.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
