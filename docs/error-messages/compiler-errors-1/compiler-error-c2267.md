---
title: Erreur du compilateur C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: 5ff8b0bee1f79d9534841e4368fd5a5249cbb413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534844"
---
# <a name="compiler-error-c2267"></a>Erreur du compilateur C2267

'fonction' : les fonctions static avec portée de bloc ne sont pas conformes

Une fonction locale est déclarée `static`. Fonctions statiques doivent avoir une portée globale.

L’exemple suivant génère l’erreur C2267 :

```
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```