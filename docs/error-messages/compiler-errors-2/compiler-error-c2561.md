---
title: Erreur du compilateur C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 9c42a2da662a286f3e6887f6a1dba381687136bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206963"
---
# <a name="compiler-error-c2561"></a>Erreur du compilateur C2561

'identificateur' : la fonction doit retourner une valeur

La fonction a été déclarée comme retournant une valeur, mais la définition de fonction ne contient pas d' **`return`** instruction.

Cette erreur peut être due à un prototype de fonction incorrect :

1. Si la fonction ne retourne pas de valeur, déclarez la fonction avec le type de retour [void](../../cpp/void-cpp.md).

1. Vérifiez que toutes les branches possibles de la fonction retournent une valeur du type déclaré dans le prototype.

1. Les fonctions C++ contenant des routines d’assembly inline qui stockent la valeur de retour dans le `AX` Registre peuvent nécessiter une instruction return. Copiez la valeur dans `AX` une variable temporaire et retournez cette variable à partir de la fonction.

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
