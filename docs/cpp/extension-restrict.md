---
title: '`__restrict`'
description: Décrit le `__restrict` mot clé Microsoft Visual C++.
ms.date: 11/6/2020
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.openlocfilehash: f23574f49712928e0095f29a3b88b0c05b185eab
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381569"
---
# `__restrict`

Comme le modificateur **`__declspec` ( [`restrict`](../cpp/restrict.md) )** , le **`__restrict`** mot clé (deux traits de soulignement de début' _ ') indique qu’un symbole n’est pas un alias dans l’étendue actuelle. Le **`__restrict`** mot clé diffère du `__declspec (restrict)` modificateur des manières suivantes :

- Le **`__restrict`** mot clé est valide uniquement sur les variables et `__declspec (restrict)` n’est valide que sur les déclarations et les définitions de fonctions.

- **`__restrict`** est semblable à [`restrict`](../c-language/type-qualifiers.md#restrict) pour C à partir de C99, mais **`__restrict`** peut être utilisé dans les programmes C++ et C.

- Lorsque **`__restrict`** est utilisé, le compilateur ne propage pas la propriété d’absence d’alias d’une variable. Autrement dit, si vous assignez une **`__restrict`** variable à une variable non- **`__restrict`** , le compilateur autorisera toujours l’alias de la variable non-__restrict. Cela diffère du comportement du mot clé du langage C C99 **`restrict`** .

En règle générale, si vous souhaitez affecter le comportement d’une fonction entière, utilisez à **`__declspec (restrict)`** la place du mot clé.

Pour la compatibilité avec les versions précédentes, **`_restrict`** est un synonyme de, **`__restrict`** sauf si l’option de compilateur [ `/Za` \( désactive les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Dans Visual Studio 2015 et versions ultérieures, **`__restrict`** peut être utilisé sur les références C++.

> [!NOTE]
> En cas d’utilisation sur une variable qui possède également le [`volatile`](../cpp/volatile-cpp.md) mot clé, **`volatile`** est prioritaire.

## <a name="example"></a>Exemple

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
