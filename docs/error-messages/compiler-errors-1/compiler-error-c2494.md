---
description: 'En savoir plus sur : erreur du compilateur C2494'
title: Erreur du compilateur C2494
ms.date: 11/04/2016
f1_keywords:
- C2494
helpviewer_keywords:
- C2494
ms.assetid: 5dfd07ab-351d-49c9-b54e-f0a104776ab8
ms.openlocfilehash: 4842ad7360b4d8a943ee118cb56d79b694232c84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283652"
---
# <a name="compiler-error-c2494"></a>Erreur du compilateur C2494

> '*Keyword*'ne peut pas être appelé à partir d’une expression de filtre ou d’un bloc __finally/finally

Vous ne pouvez pas utiliser de *mot clé* dans un **`__finally`** **`finally`** bloc ou.

L’exemple suivant génère l’C2494 :

```cpp
// C2494.cpp
#include <malloc.h>

int main() {
   __try {}
   __except ( _alloca(100), 1 ) {}   // C2494
   __try {}
   __finally {
      _alloca(100);   // C2494
   }
}
```

C2494 peut également se produire lors de l’utilisation de **/CLR**.

```cpp
// C2494b.cpp
// compile with: /clr
#include <malloc.h>

int main() {
   char * buf;
   try {}
   catch (char * buf2) {}
   finally {
      _alloca(100);   // C2494
   }
}
```
