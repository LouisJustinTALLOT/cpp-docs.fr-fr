---
title: Avertissement du compilateur (niveau 1) C4551
ms.date: 11/04/2016
f1_keywords:
- C4551
helpviewer_keywords:
- C4551
ms.assetid: 458b59bd-e2d7-425f-9ba6-268ff200424f
ms.openlocfilehash: 8a30ad5622d8e889a7f3ec64b73ead7c63f65b48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616820"
---
# <a name="compiler-warning-level-1-c4551"></a>Avertissement du compilateur (niveau 1) C4551

liste d’arguments de fonction appel manquant

Un appel de fonction doit inclure les parenthèses ouvrantes et fermantes après le nom de fonction, même si la fonction ne prend aucun paramètre.

L’exemple suivant génère C4551 :

```
// C4551.cpp
// compile with: /W1
void function1() {
}

int main() {
   function1;   // C4551
   function1();   // OK
}
```