---
title: Erreur du compilateur C3280
ms.date: 11/04/2016
f1_keywords:
- C3280
helpviewer_keywords:
- C3280
ms.assetid: 86dc5bbc-8818-4786-a728-9334268d308b
ms.openlocfilehash: b43ea73a626ba35f58054a94046915d4eba97181
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566242"
---
# <a name="compiler-error-c3280"></a>Erreur du compilateur C3280

'class' : une fonction membre d’un type managé ne peut pas être compilée comme fonction non managée

Les fonctions membres de classe managée ne peuvent pas être compilées en tant que fonctions non managées.

L’exemple suivant génère l’erreur C3280 :

```
// C3280_2.cpp
// compile with: /clr
ref struct A {
   void func();
};

#pragma managed(push,off)

void A::func()   // C3280
{
}

#pragma managed(pop)
```
