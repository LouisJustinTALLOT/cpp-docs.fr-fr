---
title: Erreur du compilateur C2008 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2008
dev_langs:
- C++
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a00c2a55d7176beae88f7e5db3045722568bd293
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051241"
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