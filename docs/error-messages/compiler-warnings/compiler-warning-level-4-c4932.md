---
title: Avertissement du compilateur (niveau 4) C4932
description: Décrit l’avertissement du compilateur Microsoft C/C++ C4932.
ms.date: 08/25/2020
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: ece2ae14fd8e1198a97f5e772fcce52c47464878
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898289"
---
# <a name="compiler-warning-level-4-c4932"></a>Avertissement du compilateur (niveau 4) C4932

> `__identifier(identifier_1)` et `__identifier(identifier_2)` ne peuvent pas être distingués

Le compilateur ne peut pas faire la distinction entre **`_finally`** et **`__finally`** ou **`__try`** et **`_try`** en tant que paramètre passé à [`__identifier`](../../extensions/identifier-cpp-cli.md) . Vous ne devez pas essayer de les utiliser tous les deux en tant qu’identificateurs dans le même programme, car cela se traduit par une erreur [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) .

L’exemple suivant génère l’erreur C4932 :

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
