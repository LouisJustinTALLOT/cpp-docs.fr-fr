---
title: Avertissement du compilateur (niveau 1) C4552
ms.date: 11/04/2016
f1_keywords:
- C4552
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
ms.openlocfilehash: 1fb2dc7fd4bc685e457898b47c513c21009146ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585547"
---
# <a name="compiler-warning-level-1-c4552"></a>Avertissement du compilateur (niveau 1) C4552

'opérateur' : opérateur n’a aucun effet ; opérateur avec effet secondaire attendu

Si une instruction d’expression a un opérateur sans effet que la partie supérieure de l’expression, il est probablement une erreur.

Pour ignorer cet avertissement, placez l’expression entre parenthèses.

L’exemple suivant génère l’erreur C4552 :

```
// C4552.cpp
// compile with: /W1
int main() {
   int i, j;
   i + j;   // C4552
   // try the following line instead
   // (i + j);
}
```