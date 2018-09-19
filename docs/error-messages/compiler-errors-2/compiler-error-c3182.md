---
title: Erreur du compilateur C3182 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3182
dev_langs:
- C++
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 722f95b41f9f5ec467af25ccf927631590f90e45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110214"
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
