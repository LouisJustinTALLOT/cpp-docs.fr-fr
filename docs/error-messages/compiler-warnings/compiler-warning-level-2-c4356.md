---
title: Avertissement du compilateur (niveau 2) C4356
ms.date: 11/04/2016
f1_keywords:
- C4356
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
ms.openlocfilehash: 218aac1cc98d9b119490a547d63b4b5ee83e53df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447357"
---
# <a name="compiler-warning-level-2-c4356"></a>Avertissement du compilateur (niveau 2) C4356

'membre' : données membres static ne peuvent pas être initialisées via une classe dérivée

L’initialisation d’un membre de données statique est incorrecte. Le compilateur a accepté l’initialisation. Pour éviter l’avertissement, initialisez le membre via la classe de base.

Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour supprimer cet avertissement.

L’exemple suivant génère l’erreur C4356 :

```
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