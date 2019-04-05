---
title: Erreur du compilateur C3374
ms.date: 11/04/2016
f1_keywords:
- C3374
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
ms.openlocfilehash: 4b00b1cea8ac462c82c11d9f5b207706af74959c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022630"
---
# <a name="compiler-error-c3374"></a>Erreur du compilateur C3374

impossible de récupérer l'adresse de 'function' à moins de créer une instance de délégué

L'adresse d'une fonction a été récupérée dans un autre contexte que la création d'une instance de délégué.

L'exemple suivant génère l'erreur C3374 :

```
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

[Procédure : Définir et utiliser des délégués (C++ / c++ / CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)