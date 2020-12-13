---
description: 'En savoir plus sur : classe SyncLockT'
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
ms.openlocfilehash: 289a31d87ce395be2d2a72a8fe062c9c0bfa8f56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135107"
---
# <a name="synclockt-class"></a>SyncLockT (classe)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Paramètres

*SyncTraits*<br/>
Type qui peut prendre possession d’une ressource.

## <a name="remarks"></a>Notes

Représente un type qui peut prendre la propriété exclusive ou partagée d’une ressource.

La `SyncLockT` classe est utilisée, par exemple, pour aider à implémenter la classe [SRWLock](srwlock-class.md) .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                      | Description
----------------------------------------- | ----------------------------------------------------
[SyncLockT :: SyncLockT](#synclockt)        | Initialise une nouvelle instance de la classe `SyncLockT`.
[SyncLockT :: ~ SyncLockT](#tilde-synclockt) | Déinitialise une instance de la `SyncLockT` classe.

### <a name="protected-constructors"></a>Constructeurs protégés

Nom                               | Description
---------------------------------- | ----------------------------------------------------
[SyncLockT :: SyncLockT](#synclockt) | Initialise une nouvelle instance de la classe `SyncLockT`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                             | Description
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT :: IsLocked](#islocked) | Indique si l' `SyncLockT` objet actuel possède une ressource ; autrement dit, l' `SyncLockT` objet est *verrouillé*.
[SyncLockT :: Unlock](#unlock)     | Libère le contrôle de la ressource détenue par l' `SyncLockT` objet actuel, le cas échéant.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                      | Description
------------------------- | -------------------------------------------------------------------
[SyncLockT :: sync_](#sync) | Contient la ressource sous-jacente représentée par la `SyncLockT` classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SyncLockT`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers ::D étails

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a> SyncLockT :: ~ SyncLockT

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Notes

Déinitialise une instance de la `SyncLockT` classe.

Ce destructeur déverrouille également l' `SyncLockT` instance actuelle.

## <a name="synclocktislocked"></a><a name="islocked"></a> SyncLockT :: IsLocked

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l' `SyncLockT` objet est verrouillé ; sinon, **`false`** .

### <a name="remarks"></a>Notes

Indique si l' `SyncLockT` objet actuel possède une ressource ; autrement dit, l' `SyncLockT` objet est *verrouillé*.

## <a name="synclocktsync_"></a><a name="sync"></a> SyncLockT :: sync_

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Notes

Contient la ressource sous-jacente représentée par la `SyncLockT` classe.

## <a name="synclocktsynclockt"></a><a name="synclockt"></a> SyncLockT :: SyncLockT

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

*autres*<br/>
Référence rvalue à un autre `SyncLockT` objet.

*synchronisation*<br/>
Référence à un autre `SyncLockWithStatusT` objet.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `SyncLockT`.

Le premier constructeur initialise l’objet actuel `SyncLockT` à partir d’un autre `SyncLockT` objet spécifié par le paramètre *other*, puis invalide l’autre `SyncLockT` objet. Le deuxième constructeur est **`protected`** , et initialise l’objet actuel `SyncLockT` à un État non valide.

## <a name="synclocktunlock"></a><a name="unlock"></a> SyncLockT :: Unlock

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void Unlock();
```

### <a name="remarks"></a>Notes

Libère le contrôle de la ressource détenue par l' `SyncLockT` objet actuel, le cas échéant.
