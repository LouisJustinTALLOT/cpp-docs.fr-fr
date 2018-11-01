---
title: Erreur du compilateur C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: 7366995f8930b4733ccff73aef38ebcf65a0c120
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575654"
---
# <a name="compiler-error-c2054"></a>Erreur du compilateur C2054

attendu ' (' suivre 'identificateur'

L’identificateur de fonction est utilisé dans un contexte qui requiert des parenthèses fermantes.

Cette erreur peut résulter de l’omission d’un signe égal (=) dans une initialisation complexe.

L’exemple suivant génère l’erreur C2054 :

```
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

Solution possible :

```
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```