---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4319'
title: Avertissement du compilateur (niveau 1) C4319
ms.date: 01/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: af38714ab506fad389d9d2407b5a83aebf01f7c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340058"
---
# <a name="compiler-warning-level-1-c4319"></a>Avertissement du compilateur (niveau 1) C4319

> ' ~ ' : zéro étendant'*type1*'à'*type2*'d’une taille supérieure

Le résultat de l' **~** opérateur (complément de bits) est non signé, puis étendu à zéro lorsqu’il est converti en un type plus grand.

## <a name="example"></a>Exemple

Dans l’exemple suivant, `~(a - 1)` est évaluée en tant qu’expression longue non signée 32 bits, puis convertie en 64 bits par extension de zéro. Cela peut entraîner des résultats d'opération inattendus.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
