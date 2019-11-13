---
title: Avertissement du compilateur (niveau 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0bc95cc770914a1c02a7a40f9754415c2f013d63
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051347"
---
# <a name="compiler-warning-level-1-c4717"></a>Avertissement du compilateur (niveau 1) C4717

'fonction' : récurrent sur tous les chemins d’accès de contrôle, la fonction provoque un dépassement de capacité de la pile Runtime

Chaque chemin d’accès par le biais d’une fonction contient un appel à la fonction. Étant donné qu’il n’existe aucun moyen de quitter la fonction sans avoir d’abord appelé de manière récursive, la fonction ne se fermera jamais.

L’exemple suivant génère l’C4717 :

```cpp
// C4717.cpp
// compile with: /W1 /c
// C4717 expected
int func(int x) {
   if (x > 1)
      return func(x - 1); // recursive call
   else {
      int y = func(0) + 1; // recursive call
      return y;
   }
}

int main(){
   func(1);
}
```