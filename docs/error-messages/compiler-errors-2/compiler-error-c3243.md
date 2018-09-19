---
title: Erreur du compilateur C3243 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3243
dev_langs:
- C++
helpviewer_keywords:
- C3243
ms.assetid: 35d8ad1a-377d-47df-be9d-c55eea23340f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07f03ac41d3c2548e9b94071007412e125e02e44
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075395"
---
# <a name="compiler-error-c3243"></a>Erreur du compilateur C3243

aucune des fonctions de surcharge n’a été introduite par 'interface'

Vous avez essayé de [remplacer explicitement](../../cpp/explicit-overrides-cpp.md) un membre qui n’existe pas dans l’interface spécifiée.

L’exemple suivant génère l’erreur C3243 :

```
// C3243.cpp
#pragma warning(disable:4199)
__interface IX14A {
   void g();
};

__interface IX14B {
   void f();
   void f(int);
};

class CX14 : public IX14A, public IX14B {
public:
   void IX14A::g();
   void IX14B::f();
   void IX14B::f(int);
};

void CX14::IX14A::f()   // C3243 occurs here
{
}
```