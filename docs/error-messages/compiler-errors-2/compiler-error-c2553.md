---
title: Erreur du compilateur C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: aa3e97d576e994878ab5b080363c4c09b79f42ed
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756784"
---
# <a name="compiler-error-c2553"></a>Erreur du compilateur C2553

'base_function' : le type de retour de la fonction virtuelle de substitution diffère de’override_function'

Une fonction dans une classe dérivée a tenté de substituer une fonction virtuelle dans une classe de base, mais la fonction de classe dérivée n’a pas le même type de retour que la fonction de classe de base.  Une signature de fonction de remplacement doit correspondre à la signature de la fonction en cours de substitution.

L’exemple suivant génère l’C2553 :

```cpp
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```
