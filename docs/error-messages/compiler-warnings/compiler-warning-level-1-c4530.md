---
title: Compilateur avertissement (niveau 1) C4530 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbfbc67377dd48eeb692bdd4cac1f113fbdf7f6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110456"
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