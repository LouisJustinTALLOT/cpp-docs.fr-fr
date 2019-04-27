---
title: Erreur du compilateur C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 3cbab274f8f7cd04d5fb86db69572e0b7fc1c04e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208969"
---
# <a name="compiler-error-c2450"></a>Erreur du compilateur C2450

expression de switch de type 'type' n’est pas conforme

Le `switch` expression correspond à un type non valide. Elle doit correspondre à un type entier ou un type de classe avec une conversion non ambiguë à un type entier. Si sa valeur est un type défini par l’utilisateur, vous devez fournir un opérateur de conversion.

L’exemple suivant génère l’erreur C2450 :

```
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