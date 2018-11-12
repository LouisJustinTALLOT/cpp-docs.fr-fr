---
title: Erreur du compilateur C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 0bd9193d6e305a4b6c6851ef2524a68ecc056816
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565709"
---
# <a name="compiler-error-c2008"></a>Erreur du compilateur C2008

'character' : inattendu dans la définition d’une macro

Le caractère apparaît immédiatement après le nom de macro. Pour résoudre l’erreur, il doit y avoir un espace après le nom de macro.

L’exemple suivant génère l’erreur C2008 :

```
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

Solution possible :

```
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```