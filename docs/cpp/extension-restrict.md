---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 27ac76251456d9a0bf5908ad6d1fc2bee7534e9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360818"
---
# <a name="__restrict"></a>__restrict

Comme le **__declspec ( [limiter)](../cpp/restrict.md) ** modificateur, le mot clé **__restrict** indique qu’un symbole n’est pas alias dans la portée actuelle. Le mot clé **__restrict** diffère `__declspec ( restrict )` du modificateur de la manière suivante :

- Le mot clé **__restrict** n’est valable `__declspec ( restrict )` que sur les variables et n’est valable que sur les déclarations et définitions des fonctions.

- **__restrict** est similaire à **restreindre** de la spécification C99, mais **__restrict** peuvent être utilisés dans les programmes C ou C.

- Lorsque **__restrict** est utilisé, le compilateur ne propagera pas la propriété sans pseudonyme d’une variable. Autrement dit, si vous attribuez une variable **__restrict** à une variable non **__restrict,** le compilateur permettra toujours à la variable non __restrict d’être alias. Ceci est différent du comportement du mot clé de **restriction** de la spécification C99.

En général, si vous influez sur le comportement d'une fonction entière, il est préférable d'utiliser `__declspec ( restrict )` plutôt que le mot clé.

Pour la compatibilité avec les versions précédentes, **_restrict** est synonyme de __restrict à moins que **l’option** compilateur [/Za \(Désactiver extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Dans Visual Studio 2015 et plus tard, **__restrict** peuvent être utilisés sur les références C.

> [!NOTE]
> Lorsqu’il est utilisé sur une variable qui a également le mot clé [volatil,](../cpp/volatile-cpp.md) **volatile** aura préséance.

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
