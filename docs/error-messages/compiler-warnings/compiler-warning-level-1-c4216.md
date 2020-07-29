---
title: Avertissement du compilateur (niveau 4) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: b7fc44fd15f761c19ed28402a41b3bd3619b21a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223263"
---
# <a name="compiler-warning-level-1-c4216"></a>Avertissement du compilateur (niveau 4) C4216

extension non standard utilisée : float long

Les extensions Microsoft par défaut (/Ze) traitent la valeur **float long** comme **`double`** . Compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)). Utilisez **`double`** pour maintenir la compatibilité. L’exemple suivant génère l’C4216 :

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```
