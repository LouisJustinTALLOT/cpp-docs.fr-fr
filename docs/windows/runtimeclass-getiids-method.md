---
title: Runtimeclass::getiids, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d3c16d54b08d0c687b33381107eb17be351e9d6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589480"
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids, méthode

Obtient un tableau qui contient l’interface implémentées par actuel des ID **RuntimeClass** objet.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   GetIids
)  
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Paramètres

*iidCount*  
Lorsque cette opération se termine, le nombre total d’éléments du tableau *IID*.

*IID*  
Lorsque cette opération se termine, un pointeur vers un tableau d’ID d’interface.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_OUTOFMEMORY.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](../windows/runtimeclass-class.md)