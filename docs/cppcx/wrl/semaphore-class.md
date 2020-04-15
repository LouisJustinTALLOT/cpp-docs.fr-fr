---
title: Semaphore, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: e017b1b6316c4b6d49563d9a543950ab28961d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359358"
---
# <a name="semaphore-class"></a>Semaphore, classe

Représente un objet de synchronisation qui contrôle une ressource partagée qui peut prendre en charge un nombre limité d’utilisateurs.

## <a name="syntax"></a>Syntaxe

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom       | Description
---------- | ------------------------------------------------------
`SyncLock` | Un synonyme pour une classe qui prend en charge les serrures synchrones.

### <a name="public-constructors"></a>Constructeurs publics

Nom                               | Description
---------------------------------- | ----------------------------------------------------
[Sémaphore::Semaphore](#semaphore) | Initialise une nouvelle instance de la classe `Semaphore`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                     | Description
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Sémaphore::Lock](#lock) | Attend que l’objet actuel, ou l’objet associé à la poignée spécifiée, soit dans l’état signalé ou que l’intervalle de temps d’écoulement spécifié s’est écoulé.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                     | Description
---------------------------------------- | ---------------------------------------------------------------------------------------
[Sémaphore::opérateur](#operator-assign) | Déplace la poignée `Semaphore` spécifiée d’un objet à l’objet actuel. `Semaphore`

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Semaphore`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="semaphorelock"></a><a name="lock"></a>Sémaphore::Lock

Attend que l’objet actuel, ou l’objet `Semaphore` associé à la poignée spécifiée, soit dans l’état signalé ou que l’intervalle de temps d’écoulement spécifié s’est écoulé.

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
Une poignée `Semaphore` à un objet.

### <a name="return-value"></a>Valeur de retour

Une variable de type `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`.

## <a name="semaphoreoperator"></a><a name="operator-assign"></a>Sémaphore::opérateur

Déplace la poignée `Semaphore` spécifiée d’un objet à l’objet actuel. `Semaphore`

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Rvalue-référence à `Semaphore` un objet.

### <a name="return-value"></a>Valeur de retour

Une référence à `Semaphore` l’objet actuel.

## <a name="semaphoresemaphore"></a><a name="semaphore"></a>Sémaphore::Semaphore

Initialise une nouvelle instance de la classe `Semaphore`.

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une poignée ou une référence rvalue à un `Semaphore` objet.
