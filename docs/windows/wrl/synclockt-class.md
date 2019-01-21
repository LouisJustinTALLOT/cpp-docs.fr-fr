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
ms.openlocfilehash: d27e6ba8601d0e822113bf3a4a65269c89437271
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336036"
---
# <a name="synclockt-class"></a>SyncLockT (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Paramètres

*SyncTraits*<br/>
Type qui peut prendre possession d’une ressource.

## <a name="remarks"></a>Notes

Représente un type qui peut prendre exclusif ou la propriété d’une ressource partagée.

Le `SyncLockT` classe est utilisée, par exemple, pour aider à implémenter la [SRWLock](srwlock-class.md) classe.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                      | Description
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | Initialise une nouvelle instance de la classe `SyncLockT`.
[SyncLockT::~SyncLockT](#tilde-synclockt) | Annule l’initialisation d’une instance de la `SyncLockT` classe.

### <a name="protected-constructors"></a>Constructeurs protégés

Nom                               | Description
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | Initialise une nouvelle instance de la classe `SyncLockT`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                             | Description
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::IsLocked](#islocked) | Indique si l’actuel `SyncLockT` objet possède une ressource, c'est-à-dire, le `SyncLockT` objet est *verrouillé*.
[SyncLockT::Unlock](#unlock)     | Contrôle de la ressource détenue par l’actuel `SyncLockT` de l’objet, le cas échéant.

### <a name="protected-data-members"></a>Membres de données protégés

Name                      | Description
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Contient la ressource sous-jacente représentée par la `SyncLockT` classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SyncLockT`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::WRL::Wrappers::Details

## <a name="tilde-synclockt"></a>SyncLockT::~SyncLockT

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Notes

Annule l’initialisation d’une instance de la `SyncLockT` classe.

Ce destructeur libère également actuel `SyncLockT` instance.

## <a name="islocked"></a>SyncLockT::IsLocked

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le `SyncLockT` objet est verrouillé ; sinon, **false**.

### <a name="remarks"></a>Notes

Indique si l’actuel `SyncLockT` objet possède une ressource, c'est-à-dire, le `SyncLockT` objet est *verrouillé*.

## <a name="sync"></a>SyncLockT::sync_

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Notes

Contient la ressource sous-jacente représentée par la `SyncLockT` classe.

## <a name="synclockt"></a>SyncLockT::SyncLockT

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Une référence rvalue à un autre `SyncLockT` objet.

*sync*<br/>
Une référence à un autre `SyncLockWithStatusT` objet.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `SyncLockT`.

Le premier constructeur initialise actuel `SyncLockT` objet à partir d’un autre `SyncLockT` objet spécifié par le paramètre *autres*et puis invalide l’autre `SyncLockT` objet. Le deuxième constructeur est `protected`et l’initialise actuel `SyncLockT` objet à un état non valide.

## <a name="unlock"></a>SyncLockT::Unlock

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
void Unlock();
```

### <a name="remarks"></a>Notes

Contrôle de la ressource détenue par l’actuel `SyncLockT` de l’objet, le cas échéant.