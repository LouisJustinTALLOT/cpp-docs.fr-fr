---
description: 'En savoir plus sur : bool (C++)'
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: ea3af17260f21d3724f05b8bbad54091b23203e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229585"
---
# <a name="bool-c"></a>bool (C++)

Ce mot clé est un type intégré. Une variable de ce type peut avoir des valeurs [`true`](../cpp/true-cpp.md) et [`false`](../cpp/false-cpp.md) . Les expressions conditionnelles ont le type **`bool`** et ont donc des valeurs de type **`bool`** . Par exemple, `i != 0` possède **`true`** ou **`false`** en fonction de la valeur de `i` .

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : l’opérande d’un opérateur postfix ou de préfixe d’incrémentation ou de décrémentation ne peut pas être de type **`bool`** . En d’autres termes, étant donné une variable `b` de type **`bool`** , ces expressions ne sont plus autorisées :

```cpp
    b++;
    ++b;
    b--;
    --b;
```

Les valeurs **`true`** et **`false`** ont la relation suivante :

```cpp
!false == true
!true == false
```

Dans l'instruction suivante :

```cpp
if (condexpr1) statement1;
```

Si `condexpr1` est **`true`** , `statement1` est toujours exécuté ; si `condexpr1` est **`false`** , `statement1` n’est jamais exécuté.

Lorsqu’un opérateur de suffixe ou de préfixe **`++`** est appliqué à une variable de type **`bool`** , la variable a la valeur **`true`** .

**Visual Studio 2017 version 15,3 et versions ultérieures**: `operator++` pour **`bool`** a été supprimé du langage et n’est plus pris en charge.

L’opérateur postfix ou prefix **`--`** ne peut pas être appliqué à une variable de ce type.

Le **`bool`** type participe aux promotions intégrales par défaut. Une r-value de type **`bool`** peut être convertie en r-value de type **`int`** , avec une valeur **`false`** égale à zéro et en **`true`** devenant un. En tant que type distinct, **`bool`** participe à la résolution de surcharge.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types intégrés](../cpp/fundamental-types-cpp.md)
