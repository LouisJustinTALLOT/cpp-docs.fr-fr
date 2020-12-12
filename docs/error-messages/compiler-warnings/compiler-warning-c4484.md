---
description: 'En savoir plus sur : avertissement du compilateur C4484'
title: Avertissement du compilateur C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 43228cabc8dfd728ea104f6c3b57d863ec9e5e5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180732"
---
# <a name="compiler-warning-c4484"></a>Avertissement du compilateur C4484

'override_function' : correspond à la méthode de classe ref de base’base_class_function', mais n’est pas marqué comme’Virtual', 'New’ou’override'; 'New' (et non’Virtual') est pris par défaut

Lors de la compilation avec **/CLR**, le compilateur ne substituera pas implicitement une fonction de classe de base, ce qui signifie que la fonction obtiendra un nouvel emplacement dans la vtable. Pour résoudre le, spécifiez explicitement si une fonction est une substitution.

Pour plus d'informations, consultez les pages suivantes :

- [/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

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
