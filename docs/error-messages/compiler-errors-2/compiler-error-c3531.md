---
title: Erreur du compilateur C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 7da9da2daedc79db619f82848dc864d1cb7bd1f1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750089"
---
# <a name="compiler-error-c3531"></a>Erreur du compilateur C3531

'Symbol' : un symbole dont le type contient’auto’doit avoir un initialiseur

La variable spécifiée n’a pas d’expression d’initialiseur.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Spécifiez une expression d’initialiseur, telle qu’une assignation simple qui utilise la syntaxe de signe égal, lorsque vous déclarez la variable.

## <a name="example"></a>Exemple

L’exemple suivant génère C3531, car les variables `x1`, `y1, y2, y3`et `z2` ne sont pas initialisées.

```cpp
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>Voir aussi

[auto, mot clé](../../cpp/auto-keyword.md)
