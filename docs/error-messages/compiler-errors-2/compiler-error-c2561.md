---
title: Erreur du compilateur C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: b4a14be9cd32c752e2ab889417494e80b935e31b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755562"
---
# <a name="compiler-error-c2561"></a>Erreur du compilateur C2561

'identificateur' : la fonction doit retourner une valeur

La fonction a été déclarée comme retournant une valeur, mais la définition de fonction ne contient pas d’instruction `return`.

Cette erreur peut être due à un prototype de fonction incorrect :

1. Si la fonction ne retourne pas de valeur, déclarez la fonction avec le type de retour [void](../../cpp/void-cpp.md).

1. Vérifiez que toutes les branches possibles de la fonction retournent une valeur du type déclaré dans le prototype.

1. C++les fonctions contenant des routines d’assembly inline qui stockent la valeur de retour dans le registre `AX` peuvent nécessiter une instruction return. Copiez la valeur de `AX` dans une variable temporaire et retournez cette variable à partir de la fonction.

L’exemple suivant génère l’C2561 :

```cpp
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```
