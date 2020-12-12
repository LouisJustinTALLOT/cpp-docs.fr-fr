---
description: 'En savoir plus sur : classe d’événements (WRL)'
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
ms.openlocfilehash: e3a61a40d1160830df80a7e0650e60fbf803e3d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272823"
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

## <a name="eventevent"></a><a name="event"></a> Event :: Event

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

## <a name="eventoperator"></a><a name="operator-assign"></a> Event :: Operator =

Assigne la `Event` référence spécifiée à l' `Event` instance actuelle.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Référence rvalue à une `Event` instance.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’instance actuelle `Event` .
