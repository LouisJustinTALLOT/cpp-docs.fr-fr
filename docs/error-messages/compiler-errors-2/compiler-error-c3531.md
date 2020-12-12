---
description: 'En savoir plus sur : erreur du compilateur C3531'
title: Erreur du compilateur C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 996a9cbda0bf1719c5fd14a1b36632d1710f8beb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113179"
---
# <a name="compiler-error-c3531"></a>Erreur du compilateur C3531

'Symbol' : un symbole dont le type contient’auto’doit avoir un initialiseur

La variable spécifiée n’a pas d’expression d’initialiseur.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Spécifiez une expression d’initialiseur, telle qu’une assignation simple qui utilise la syntaxe de signe égal, lorsque vous déclarez la variable.

## <a name="example"></a>Exemple

L’exemple suivant génère C3531, car les variables `x1` , `y1, y2, y3` et ne `z2` sont pas initialisées.

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

[Auto, mot clé](../../cpp/auto-cpp.md)
