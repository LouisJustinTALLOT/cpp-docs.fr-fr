---
title: Erreur du compilateur C3531 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3531
dev_langs:
- C++
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 375eb419e3f2f492df328a964eeb1bb77bc0d5dd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106844"
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