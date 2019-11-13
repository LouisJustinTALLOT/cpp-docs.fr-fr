---
title: Avertissement du compilateur (niveau 1) C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: ebf7b3baec3519a142c7a1835aa15a980974bb48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052350"
---
# <a name="compiler-warning-level-1-c4803"></a>Avertissement du compilateur (niveau 1) C4803

'méthode' : la méthode Raise a une classe de stockage différente de celle de l’événement, 'Event'

Les méthodes d’événement doivent avoir la même classe de stockage que la déclaration d’événement. Le compilateur ajuste les méthodes de l’événement afin que les classes de stockage soient les mêmes.

Cet avertissement peut se produire si vous avez une classe qui implémente un événement à partir d’une interface. Le compilateur ne génère pas implicitement une méthode Raise pour un événement dans une interface. Lorsque vous implémentez cette interface dans une classe, le compilateur génère implicitement une méthode Raise et cette méthode n’est pas virtuelle, par conséquent l’avertissement. Pour plus d’informations sur les événements, consultez [Event](../../extensions/event-cpp-component-extensions.md).

Pour plus d’informations sur la façon de désactiver un avertissement, consultez pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4803.

```cpp
// C4803.cpp
// compile with: /clr /W1
using namespace System;

public delegate void Del();

ref struct E {
   Del ^ _pd1;
   event Del ^ E1 {
      void add (Del ^ pd1) {
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));
      }

      void remove(Del^ pd1) {
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));
      }

      virtual void raise() {   // C4803 warning (remove virtual)
         if (_pd1)
            _pd1();
      }
   }

   void func() {
      Console::WriteLine("In E::func()");
   }
};

int main() {
   E ^ ep = gcnew E;
   ep->E1 += gcnew Del(ep, &E::func);
   ep->E1();
   ep->E1 -= gcnew Del(ep, &E::func);
   ep->E1();
}
```
