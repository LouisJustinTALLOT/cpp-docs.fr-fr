---
title: SyncLockT (classe)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: 52c4404fa28f680a9a7a4592d03f535e8406d1a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374282"
---
# <a name="synclockt-class"></a>SyncLockT (classe)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Paramètres

*SyncTraits SyncTraits*<br/>
Le type qui peut prendre possession d’une ressource.

## <a name="remarks"></a>Notes

Représente un type qui peut prendre la propriété exclusive ou partagée d’une ressource.

La `SyncLockT` classe est utilisée, par exemple, pour aider à mettre en œuvre la classe [SRWLock.](srwlock-class.md)

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                      | Description
----------------------------------------- | ----------------------------------------------------
[SyncLockt::SyncLockt](#synclockt)        | Initialise une nouvelle instance de la classe `SyncLockT`.
[SyncLockt: :-SyncLockt](#tilde-synclockt) | Désinitialise un exemple `SyncLockT` de la classe.

### <a name="protected-constructors"></a>Constructeurs protégés

Nom                               | Description
---------------------------------- | ----------------------------------------------------
[SyncLockt::SyncLockt](#synclockt) | Initialise une nouvelle instance de la classe `SyncLockT`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                             | Description
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::IsLocked](#islocked) | indique si `SyncLockT` l’objet actuel possède une ressource; c’est-à-dire que l’objet `SyncLockT` est *verrouillé*.
[SyncLockT::Unlock](#unlock)     | Libère le contrôle de la `SyncLockT` ressource détenue par l’objet actuel, le cas échéant.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                      | Description
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Détient la ressource sous-jacente représentée par la `SyncLockT` classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SyncLockT`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers::Details

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>SyncLockt: :-SyncLockt

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Notes

Désinitialise un exemple `SyncLockT` de la classe.

Ce destructeur déverrouille `SyncLockT` également l’instance actuelle.

## <a name="synclocktislocked"></a><a name="islocked"></a>SyncLockT::IsLocked

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si `SyncLockT` l’objet est verrouillé; autrement, **faux**.

### <a name="remarks"></a>Notes

indique si `SyncLockT` l’objet actuel possède une ressource; c’est-à-dire que l’objet `SyncLockT` est *verrouillé*.

## <a name="synclocktsync_"></a><a name="sync"></a>SyncLockT::sync_

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Notes

Détient la ressource sous-jacente représentée par la `SyncLockT` classe.

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>SyncLockt::SyncLockt

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Une référence rvalue `SyncLockT` à un autre objet.

*Synchronisation*<br/>
Une référence `SyncLockWithStatusT` à un autre objet.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `SyncLockT`.

Le premier constructeur initialise `SyncLockT` l’objet `SyncLockT` actuel à partir d’un autre `SyncLockT` objet spécifié par un paramètre *autre,* puis invalide l’autre objet. Le deuxième constructeur `protected`est, et initialise l’objet actuel `SyncLockT` à un état invalide.

## <a name="synclocktunlock"></a><a name="unlock"></a>SyncLockT::Unlock

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void Unlock();
```

### <a name="remarks"></a>Notes

Libère le contrôle de la `SyncLockT` ressource détenue par l’objet actuel, le cas échéant.
