---
title: Erreur du compilateur C3182
ms.date: 11/04/2016
f1_keywords:
- C3182
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
ms.openlocfilehash: 6866c7bbcee0a4097e490b344c79a6eec7f94570
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382408"
---
# <a name="compiler-error-c3182"></a>Erreur du compilateur C3182

'classe' : une déclaration de déclaration using ou d’accès de membre n’est pas conforme au sein d’un élément géré ou WinRTtype

Un [à l’aide de](../../cpp/using-declaration.md) déclaration n’est pas valide dans toutes les formes de classes managées.

L'exemple suivant génère l'erreur C3182 et montre comment la corriger.

```
// C3182a.cpp
// compile with: /clr /c
ref struct B {
   void mf(int) {
   }
};

ref struct D : B {
   using B::mf;   // C3182, delete to resolve
   void mf(char) {
   }
};
```
