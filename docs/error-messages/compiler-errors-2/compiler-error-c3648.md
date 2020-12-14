---
description: 'En savoir plus sur : erreur du compilateur C3648'
title: Erreur du compilateur C3648
ms.date: 11/04/2016
f1_keywords:
- C3648
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
ms.openlocfilehash: 532c65896ae5c3707c86735c661a095698417288
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203742"
---
# <a name="compiler-error-c3648"></a>Erreur du compilateur C3648

Cette syntaxe de substitution explicite requiert/CLR : oldSyntax

Lors de la compilation de la dernière syntaxe managée, le compilateur a trouvé une syntaxe de substitution explicite pour les versions précédentes qui n’est plus prise en charge.

Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3648 :

```cpp
// C3648.cpp
// compile with: /clr
public interface struct I {
   void f();
};

public ref struct R : I {
   virtual void I::f() {}   // C3648
   // try the following line instead
   // virtual void f() = I::f{}
};
```
