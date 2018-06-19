---
title: _HAS_ITERATOR_DEBUGGING | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
dev_langs:
- C++
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab2de61df8c4e22b1955e9fd4798b5128a3e12be
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845893"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Remplacé par [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), cette macro définit si la fonctionnalité de débogage d’itérateur est activée dans une version de débogage. Par défaut, le débogage d’itérateur est activé dans les versions de débogage et désactivé dans les versions commerciales. Pour plus d’informations, consultez [Itérateurs de débogage, prise en charge](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> L’utilisation directe de la macro `_HAS_ITERATOR_DEBUGGING` est dépréciée. Utilisez plutôt `_ITERATOR_DEBUG_LEVEL` pour contrôler les paramètres de débogage d’itérateur. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Notes

Pour activer le débogage d’itérateur dans les versions de débogage, affectez la valeur 2 à `_ITERATOR_DEBUG_LEVEL`. Cela équivaut à un paramètre `_HAS_ITERATOR_DEBUGGING` de 1, ou activé :

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

`_ITERATOR_DEBUG_LEVEL` ne peut pas avoir la valeur 2 (et `_HAS_ITERATOR_DEBUGGING` ne peut pas avoir la valeur 1) dans les versions commerciales.

Pour désactiver les itérateurs de débogage dans les versions de débogage, affectez la valeur 0 ou 1 à `_ITERATOR_DEBUG_LEVEL`. Cela équivaut à un paramètre `_HAS_ITERATOR_DEBUGGING` de 0, ou désactivé :

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Voir aussi

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Bibliothèques sécurisées : bibliothèque standard C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
