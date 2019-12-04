---
title: Erreur du compilateur C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: 6129ff691f804b31fdb8cb487ac4609e4bca6ef2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755185"
---
# <a name="compiler-error-c2698"></a>Erreur du compilateur C2698

la déclaration using pour’declaration 1 'ne peut pas coexister avec la déclaration using existante pour’declaration 2 '

Une fois que vous avez une [déclaration using](../../cpp/using-declaration.md) pour un membre de données, toute déclaration using dans la même portée qui utilise le même nom n’est pas autorisée, car seules les fonctions peuvent être surchargées.

L’exemple suivant génère l’C2698 :

```cpp
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```
