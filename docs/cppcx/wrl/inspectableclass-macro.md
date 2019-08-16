---
title: InspectableClass, macro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: ee2a76edb967923a03ce6720b4163baf1cc48c32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500478"
---
# <a name="inspectableclass-macro"></a>InspectableClass, macro

Définit le nom de la classe d’exécution et le niveau de confiance.

## <a name="syntax"></a>Syntaxe

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Paramètres

*runtimeClassName*<br/>
Nom textuel complet de la classe Runtime.

*trustLevel*<br/>
Une des valeurs énumérées de [trustLevel](/windows/win32/api/inspectable/ne-inspectable-trustlevel) .

## <a name="remarks"></a>Notes

La macro **inspectableclass,** peut être utilisée uniquement avec des types de Windows Runtime.

## <a name="requirements"></a>Configuration requise

**En-tête:** Implements. h

**Espace de noms :** Microsoft:: WRL

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](runtimeclass-class.md)