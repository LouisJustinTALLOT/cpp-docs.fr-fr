---
title: SyncLockWithStatusT, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 77bcb8336e4650de7ed01a067fa1bdd7ec0ba3e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374265"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT, classe

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Paramètres

*SyncTraits SyncTraits*<br/>
Un type qui peut prendre la propriété exclusive ou partagée d’une ressource.

## <a name="remarks"></a>Notes

Représente un type qui peut prendre la propriété exclusive ou partagée d’une ressource.

La `SyncLockWithStatusT` classe est utilisée pour mettre en œuvre les classes [Mutex](mutex-class.md) et [Semaphore.](semaphore-class.md)

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                             | Description
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Initialise une nouvelle instance de la classe `SyncLockWithStatusT`.

### <a name="protected-constructors"></a>Constructeurs protégés

Nom                                                             | Description
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Initialise une nouvelle instance de la classe `SyncLockWithStatusT`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                         | Description
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | Récupère l’état d’attente de l’objet actuel. `SyncLockWithStatusT`
[SyncLockWithStatusT::IsLocked](#islocked)   | indique si `SyncLockWithStatusT` l’objet actuel possède une ressource; c’est-à-dire que l’objet `SyncLockWithStatusT` est *verrouillé*.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                                    | Description
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Détient le résultat de l’opération d’attente sous-jacente `SyncLockWithStatusT` après une opération de verrouillage sur un objet basé sur l’objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers::Details

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>SyncLockWithStatusT::GetStatus

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Valeur de retour

Le résultat d’une opération d’attente `SyncLockWithStatusT` sur l’objet qui est basé sur la classe, comme un [Mutex](mutex-class.md) ou [Sémaphore](semaphore-class.md). Zéro (0) indique que l’opération d’attente a renvoyé l’état signalé; autrement, un autre état s’est produit, comme la valeur de temps d’out s’est écoulée.

### <a name="remarks"></a>Notes

Récupère l’état d’attente de l’objet actuel. `SyncLockWithStatusT`

La fonction GetStatus() récupère la valeur du membre sous-jacent [des données status_.](#status) Lorsqu’un objet `SyncLockWithStatusT` basé sur la classe effectue une opération de verrouillage, l’objet attend d’abord que l’objet soit disponible. Le résultat de cette opération `status_` d’attente est stocké dans le membre des données. Les valeurs possibles `status_` du membre de données sont les valeurs de retour de l’opération d’attente. Pour plus d’informations, consultez `WaitForSingleObjectEx()` les valeurs de retour de la fonction dans la bibliothèque MSDN.

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>SyncLockWithStatusT::IsLocked

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Notes

indique si `SyncLockWithStatusT` l’objet actuel possède une ressource; c’est-à-dire que l’objet `SyncLockWithStatusT` est *verrouillé*.

### <a name="return-value"></a>Valeur de retour

**vrai** si `SyncLockWithStatusT` l’objet est verrouillé; autrement, **faux**.

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>SyncLockWithStatusT::status_

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Notes

Détient le résultat de l’opération d’attente sous-jacente `SyncLockWithStatusT` après une opération de verrouillage sur un objet basé sur l’objet actuel.

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Une référence rvalue `SyncLockWithStatusT` à un autre objet.

*Synchronisation*<br/>
Une référence `SyncLockWithStatusT` à un autre objet.

*statut*<br/>
La valeur du [status_](#status) membre des données de *l’autre* paramètre ou le *paramètre de synchronisation.*

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `SyncLockWithStatusT`.

Le premier constructeur initialise `SyncLockWithStatusT` l’objet `SyncLockWithStatusT` actuel à partir d’un `SyncLockWithStatusT` autre spécifié par un autre *paramètre,* puis invalide l’autre objet. Le deuxième constructeur `protected`est, et initialise l’objet actuel `SyncLockWithStatusT` à un état invalide.
