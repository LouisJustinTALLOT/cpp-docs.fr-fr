---
title: Erreur du compilateur C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: 78536fdc0c2a6a6e9c4842fdea6423037496b30b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755549"
---
# <a name="compiler-error-c2562"></a>Erreur du compilateur C2562

'identificateur' : fonction’void’retournant une valeur

La fonction est déclarée comme `void` mais retourne une valeur.

Cette erreur peut être due à un prototype de fonction incorrect.

Cette erreur peut être résolue si vous spécifiez le type de retour dans la déclaration de la fonction.

L’exemple suivant génère l’C2562 :

```cpp
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```
