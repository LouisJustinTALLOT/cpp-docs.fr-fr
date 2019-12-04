---
title: Erreur du compilateur C2886
ms.date: 11/04/2016
f1_keywords:
- C2886
helpviewer_keywords:
- C2886
ms.assetid: c01588a1-484c-4dc9-a3f1-f900c6e44543
ms.openlocfilehash: a64457c84a48c73ad6714da01e48d41f3cc92efb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748721"
---
# <a name="compiler-error-c2886"></a>Erreur du compilateur C2886

'Class :: identifier' : le symbole ne peut pas être utilisé dans une déclaration using de membre

Une déclaration de `using` utilise un symbole, tel qu’un nom d’espace de noms. Une déclaration de `using` est destinée à déclarer des membres de la classe de base.

L’exemple suivant génère l’C2886 :

```cpp
// C2886.cpp
// compile with: /c
namespace Z {
    int i;
}

class B {
protected:
    int i;
};

class D : public B {
    // Error: Z is a namespace
    using Z::i;   // C2886

    // OK: B is a base class
    using B::i;
};
```
