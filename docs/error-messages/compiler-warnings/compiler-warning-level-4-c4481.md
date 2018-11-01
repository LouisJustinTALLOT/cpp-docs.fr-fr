---
title: Avertissement du compilateur (niveau 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: f88a61a40a789c31e80875d785b95136ac69253c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466935"
---
# <a name="compiler-warning-level-4-c4481"></a>Avertissement du compilateur (niveau 4) C4481

extension non standard utilisée : spécificateur 'mot_clé' de substitution

Un mot clé a été utilisé qui n’est pas dans la norme C++, par exemple, un des spécificateurs de substitution qui fonctionne également sous/CLR.  Pour plus d'informations, consultez

- [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Spécificateurs de substitution](../../windows/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>Exemple

L’exemple suivant génère C4481.

```
// C4481.cpp
// compile with: /W4 /c
class B {
   virtual void f(unsigned);
};

class C : B {
   void f(unsigned) override;   // C4481
   void f2(unsigned);
};
```