---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4130'
title: Avertissement du compilateur (niveau 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: e7096f471405b0b22bcb0a825dd9ccd0de4e3510
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261812"
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
