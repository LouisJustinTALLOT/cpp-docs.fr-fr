---
title: Erreur du compilateur C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 8526dc1fe3cacc872aa91ca058677d15318fd703
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760268"
---
# <a name="compiler-error-c2683"></a>Erreur du compilateur C2683

'Cast' : 'type’n’est pas un type polymorphe

Vous ne pouvez pas utiliser [dynamic_cast](../../cpp/dynamic-cast-operator.md) pour effectuer une conversion à partir d’une classe non polymorphe (une classe sans fonctions virtuelles).

Vous pouvez utiliser [static_cast](../../cpp/static-cast-operator.md) pour effectuer des conversions de types non polymorphes. Toutefois, `static_cast` n’effectue pas de contrôle au moment de l’exécution.

L’exemple suivant génère l’C2683 :

```cpp
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```
