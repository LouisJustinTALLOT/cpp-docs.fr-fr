---
title: Avertissement du compilateur (niveau 4) C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: cd37ee67545918991b286d16d0fe27b47414b3c3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779269"
---
# <a name="compiler-warning-level-4-c4932"></a>Avertissement du compilateur (niveau 4) C4932

__identifier (identifier) et \__identifier(identifier) ne se distinguent pas

Le compilateur ne peut pas faire la distinction entre **_finally** et `__finally` ou `__try` et **_try** en tant que paramètre passé à [__identifier](../../extensions/identifier-cpp-cli.md). Vous ne devez pas essayer de les utiliser tous les deux en tant qu’identificateurs dans le même programme, car cela se traduit par une erreur [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) .

L’exemple suivant génère l’erreur C4932 :

```
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```