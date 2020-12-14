---
description: 'En savoir plus sur : erreur du compilateur C3182'
title: Erreur du compilateur C3182
ms.date: 11/04/2016
f1_keywords:
- C3182
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
ms.openlocfilehash: d4cf5d86a553a597636c09f72ff3a068e2a6b9b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242026"
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
