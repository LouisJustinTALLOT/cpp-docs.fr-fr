---
title: Avertissement du compilateur (niveau 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 98ea72bef0cb95163604144c1069a13c3b27d81c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324530"
---
# <a name="compiler-warning-level-1-c4630"></a>Avertissement du compilateur (niveau 1) C4630

'symbole' : spécificateur de classe de stockage 'extern' non conforme sur définition de membre

Un membre de données ou d’une fonction membre est définie en tant que `extern`. Les membres ne peut pas être externes, bien que les objets entiers. Le compilateur ignore le `extern` mot clé. L’exemple suivant génère l’erreur C4630 :

```
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```