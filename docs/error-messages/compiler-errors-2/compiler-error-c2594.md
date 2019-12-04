---
title: Erreur du compilateur C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: ade657f9ada2a2249d2f96b7caada7b9719195d1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759332"
---
# <a name="compiler-error-c2594"></a>Erreur du compilateur C2594

'opérateur' : conversions ambiguës de’type1 'en’type2 '

Aucune conversion de *type1* en *type2* n’était plus directe que les autres. Nous vous suggérons deux solutions possibles pour convertir de *type1* en *type2*. La première option consiste à définir une conversion directe de *type1* en *type2*, et la deuxième option est de spécifier une séquence de conversions de *type1* en *type2*.

L’exemple suivant génère l’C2594. La résolution suggérée à l’erreur est une séquence de conversions :

```cpp
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```
