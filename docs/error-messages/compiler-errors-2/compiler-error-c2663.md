---
title: Erreur du compilateur C2663 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fed35dcce056eb3d2a660c154e94b8058563dba7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083689"
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