---
title: Avertissement du compilateur (niveau 1) C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: f4d0b87c91649c5f2f6b5823fea82d2ce355d11a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518636"
---
# <a name="compiler-warning-level-1-c4669"></a>Avertissement du compilateur (niveau 1) C4669

'cast' : conversion risquée : 'classe' est un objet de type managé ou WinRT

Un cast contient un type managé ou Windows Runtime. Le compilateur termine le cast en effectuant une copie bit par bit d'un pointeur vers l'autre, mais ne fournit aucune autre vérification. Pour résoudre cet avertissement, n'effectuez pas de cast des classes qui contiennent des membres managés ou des types Windows Runtime.

L'exemple suivant génère l'avertissement C4669 et montre comment le corriger :

```
// C4669.cpp
// compile with: /clr /W1
ref struct A {
   int i;
   Object ^ pObj;   // remove the managed member to fix the warning
};

ref struct B {
   int j;
};

int main() {
   A ^ a = gcnew A;
   B ^ b = reinterpret_cast<B ^>(a);   // C4669
}
```