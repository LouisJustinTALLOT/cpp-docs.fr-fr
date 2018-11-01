---
title: Erreur du compilateur C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 96fd97aa5021b7e1bc5226162f9c54ff4d6211b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649742"
---
# <a name="compiler-error-c3160"></a>Erreur du compilateur C3160

'pointeur' :  les données membres d'une classe managée ou WinRT ne peuvent pas avoir ce type

Les pointeurs intérieurs de garbage collection peuvent pointer vers l’intérieur d’une classe managée ou WinRT. Comme ils sont plus lents que les pointeurs d'objet entier et nécessitent un traitement spécial par le récupérateur de mémoire, vous ne pouvez pas déclarer les pointeurs managés intérieurs en tant que membres d'une classe.

L'exemple suivant génère l'erreur C3160 :

```
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
