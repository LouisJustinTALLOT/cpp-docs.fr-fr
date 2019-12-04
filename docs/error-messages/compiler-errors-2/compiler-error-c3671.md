---
title: Erreur du compilateur C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: 030a6acb19c0907956d2a5b833b683821591e5c5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758110"
---
# <a name="compiler-error-c3671"></a>Erreur du compilateur C3671

'function_1 ' : la fonction ne substitue pas’function_2 '

Lors de l’utilisation de la syntaxe de substitution explicite, le compilateur génère une erreur si une fonction n’est pas substituée.  Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3671.

```cpp
// C3671.cpp
// compile with: /clr /c
ref struct S {
   virtual void f();
};

ref struct S1 : S {
   virtual void f(int) new sealed = S::f;   // C3671
   virtual void f() new sealed = S::f;
};
```
