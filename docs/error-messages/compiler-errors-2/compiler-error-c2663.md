---
title: Erreur du compilateur C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: d74326e49edd980896276e2c6e67526d8d769cb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644338"
---
# <a name="compiler-error-c2663"></a>Erreur du compilateur C2663

'fonction' : nombre surcharges n’ont pas de conversion autorisée pour le pointeur 'this'

Le compilateur n’a pas pu convertir `this` à une des versions surchargées de la fonction membre.

Cette erreur peut être provoquée en appelant une non -`const` fonction membre sur un `const` objet.  Solutions possibles :

1. Supprimer le `const` à partir de la déclaration de l’objet.

1. Ajouter `const` à une des surcharges de fonction membre.

L’exemple suivant génère l’erreur C2663 :

```
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```