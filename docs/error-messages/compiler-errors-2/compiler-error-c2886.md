---
description: 'En savoir plus sur : erreur du compilateur C2886'
title: Erreur du compilateur C2886
ms.date: 11/04/2016
f1_keywords:
- C2886
helpviewer_keywords:
- C2886
ms.assetid: c01588a1-484c-4dc9-a3f1-f900c6e44543
ms.openlocfilehash: 0a2591a18fc7113b77f90e689860906d35fa9460
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337467"
---
# <a name="compiler-error-c2886"></a>Erreur du compilateur C2886

'Class :: identifier' : le symbole ne peut pas être utilisé dans une déclaration using de membre

Une **`using`** déclaration utilise un symbole, tel qu’un nom d’espace de noms. Une **`using`** déclaration est destinée à déclarer des membres de la classe de base.

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
