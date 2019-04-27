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
ms.openlocfilehash: 76cdf9424e6eab33a3a92b3f98d9c2b0b04ff667
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183750"
---
# <a name="restrict"></a>__restrict

Comme le **__declspec ( [restreindre](../cpp/restrict.md) )** modificateur, le **__restrict** mot-clé indique qu’un symbole n’est pas un alias dans la portée actuelle. Le **__restrict** mot clé diffère la `__declspec ( restrict )` modificateur comme suit :

- Le **__restrict** mot clé est valide uniquement sur les variables, et `__declspec ( restrict )` est valide uniquement sur les définitions et déclarations de fonction.

- **__restrict** est similaire à **restreindre** à partir de la norme C99, mais **__restrict** peut être utilisé dans C++ ou programmes C.

- Lorsque **__restrict** est utilisé, le compilateur ne propage pas la propriété anti-alias d’une variable. Autrement dit, si vous affectez un **__restrict** variable non -**__restrict** variable, le compilateur permet toujours la variable pour avoir un alias non-__restrict. Cela est différent du comportement de la **restreindre** mot clé à partir de la norme C99.

En général, si vous influez sur le comportement d'une fonction entière, il est préférable d'utiliser `__declspec ( restrict )` plutôt que le mot clé.

Pour assurer la compatibilité avec les versions précédentes, **_restrict** est un synonyme de **__restrict** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

Dans Visual Studio 2015 et versions ultérieures, **__restrict** peut être utilisé sur C++ références.

> [!NOTE]
>  Lorsqu’il est utilisé sur une variable qui a également la [volatile](../cpp/volatile-cpp.md) mot clé, **volatile** est prioritaire.

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