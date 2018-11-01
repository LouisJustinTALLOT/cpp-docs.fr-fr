---
title: Erreur du compilateur C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: 4b99578ed40b4ff70f3606840198b7062083ca83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667039"
---
# <a name="compiler-error-c3671"></a>Erreur du compilateur C3671

'function_1' : fonction ne substitue pas 'function_2'

Lorsque vous utilisez la syntaxe de substitution explicite, le compilateur génère une erreur si une fonction n’est pas remplacée.  Consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère C3671.

```
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