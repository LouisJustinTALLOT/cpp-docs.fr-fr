---
description: 'En savoir plus sur : erreur du compilateur C3883'
title: Erreur du compilateur C3883
ms.date: 11/04/2016
f1_keywords:
- C3883
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
ms.openlocfilehash: 216cfdc6385f12ff565eca581068ac5625a09044
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274422"
---
# <a name="compiler-error-c3883"></a>Erreur du compilateur C3883

'var' : les données membres static initonly doivent être initialisées

Une variable marquée avec [initonly](../../dotnet/initonly-cpp-cli.md) n’a pas été initialisée correctement.

L’exemple suivant génère l’C3883 :

```cpp
// C3883.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   static int staticConst1;   // C3883
};
```

L’exemple suivant illustre une résolution possible :

```cpp
// C3883b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst2 = 0;
};
```

L’exemple suivant montre comment initialiser dans un constructeur statique :

```cpp
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
