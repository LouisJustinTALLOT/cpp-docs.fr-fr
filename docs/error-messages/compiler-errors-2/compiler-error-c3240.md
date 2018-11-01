---
title: Erreur du compilateur C3240
ms.date: 11/04/2016
f1_keywords:
- C3240
helpviewer_keywords:
- C3240
ms.assetid: 1a8dc213-b80c-47ae-ada0-e9554b635d1e
ms.openlocfilehash: a8334b4f95ccadcce73a79d787669cba9f911199
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504609"
---
# <a name="compiler-error-c3240"></a>Erreur du compilateur C3240

'fonction' : doit être une fonction membre abstraite non surchargée de 'type'

Un type de base contenait une fonction qui a été définie. Fonction doit être virtuelle.

## <a name="example"></a>Exemple

L’exemple suivant génère C3240.

```
// C3240.cpp
// compile with: /c
__interface I {
   void f();
};

struct A1 : I {
   void f() {}
};

struct A2 : I {
   void f() = 0;
};

template <class T>
struct A3 : T {
   void T::f() {}
};

template <class T>
struct A4 : T {
   void T::f() {}
};

A3<A1> x;   // C3240
A3<I> x2;
A4<A2> x3;
```