---
title: Erreur du compilateur C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 4a2b4dc9dcd71d518845651dee97c566b778eb0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353064"
---
# <a name="compiler-error-c2556"></a>Erreur du compilateur C2556

'identificateur' : les fonctions surchargées ne diffèrent que par le type de retour

Les fonctions surchargées ont des types de retour différents mais la même liste de paramètres. Chaque fonction surchargée doit avoir une liste de paramètres formels distincte.

L’exemple suivant génère l’erreur C2556 :

```
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```