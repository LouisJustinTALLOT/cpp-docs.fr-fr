---
title: Erreur du compilateur C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 6b6f08ac52eff355f0857968817a681818e3c3dc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756771"
---
# <a name="compiler-error-c2556"></a>Erreur du compilateur C2556

'identificateur' : les fonctions surchargées diffèrent uniquement par le type de retour

Les fonctions surchargées ont des types de retour différents, mais la même liste de paramètres. Chaque fonction surchargée doit avoir une liste de paramètres formels distincte.

L’exemple suivant génère l’C2556 :

```cpp
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```
