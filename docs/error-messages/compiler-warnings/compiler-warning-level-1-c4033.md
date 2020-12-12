---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4033'
title: Avertissement du compilateur (niveau 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: 1d2455d62b3c375b0f1a863e6cfc3064f44e840a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325957"
---
# <a name="compiler-warning-level-1-c4033"></a>Avertissement du compilateur (niveau 1) C4033

'fonction' doit retourner une valeur

La fonction ne retourne pas de valeur. Une valeur non définie est retournée.

Les fonctions qui utilisent **`return`** sans valeur de retour doivent être déclarées en tant que type **`void`** .

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
