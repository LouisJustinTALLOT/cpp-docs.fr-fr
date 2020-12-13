---
description: 'En savoir plus sur : erreur du compilateur C2562'
title: Erreur du compilateur C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: 9e9da8a7463b450073f4b537ec36512242995760
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338712"
---
# <a name="compiler-error-c2562"></a>Erreur du compilateur C2562

'identificateur' : fonction’void’retournant une valeur

La fonction est déclarée comme, **`void`** mais retourne une valeur.

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
