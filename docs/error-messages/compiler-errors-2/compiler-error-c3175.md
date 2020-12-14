---
description: 'En savoir plus sur : erreur du compilateur C3175'
title: Erreur du compilateur C3175
ms.date: 11/04/2016
f1_keywords:
- C3175
helpviewer_keywords:
- C3175
ms.assetid: 3f19d513-a05a-4b6c-806f-276fe5c36b90
ms.openlocfilehash: 278d8de3d18aaa3437f4d2c0b1d8c9e3306630a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242078"
---
# <a name="compiler-error-c3175"></a>Erreur du compilateur C3175

'fonction1 ' : impossible d’appeler une méthode d’un type managé à partir d’une fonction non managée’fonction2 '

Les fonctions non managées ne peuvent pas appeler les fonctions membres des classes managées.

L’exemple suivant génère l’C3175 :

```cpp
// C3175_2.cpp
// compile with: /clr

ref struct A {
   static void func() {
   }
};

#pragma unmanaged   // remove this line to resolve

void func2() {
   A::func();   // C3175
}

#pragma managed

int main() {
   A ^a = gcnew A;
   func2();
}
```
