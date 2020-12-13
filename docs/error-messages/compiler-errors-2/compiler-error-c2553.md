---
description: 'En savoir plus sur : erreur du compilateur C2553'
title: Erreur du compilateur C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: 5f5e3eb9d94935aa8e6974f72517e7193ba07db3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134496"
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
