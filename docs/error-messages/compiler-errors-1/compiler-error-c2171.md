---
title: Erreur du compilateur C2171
ms.date: 11/04/2016
f1_keywords:
- C2171
helpviewer_keywords:
- C2171
ms.assetid: a80343b5-ab3f-4413-b6f1-3ce9d7e519e5
ms.openlocfilehash: 467abd87d521b1a2a7b383406b9992067438afed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649005"
---
# <a name="compiler-error-c2171"></a>Erreur du compilateur C2171

'opérateur' : non conforme sur les opérandes de type 'type'

Un opérateur unaire est utilisé avec un type d’opérande non valide.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2171 :

```
// C2171.cpp
int main() {
   double d, d1;
   d = ~d1;   // C2171

   // OK
   int d2 = 0, d3 = 0;
   d2 = ~d3;
}
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2171 :

```
// C2171_b.cpp
// compile with: /c
class A {
public:
   A() { STF( &A::D ); }

   void D() {}
   void DTF() {
      (*TF)();   // C2171
      (this->*TF)();   // OK
   }

   void STF(void (A::*fnc)()) {
      TF = fnc;
   }

private:
   void (A::*TF)();
};
```