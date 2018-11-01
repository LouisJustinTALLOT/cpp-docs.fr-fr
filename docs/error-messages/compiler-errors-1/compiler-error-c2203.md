---
title: Erreur du compilateur C2203
ms.date: 11/04/2016
f1_keywords:
- C2203
helpviewer_keywords:
- C2203
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
ms.openlocfilehash: 848fdad460402238f4957344dd49bd9128352b4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499874"
---
# <a name="compiler-error-c2203"></a>Erreur du compilateur C2203

supprimer opérateur ne peut pas spécifier de limites pour un tableau

Avec le **/Za** option (ANSI), le `delete` opérateur peut supprimer la totalité d’un tableau, mais pas des parties ou des membres spécifiques du tableau.

L’exemple suivant génère l’erreur C2203 :

```
// C2203.cpp
// compile with: /Za
int main() {
   int *ar = new int[10];
   delete [4] ar;   // C2203
   // try the following line instead
   // delete [] ar;
}
```