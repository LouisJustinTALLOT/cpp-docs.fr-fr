---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4296'
title: Avertissement du compilateur (niveau 4) C4296
ms.date: 11/04/2016
f1_keywords:
- C4296
helpviewer_keywords:
- C4296
ms.assetid: 9d99aafe-f6bd-4ee0-b8d0-98ce5712274d
ms.openlocfilehash: 995c332a0f1ee46c9df7081dd34a97b51de40ac6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294533"
---
# <a name="compiler-warning-level-4-c4296"></a>Avertissement du compilateur (niveau 4) C4296

'opérateur' : l’expression est toujours false

Une variable non signée a été utilisée dans une opération de comparaison avec la valeur zéro.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4296 :

```cpp
// C4296.cpp
// compile with: /W4
#pragma warning(default : 4296)
int main()
{
   unsigned int u = 9;
   if (u < 0)    // C4296
      u++;
   if (u >= 0)   // C4296
      u++;
}
```
