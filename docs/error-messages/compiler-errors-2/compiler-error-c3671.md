---
description: 'En savoir plus sur : erreur du compilateur C3671'
title: Erreur du compilateur C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: a8fba0ccec84789b7fe5e45cd72b18abc3fe63b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228870"
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
