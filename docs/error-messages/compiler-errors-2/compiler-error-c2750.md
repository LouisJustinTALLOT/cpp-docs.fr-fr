---
description: 'En savoir plus sur : erreur du compilateur C2750'
title: Erreur du compilateur C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 727bf085e1377de8725f6537a33917283d51d839
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174492"
---
# <a name="compiler-error-c2750"></a>Erreur du compilateur C2750

'type' : impossible d’utiliser’New’sur le type référence ; Utilisez’gcnew’à la place

Pour créer une instance d’un type CLR, ce qui provoque le placement de l’instance sur le tas récupéré par le garbage collector, vous devez utiliser [gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md).

L’exemple suivant génère l’C2750 :

```cpp
// C2750.cpp
// compile with: /clr
ref struct Y1 {};

int main() {
   Y1 ^ x = new Y1;   // C2750

   // try the following line instead
   Y1 ^ x2 = gcnew Y1;
}
```
