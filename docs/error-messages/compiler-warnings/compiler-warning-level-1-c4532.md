---
title: Avertissement du compilateur (niveau 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: b47eb192bc01e6fe2c6c9423ed2c672f16c6818f
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966249"
---
# <a name="compiler-warning-level-1-c4532"></a>Avertissement du compilateur (niveau 1) C4532

'continue' : saut hors de __finally bloc/finally a un comportement indéfini lors de la gestion des arrêts

Le compilateur a rencontré l’un des mots clés suivants :

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

provoquer un saut hors d’un bloc [__finally](../../cpp/try-finally-statement.md) ou [finally](../../dotnet/finally.md) pendant un arrêt anormal.

Si une exception se produit et que la pile est déroulée pendant l’exécution des gestionnaires de terminaisons (les blocs `__finally` ou finally) et que votre code passe hors d’un bloc `__finally` avant la fin du bloc `__finally`, le comportement n’est pas défini. Le contrôle peut ne pas retourner au code de déroulement. l’exception peut donc ne pas être gérée correctement.

Si vous devez sortir d’un bloc de **__finally** , recherchez d’abord un arrêt anormal.

L’exemple suivant génère l’C4532 ; il vous suffit de commenter les instructions de saut pour résoudre les avertissements.

```cpp
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