---
title: Erreur du compilateur C2254
ms.date: 11/04/2016
f1_keywords:
- C2254
helpviewer_keywords:
- C2254
ms.assetid: 49bb3d7e-3bdf-4af6-937c-fa627be412a9
ms.openlocfilehash: da89741811bbb9055f3f6793d115a357d80ab79a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397534"
---
# <a name="compiler-error-c2254"></a>Erreur du compilateur C2254

'fonction' : spécificateur pure ou substitution abstrait spécificateur non autorisé sur une fonction friend

Un `friend` (fonction) est spécifiée comme pure `virtual`.

L’exemple suivant génère C2254 :

```
// C2254.cpp
// compile with: /c
class A {
public:
   friend void func1() = 0;   // C2254, func1 is friend
   void virtual func2() = 0;   // OK, pure virtual
   friend void func3();   // OK, friend not virtual nor pure
};

void func1() {};
void func3() {};
```