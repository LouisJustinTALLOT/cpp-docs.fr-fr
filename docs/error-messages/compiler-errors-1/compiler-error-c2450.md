---
description: 'En savoir plus sur : erreur du compilateur C2450'
title: Erreur du compilateur C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 5e2d838ea03ca8d42b2addb2e52d4cf29deabfa1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332414"
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
