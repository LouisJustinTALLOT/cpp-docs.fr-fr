---
title: Erreur du compilateur C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 49e4897ad5db866aa1ca42589859bedff12718df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625154"
---
# <a name="compiler-error-c2683"></a>Erreur du compilateur C2683

'cast' : 'type' n’est pas un type polymorphe

Vous ne pouvez pas utiliser [dynamic_cast](../../cpp/dynamic-cast-operator.md) à convertir à partir d’une classe non polymorphe (une classe sans fonctions virtuelles).

Vous pouvez utiliser [static_cast](../../cpp/static-cast-operator.md) pour effectuer des conversions des types non polymorphes. Toutefois, `static_cast` n’effectue pas une vérification de l’exécution.

L’exemple suivant génère l’erreur C2683 :

```
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```