---
title: Erreur du compilateur C2108
ms.date: 11/04/2016
f1_keywords:
- C2108
helpviewer_keywords:
- C2108
ms.assetid: c84f0b47-5e2c-47d2-8edb-427a40e17c36
ms.openlocfilehash: 069f369627f42314cc14688a9e0c0a55808db507
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752026"
---
# <a name="compiler-error-c2108"></a>Erreur du compilateur C2108

l’indice n’est pas de type intégral

L’indice de tableau est une expression non entière.

## <a name="example"></a>Exemple

C2108 peut se produire si vous utilisez incorrectement le pointeur `this` d’un type valeur pour accéder à l’indexeur par défaut du type. Pour plus d’informations, consultez [sémantiques du pointeur this](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

L’exemple suivant génère l’C2108.

```cpp
// C2108.cpp
// compile with: /clr
using namespace System;

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      Console::WriteLine("{0}", this[3.3]);   // C2108
      Console::WriteLine("{0}", this->default[3.3]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
