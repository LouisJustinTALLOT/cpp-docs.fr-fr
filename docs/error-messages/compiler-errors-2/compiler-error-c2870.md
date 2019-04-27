---
title: Erreur du compilateur C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165038"
---
# <a name="compiler-error-c2870"></a>Erreur du compilateur C2870

'name' : une définition de l’espace de noms doit apparaître soit au niveau de la portée du fichier, soit immédiatement au sein d’une autre définition de l’espace de noms

Vous avez défini l’espace de noms `name` incorrectement. Espaces de noms doit être définie dans la portée du fichier (en dehors de tous les blocs et classes) ou immédiatement au sein d’un autre espace de noms.

L’exemple suivant génère l’erreur C2870 :

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```