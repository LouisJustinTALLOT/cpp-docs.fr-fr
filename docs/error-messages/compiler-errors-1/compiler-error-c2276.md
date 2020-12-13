---
description: 'En savoir plus sur : erreur du compilateur C2276'
title: Erreur du compilateur C2276
ms.date: 11/04/2016
f1_keywords:
- C2276
helpviewer_keywords:
- C2276
ms.assetid: 62005ad9-6cb9-4b1f-965d-b875adaf695e
ms.openlocfilehash: dc6a407110ee121444b7e767f43d7d29ba42db72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134509"
---
# <a name="compiler-error-c2276"></a>Erreur du compilateur C2276

'operator' : opération non conforme sur l’expression d’une fonction membre liée

Le compilateur a détecté un problème avec la syntaxe pour créer un pointeur vers membre.

L’exemple suivant génère l’C2276 :

```cpp
// C2276.cpp
class A {
public:
   int func(){return 0;}
} a;

int (*pf)() = &a.func;   // C2276
// try the following line instead
// int (A::*pf3)() = &A::func;

class B {
public:
   void mf() {
      &this -> mf;   // C2276
      // try the following line instead
      // &B::mf;
   }
};

int main() {
   A a;
   &a.func;   // C2276
   // try the following line instead
   // &A::func;
}
```
