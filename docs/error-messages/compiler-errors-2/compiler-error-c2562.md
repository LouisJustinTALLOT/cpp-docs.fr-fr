---
title: Erreur du compilateur C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: c665c4ed82fefaf0ee724defb8c205f86fc06dd0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228882"
---
# <a name="compiler-error-c2562"></a>Erreur du compilateur C2562

'identificateur' : fonction 'void' retournant une valeur

La fonction est déclarée en tant que `void` mais retourne une valeur.

Cette erreur peut être dû à un prototype de fonction incorrect.

Cette erreur peut être résolue si vous spécifiez le type de retour dans la déclaration de fonction.

L’exemple suivant génère l’erreur C2562 :

```
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```