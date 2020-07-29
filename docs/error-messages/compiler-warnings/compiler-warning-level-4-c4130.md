---
title: Avertissement du compilateur (niveau 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: 7b2fbccfd3b124220d6e310c01adace1d3e112c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219961"
---
# <a name="compiler-warning-level-4-c4130"></a>Avertissement du compilateur (niveau 4) C4130

'opérateur' : opération logique sur l’adresse d’une constante de chaîne

L’utilisation de l’opérateur avec l’adresse d’un littéral de chaîne génère du code inattendu.

L’exemple suivant génère l’avertissement C4130 :

```cpp
// C4130.cpp
// compile with: /W4
int main()
{
   char *pc;
   pc = "Hello";
   if (pc == "Hello") // C4130
   {
   }
}
```

L' **`if`** instruction compare la valeur stockée dans le pointeur `pc` à l’adresse de la chaîne « Hello », qui est allouée séparément chaque fois que la chaîne se trouve dans le code. L' **`if`** instruction ne compare pas la chaîne pointée par à `pc` la chaîne « Hello ».

Pour comparer des chaînes, utilisez la fonction `strcmp` .
