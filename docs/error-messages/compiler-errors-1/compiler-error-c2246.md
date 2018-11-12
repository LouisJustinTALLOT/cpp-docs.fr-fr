---
title: Erreur du compilateur C2246
ms.date: 11/04/2016
f1_keywords:
- C2246
helpviewer_keywords:
- C2246
ms.assetid: 4f3e4f83-21f3-4256-af96-43e0bb060311
ms.openlocfilehash: c8efb71e0a39c56628fc582421e0f24ceb9b290c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464972"
---
# <a name="compiler-error-c2246"></a>Erreur du compilateur C2246

'identificateur' : données membres static non conformes dans une classe définie localement

Un membre d’une classe, d’une structure ou d’une union avec une portée locale est déclaré `static`.

L’exemple suivant génère l’erreur C2246 :

```
// C2246.cpp
// compile with: /c
void func( void ) {
   class A { static int i; };   // C2246  i is local to func
   static int j;   // OK
};
```