---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4356'
title: Avertissement du compilateur (niveau 2) C4356
ms.date: 11/04/2016
f1_keywords:
- C4356
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
ms.openlocfilehash: 328f177c90b34f17f8f8c5ec480cb829a22f2f14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173569"
---
# <a name="compiler-warning-level-2-c4356"></a>Avertissement du compilateur (niveau 2) C4356

'membre' : les données membres static ne peuvent pas être initialisées via une classe dérivée

L’initialisation d’un membre de données statique était incorrecte. Le compilateur a accepté l’initialisation. Pour éviter l’avertissement, initialisez le membre par le biais de la classe de base.

Utilisez le pragma [Warning](../../preprocessor/warning.md) pour supprimer cet avertissement.

L’exemple suivant génère l’C4356 :

```cpp
// C4356.cpp
// compile with: /W2 /EHsc
#include <iostream>

template <class T>
class C {
   static int n;
};

class D : C<int> {};

int D::n = 0; // C4356
// try the following line instead
// int C<int>::n = 0;

class A {
public:
   static int n;
};

class B : public A {};

int B::n = 10;   // C4356
// try the following line instead
// int A::n = 99;

int main() {
   using namespace std;
   cout << B::n << endl;
}
```
