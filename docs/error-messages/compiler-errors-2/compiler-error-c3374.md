---
title: Erreur du compilateur C3374
ms.date: 11/04/2016
f1_keywords:
- C3374
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
ms.openlocfilehash: 760eb1bafdaab9995d3238c8bc4e3114acd743eb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755575"
---
# <a name="compiler-error-c3374"></a>Erreur du compilateur C3374

impossible de récupérer l'adresse de 'function' à moins de créer une instance de délégué

L'adresse d'une fonction a été récupérée dans un autre contexte que la création d'une instance de délégué.

L'exemple suivant génère l'erreur C3374 :

```cpp
// C3374.cpp
// compile with: /clr
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      System::Console::WriteLine("in func1 {0}", i);
   }
};

int main() {
   &A::func1;   // C3374

   // OK
   A ^ a = gcnew A;
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);
}
```

## <a name="see-also"></a>Voir aussi

[Guide pratique pour définir et utiliser des délégués (C++-CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)
