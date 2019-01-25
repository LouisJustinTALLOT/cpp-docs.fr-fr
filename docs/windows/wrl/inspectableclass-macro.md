---
title: InspectableClass, macro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: cedf395ae98a423e0335851327b5fdda1a4bc7d6
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893273"
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
Parmi les [TrustLevel](/windows/desktop/api/inspectable/ne-inspectable-trustlevel) valeurs énumérées.

## <a name="remarks"></a>Notes

Le **InspectableClass** macro peut être utilisée uniquement avec les types Windows Runtime.

## <a name="requirements"></a>Spécifications

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](runtimeclass-class.md)