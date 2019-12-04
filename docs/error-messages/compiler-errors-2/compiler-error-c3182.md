---
title: Erreur du compilateur C3182
ms.date: 11/04/2016
f1_keywords:
- C3182
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
ms.openlocfilehash: c6b183eb30dd0e617e69ab9aac58bea5cb721591
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761658"
---
# <a name="compiler-error-c3182"></a>Erreur du compilateur C3182

'classe' : une déclaration using de membre ou une déclaration d’accès est non conforme dans un managé ou un WinRTtype

Une déclaration [using](../../cpp/using-declaration.md) n’est pas valide dans toutes les formes de classes managées.

L'exemple suivant génère l'erreur C3182 et montre comment la corriger.

```cpp
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
