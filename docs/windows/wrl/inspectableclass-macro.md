---
title: InspectableClass, macro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: bdc3dc5b54aa28280f22b1481a9be20ee0be22c6
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336125"
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

*runtimeClassName*<br/>
Le nom textuel complet de la classe runtime.

*trustLevel*<br/>
Parmi les [TrustLevel](https://msdn.microsoft.com/library/br224625.aspx) valeurs énumérées.

## <a name="remarks"></a>Notes

Le **InspectableClass** macro peut être utilisée uniquement avec les types Windows Runtime.

## <a name="requirements"></a>Spécifications

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](runtimeclass-class.md)