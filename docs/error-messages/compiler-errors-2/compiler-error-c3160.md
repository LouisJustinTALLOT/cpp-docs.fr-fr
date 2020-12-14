---
description: 'En savoir plus sur : erreur du compilateur C3160'
title: Erreur du compilateur C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 863670f30a6a911977ead0d541dcba825e4f124a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242325"
---
# <a name="compiler-error-c3160"></a>Erreur du compilateur C3160

'pointeur' :  les données membres d'une classe managée ou WinRT ne peuvent pas avoir ce type

Les pointeurs intérieurs de garbage collection peuvent pointer vers l’intérieur d’une classe managée ou WinRT. Comme ils sont plus lents que les pointeurs d'objet entier et nécessitent un traitement spécial par le récupérateur de mémoire, vous ne pouvez pas déclarer les pointeurs managés intérieurs en tant que membres d'une classe.

L'exemple suivant génère l'erreur C3160 :

```cpp
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
