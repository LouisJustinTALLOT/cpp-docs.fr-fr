---
title: Avertissement du compilateur C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: b5afb829485e0e9533a14e818e6d6785f268a83b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772087"
---
# <a name="compiler-warning-c4485"></a>Avertissement du compilateur C4485

'fonction_substitution' : correspond à la méthode de classe ref de base 'fonction_classe_base', mais n’est pas marqué comme 'new' ou 'override' ; 'new' (et 'virtual') sont supposés.

Un accesseur substitue, avec ou sans le `virtual` mot clé, une fonction d’accesseur de classe de base, mais la `override` ou `new` spécificateur ne faisait pas partie de la signature de fonction de substitution. Ajouter le `new` ou `override` spécificateur pour résoudre cet avertissement.

Consultez [remplacer](../../extensions/override-cpp-component-extensions.md) et [new (nouvel emplacement dans vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) pour plus d’informations.

C4485 est toujours émis en tant qu’erreur. Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour supprimer l’erreur C4485.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4485

```
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