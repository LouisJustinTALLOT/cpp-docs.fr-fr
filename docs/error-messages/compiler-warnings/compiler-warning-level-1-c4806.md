---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4806'
title: Avertissement du compilateur (niveau 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: 3e4aaa67c2a979afde2d1a7643d0c5ab1b879418
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238243"
---
# <a name="compiler-warning-level-1-c4806"></a>Avertissement du compilateur (niveau 1) C4806

'opération' : opération risquée : aucune valeur de type 'type' promue en type 'type' ne peut être égale à la constante donnée

Ce message vous avertit du code tel que `b == 3` , où `b` est de type **`bool`** . Les règles de promotion entraînent la promotion de en **`bool`** **`int`** . Cela est légal, mais ne peut jamais être **`true`** . L’exemple suivant génère l’erreur C4806 :

```cpp
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
