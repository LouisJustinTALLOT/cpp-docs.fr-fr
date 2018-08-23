---
title: Classe d’événements (Windows Runtime bibliothèque de modèles C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
dev_langs:
- C++
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b40e9c5e04c21cdbcc56581e02751edc84e4617d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606287"
---
# <a name="event-class-windows-runtime-c-template-library"></a>Event, classe (bibliothèque de modèles Windows Runtime C++)

Représente un événement.

## <a name="syntax"></a>Syntaxe

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Event::Event, constructeur (bibliothèque de modèles Windows Runtime C++)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|Initialise une nouvelle instance de la **événement** classe.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Event::operator=, opérateur](../windows/event-operator-assign-operator.md)|Assigne le texte spécifié **événement** référence à le **événement** instance.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

`Event`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)