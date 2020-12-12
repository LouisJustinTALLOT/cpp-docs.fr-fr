---
description: 'En savoir plus sur : erreur du compilateur C2131'
title: Erreur du compilateur C2131
ms.date: 02/28/2019
f1_keywords:
- C2131
helpviewer_keywords:
- C2131
ms.openlocfilehash: 3c1f4e783c9341acf9e41fff99bba784acd8bbec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124174"
---
# <a name="compiler-error-c2131"></a>Erreur du compilateur C2131

> l’expression n’a pas été évaluée en constante

Une expression déclarée comme **`const`** ou **`constexpr`** n’a pas été évaluée à une constante au moment de la compilation. Le compilateur doit pouvoir déterminer la valeur de l’expression au point où il est utilisé.

## <a name="example"></a>Exemple

Cet exemple montre comment générer une erreur C2131 et comment la corriger.

```cpp
// c2131.cpp
// compile by using: cl /EHsc /W4 /c c2131.cpp

struct test
{
    static const int array_size; // To fix, init array_size here.
    int size_array[array_size];  // C2131
};

const int test::array_size = 42;
```

```Output
c2131.cpp
c2131.cpp(7): error C2131: expression did not evaluate to a constant
c2131.cpp(7): note: failure was caused by non-constant arguments or reference to a non-constant symbol
c2131.cpp(7): note: see usage of 'array_size'
```

## <a name="see-also"></a>Voir aussi

[const](../../cpp/const-cpp.md)<br/>
[constexpr](../../cpp/constexpr-cpp.md)<br/>
