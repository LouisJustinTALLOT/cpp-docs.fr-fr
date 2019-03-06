---
title: C2131 d’erreur du compilateur
ms.date: 02/28/2019
f1_keywords:
- C2131
helpviewer_keywords:
- C2131
ms.openlocfilehash: 19bdf73efa82e624382446c94642ceddac00bf2e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426956"
---
# <a name="compiler-error-c2131"></a>C2131 d’erreur du compilateur

> expression ne correspond pas à une constante

Une expression est déclarée en tant que **const** ou **constexpr** n’a pas été évaluée en constante au moment de la compilation. Le compilateur doit être en mesure de déterminer la valeur de l’expression au point qu’il est utilisé.

## <a name="example"></a>Exemple

Cet exemple illustre une méthode pour provoquer l’erreur C2131 et comment la corriger.

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
