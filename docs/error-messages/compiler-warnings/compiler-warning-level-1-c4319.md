---
title: Avertissement du compilateur (niveau 1) C4319
ms.date: 1/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 20b268bacd6e7e259e9b4fa1c9e98fa6fd353718
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599444"
---
# <a name="compiler-warning-level-1-c4319"></a>Avertissement du compilateur (niveau 1) C4319

> ' ~' : zéro étendant '*type1*'en'*type2*' d’une taille supérieure

Le résultat de la **~** (complément au niveau du bit) opérateur est non signé et puis étendu par zéro lorsqu’il est converti en un type plus grand.

## <a name="example"></a>Exemple

Dans l’exemple suivant, `~(a - 1)` est évaluée comme une expression de type long non signée 32 bits et puis converti en 64 bits par extension zéro. Cela peut entraîner des résultats d'opération inattendus.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
