---
title: Erreur du compilateur C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: 503f295d62c598e3138b1a001d6b350c0d90ea84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549732"
---
# <a name="compiler-error-c3898"></a>Erreur du compilateur C3898

'var' : les membres de données de type peuvent uniquement être des membres de types managés

Un [initonly](../../dotnet/initonly-cpp-cli.md) membre de données a été déclaré dans une classe native.  Un `initonly` données membre peut uniquement être déclaré dans une classe CLR.

L’exemple suivant génère l’erreur C3898 :

```
// C3898.cpp
// compile with: /clr
struct Y1 {
   initonly
   static int data_var = 9;   // C3898
};
```

Solution possible :

```
// C3898b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int data_var = 9;
};
```