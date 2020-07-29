---
title: Avertissement du compilateur C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: d730441772f021bbece9af8313229543e432b2d7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197291"
---
# <a name="compiler-warning-c4485"></a>Avertissement du compilateur C4485

'override_function' : correspond à la méthode de classe ref de base’base_class_function', mais n’est pas marqué comme’New’ou’override'; 'New' (et’Virtual') est pris par défaut

Un accesseur substitue, avec ou sans le **`virtual`** mot clé, une fonction d’accesseur de classe de base, mais le `override` **`new`** spécificateur ou ne faisait pas partie de la signature de la fonction de substitution. Ajoutez le **`new`** `override` spécificateur ou pour résoudre cet avertissement.

Pour plus d’informations, consultez [override](../../extensions/override-cpp-component-extensions.md) et [New (nouvel emplacement dans vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) .

C4485 est toujours émis en tant qu’erreur. Utilisez le pragma [Warning](../../preprocessor/warning.md) pour supprimer C4485.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4485

```cpp
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```
