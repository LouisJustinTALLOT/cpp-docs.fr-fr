---
title: Avertissement du compilateur (niveau 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: bcadf31eda079ebb8ea7a496efe4c945e16b1ab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622843"
---
# <a name="compiler-warning-level-1-c4532"></a>Avertissement du compilateur (niveau 1) C4532

'continue' : saut hors du bloc __finally/finally a un comportement indéfini lors de la gestion de l’arrêt

Le compilateur a rencontré un des mots clés suivants :

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

à l’origine d’un saut en dehors d’un [__finally](../../cpp/try-finally-statement.md) ou [enfin](../../dotnet/finally.md) bloc pendant un arrêt anormal.

Si une exception se produit, et pendant que la pile n’est pas vidée pendant l’exécution des gestionnaires de terminaisons (le `__finally` ou blocs finally), et votre code saute hors d’un `__finally` bloc avant le `__finally` bloc se termine, le comportement n’est pas défini. Contrôle ne peut pas retourner au code de déroulement, donc l’exception ne peut pas être gérée correctement.

Si vous devez sauter hors d’un **__finally** bloquer, vérifiez d’abord pour un arrêt anormal.

L’exemple suivant génère C4532 ; simplement mettre en commentaire les instructions de saut à résoudre les avertissements.

```
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```