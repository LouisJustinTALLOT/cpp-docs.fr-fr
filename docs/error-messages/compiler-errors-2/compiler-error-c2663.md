---
title: Erreur du compilateur C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f07b63202d8f171dfb69f4bb294b392152b9290b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756030"
---
# <a name="compiler-error-c2663"></a>Erreur du compilateur C2663

'fonction' : les surcharges de nombre n’ont pas de conversion autorisée pour le pointeur’This'

Le compilateur n’a pas pu convertir `this` en aucune des versions surchargées de la fonction membre.

Cette erreur peut être causée par l’appel d’une fonction membre non`const` sur un objet `const`.  Solutions possibles :

1. Supprimez le `const` de la déclaration de l’objet.

1. Ajoutez `const` à l’une des surcharges de la fonction membre.

L’exemple suivant génère l’C2663 :

```cpp
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
