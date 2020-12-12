---
description: 'En savoir plus sur : classe Mutex'
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
ms.openlocfilehash: f69c14014a2283fe56ef8e7f705bebe5a5f6dc9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330843"
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
`SyncLock` | Synonyme pour une classe qui prend en charge les verrous synchrones.

### <a name="public-constructor"></a>Constructeur public

Nom                   | Description
---------------------- | ------------------------------------------------
[Mutex :: mutex](#mutex) | Initialise une nouvelle instance de la classe `Mutex`.

### <a name="public-members"></a>Membres publics

Nom                 | Description
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex :: Lock](#lock) | Attend la fin de l’objet actif ou de l' `Mutex` objet associé au handle spécifié, libère le mutex ou l’intervalle de délai d’attente spécifié s’est écoulé.

### <a name="public-operator"></a>Opérateur public

Nom                                 | Description
------------------------------------ | ---------------------------------------------------------------------------
[Mutex :: Operator =](#operator-assign) | Assigne (déplace) l' `Mutex` objet spécifié à l' `Mutex` objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Mutex`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="mutexlock"></a><a name="lock"></a> Mutex :: Lock

Attend la fin de l’objet actif ou de l' `Mutex` objet associé au handle spécifié, libère le mutex ou l’intervalle de délai d’attente spécifié s’est écoulé.

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
Handle d’un `Mutex` objet.

### <a name="return-value"></a>Valeur renvoyée

## <a name="mutexmutex"></a><a name="mutex"></a> Mutex :: mutex

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
Handle, ou référence rvalue à un handle, à un `Mutex` objet.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un `Mutex` objet à partir du handle spécifié. Le deuxième constructeur initialise un `Mutex` objet à partir du handle spécifié, puis déplace la propriété du mutex à l’objet actuel `Mutex` .

## <a name="mutexoperator"></a><a name="operator-assign"></a> Mutex :: Operator =

Assigne (déplace) l' `Mutex` objet spécifié à l' `Mutex` objet actuel.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Référence rvalue à un `Mutex` objet.

### <a name="return-value"></a>Valeur renvoyée

Référence à l’objet actuel `Mutex` .

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez la section relative à la **sémantique de déplacement** du [déclarateur de référence rvalue :  &&](../../cpp/rvalue-reference-declarator-amp-amp.md).
