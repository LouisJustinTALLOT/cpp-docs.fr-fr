---
title: Erreur du compilateur C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: 75e3b438dd69f8879fdc2273a8f0357229941340
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386900"
---
# <a name="compiler-error-c2594"></a>Erreur du compilateur C2594

'opérateur' : conversions ambiguës de 'type1' en 'type2'

Aucune conversion de *type1* à *type2* a été plus directe qu’une autre. Nous vous suggérons deux solutions possibles pour la conversion de *type1* à *type2*. La première option consiste à définir une conversion directe de *type1* à *type2*, et la deuxième option consiste à spécifier une séquence de conversions de *type1* à  *type2*.

L’exemple suivant génère l’erreur C2594. La résolution suggérée à l’erreur est une séquence de conversions :

```
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