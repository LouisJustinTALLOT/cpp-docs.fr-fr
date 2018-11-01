---
title: Erreur du compilateur C2277
ms.date: 11/04/2016
f1_keywords:
- C2277
helpviewer_keywords:
- C2277
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
ms.openlocfilehash: 5b20594df8a250a54a0fd5902e0453f7438cbbfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448085"
---
# <a name="compiler-error-c2277"></a>Erreur du compilateur C2277

'identificateur' : ne peut pas prendre l’adresse de cette fonction membre

Vous ne pouvez pas prendre l’adresse d’une fonction membre.

L’exemple suivant génère l’erreur C2277 :

```
// C2277.cpp
class A {
public:
   A();
};
(*pctor)() = &A::A;   // C2277
```