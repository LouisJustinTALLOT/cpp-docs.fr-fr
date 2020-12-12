---
description: 'En savoir plus sur : erreur du compilateur C3239'
title: Erreur du compilateur C3239
ms.date: 11/04/2016
f1_keywords:
- C3239
helpviewer_keywords:
- C3239
ms.assetid: 22a518b7-020f-4f3c-9963-a094667fd1ac
ms.openlocfilehash: ed16767b8076d93176936e53922426d1c87b35da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307351"
---
# <a name="compiler-error-c3239"></a>Erreur du compilateur C3239

'type' : pointeur vers un pointeur intérieur/épinglé est interdit par le Common Language Runtime

Le compilateur a rencontré un type non valide.

L’exemple suivant génère l’erreur C3229 :

```cpp
// C3239.cpp
// compile with: /clr
int main() {
   interior_ptr<int>* pip0;   // C3239

   // OK
   int * pip1;
   interior_ptr<int> pip2;
   int ** pip;
}
```
