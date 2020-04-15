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
ms.openlocfilehash: 85b4c2d1f1a27e90a65e47aa749e079f4aa08739
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371522"
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
[Événement::Événement](#event) | Initialise une nouvelle instance de la classe `Event`.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                 | Description
------------------------------------ | ------------------------------------------------------------------------
[Événement::opérateur](#operator-assign) | Attribue la `Event` référence spécifiée `Event` à l’instance actuelle.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

`Event`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="eventevent"></a><a name="event"></a>Événement::Événement

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
Handle vers un événement. Par défaut, *h* est `nullptr`parasé à .

## <a name="eventoperator"></a><a name="operator-assign"></a>Événement::opérateur

Attribue la `Event` référence spécifiée `Event` à l’instance actuelle.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une référence rvalue `Event` à une instance.

### <a name="return-value"></a>Valeur de retour

Un pointeur `Event` à l’instance actuelle.
