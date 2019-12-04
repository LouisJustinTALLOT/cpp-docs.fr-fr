---
title: Erreur du compilateur C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 3b006592723df1222d05e39b3bc9e5729efc8aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755029"
---
# <a name="compiler-error-c2870"></a>Erreur du compilateur C2870

'nom' : une définition d’espace de noms doit apparaître soit au niveau de la portée du fichier, soit immédiatement dans une autre définition d’espace de noms

Vous avez défini l’espace de noms `name` de manière incorrecte. Les espaces de noms doivent être définis au niveau de la portée du fichier (à l’extérieur de tous les blocs et classes) ou immédiatement dans un autre espace de noms.

L’exemple suivant génère l’C2870 :

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
