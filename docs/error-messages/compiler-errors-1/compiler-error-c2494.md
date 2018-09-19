---
title: Erreur du compilateur C2494 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2494
dev_langs:
- C++
helpviewer_keywords:
- C2494
ms.assetid: 5dfd07ab-351d-49c9-b54e-f0a104776ab8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e651e66ce571ddd084c470b52494235f35f2b008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066802"
---
# <a name="compiler-error-c2494"></a>Erreur du compilateur C2494

'mot_clé' ne peut pas être appelée à partir d’une expression de filtre ou bloc __finally/finally

Vous ne pouvez pas utiliser `keyword` dans un `__finally` ou le bloc finally.

L’exemple suivant génère l’erreur C2494 :

```
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

C2494 peut également se produire lorsque vous utilisez **/CLR**.

```
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