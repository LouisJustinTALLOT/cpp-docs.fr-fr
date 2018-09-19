---
title: Compilateur avertissement (niveau 2) C4356 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4356
dev_langs:
- C++
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 463ecd1bdd41c07baab0cf90c978411e51b4be04
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118724"
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