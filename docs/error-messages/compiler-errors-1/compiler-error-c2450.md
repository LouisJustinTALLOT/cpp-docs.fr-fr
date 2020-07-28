---
title: Erreur du compilateur C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 55c7f7ba8708e1475404a474f85df7dbe37fcec0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220351"
---
# <a name="compiler-error-c2450"></a>Erreur du compilateur C2450

l’expression de switch de type’type’n’est pas conforme

L' **`switch`** expression prend la valeur d’un type non valide. Il doit correspondre à un type entier ou à un type de classe avec une conversion non ambiguë en type entier. Si elle prend la valeur d’un type défini par l’utilisateur, vous devez fournir un opérateur de conversion.

L’exemple suivant génère l’C2450 :

```cpp
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```
