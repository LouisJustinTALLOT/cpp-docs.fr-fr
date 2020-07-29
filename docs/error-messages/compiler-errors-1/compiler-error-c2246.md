---
title: Erreur du compilateur C2246
ms.date: 11/04/2016
f1_keywords:
- C2246
helpviewer_keywords:
- C2246
ms.assetid: 4f3e4f83-21f3-4256-af96-43e0bb060311
ms.openlocfilehash: c7dac0abb7d65d3f26522ea1a04577643b7b9eca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212824"
---
# <a name="compiler-error-c2246"></a>Erreur du compilateur C2246

'identificateur' : données membres static non conformes dans une classe définie localement

Un membre d’une classe, d’une structure ou d’une Union avec une portée locale est déclaré **`static`** .

L’exemple suivant génère l’erreur C2246 :

```cpp
// C2246.cpp
// compile with: /c
void func( void ) {
   class A { static int i; };   // C2246  i is local to func
   static int j;   // OK
};
```
