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
ms.openlocfilehash: e305ad54e30455ce7c25f356c454791da0783591
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377277"
---
# <a name="srwlock-class"></a>SRWLock (classe)

Représente un verrou de lecteur/écrivain mince.

## <a name="syntax"></a>Syntaxe

```cpp
class SRWLock;
```

## <a name="remarks"></a>Notes

Un verrou lecteur/écrivain mince est utilisé pour synchroniser l’accès à travers les fils à un objet ou une ressource. Pour plus d’informations, voir [Fonctions de synchronisation](/windows/win32/Sync/synchronization-functions).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom                | Description
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonyme d’un `SRWLock` objet acquis en mode exclusif.
`SyncLockShared`    | Synonyme d’un `SRWLock` objet acquis en mode partagé.

### <a name="public-constructors"></a>Constructeurs publics

Nom                                     | Description
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Initialise une nouvelle instance de la classe `SRWLock`.
[SRWLock: :SRWLock](#tilde-srwlock)      | Désinitialise un exemple `SRWLock` de la classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                           | Description
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Acquiert `SRWLock` un objet en mode exclusif.
[SRWLock::LockShared](#lockshared)             | Acquiert `SRWLock` un objet en mode partagé.
[SRWLock::TryLockExclusive](#trylockexclusive) | Tentatives d’acquisition d’un `SRWLock` objet `SRWLock` en mode exclusif pour l’objet actuel ou spécifié.
[SRWLock::TryLockShared](#trylockshared)       | Tentatives d’acquisition d’un `SRWLock` objet `SRWLock` en mode partagé pour l’objet actuel ou spécifié.

### <a name="protected-data-member"></a>Membre des données protégées

Nom                                      | Description
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock:SRWLock_](#srwlock-data-member) | Contient la variable de `SRWLock` verrouillage sous-jacente pour l’objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLock`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="srwlocksrwlock"></a><a name="tilde-srwlock"></a>SRWLock: :SRWLock

Désinitialise un exemple `SRWLock` de la classe.

```cpp
~SRWLock();
```

## <a name="srwlocklockexclusive"></a><a name="lockexclusive"></a>SRWLock::LockExclusive

Acquiert `SRWLock` un objet en mode exclusif.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Pointeur `SRWLock` vers un objet.

### <a name="return-value"></a>Valeur de retour

Un `SRWLock` objet en mode exclusif.

## <a name="srwlocklockshared"></a><a name="lockshared"></a>SRWLock::LockShared

Acquiert `SRWLock` un objet en mode partagé.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Pointeur `SRWLock` vers un objet.

### <a name="return-value"></a>Valeur de retour

Un `SRWLock` objet en mode partagé.

## <a name="srwlocksrwlock"></a><a name="srwlock-constructor"></a>SRWLock::SRWLock

Initialise une nouvelle instance de la classe `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlocksrwlock_"></a><a name="srwlock-data-member"></a>SRWLock:SRWLock_

Contient la variable de `SRWLock` verrouillage sous-jacente pour l’objet actuel.

```cpp
SRWLOCK SRWLock_;
```

## <a name="srwlocktrylockexclusive"></a><a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Tentatives d’acquisition d’un `SRWLock` objet `SRWLock` en mode exclusif pour l’objet actuel ou spécifié. Si l’appel est réussi, le fil d’appel prend possession du verrou.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Pointeur `SRWLock` vers un objet.

### <a name="return-value"></a>Valeur de retour

En cas `SRWLock` de succès, un objet en mode exclusif et le fil d’appel prend possession de la serrure. Sinon, `SRWLock` un objet dont l’état est invalide.

## <a name="srwlocktrylockshared"></a><a name="trylockshared"></a>SRWLock::TryLockShared

Tentatives d’acquisition d’un `SRWLock` objet `SRWLock` en mode partagé pour l’objet actuel ou spécifié.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*Verrouillage*<br/>
Pointeur `SRWLock` vers un objet.

### <a name="return-value"></a>Valeur de retour

En cas `SRWLock` de succès, un objet en mode partagé et le fil d’appel prend possession de la serrure. Sinon, `SRWLock` un objet dont l’état est invalide.
