---
title: Erreur du compilateur C2882
ms.date: 11/04/2016
f1_keywords:
- C2882
helpviewer_keywords:
- C2882
ms.assetid: 617018ee-5a0d-4b8d-9612-77e8ae52679b
ms.openlocfilehash: e5fd20695f6922ba5832abb1042cce63b7c4f5a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378880"
---
# <a name="compiler-error-c2882"></a>Erreur du compilateur C2882

'name' : utilisation non conforme de l’identificateur d’espace de noms dans l’expression

Vous avez essayé d’utiliser le nom d’un espace de noms dans une expression.

L’exemple suivant génère l’erreur C2882 :

```
// C2882.cpp
// compile with: /c
namespace A {
   int k;
}

int i = A;   // C2882, can't assign A to i
```