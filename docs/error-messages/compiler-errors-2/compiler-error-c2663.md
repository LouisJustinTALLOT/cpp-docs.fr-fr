---
title: Erreur du compilateur C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f9746ecb41e873fb1d929a939c78f1817dc0e2f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220273"
---
# <a name="compiler-error-c2663"></a>Erreur du compilateur C2663

'fonction' : les surcharges de nombre n’ont pas de conversion autorisée pour le pointeur’This'

Le compilateur n’a pas pu effectuer la conversion **`this`** en une des versions surchargées de la fonction membre.

Cette erreur peut être causée par l’appel d’une **`const`** fonction non membre sur un **`const`** objet.  Solutions possibles :

1. Supprimez **`const`** de la déclaration de l’objet.

1. Ajoutez **`const`** à l’une des surcharges de la fonction membre.

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
