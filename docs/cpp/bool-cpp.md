---
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: e481cb9de7c80d147179efceab2fda9b160f3c21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184274"
---
# <a name="bool-c"></a>bool (C++)

Ce mot clé est un type intégré. Une variable de ce type peut avoir des valeurs [true](../cpp/true-cpp.md) et [false](../cpp/false-cpp.md). Expressions conditionnelles ont le type **bool** et ont ainsi des valeurs de type **bool**. Par exemple, `i!=0` a maintenant TRUE ou FALSE selon la valeur de `i`.

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : L’opérande d’un préfixe ou suffixe incrémentation ou de décrémentation opérateur ne peut pas être de type **bool**. En d’autres termes, avec une variable `b` de type **bool**, ces expressions ne sont plus autorisées :

```cpp
    b++;
    ++b;
    b--;
    --b;
```

Les valeurs TRUE et FALSE ont la relation suivante :

```cpp
!false == true
!true == false
```

Dans l'instruction suivante :

```cpp
if (condexpr1) statement1;
```

Si `condexpr1` a la valeur TRUE, `statement1` est toujours exécuté ; si `condexpr1` est FALSE, `statement1` n’est jamais exécutée.

Lorsqu’un préfixe ou suffixe **++** opérateur est appliqué à une variable de type **bool**, la variable est définie sur TRUE.
**Visual Studio 2017 15.3 et versions ultérieures**: opérateur ++ pour **bool** a été supprimé du langage et n’est plus pris en charge.

Le préfixe ou suffixe **--** opérateur ne peut pas être appliqué à une variable de ce type.

Le **bool** type participe aux promotions intégrales. R-value de type **bool** peut être converti en une r-value de type **int**, avec FALSE devenant zéro et TRUE devenant un. Comme un type distinct, **bool** participe à la résolution de surcharge.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types fondamentaux](../cpp/fundamental-types-cpp.md)