---
title: Avertissement du compilateur (niveau 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0cf9aef8f68ca5972fd3d7886cd8061b88d043ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221139"
---
# <a name="compiler-warning-level-1-c4717"></a>Avertissement du compilateur (niveau 1) C4717

'fonction' : récurrent sur tous les chemins d’accès de contrôle, la fonction entraînera un débordement de pile d’exécution

Chaque chemin d’accès via une fonction contienne un appel à la fonction. Dans la mesure où il n’existe aucun moyen pour quitter la fonction sans préalablement appeler lui-même de manière récursive, la fonction ne s’arrête jamais.

L’exemple suivant génère C4717 :

```
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