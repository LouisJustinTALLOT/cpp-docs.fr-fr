---
title: Erreur du compilateur C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: 11cb2b83d958f0c59d05034a716a022f00b326ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658677"
---
# <a name="compiler-error-c2553"></a>Erreur du compilateur C2553

'fonction_base' : retour de fonction virtuelle de substitution type diffère de 'fonction_substitution'

Une fonction dans une classe dérivée a tenté de substituer une fonction virtuelle dans une classe de base, mais la fonction de la classe dérivée ne disposait pas du même type de retour que la fonction de la classe de base.  Une signature de fonction de remplacement doit correspondre à la signature de la fonction qui est substituée.

L’exemple suivant génère l’erreur C2553 :

```
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