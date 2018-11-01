---
title: Avertissement du compilateur (niveau 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 4ca00f892adc8fe3ac1bffb59a27ea1744249dea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479519"
---
# <a name="compiler-warning-level-3-c4390"></a>Avertissement du compilateur (niveau 3) C4390

' ;' : vide instruction contrôlée est trouvée ; est-ce l’intention ?

Un point-virgule a été trouvé après une instruction de contrôle qui ne contient aucune instruction.

Si vous obtenez C4390 en raison d’une macro, vous devez utiliser le [avertissement](../../preprocessor/warning.md) pragma pour désactiver C4390 dans le module contenant la macro.

L’exemple suivant génère l’erreur C4390 :

```
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```