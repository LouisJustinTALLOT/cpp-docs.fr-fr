---
title: Avertissement du compilateur (niveau 2) C4309
ms.date: 11/04/2016
f1_keywords:
- C4309
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
ms.openlocfilehash: 41184571dc07213c796c039170966a0c7150bd45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516140"
---
# <a name="compiler-warning-level-2-c4309"></a>Avertissement du compilateur (niveau 2) C4309

'conversion' : troncation de valeur de constante

La conversion de type provoque une constante à dépasser l’espace alloué pour celui-ci. Vous devrez peut-être utiliser un type plus grand pour la constante.

L’exemple suivant génère l’erreur C4309 :

```
// C4309.cpp
// compile with: /W2
int main()
{
   char c = 128;   // C4309
}
```