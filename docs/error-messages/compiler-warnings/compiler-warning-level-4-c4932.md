---
title: Avertissement du compilateur (niveau 4) C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: 992e047f31e4a30edd29ba6110bf119d2bc8928b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230595"
---
# <a name="compiler-warning-level-4-c4932"></a>Avertissement du compilateur (niveau 4) C4932

__identifier (identificateur) et \_ _Identifier (identificateur) ne peuvent pas être différenciés

Le compilateur ne peut pas faire la distinction entre **_finally** et **`__finally`** ou `__try` et **_try** en tant que paramètre passé à [__identifier](../../extensions/identifier-cpp-cli.md). Vous ne devez pas essayer de les utiliser tous les deux en tant qu’identificateurs dans le même programme, car cela se traduit par une erreur [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) .

L’exemple suivant génère l’erreur C4932 :

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
