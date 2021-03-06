---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4239'
title: Avertissement du compilateur (niveau 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: 635795392b5544f4985305a02e8534188c049224
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334860"
---
# <a name="compiler-warning-level-4-c4239"></a>Avertissement du compilateur (niveau 4) C4239

extension non standard utilisée : 'Token' : conversion de’type’en’type'

Cette conversion de type n’est pas autorisée par la norme C++, mais elle est autorisée ici en tant qu’extension. Cet avertissement est toujours suivi d’au moins une ligne d’explication décrivant la règle de langue non respectée.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C4239.

```cpp
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

La conversion d’un type intégral en type enum n’est pas strictement autorisée.

L’exemple suivant génère l’C4239.

```cpp
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```
