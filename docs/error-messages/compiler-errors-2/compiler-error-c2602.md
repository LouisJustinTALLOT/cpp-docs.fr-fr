---
title: Erreur du compilateur C2602 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2602
dev_langs:
- C++
helpviewer_keywords:
- C2602
ms.assetid: 6c07a40e-537e-4954-b5c5-1e0e58fe1952
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22c4b2ec765259aa7797b49c003f1b2e2860226f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049525"
---
# <a name="compiler-error-c2602"></a>Erreur du compilateur C2602

'classe::identificateur' n’est pas un membre de classe de base de 'class'

`Identifier` n’est pas accessible, car il n’est pas un membre hérité à partir de n’importe quelle classe de base.

L’exemple suivant génère l’erreur C2602 :

```
// C2602.cpp
// compile with: /c
struct X {
   int x;
};
struct A {
   int a;
};
struct B : public A {
   X::x;   // C2602 B is not derived from X
   A::a;   // OK
};
```