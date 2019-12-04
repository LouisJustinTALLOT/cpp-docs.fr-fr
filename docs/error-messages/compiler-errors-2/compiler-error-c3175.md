---
title: Erreur du compilateur C3175
ms.date: 11/04/2016
f1_keywords:
- C3175
helpviewer_keywords:
- C3175
ms.assetid: 3f19d513-a05a-4b6c-806f-276fe5c36b90
ms.openlocfilehash: 8be6cfa72c33212593c0b2a73ad38ad9fc113f26
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761710"
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
