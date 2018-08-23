---
title: Runtimeclass::getweakreference, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
dev_langs:
- C++
helpviewer_keywords:
- GetWeakReference method
ms.assetid: 26656ace-7f20-4364-87c9-4a75dd30912e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc4d2e542afcd72426cb3b0aba57b7d7cbabad06
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583642"
---
# <a name="runtimeclassgetweakreference-method"></a>RuntimeClass::GetWeakReference, méthode

Obtient un pointeur vers l’objet de référence faible pour actuel **RuntimeClass** objet.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Paramètres

*weakReference*  
Lorsque cette opération se termine, un pointeur vers un objet de référence faible.

## <a name="return-value"></a>Valeur de retour

Toujours S_OK.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](../windows/runtimeclass-class.md)