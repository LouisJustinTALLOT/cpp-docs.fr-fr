---
title: Avertissement du compilateur (niveau 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: 067d1aef41280f4d14fe799e4f4ee26a9f1b9f5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451506"
---
# <a name="compiler-warning-level-4-c4239"></a>Avertissement du compilateur (niveau 4) C4239

extension non standard utilisée : 'token' : conversion de 'type' en 'type'

Cette conversion de type n’est pas autorisée par la norme C++, mais elle est autorisée ici en tant qu’extension. Cet avertissement est toujours suivi d’au moins une ligne d’explication décrivant la règle de langage violée.

## <a name="example"></a>Exemple

L’exemple suivant génère C4239.

```
// C4239.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

void func(void) {
   C & rC = C();   // C4239
   const C & rC2 = C();   // OK
   rC2;
}
```

## <a name="example"></a>Exemple

Conversion d’un type intégral en type enum n’est pas strictement autorisée.

L’exemple suivant génère C4239.

```
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```