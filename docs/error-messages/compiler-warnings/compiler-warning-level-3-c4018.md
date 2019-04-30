---
title: Compilateur avertissement (niveau 3) C4018
ms.date: 11/04/2016
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
ms.openlocfilehash: 6436f62a06cbe931ca5b42751d60507f21675c5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402370"
---
# <a name="compiler-warning-level-3-c4018"></a>Compilateur avertissement (niveau 3) C4018

'expression' : incompatibilité signed/unsigned

Comparaison d’un nombre signé et non signé requis au compilateur de convertir la valeur signée non signé.

Cet avertissement peut être résolu si vous transformez un des deux types lors du test de types signés et non signés.

L’exemple suivant génère l’erreur C4018 :

```
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```