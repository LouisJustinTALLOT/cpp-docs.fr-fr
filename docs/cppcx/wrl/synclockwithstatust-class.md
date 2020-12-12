---
description: 'En savoir plus sur : classe SyncLockWithStatusT'
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
ms.openlocfilehash: 6a19ae22253fddd48c7baaf29e4b88a4863b89bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186153"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT, classe

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Paramètres

*SyncTraits*<br/>
Type qui peut prendre la propriété exclusive ou partagée d’une ressource.

## <a name="remarks"></a>Notes

Représente un type qui peut prendre la propriété exclusive ou partagée d’une ressource.

La `SyncLockWithStatusT` classe est utilisée pour implémenter les classes [mutex](mutex-class.md) et [Semaphore](semaphore-class.md) .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                             | Description
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT :: SyncLockWithStatusT](#synclockwithstatust) | Initialise une nouvelle instance de la classe `SyncLockWithStatusT`.

### <a name="protected-constructors"></a>Constructeurs protégés

Nom                                                             | Description
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT :: SyncLockWithStatusT](#synclockwithstatust) | Initialise une nouvelle instance de la classe `SyncLockWithStatusT`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                         | Description
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT :: GetStatus](#getstatus) | Récupère l’état d’attente de l' `SyncLockWithStatusT` objet actuel.
[SyncLockWithStatusT :: IsLocked](#islocked)   | Indique si l' `SyncLockWithStatusT` objet actuel possède une ressource ; autrement dit, l' `SyncLockWithStatusT` objet est *verrouillé*.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                                    | Description
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT :: status_](#status) | Contient le résultat de l’opération d’attente sous-jacente après une opération de verrouillage sur un objet basé sur l' `SyncLockWithStatusT` objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers ::D étails

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a> SyncLockWithStatusT :: GetStatus

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Valeur renvoyée

Résultat d’une opération d’attente sur l’objet qui est basé sur la `SyncLockWithStatusT` classe, tel qu’un [mutex](mutex-class.md) ou un [sémaphore](semaphore-class.md). Zéro (0) indique que l’opération d’attente a retourné l’état signalé ; dans le cas contraire, un autre État s’est produit, tel que la valeur du délai d’attente s’est écoulée.

### <a name="remarks"></a>Notes

Récupère l’état d’attente de l' `SyncLockWithStatusT` objet actuel.

La fonction GetStatus () récupère la valeur du membre de données [STATUS_](#status) sous-jacent. Lorsqu’un objet basé sur la `SyncLockWithStatusT` classe effectue une opération de verrouillage, l’objet commence par attendre que l’objet devienne disponible. Le résultat de cette opération d’attente est stocké dans le `status_` membre de données. Les valeurs possibles du `status_` membre de données sont les valeurs de retour de l’opération d’attente. Pour plus d’informations, consultez les valeurs de retour de la [`WaitForSingleObjectEx`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobjectex) fonction.

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a> SyncLockWithStatusT :: IsLocked

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Notes

Indique si l' `SyncLockWithStatusT` objet actuel possède une ressource ; autrement dit, l' `SyncLockWithStatusT` objet est *verrouillé*.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l' `SyncLockWithStatusT` objet est verrouillé ; sinon, **`false`** .

## <a name="synclockwithstatuststatus_"></a><a name="status"></a> SyncLockWithStatusT :: status_

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Notes

Contient le résultat de l’opération d’attente sous-jacente après une opération de verrouillage sur un objet basé sur l' `SyncLockWithStatusT` objet actuel.

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a> SyncLockWithStatusT :: SyncLockWithStatusT

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

*autres*<br/>
Référence rvalue à un autre `SyncLockWithStatusT` objet.

*synchronisation*<br/>
Référence à un autre `SyncLockWithStatusT` objet.

*statut*<br/>
Valeur de la [STATUS_](#status) membre de données de l' *autre* paramètre ou du paramètre de *synchronisation* .

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `SyncLockWithStatusT`.

Le premier constructeur initialise l’objet actuel `SyncLockWithStatusT` à partir d’un autre `SyncLockWithStatusT` spécifié par le paramètre *other*, puis invalide l’autre `SyncLockWithStatusT` objet. Le deuxième constructeur est **`protected`** , et initialise l’objet actuel `SyncLockWithStatusT` à un État non valide.
