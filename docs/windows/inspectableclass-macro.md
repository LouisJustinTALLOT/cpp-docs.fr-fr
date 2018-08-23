---
title: Inspectableclass, Macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0a19635b635b80d65e0da99b8f50606154a5b4b2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594766"
---
# <a name="inspectableclass-macro"></a>InspectableClass, macro

Définit le niveau de confiance et de nom de la classe runtime.

## <a name="syntax"></a>Syntaxe

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)  
```

### <a name="parameters"></a>Paramètres

*runtimeClassName*  
Le nom textuel complet de la classe runtime.

*trustLevel*  
Parmi les [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) valeurs énumérées.

## <a name="remarks"></a>Notes

Le **InspectableClass** macro peut être utilisée uniquement avec les types Windows Runtime.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](../windows/runtimeclass-class.md)