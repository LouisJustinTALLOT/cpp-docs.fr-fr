---
title: __restrict | Microsoft Docs
ms.custom: ''
ms.date: 10/10/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
dev_langs:
- C++
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9245571e21be04cc250347f30ce8ddb464ff9b55
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163450"
---
# <a name="restrict"></a>__restrict

Comme le **__declspec ( [restreindre](../cpp/restrict.md) )** modificateur, le **__restrict** mot-clé indique qu’un symbole n’est pas un alias dans la portée actuelle. Le **__restrict** mot clé diffère la `__declspec ( restrict )` modificateur comme suit :

- Le **__restrict** mot clé est valide uniquement sur les variables, et `__declspec ( restrict )` est valide uniquement sur les définitions et déclarations de fonction.

- **__restrict** est similaire à **restreindre** à partir de la norme C99, mais **__restrict** peuvent être utilisés dans les programmes C++ ou C.

- Lorsque **__restrict** est utilisé, le compilateur ne propage pas la propriété anti-alias d’une variable. Autrement dit, si vous affectez un **__restrict** variable non -**__restrict** variable, le compilateur permet toujours la variable pour avoir un alias non-__restrict. Cela est différent du comportement de la **restreindre** mot clé à partir de la norme C99.

En général, si vous influez sur le comportement d'une fonction entière, il est préférable d'utiliser `__declspec ( restrict )` plutôt que le mot clé.

Pour assurer la compatibilité avec les versions précédentes, **_restrict** est un synonyme de **__restrict** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

Dans Visual Studio 2015 et versions ultérieures, **__restrict** peut être utilisé dans les références C++.

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