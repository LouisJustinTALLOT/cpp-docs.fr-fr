---
title: Erreur du compilateur C3883 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3883
dev_langs:
- C++
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4387eacb4e35c82af5c2617771b8c887dae42c4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045469"
---
# <a name="compiler-error-c3883"></a>Erreur du compilateur C3883

'var' : un données membres static initonly doivent être initialisées

Une variable marquée avec [initonly](../../dotnet/initonly-cpp-cli.md) n’a pas été initialisé correctement.

L’exemple suivant génère l’erreur C3883 :

```
// C3883.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   static int staticConst1;   // C3883
};
```

L’exemple suivant illustre une résolution possible :

```
// C3883b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst2 = 0;
};
```

L’exemple suivant illustre l’initialisation dans un constructeur statique :

```
// C3883c.cpp
// compile with: /clr /LD
ref struct Y1 {
   initonly
   static int staticConst1;

   static Y1() {
      staticConst1 = 0;
   }
};
```