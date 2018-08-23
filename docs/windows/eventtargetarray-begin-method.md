---
title: Eventtargetarray::BEGIN, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::Begin
dev_langs:
- C++
helpviewer_keywords:
- Begin method
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 738ee52eb68cfbb03a380ffac52efdb4010b5205
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602129"
---
# <a name="eventtargetarraybegin-method"></a>EventTargetArray::Begin, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
ComPtr<IUnknown>* Begin();
```

## <a name="return-value"></a>Valeur de retour

L’adresse du premier élément dans le tableau interne de gestionnaires d’événements.

## <a name="remarks"></a>Notes

Obtient l’adresse du premier élément dans le tableau interne de gestionnaires d’événements.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[EventTargetArray, classe](../windows/eventtargetarray-class.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)