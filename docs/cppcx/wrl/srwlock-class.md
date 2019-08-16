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
ms.openlocfilehash: 079f1abe652d8c1610a084f5e1158cc5798d61c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498292"
---
# <a name="srwlock-class"></a>SRWLock (classe)

Représente un verrou de lecture/écriture Slim.

## <a name="syntax"></a>Syntaxe

```cpp
class SRWLock;
```

## <a name="remarks"></a>Notes

Un verrou de lecture/écriture Slim est utilisé pour synchroniser l’accès entre les threads à un objet ou une ressource. Pour plus d’informations, consultez [fonctions de synchronisation](/windows/win32/Sync/synchronization-functions).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom                | Description
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonyme d’un `SRWLock` objet qui est acquis en mode exclusif.
`SyncLockShared`    | Synonyme d’un `SRWLock` objet qui est acquis en mode partagé.

### <a name="public-constructors"></a>Constructeurs publics

Nom                                     | Description
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Initialise une nouvelle instance de la classe `SRWLock`.
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | Déinitialise une instance de la `SRWLock` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                           | Description
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Acquiert un `SRWLock` objet en mode exclusif.
[SRWLock::LockShared](#lockshared)             | Acquiert un `SRWLock` objet en mode partagé.
[SRWLock::TryLockExclusive](#trylockexclusive) | Tente d’acquérir un `SRWLock` objet en mode exclusif pour l’objet actuel ou `SRWLock` spécifié.
[SRWLock::TryLockShared](#trylockshared)       | Tente d’acquérir un `SRWLock` objet en mode partagé pour l’objet actuel ou `SRWLock` spécifié.

### <a name="protected-data-member"></a>Membre de données protégées

Nom                                      | Description
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock:: SRWLock_](#srwlock-data-member) | Contient la variable de verrouillage sous-jacente `SRWLock` pour l’objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLock`

## <a name="requirements"></a>Configuration requise

**En-tête:** corewrappers. h

**Espace de noms :** Microsoft:: WRL:: wrappers

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

Déinitialise une instance de la `SRWLock` classe.

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

`SRWLock` Objet en mode exclusif.

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

`SRWLock` Objet en mode partagé.

## <a name="srwlock-constructor"></a>SRWLock:: SRWLock

Initialise une nouvelle instance de la classe `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

Contient la variable de verrouillage sous-jacente `SRWLock` pour l’objet actuel.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Tente d’acquérir un `SRWLock` objet en mode exclusif pour l’objet actuel ou `SRWLock` spécifié. Si l’appel réussit, le thread appelant prend la propriété du verrou.

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

En cas de réussite `SRWLock` , un objet en mode exclusif et le thread appelant prennent la propriété du verrou. Sinon, un `SRWLock` objet dont l’État n’est pas valide.

## <a name="trylockshared"></a>SRWLock::TryLockShared

Tente d’acquérir un `SRWLock` objet en mode partagé pour l’objet actuel ou `SRWLock` spécifié.

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

En cas de réussite `SRWLock` , un objet en mode partagé et le thread appelant prennent la propriété du verrou. Sinon, un `SRWLock` objet dont l’État n’est pas valide.
