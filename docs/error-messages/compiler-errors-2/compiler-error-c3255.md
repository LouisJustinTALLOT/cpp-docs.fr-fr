---
title: Erreur du compilateur C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: a5b483f3aaa82e543d561cb7c550495069a19f7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519936"
---
# <a name="compiler-error-c3255"></a>Erreur du compilateur C3255

'type valeur' : Impossible d’allouer dynamiquement cet objet de type valeur sur un tas natif

Instances d’un type valeur (voir [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md)) qui contient des membres managés peuvent être créées sur la pile, mais pas sur le tas.

L’exemple suivant génère l’erreur C3255 :

```
// C3255.cpp
// compile with: /clr
using namespace System;
value struct V {
   Object^ o;
};

value struct V2 {
   int i;
};

int main() {
   V* pv = new V;   // C3255
   V2* pv2 = new V2;
   V v2;
}
```
