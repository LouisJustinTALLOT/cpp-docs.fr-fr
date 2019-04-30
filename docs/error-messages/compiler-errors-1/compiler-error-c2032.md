---
title: Erreur du compilateur C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: 5743aba880f23d7706940936fc4a3a1973a84ca1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400511"
---
# <a name="compiler-error-c2032"></a>Erreur du compilateur C2032

'identificateur' : fonction ne peut pas être membre de struct/union 'StructOuUnion'

La structure ou union a une fonction membre, ce qui est autorisée en C++, mais pas dans C. Pour résoudre l’erreur, compilez comme un programme C++ ou supprimez la fonction membre.

L’exemple suivant génère l’erreur C2032 :

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

Solution possible :

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```