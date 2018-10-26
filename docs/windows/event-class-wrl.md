---
title: Classe d’événements (WRL) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7fce42093eb5d5c9eede67699b58124218d924d4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075461"
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
[Event::operator =](#operator-assign) | Assigne le texte spécifié `Event` référence à actuel `Event` instance.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

`Event`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

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

## <a name="operator-assign"></a>Event::operator =

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
