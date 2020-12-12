---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4630'
title: Avertissement du compilateur (niveau 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 49a73dcd3ce11fefa1d4275e57ad98092c242d8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318908"
---
# <a name="compiler-warning-level-1-c4630"></a>Avertissement du compilateur (niveau 1) C4630

'Symbol' : spécificateur de classe de stockage’extern’non conforme sur la définition de membre

Un membre de données ou une fonction membre est défini comme **`extern`** . Les membres ne peuvent pas être externes, bien que les objets entiers puissent. Le compilateur ignore le **`extern`** mot clé. L’exemple suivant génère l’C4630 :

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```
