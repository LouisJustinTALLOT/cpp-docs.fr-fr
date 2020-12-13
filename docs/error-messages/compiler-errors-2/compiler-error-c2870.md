---
description: 'En savoir plus sur : erreur du compilateur C2870'
title: Erreur du compilateur C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 74e7f2de5cfbb5aca6bd653f5711b989de4ef326
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333761"
---
# <a name="compiler-error-c2870"></a>Erreur du compilateur C2870

'nom' : une définition d’espace de noms doit apparaître soit au niveau de la portée du fichier, soit immédiatement dans une autre définition d’espace de noms

Vous avez défini un espace de noms de `name` manière incorrecte. Les espaces de noms doivent être définis au niveau de la portée du fichier (à l’extérieur de tous les blocs et classes) ou immédiatement dans un autre espace de noms.

L’exemple suivant génère l’C2870 :

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
