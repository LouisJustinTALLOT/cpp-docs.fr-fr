---
title: Avertissement du compilateur (niveau 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: b6fc5708d4e2f9982ceaab57260f13e134e4d247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578257"
---
# <a name="compiler-warning-level-1-c4806"></a>Avertissement du compilateur (niveau 1) C4806

'opération' : opération risquée : aucune valeur de type 'type' promue en type 'type' ne peut être égale à la constante donnée

Ce message fournit un avertissement contre le code tel que `b == 3`, où `b` est de type `bool`. Les règles de promotion entraînent la promotion de `bool` en `int`. Cela est légal, mais ne peut jamais être **true**. L’exemple suivant génère l’erreur C4806 :

```
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```