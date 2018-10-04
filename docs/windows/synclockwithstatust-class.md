---
title: Synclockwithstatust, classe | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7e59631592cd0bf9d147110e1a72d27d4bc781e
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789083"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT, classe

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Paramètres

*SyncTraits*<br/>
Un type qui peut prendre exclusif ou la propriété d’une ressource partagée.

## <a name="remarks"></a>Notes

Représente un type qui peut prendre exclusif ou la propriété d’une ressource partagée.

Le `SyncLockWithStatusT` classe est utilisée pour implémenter le [Mutex](../windows/mutex-class1.md) et [sémaphore](../windows/semaphore-class.md) classes.

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
[SyncLockWithStatusT::GetStatus](#getstatus) | Récupère l’état d’attente de l’actuel `SyncLockWithStatusT` objet.
[SyncLockWithStatusT::IsLocked](#islocked)   | Indique si l’actuel `SyncLockWithStatusT` objet possède une ressource, c'est-à-dire, le `SyncLockWithStatusT` objet est *verrouillé*.

### <a name="protected-data-members"></a>Membres de données protégés

Name                                    | Description
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Contient le résultat de l’opération d’attente sous-jacente après une opération de verrouillage sur un objet selon actuel `SyncLockWithStatusT` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::Details

## <a name="getstatus"></a>SyncLockWithStatusT::GetStatus

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Valeur de retour

Le résultat d’une opération d’attente sur l’objet qui est basé sur le `SyncLockWithStatusT` de classe, comme un [Mutex](../windows/mutex-class1.md) ou [sémaphore](../windows/semaphore-class.md). Zéro (0) indique que l’opération d’attente a renvoyé l’état signalé ; Sinon, un autre état s’est produite, telles que la valeur de délai d’expiration est écoulé.

### <a name="remarks"></a>Notes

Récupère l’état d’attente de l’actuel `SyncLockWithStatusT` objet.

La fonction GetStatus() récupère la valeur de l’objet sous-jacent [status_](#status) membre de données. Quand un objet basé sur la `SyncLockWithStatusT` classe effectue une opération de verrouillage, l’objet attend tout d’abord l’objet devienne disponible. Le résultat de cette opération d’attente est stocké dans le `status_` membre de données. Les valeurs possibles de le `status_` membre de données sont les valeurs de retour de l’opération d’attente. Pour plus d’informations, consultez les valeurs de retour de la `WaitForSingleObjectEx()` (fonction) dans MSDN Library.

## <a name="islocked"></a>SyncLockWithStatusT::IsLocked

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Notes

Indique si l’actuel `SyncLockWithStatusT` objet possède une ressource, c'est-à-dire, le `SyncLockWithStatusT` objet est *verrouillé*.

### <a name="return-value"></a>Valeur de retour

`true` Si le `SyncLockWithStatusT` objet est verrouillé ; sinon, `false`.

## <a name="status"></a>SyncLockWithStatusT::status_

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Notes

Contient le résultat de l’opération d’attente sous-jacente après une opération de verrouillage sur un objet selon actuel `SyncLockWithStatusT` objet.

## <a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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

*other*<br/>
Une référence rvalue à un autre `SyncLockWithStatusT` objet.

*sync*<br/>
Une référence à un autre `SyncLockWithStatusT` objet.

*status*<br/>
La valeur de la [status_](#status) membre de données de la *autres* paramètre ou le *synchronisation* paramètre.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `SyncLockWithStatusT`.

Le premier constructeur initialise actuel `SyncLockWithStatusT` objet à partir d’un autre `SyncLockWithStatusT` spécifié par le paramètre *autres*et puis invalide l’autre `SyncLockWithStatusT` objet. Le deuxième constructeur est `protected`et l’initialise actuel `SyncLockWithStatusT` objet à un état non valide.
