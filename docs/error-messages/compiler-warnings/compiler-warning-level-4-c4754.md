---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4754'
title: Avertissement du compilateur (niveau 4) C4754
ms.date: 11/04/2016
f1_keywords:
- C4754
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
ms.openlocfilehash: b997f81a7d922837ff3f1ea2e5d015e5267428dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330516"
---
# <a name="compiler-warning-level-4-c4754"></a>Avertissement du compilateur (niveau 4) C4754

Les règles de conversion pour les opérations arithmétiques dans une comparaison signifient qu’une branche ne peut pas être exécutée.

L'avertissement C4754 est généré, car le résultat de la comparaison est toujours identique. Cela indique qu’une des branches de la condition n’est jamais exécutée, très probablement parce que l’expression d’entier associée est incorrecte. Cette erreur de code se produit souvent dans les contrôles incorrects de dépassement sur les entiers sur les architectures 64 bits.

Les règles de conversion d'entier sont complexes, et il existe de nombreuses pièges subtils. Comme alternative à la résolution de chaque AVERTISSEMENT C4754, vous pouvez mettre à jour le code pour utiliser la [bibliothèque SafeInt](../../safeint/safeint-library.md).

## <a name="examples"></a>Exemples

Cet exemple génère C4754 :

```cpp
// C4754a.cpp
// Compile with: /W4 /c
#include "errno.h"

int sum_overflow(unsigned long a, unsigned long b)
{
   unsigned long long x = a + b; // C4754

   if (x > 0xFFFFFFFF)
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

L'addition `a + b` peut provoquer un dépassement de capacité arithmétique avant que le résultat fasse l'objet d'un upcast vers une valeur 64 bits et soit assigné à la variable 64 bits `x`. Cela signifie que le contrôle sur `x` est redondant et n'intercepte jamais un dépassement de capacité. Dans ce cas, le compilateur génère l'avertissement suivant :

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).
```

Pour éliminer l'avertissement, il est possible de modifier l'instruction d'assignation pour effectuer un cast des opérandes vers des valeurs de 8 octets :

```cpp
// Casting one operand is sufficient to force all the operands in
// the addition be upcast according to C/C++ conversion rules, but
// casting both is clearer.
unsigned long long x =
   (unsigned long long)a + (unsigned long long)b;
```

L'exemple suivant génère également l'avertissement C4754.

```cpp
// C4754b.cpp
// Compile with: /W4 /c
#include "errno.h"

int wrap_overflow(unsigned long a)
{
   if (a + sizeof(unsigned long) < a) // C4754
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

L'opérateur `sizeof()` retourne `size_t` dont la taille dépend de l'architecture. L'exemple de code fonctionne sur les architectures 32 bits, où `size_t` est un type 32 bits. Toutefois, sur les architectures 64 bits, `size_t` est un type 64 bits. Les règles de conversion pour les entiers signifient que `a` fait l'objet d'un upcast vers une valeur 64 bits dans l'expression `a + b < a`, comme si elle était écrite `(size_t)a + (size_t)b < (size_t)a`. Lorsque `a` et `b` sont des entiers 32 bits, l'opération d'addition 64 bits ne peut jamais déborder, et la contrainte n'est jamais conservée. Par conséquent, le code ne détecte jamais une condition de dépassement sur les entiers sur les architectures 64 bits. Cet exemple entraîne le compilateur à générer l'avertissement suivant :

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).
```

Notez que le message d'avertissement répertorie explicitement la valeur de constante 4 au lieu de la chaîne source d'origine. Au moment où l'analyse de l'avertissement rencontre le code incriminé, `sizeof(unsigned long)` a déjà été converti en constante. Par conséquent, vous devrez peut-être trouver quelle expression dans le code source est associée à la valeur de constante dans le message d'avertissement. Les sources de code les plus courantes résolues en constantes dans les messages d'avertissement C4754 sont des expressions telles que `sizeof(TYPE)` et `strlen(szConstantString)`.

Dans ce cas, le code résolu se présente comme suit :

```cpp
// Casting the result of sizeof() to unsigned long ensures
// that all the addition operands are 32-bit, so any overflow
// is detected by the check.
if (a + (unsigned long)sizeof(unsigned long) < a)
```

**Remarque** Le numéro de ligne référencé dans les avertissements du compilateur est la dernière ligne d’une instruction. Dans un message d'avertissement concernant une instruction conditionnelle complexe répartie sur plusieurs lignes, la ligne contenant l'erreur de code peut être plusieurs lignes avant la ligne indiquée. Par exemple :

```cpp
unsigned long a;

if (a + sizeof(unsigned long) < a || // incorrect check
    condition1() ||
    a == 0) {    // C4754 warning reported on this line
         // never executes!
         return INVALID_PARAMETER;
}
```
