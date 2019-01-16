---
title: Classe d’événements (WRL)
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
ms.openlocfilehash: 2d36b4fa3d1824f43e0cfafe55c439a6bdeccb6f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336411"
---
# <a name="event-class-wrl"></a>Classe d’événements (WRL)

Représente un événement.

## <a name="syntax"></a>Syntaxe

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                   | Description
---------------------- | ------------------------------------------------
[Event::Event](#event) | Initialise une nouvelle instance de la classe `Event`.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                 | Description
------------------------------------ | ------------------------------------------------------------------------
[Event::operator=](#operator-assign) | Assigne le texte spécifié `Event` référence à actuel `Event` instance.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

`Event`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="event"></a>Event::Event

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
Handle vers un événement. Par défaut, *h* est initialisée à `nullptr`.

## <a name="operator-assign"></a>Event::operator=

Assigne le texte spécifié `Event` référence à actuel `Event` instance.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une référence rvalue à un `Event` instance.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’actuel `Event` instance.
