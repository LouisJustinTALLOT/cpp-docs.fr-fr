---
description: 'En savoir plus sur : classe Semaphore'
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
ms.openlocfilehash: 0cf99ff0a0e5263b3ed924ec5ac69b7edb0bd1f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186231"
---
# <a name="semaphore-class"></a>Semaphore, classe

Représente un objet de synchronisation qui contrôle une ressource partagée pouvant prendre en charge un nombre limité d’utilisateurs.

## <a name="syntax"></a>Syntaxe

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom       | Description
---------- | ------------------------------------------------------
`SyncLock` | Synonyme pour une classe qui prend en charge les verrous synchrones.

### <a name="public-constructors"></a>Constructeurs publics

Nom                               | Description
---------------------------------- | ----------------------------------------------------
[Sémaphore :: Semaphore](#semaphore) | Initialise une nouvelle instance de la classe `Semaphore`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                     | Description
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Sémaphore :: Lock](#lock) | Attend que l’objet en cours ou l’objet associé au handle spécifié soit dans l’état signalé ou que l’intervalle de délai d’attente spécifié se soit écoulé.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                     | Description
---------------------------------------- | ---------------------------------------------------------------------------------------
[Sémaphore :: Operator =](#operator-assign) | Déplace le handle spécifié d’un `Semaphore` objet vers l' `Semaphore` objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Semaphore`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="semaphorelock"></a><a name="lock"></a> Sémaphore :: Lock

Attend que l’objet en cours ou l' `Semaphore` objet associé au handle spécifié soit dans l’état signalé ou que l’intervalle de délai d’attente spécifié se soit écoulé.

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
Intervalle de délai d’attente, en millisecondes. La valeur par défaut est Infinite, qui attend indéfiniment.

*h*<br/>
Handle d’un `Semaphore` objet.

### <a name="return-value"></a>Valeur de retour

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="semaphoreoperator"></a><a name="operator-assign"></a> Sémaphore :: Operator =

Déplace le handle spécifié d’un `Semaphore` objet vers l' `Semaphore` objet actuel.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Rvalue-référence à un `Semaphore` objet.

### <a name="return-value"></a>Valeur renvoyée

Référence à l’objet actuel `Semaphore` .

## <a name="semaphoresemaphore"></a><a name="semaphore"></a> Sémaphore :: Semaphore

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
Handle ou référence rvalue à un `Semaphore` objet.
