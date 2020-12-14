---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4739'
title: Avertissement du compilateur (niveau 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 03473c8bb5434e8ee05778f40c2cf773de1b64da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228545"
---
# <a name="compiler-warning-level-1-c4739"></a>Avertissement du compilateur (niveau 1) C4739

la référence à la variable ’var’ dépasse la taille de son espace de stockage

Une valeur a été assignée à une variable, mais la valeur est supérieure à la taille de la variable. La mémoire sera écrite au delà de l’emplacement de mémoire de la variable, et une perte de données est possible.

Pour résoudre cet avertissement, affectez une valeur uniquement à une variable dont la taille lui permet de contenir la valeur.

L’exemple suivant génère l’erreur C4739 :

```cpp
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
