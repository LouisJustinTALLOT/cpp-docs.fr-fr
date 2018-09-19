---
title: Compilateur avertissement (niveau 1) C4739 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4739
dev_langs:
- C++
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7beaaca5d5791079fd8ea1ff8764f0b721f8d57d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112393"
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