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
ms.openlocfilehash: 93de43ac7e5314501d0391e2cde862ba32be0b4b
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336368"
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
`SyncLock` | Un synonyme pour une classe qui prend en charge les verrous synchrones.

### <a name="public-constructor"></a>Constructeur public

Name                   | Description
---------------------- | ------------------------------------------------
[Mutex::Mutex](#mutex) | Initialise une nouvelle instance de la classe `Mutex`.

### <a name="public-members"></a>Membres publics

Name                 | Description
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Lock](#lock) | Attend jusqu'à ce que l’objet actuel, ou le `Mutex` objet associé au handle spécifié, versions le mutex ou l’intervalle de délai d’attente spécifié se soit écoulé.

### <a name="public-operator"></a>Opérateur public

Name                                 | Description
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operator=](#operator-assign) | Assigne le texte spécifié (déplace) `Mutex` objet actuel `Mutex` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Mutex`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="lock"></a>Mutex::Lock

Attend jusqu'à ce que l’objet actuel, ou le `Mutex` objet associé au handle spécifié, versions le mutex ou l’intervalle de délai d’attente spécifié se soit écoulé.

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
Le handle d’un `Mutex` objet.

### <a name="return-value"></a>Valeur de retour

## <a name="mutex"></a>Mutex::Mutex

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
Un handle ou une référence rvalue à un handle, pour un `Mutex` objet.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un `Mutex` objet à partir du handle spécifié. Le deuxième constructeur initialise un `Mutex` objet à partir du handle spécifié, puis passe la propriété du mutex actuel `Mutex` objet.

## <a name="operator-assign"></a>Mutex::operator=

Assigne le texte spécifié (déplace) `Mutex` objet actuel `Mutex` objet.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une référence rvalue à un `Mutex` objet.

### <a name="return-value"></a>Valeur de retour

Une référence à l’actuel `Mutex` objet.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le **sémantique déplacer** section de [déclarateur de référence Rvalue : & &](../../cpp/rvalue-reference-declarator-amp-amp.md).
