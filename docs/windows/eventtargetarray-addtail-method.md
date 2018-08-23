---
title: Eventtargetarray::AddTail, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
dev_langs:
- C++
helpviewer_keywords:
- AddTail method
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6609bba6d7adbddda152007e4db45c82f8039bc0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603676"
---
# <a name="eventtargetarrayaddtail-method"></a>EventTargetArray::AddTail, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Paramètres

*Élément*  
Pointeur vers le Gestionnaire d’événements à ajouter.

## <a name="remarks"></a>Notes

Ajoute le Gestionnaire d’événements spécifié à la fin du tableau interne de gestionnaires d’événements.

**AddTail()** est destinée à être utilisée en interne par uniquement la `EventSource` classe.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[EventTargetArray, classe](../windows/eventtargetarray-class.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)