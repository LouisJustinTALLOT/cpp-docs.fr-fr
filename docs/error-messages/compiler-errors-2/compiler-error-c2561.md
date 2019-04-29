---
title: Erreur du compilateur C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 8350c5baf129b88c178be280d2da7fe856c6cf57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368420"
---
# <a name="compiler-error-c2561"></a>Erreur du compilateur C2561

'identificateur' : fonction doit retourner une valeur

La fonction a été déclarée comme retournant une valeur, mais la définition de fonction ne contient-elle pas un `return` instruction.

Cette erreur peut être provoquée par un prototype de fonction incorrect :

1. Si la fonction ne retourne pas de valeur, déclarez la fonction avec le type de retour [void](../../cpp/void-cpp.md).

1. Vérifiez que toutes les branches possibles de la fonction retournent la valeur du type déclaré dans le prototype.

1. Les fonctions C++ contenant des routines d’assembly inline qui stockent la valeur de retour dans le `AX` register peut-être une instruction return. Copiez la valeur dans `AX` à une variable temporaire et retournez cette variable à partir de la fonction.

L’exemple suivant génère l’erreur C2561 :

```
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