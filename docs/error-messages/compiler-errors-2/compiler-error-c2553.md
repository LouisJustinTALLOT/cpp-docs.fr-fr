---
title: Erreur du compilateur C2553 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38fb61b7281dd0371c546fd7b7bc960232cf2e00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043987"
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