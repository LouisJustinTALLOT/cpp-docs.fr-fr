---
title: Avertissement du compilateur (niveau 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 414388fc1b9c6a7425d45e2ba92546960cadf404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199613"
---
# <a name="compiler-warning-level-1-c4630"></a>Avertissement du compilateur (niveau 1) C4630

'Symbol' : spécificateur de classe de stockage’extern’non conforme sur la définition de membre

Un membre de données ou une fonction membre est défini en tant que `extern`. Les membres ne peuvent pas être externes, bien que les objets entiers puissent. Le compilateur ignore le mot clé `extern`. L’exemple suivant génère l’C4630 :

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```
