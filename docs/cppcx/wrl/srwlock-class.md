---
title: SRWLock (classe)
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: 6d4a504d9465c858af59a88cf0ef611bf88c3fde
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784683"
---
# <a name="srwlock-class"></a>SRWLock (classe)

Représente un verrou SRW.

## <a name="syntax"></a>Syntaxe

```cpp
class SRWLock;
```

## <a name="remarks"></a>Notes

Un verrou SRW est utilisé pour synchroniser l’accès entre plusieurs threads à un objet ou une ressource. Pour plus d’informations, consultez [des fonctions de synchronisation](/windows/desktop/Sync/synchronization-functions).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom                | Description
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonyme pour un `SRWLock` objet est acquis en mode exclusif.
`SyncLockShared`    | Synonyme pour un `SRWLock` objet est acquis en mode partagé.

### <a name="public-constructors"></a>Constructeurs publics

Nom                                     | Description
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Initialise une nouvelle instance de la classe `SRWLock`.
[SRWLock::~SRWLock](#tilde-srwlock)      | Annule l’initialisation d’une instance de la `SRWLock` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                           | Description
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Acquiert un `SRWLock` objet en mode exclusif.
[SRWLock::LockShared](#lockshared)             | Acquiert un `SRWLock` objet en mode partagé.
[SRWLock::TryLockExclusive](#trylockexclusive) | Tente d’acquérir un `SRWLock` objet en mode exclusif pour la valeur actuelle ou spécifiée `SRWLock` objet.
[SRWLock::TryLockShared](#trylockshared)       | Tente d’acquérir un `SRWLock` objet en mode partagé pour la valeur actuelle ou spécifiée `SRWLock` objet.

### <a name="protected-data-member"></a>Membre de données protégées

Nom                                      | Description
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Contient la variable sous-jacente de verrou actif `SRWLock` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLock`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="tilde-srwlock"></a>SRWLock :: ~ SRWLock

Annule l’initialisation d’une instance de la `SRWLock` classe.

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

Acquiert un `SRWLock` objet en mode exclusif.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Pointeur vers un `SRWLock` objet.

### <a name="return-value"></a>Valeur de retour

Un `SRWLock` objet en mode exclusif.

## <a name="lockshared"></a>SRWLock::LockShared

Acquiert un `SRWLock` objet en mode partagé.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Pointeur vers un `SRWLock` objet.

### <a name="return-value"></a>Valeur de retour

Un `SRWLock` objet en mode partagé.

## <a name="srwlock-constructor"></a>SRWLock::SRWLock

Initialise une nouvelle instance de la classe `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

Contient la variable sous-jacente de verrou actif `SRWLock` objet.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Tente d’acquérir un `SRWLock` objet en mode exclusif pour la valeur actuelle ou spécifiée `SRWLock` objet. Si l’appel réussit, le thread appelant prend possession du verrou.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Pointeur vers un `SRWLock` objet.

### <a name="return-value"></a>Valeur de retour

Si l’opération réussit, un `SRWLock` objet en mode exclusif et que le thread appelant prend possession du verrou. Sinon, un `SRWLock` objet dont l’état n’est pas valide.

## <a name="trylockshared"></a>SRWLock::TryLockShared

Tente d’acquérir un `SRWLock` objet en mode partagé pour la valeur actuelle ou spécifiée `SRWLock` objet.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Pointeur vers un `SRWLock` objet.

### <a name="return-value"></a>Valeur de retour

Si l’opération réussit, un `SRWLock` objet dans le mode partagé et le thread appelant prend possession du verrou. Sinon, un `SRWLock` objet dont l’état n’est pas valide.
