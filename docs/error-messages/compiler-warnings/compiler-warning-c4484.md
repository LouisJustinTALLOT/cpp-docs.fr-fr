---
title: Avertissement du compilateur C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 4d3f72ddf7675ea7ad73022dc55a60fdc74d4390
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623627"
---
# <a name="compiler-warning-c4484"></a>Avertissement du compilateur C4484

'override_function' : correspond à la méthode de classe ref de base’base_class_function', mais n’est pas marqué comme’Virtual', 'New’ou’override'; 'New' (et non’Virtual') est pris par défaut

Lors de la compilation avec **/CLR**, le compilateur ne substituera pas implicitement une fonction de classe de base, ce qui signifie que la fonction obtiendra un nouvel emplacement dans la vtable. Pour résoudre le, spécifiez explicitement si une fonction est une substitution.

Pour plus d'informations, voir :

- [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../extensions/override-cpp-component-extensions.md)

- [new (nouvel emplacement dans vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 est toujours émis en tant qu’erreur. Utilisez le pragma [Warning](../../preprocessor/warning.md) pour supprimer C4484.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4484.

```cpp
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```