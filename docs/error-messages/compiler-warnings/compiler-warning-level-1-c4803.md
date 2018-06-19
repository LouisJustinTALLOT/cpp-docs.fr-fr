---
title: Compilateur avertissement (niveau 1) C4803 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4803
dev_langs:
- C++
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c574b51fc13f9224d48495f8b591a56abdc74966
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280827"
---
# <a name="compiler-warning-level-1-c4803"></a>Avertissement du compilateur (niveau 1) C4803
'méthode' : la méthode raise a une classe de stockage différente de celle de l’événement, 'event'  
  
Méthodes d’événement doivent avoir la même classe de stockage que la déclaration d’événement. Le compilateur ajuste les méthodes d’événement afin que les classes de stockage sont les mêmes.  
  
Cet avertissement peut se produire si vous avez une classe qui implémente un événement à partir d’une interface. Le compilateur ne génère pas implicitement une méthode raise pour un événement dans une interface. Lorsque vous implémentez cette interface dans une classe, le compilateur génère implicitement une méthode raise et cette méthode ne sera pas virtuelle, par conséquent, l’avertissement. Pour plus d’informations sur les événements, consultez [événement](../../windows/event-cpp-component-extensions.md).  
  
Consultez [avertissement](../../preprocessor/warning.md) pragma pour plus d’informations sur la façon de désactiver un avertissement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4803.  
  
```  
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
