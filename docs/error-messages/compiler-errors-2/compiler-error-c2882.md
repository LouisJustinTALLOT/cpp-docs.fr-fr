---
title: Erreur du compilateur C2882
ms.date: 11/04/2016
f1_keywords:
- C2882
helpviewer_keywords:
- C2882
ms.assetid: 617018ee-5a0d-4b8d-9612-77e8ae52679b
ms.openlocfilehash: a1c6f20ae33a545ae2e6bd7b373ecf2444e0d1d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736163"
---
# <a name="compiler-error-c2882"></a>Erreur du compilateur C2882

'name' : utilisation non conforme d’un identificateur d’espace de noms dans l’expression

Vous avez essayé d’utiliser le nom d’un espace de noms dans une expression.

L’exemple suivant génère l’C2882 :

```cpp
// C2882.cpp
// compile with: /c
namespace A {
   int k;
}

int i = A;   // C2882, can't assign A to i
```
