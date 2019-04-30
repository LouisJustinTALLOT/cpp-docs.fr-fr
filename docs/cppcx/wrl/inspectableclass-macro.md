---
title: InspectableClass, macro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 9d194f5a87ac4a142301bc896cb3ed172f119473
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398188"
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

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](runtimeclass-class.md)