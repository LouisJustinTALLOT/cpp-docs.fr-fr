---
title: Compilateur avertissement (niveau 1) C4532 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4532
dev_langs:
- C++
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 717af9626866fb20e92342fe90f4dde2b5030774
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025475"
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