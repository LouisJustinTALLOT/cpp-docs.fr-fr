---
description: 'En savoir plus sur : erreur du compilateur C3255'
title: Erreur du compilateur C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: 576b2c9126173f72470a6e741dd64d8a356c9224
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194200"
---
# <a name="compiler-error-c3255"></a>Erreur du compilateur C3255

'value type' : impossible d’allouer dynamiquement cet objet de type valeur sur un tas natif

Les instances d’un type valeur (voir [classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md)) qui contiennent des membres managés peuvent être créées sur la pile, mais pas sur le tas.

L’exemple suivant génère l’C3255 :

```cpp
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
