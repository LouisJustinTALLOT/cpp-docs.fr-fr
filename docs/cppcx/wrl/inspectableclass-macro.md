---
description: 'En savoir plus sur : macro Inspectableclass,'
title: InspectableClass, macro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: cb19db7f35e7bda351cd84fa4dcf1f6a2b2ea2ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229000"
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

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[RuntimeClass, classe](runtimeclass-class.md)
