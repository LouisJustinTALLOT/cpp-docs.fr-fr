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
ms.openlocfilehash: 6318e6d78f6c4c4bb6827a79d26bca028dfe3f3f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233741"
---
# <a name="__restrict"></a>__restrict

Comme le modificateur **__declspec ( [restrict](../cpp/restrict.md) )** , le **`__restrict`** mot clé indique qu’un symbole n’a pas d’alias dans la portée actuelle. Le **`__restrict`** mot clé diffère du `__declspec ( restrict )` modificateur des manières suivantes :

- Le **`__restrict`** mot clé est valide uniquement sur les variables et `__declspec ( restrict )` n’est valide que sur les déclarations et les définitions de fonctions.

- **`__restrict`** est similaire à **`restrict`** la spécification C99, mais **`__restrict`** peut être utilisé dans les programmes C++ ou C.

- Lorsque **`__restrict`** est utilisé, le compilateur ne propage pas la propriété d’absence d’alias d’une variable. Autrement dit, si vous assignez une **`__restrict`** variable à une variable non- **`__restrict`** , le compilateur autorisera toujours l’alias de la variable non-__restrict. Cela diffère du comportement du **`restrict`** mot clé de la spécification C99.

En général, si vous influez sur le comportement d'une fonction entière, il est préférable d'utiliser `__declspec ( restrict )` plutôt que le mot clé.

Pour la compatibilité avec les versions précédentes, **_restrict** est un synonyme de, **`__restrict`** sauf si l’option de compilateur [/za \( Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Dans Visual Studio 2015 et versions ultérieures, **`__restrict`** peut être utilisé sur les références C++.

> [!NOTE]
> En cas d’utilisation sur une variable qui possède également le mot clé [volatile](../cpp/volatile-cpp.md) , **`volatile`** est prioritaire.

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
