---
title: Mutex, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
ms.openlocfilehash: 36466bd00c5b100f20ee87173e68fdef4131ec23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371244"
---
# <a name="mutex-class"></a>Mutex, classe

Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.

## <a name="syntax"></a>Syntaxe

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom       | Description
---------- | ------------------------------------------------------
`SyncLock` | Un synonyme pour une classe qui prend en charge les serrures synchrones.

### <a name="public-constructor"></a>Constructeur public

Nom                   | Description
---------------------- | ------------------------------------------------
[Mutex::Mutex](#mutex) | Initialise une nouvelle instance de la classe `Mutex`.

### <a name="public-members"></a>Membres du public

Nom                 | Description
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Lock](#lock) | Attend que l’objet actuel, ou l’objet `Mutex` associé à la poignée spécifiée, libère le mutex ou l’intervalle de temps d’expiration spécifié s’est écoulé.

### <a name="public-operator"></a>Opérateur public

Nom                                 | Description
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::opérateur](#operator-assign) | Assigne (déplace) `Mutex` l’objet `Mutex` spécifié à l’objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Mutex`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="mutexlock"></a><a name="lock"></a>Mutex::Lock

Attend que l’objet actuel, ou l’objet `Mutex` associé à la poignée spécifiée, libère le mutex ou l’intervalle de temps d’expiration spécifié s’est écoulé.

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Paramètres

*Millisecondes*<br/>
L’intervalle de temps d’exécution, en millisecondes. La valeur par défaut est INFINITE, qui attend indéfiniment.

*h*<br/>
La poignée `Mutex` d’un objet.

### <a name="return-value"></a>Valeur de retour

## <a name="mutexmutex"></a><a name="mutex"></a>Mutex::Mutex

Initialise une nouvelle instance de la classe `Mutex`.

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une poignée, ou une référence rvalue à `Mutex` une poignée, à un objet.

### <a name="remarks"></a>Notes

Le premier constructeur initialise `Mutex` un objet à partir de la poignée spécifiée. Le deuxième constructeur initialise `Mutex` un objet à partir de la poignée spécifiée, puis déplace la propriété du mutex vers l’objet actuel. `Mutex`

## <a name="mutexoperator"></a><a name="operator-assign"></a>Mutex::opérateur

Assigne (déplace) `Mutex` l’objet `Mutex` spécifié à l’objet actuel.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une référence à un `Mutex` objet.

### <a name="return-value"></a>Valeur de retour

Une référence à `Mutex` l’objet actuel.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir la section **Move Semantics** de [Rvalue Reference Declarator: &&](../../cpp/rvalue-reference-declarator-amp-amp.md).
