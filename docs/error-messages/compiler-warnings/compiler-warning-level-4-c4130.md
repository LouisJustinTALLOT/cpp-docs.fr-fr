---
title: Avertissement du compilateur (niveau 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: b55594608eccc5d1e5e764bffb73ecb3787af1e4
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541597"
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