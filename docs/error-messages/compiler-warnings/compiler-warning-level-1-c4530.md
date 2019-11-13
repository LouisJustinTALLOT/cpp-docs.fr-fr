---
title: Avertissement du compilateur (niveau 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 3139d321bca64b9938badebdabccd3ca1eb96d11
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966261"
---
# <a name="compiler-warning-level-1-c4530"></a>Avertissement du compilateur (niveau 1) C4530

C++gestionnaire d’exceptions utilisé, mais les sémantiques de déroulement ne sont pas activées. Spécifier/EHsc

C++la gestion des exceptions a été utilisée mais [/EHsc](../../build/reference/eh-exception-handling-model.md) n’a pas été sélectionné.

Lorsque l’option/EHsc n’a pas été activée, un objet avec un stockage automatique dans le frame, entre la fonction qui effectue la levée et la fonction qui intercepte la levée, ne sera pas détruit. Toutefois, un objet avec un stockage automatique créé dans un bloc **try** ou **catch** sera détruit.

L’exemple suivant génère l’C4530 :

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Compilez l’exemple avec/EHsc pour résoudre l’avertissement.