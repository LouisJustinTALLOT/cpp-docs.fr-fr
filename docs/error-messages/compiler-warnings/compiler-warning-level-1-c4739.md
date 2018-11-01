---
title: Avertissement du compilateur (niveau 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 4c48ad9349361324c18ec790c51d1095cce104e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622090"
---
# <a name="compiler-warning-level-1-c4739"></a>Avertissement du compilateur (niveau 1) C4739

la référence à la variable ’var’ dépasse la taille de son espace de stockage

Une valeur a été assignée à une variable, mais la valeur est supérieure à la taille de la variable. La mémoire sera écrite au delà de l’emplacement de mémoire de la variable, et une perte de données est possible.

Pour résoudre cet avertissement, affectez une valeur uniquement à une variable dont la taille lui permet de contenir la valeur.

L’exemple suivant génère l’erreur C4739 :

```
// C4739.cpp
// compile with: /RTCs /Zi /W1 /c
char *pc;
int main() {
   char c;
   *(int *)&c = 1;   // C4739

   // OK
   *(char *)&c = 1;
}
```