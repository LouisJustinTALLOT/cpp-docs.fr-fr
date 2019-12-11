---
title: Avertissement du compilateur (niveau 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: a882fa7f78f68cb2400e4924a9ba2f17e6ee7003
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991459"
---
# <a name="compiler-warning-level-4-c4239"></a>Avertissement du compilateur (niveau 4) C4239

extension non standard utilisée : 'Token' : conversion de’type’en’type'

Cette conversion de type n’est pas autorisée C++ par la norme, mais elle est autorisée ici en tant qu’extension. Cet avertissement est toujours suivi d’au moins une ligne d’explication décrivant la règle de langue non respectée.

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

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
