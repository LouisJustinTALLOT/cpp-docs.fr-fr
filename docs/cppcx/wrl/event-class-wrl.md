---
title: Event, classe (WRL)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: 27a90bb801d1b6869b2391227464bb215dd42538
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220481"
---
# <a name="event-class-wrl"></a>Event, classe (WRL)

Représente un événement.

## <a name="syntax"></a>Syntaxe

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                   | Description
---------------------- | ------------------------------------------------
[Event :: Event](#event) | Initialise une nouvelle instance de la classe `Event`.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                 | Description
------------------------------------ | ------------------------------------------------------------------------
[Event :: Operator =](#operator-assign) | Assigne la `Event` référence spécifiée à l' `Event` instance actuelle.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

`Event`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="eventevent"></a><a name="event"></a>Event :: Event

Initialise une nouvelle instance de la classe `Event`.

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle vers un événement. Par défaut, *h* est initialisé à **`nullptr`** .

## <a name="eventoperator"></a><a name="operator-assign"></a>Event :: Operator =

Assigne la `Event` référence spécifiée à l' `Event` instance actuelle.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Référence rvalue à une `Event` instance.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’instance actuelle `Event` .
