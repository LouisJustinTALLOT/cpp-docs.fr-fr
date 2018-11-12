---
title: Erreur du compilateur C2575
ms.date: 11/04/2016
f1_keywords:
- C2575
helpviewer_keywords:
- C2575
ms.assetid: 9eb45706-37ef-4481-b373-6d193ba13634
ms.openlocfilehash: 2737f9078e1c17358e3c975a5c3f8b6d211fd308
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434358"
---
# <a name="compiler-error-c2575"></a>Erreur du compilateur C2575

'identificateur' : seules les fonctions membres et les bases peuvent être virtuelles

Une fonction globale ou la classe est déclarée `virtual`. Cette opération n’est pas autorisée.

L’exemple suivant génère l’erreur C2575 :

```
// C2575.cpp
// compile with: /c
virtual void func() {}   // C2575

void func2() {}
struct A {
   virtual void func2(){}
};
```