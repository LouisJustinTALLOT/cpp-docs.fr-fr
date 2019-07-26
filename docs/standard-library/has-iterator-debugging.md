---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: a1e3017ed7c6def18ce02d99dc8253b69c11ab58
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448831"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Remplacé par [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), cette macro définit si la fonctionnalité de débogage d’itérateur est activée dans une version de débogage. Par défaut, le débogage d’itérateur est activé dans les versions de débogage et désactivé dans les versions commerciales. Pour plus d’informations, consultez [Itérateurs de débogage, prise en charge](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> L’utilisation directe de la macro _HAS_ITERATOR_DEBUGGING est déconseillée. Utilisez plutôt _ITERATOR_DEBUG_LEVEL pour contrôler les paramètres de débogage d’itérateur. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Notes

Pour activer le débogage d’itérateur dans les versions Debug, affectez la valeur 2 à _ITERATOR_DEBUG_LEVEL. Cela équivaut à un paramètre _HAS_ITERATOR_DEBUGGING égal à 1 ou activé:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

_ITERATOR_DEBUG_LEVEL ne peut pas avoir la valeur 2 (et _HAS_ITERATOR_DEBUGGING ne peut pas avoir la valeur 1) dans les versions commerciales.

Pour désactiver les itérateurs de débogage dans les versions Debug, affectez à _ITERATOR_DEBUG_LEVEL la valeur 0 ou 1. Cela équivaut à un paramètre _HAS_ITERATOR_DEBUGGING égal à 0 ou désactivé:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Voir aussi

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[Itérateurs de débogage, prise en charge](../standard-library/debug-iterator-support.md)\
[Itérateurs vérifiés](../standard-library/checked-iterators.md)\
[Bibliothèques sécurisées : Bibliothèque C++ Standard](../standard-library/safe-libraries-cpp-standard-library.md)
