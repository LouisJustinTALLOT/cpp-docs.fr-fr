---
title: Avertissement du compilateur (niveau 1) C4358
ms.date: 11/04/2016
f1_keywords:
- C4358
helpviewer_keywords:
- C4358
ms.assetid: a9848f84-14b3-405e-81bf-ee3e91a51511
ms.openlocfilehash: aebac17a343efedf678b55f8940004c85a2db708
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637331"
---
# <a name="compiler-warning-level-1-c4358"></a>Avertissement du compilateur (niveau 1) C4358

'opérateur' : type de retour des délégués combinés n'est pas 'void' ; valeur retournée n’est pas définie

Deux délégués ont été combinés et la valeur de retour n’est pas void. Si deux délégués avec les valeurs de retour non void sont combinés, le compilateur ne sera pas en mesure d’effectuer une assignation correcte si la valeur de retour du délégué est utilisée.

L’exemple suivant génère l’erreur C4358 :

```
// C4358.cpp
// compile with: /clr /W1
delegate int D();
delegate void E();

ref class X {
   int i;
public:
   X(int ii) : i(ii) {}
   int f() {
      return i;
   }
};

ref class Y {
   int i;
public:
   Y() {}
   void g() {}
};

int main() {
   D^ d = gcnew D(gcnew X(1), &X::f);
   D^ d2 = gcnew D(gcnew X(2), &X::f);

   d += d2;   // C4358
   int j = d();   // return value indeterminate

   E^ e = gcnew E(gcnew Y, &Y::g);
   E^ e2 = gcnew E(gcnew Y, &Y::g);
   e += e2;   // OK
}
```