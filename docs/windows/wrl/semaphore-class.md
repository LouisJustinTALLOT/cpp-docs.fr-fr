---
title: Semaphore (classe)
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
ms.openlocfilehash: 10357bb1cd46a33a8d4090c1ccc30050584d1816
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336137"
---
# <a name="semaphore-class"></a>Semaphore (classe)

Représente un objet de synchronisation qui contrôle une ressource partagée prenant en charge un nombre limité d’utilisateurs.

## <a name="syntax"></a>Syntaxe

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom       | Description
---------- | ------------------------------------------------------
`SyncLock` | Un synonyme pour une classe qui prend en charge les verrous synchrones.

### <a name="public-constructors"></a>Constructeurs publics

Nom                               | Description
---------------------------------- | ----------------------------------------------------
[Semaphore::Semaphore](#semaphore) | Initialise une nouvelle instance de la classe `Semaphore`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                     | Description
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semaphore::Lock](#lock) | Attend que l’objet en cours ou l’objet associé au handle spécifié, est dans l’état signalé ou que l’intervalle de délai d’attente spécifié est écoulé.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                     | Description
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semaphore::operator=](#operator-assign) | Déplace le handle spécifié à partir d’un `Semaphore` objet actuel `Semaphore` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Semaphore`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="lock"></a>Semaphore::Lock

Attend jusqu'à ce que l’objet actuel, ou le `Semaphore` objet associé au handle spécifié, est dans l’état signalé ou que l’intervalle de délai d’attente spécifié est écoulé.

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

*milliseconds*<br/>
L’intervalle de délai d’attente, en millisecondes. La valeur par défaut est INFINITE, qui attend indéfiniment.

*h*<br/>
Un handle vers un `Semaphore` objet.

### <a name="return-value"></a>Valeur de retour

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="operator-assign"></a>Semaphore::operator=

Déplace le handle spécifié à partir d’un `Semaphore` objet actuel `Semaphore` objet.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Référence rvalue à un `Semaphore` objet.

### <a name="return-value"></a>Valeur de retour

Une référence à l’actuel `Semaphore` objet.

## <a name="semaphore"></a>Semaphore::Semaphore

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
Un handle ou une référence rvalue à un `Semaphore` objet.