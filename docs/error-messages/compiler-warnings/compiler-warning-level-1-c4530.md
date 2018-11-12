---
title: Avertissement du compilateur (niveau 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: a542f9b6bb73e561592e1e779aa6ee493612e6ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554091"
---
# <a name="compiler-warning-level-1-c4530"></a>Avertissement du compilateur (niveau 1) C4530

Gestionnaire d’exceptions C++ utilisé, mais les sémantiques de déroulement ne sont pas activés. Spécifiez /EHsc

Gestion des exceptions C++ a été utilisée mais [/EHsc](../../build/reference/eh-exception-handling-model.md) n’était pas sélectionnée.

Lorsque l’option de /EHsc n’a pas été activée, un objet à stockage automatique dans le frame, entre la fonction de levée de l’exception et la fonction de détection de l’exception, n’est pas détruit. Toutefois, un objet à stockage automatique créé dans un **essayez** ou **catch** bloc sera détruit.

L’exemple suivant génère l’erreur C4530 :

```
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Compilez l’exemple avec /EHsc pour résoudre l’avertissement.