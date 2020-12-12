---
description: 'En savoir plus sur : erreur du compilateur C2602'
title: Erreur du compilateur C2602
ms.date: 11/04/2016
f1_keywords:
- C2602
helpviewer_keywords:
- C2602
ms.assetid: 6c07a40e-537e-4954-b5c5-1e0e58fe1952
ms.openlocfilehash: 2922ee0d35dd5820e1df23d9bc812c0650501b35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312019"
---
# <a name="compiler-error-c2602"></a>Erreur du compilateur C2602

'Class :: identifier’n’est pas un membre d’une classe de base de’class'

`Identifier` n’est pas accessible, car il ne s’agit pas d’un membre hérité d’une classe de base.

L’exemple suivant génère l’C2602 :

```cpp
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
