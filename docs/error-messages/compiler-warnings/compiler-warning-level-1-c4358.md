---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4358'
title: Avertissement du compilateur (niveau 1) C4358
ms.date: 11/04/2016
f1_keywords:
- C4358
helpviewer_keywords:
- C4358
ms.assetid: a9848f84-14b3-405e-81bf-ee3e91a51511
ms.openlocfilehash: 2e3f548f5b464f712f6e5d0e20dc6da9edfdfd3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339980"
---
# <a name="compiler-warning-level-1-c4358"></a>Avertissement du compilateur (niveau 1) C4358

'opérateur' : le type de retour des délégués combinés n’est pas’void'; la valeur retournée n’est pas définie

Deux délégués ont été combinés et la valeur de retour n’est pas void. Si deux délégués avec des valeurs de retour non void sont combinés, le compilateur ne sera pas en mesure d’effectuer une assignation appropriée si la valeur de retour du délégué est utilisée.

L’exemple suivant génère l’C4358 :

```cpp
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
