---
title: Erreur du compilateur C2561 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8611af23ab884a853fc751ae82c636753993495b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070702"
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