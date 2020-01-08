---
title: Erreur du compilateur C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: d20bc61df2d0bab9115768b3bc0589f11a9bcdb9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302092"
---
# <a name="compiler-error-c2032"></a>Erreur du compilateur C2032

'identificateur' : la fonction ne peut pas être membre de struct/union’structorunion'

La structure ou l’Union a une fonction membre, ce qui est C++ autorisé dans, mais pas en C. Pour résoudre l’erreur, compilez comme C++ un programme ou supprimez la fonction membre.

L’exemple suivant génère l’C2032 :

```c
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

Solution possible :

```c
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```
