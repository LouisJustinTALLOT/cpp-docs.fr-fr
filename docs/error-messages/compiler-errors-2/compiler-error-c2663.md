---
description: 'En savoir plus sur : erreur du compilateur C2663'
title: Erreur du compilateur C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: 3e70e2d10b0a133769d92ce637bd9e5f4d44315a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169981"
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
