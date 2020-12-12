---
description: 'En savoir plus sur : avertissement du compilateur C4485'
title: Avertissement du compilateur C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: 85ce885aa299adf68b12d46f0a74af5aa55319f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180706"
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
