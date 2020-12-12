---
description: 'En savoir plus sur : _SECURE_SCL'
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: 1a0e32ada449709a60eb601138ce0bb8b7ae9123
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197099"
---
# <a name="_secure_scl"></a>_SECURE_SCL

Remplacée par [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), cette macro définit si les [itérateurs vérifiés](../standard-library/checked-iterators.md) sont activés. Par défaut, les itérateurs vérifiés sont activés dans les versions de débogage et désactivés dans les versions commerciales.

> [!IMPORTANT]
> L’utilisation directe de la macro _SECURE_SCL est déconseillée. Utilisez plutôt _ITERATOR_DEBUG_LEVEL pour contrôler les paramètres des itérateurs vérifiés. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Notes

Quand les itérateurs vérifiés sont activés, toute utilisation non sécurisée d’un itérateur provoque une erreur d’exécution et le programme se termine. Pour activer les itérateurs vérifiés, affectez à _ITERATOR_DEBUG_LEVEL la valeur 1 ou 2. Cela équivaut à un paramètre de _SECURE_SCL égal à 1 ou activé :

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Pour désactiver les itérateurs vérifiés, affectez à _ITERATOR_DEBUG_LEVEL la valeur 0. Cela équivaut à un paramètre de _SECURE_SCL égal à 0 ou désactivé :

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Pour plus d’informations sur la façon de désactiver les avertissements concernant les itérateurs vérifiés, consultez [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Voir aussi

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[Itérateurs vérifiés](../standard-library/checked-iterators.md)\
[Prise en charge des itérateurs de débogage](../standard-library/debug-iterator-support.md)\
[Bibliothèques sécurisées : bibliothèque standard C++](../standard-library/safe-libraries-cpp-standard-library.md)
