---
title: Avertissement du compilateur (niveau 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: 3bc632bf641fa3944cfd21dc405590c803498d80
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991565"
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

L’ instruction **If** compare la valeur stockée dans le pointeur `pc` à l’adresse de la chaîne « Hello », qui est allouée séparément à chaque occurrence de la chaîne dans le code. L’ instruction **If** ne compare pas la chaîne vers laquelle `pc` pointe avec la chaîne « Hello ».

Pour comparer des chaînes, utilisez la fonction `strcmp` .
