---
title: Avertissement du compilateur (niveau 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: d5bee2eb874b965ff99e3dc0038d63d65b346318
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164350"
---
# <a name="compiler-warning-level-1-c4033"></a>Avertissement du compilateur (niveau 1) C4033

'fonction' doit retourner une valeur

La fonction ne retourne pas de valeur. Une valeur non définie est retournée.

Les fonctions qui utilisent `return` sans valeur de retour doivent être déclarées comme type `void`.

Cette erreur concerne le code de langage C.

L’exemple suivant génère l’avertissement C4033 :

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```
