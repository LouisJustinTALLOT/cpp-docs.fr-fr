---
title: Erreur du compilateur C2602
ms.date: 11/04/2016
f1_keywords:
- C2602
helpviewer_keywords:
- C2602
ms.assetid: 6c07a40e-537e-4954-b5c5-1e0e58fe1952
ms.openlocfilehash: da38600ea099c9b0d73e929a100a8c338bd3388f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466350"
---
# <a name="compiler-error-c2602"></a>Erreur du compilateur C2602

'classe::identificateur' n’est pas un membre de classe de base de 'class'

`Identifier` n’est pas accessible, car il n’est pas un membre hérité à partir de n’importe quelle classe de base.

L’exemple suivant génère l’erreur C2602 :

```
// C2602.cpp
// compile with: /c
struct X {
   int x;
};
struct A {
   int a;
};
struct B : public A {
   X::x;   // C2602 B is not derived from X
   A::a;   // OK
};
```