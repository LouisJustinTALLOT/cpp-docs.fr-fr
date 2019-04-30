---
title: Erreur du compilateur C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 6961d99d1a0d7d0ea063aee5544a1009af2547c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397404"
---
# <a name="compiler-error-c3531"></a>Erreur du compilateur C3531

'symbole' : un symbole dont le type contient 'auto' doit avoir un initialiseur

La variable spécifiée n’a pas une expression d’initialiseur.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Spécifiez une expression d’initialiseur, comme une assignation simple qui utilise la syntaxe avec signe égal, lorsque vous déclarez la variable.

## <a name="example"></a>Exemple

L’exemple suivant donne C3531 parce que les variables `x1`, `y1, y2, y3`, et `z2` ne sont pas initialisés.

```
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