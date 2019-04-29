---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: dcfaee2906136dffbe79a49f089a079104112e78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295745"
---
# <a name="securescl"></a>_SECURE_SCL

Remplacée par [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), cette macro définit si les [itérateurs vérifiés](../standard-library/checked-iterators.md) sont activés. Par défaut, les itérateurs vérifiés sont activés dans les versions de débogage et désactivés dans les versions commerciales.

> [!IMPORTANT]
> Utilisation directe de la macro _SECURE_SCL est déconseillée. Au lieu de cela, utilisez _ITERATOR_DEBUG_LEVEL aux paramètres d’itérateur vérifié de contrôle. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Notes

Quand les itérateurs vérifiés sont activés, toute utilisation non sécurisée d’un itérateur provoque une erreur d’exécution et le programme se termine. Pour activer les itérateurs vérifiés, définissez _ITERATOR_DEBUG_LEVEL sur 1 ou 2. Cela équivaut à un paramètre _SECURE_SCL 1, ou activé :

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Pour désactiver les itérateurs vérifiés, définissez _ITERATOR_DEBUG_LEVEL à 0. Cela équivaut à un paramètre _SECURE_SCL 0 ou désactivé :

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Pour plus d’informations sur la façon de désactiver les avertissements concernant les itérateurs vérifiés, consultez [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Voir aussi

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Bibliothèques sécurisées : Bibliothèque C++ Standard](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
