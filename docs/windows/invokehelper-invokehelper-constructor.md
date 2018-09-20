---
title: InvokeHelper::InvokeHelper, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- InvokeHelper, constructor
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11f3e82f0834863c3cdfb476443a4dbd0bdf1f6f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385077"
---
# <a name="invokehelperinvokehelper-constructor"></a>InvokeHelper::InvokeHelper, constructeur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Paramètres

*rappel*<br/>
Un gestionnaire d’événements.

## <a name="remarks"></a>Notes

Initialise une nouvelle instance de la **InvokeHelper** classe.

Le `TCallback` paramètre de modèle spécifie le type du Gestionnaire d’événements.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[InvokeHelper, structure](../windows/invokehelper-structure.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)