---
title: Erreur du compilateur C3662
ms.date: 11/04/2016
f1_keywords:
- C3662
helpviewer_keywords:
- C3662
ms.assetid: 61bd3e41-a86b-42c0-be89-d992d3906ff1
ms.openlocfilehash: c8f2252c05e3e264740004f4126c7557f30b126a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657328"
---
# <a name="compiler-error-c3662"></a>Erreur du compilateur C3662

'membre' : spécificateur de substitution 'spécificateur' uniquement autorisé sur les fonctions membres de classes managées ou WinRT

Un spécificateur de substitution a été utilisé sur un membre de type natif, ce qui n'est pas autorisé.

Pour plus d’informations, consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3662.

```
// C3662.cpp
// compile with: /clr /c
struct S {
   virtual void f();
};

struct S1 : S {
   virtual void f() new;   // C3662
};

ref struct T {
   virtual void f();
};

ref struct T1 : T {
   virtual void f() new;   // OK
};
```