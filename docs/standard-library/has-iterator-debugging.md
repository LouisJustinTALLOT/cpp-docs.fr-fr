---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: 339c32f9b487db2e318f8763ac01a0d155fc1dc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159702"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Remplacé par [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), cette macro définit si la fonctionnalité de débogage d’itérateur est activée dans une version de débogage. Par défaut, le débogage d’itérateur est activé dans les versions de débogage et désactivé dans les versions commerciales. Pour plus d’informations, consultez [Itérateurs de débogage, prise en charge](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> Utilisation directe de la macro _SECURE_SCL est déconseillée. Au lieu de cela, utilisez _ITERATOR_DEBUG_LEVEL pour contrôler les paramètres de débogage itérateur. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Notes

Pour activer le débogage d’itérateur dans les versions debug, la valeur _ITERATOR_DEBUG_LEVEL 2. Cela équivaut à un paramètre _SECURE_SCL 1, ou activé :

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

_ITERATOR_DEBUG_LEVEL ne peut pas être défini sur 2 (et _SECURE_SCL ne peut pas être définie sur 1) dans les versions commerciales.

Pour désactiver les itérateurs de débogage dans les versions debug, la valeur _ITERATOR_DEBUG_LEVEL 0 ou 1. Cela équivaut à un paramètre _SECURE_SCL 0 ou désactivé :

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Voir aussi

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Bibliothèques sécurisées : Bibliothèque C++ Standard](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
