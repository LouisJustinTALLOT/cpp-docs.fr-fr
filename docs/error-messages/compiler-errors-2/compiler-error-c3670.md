---
description: 'En savoir plus sur : erreur du compilateur C3670'
title: Erreur du compilateur C3670
ms.date: 11/04/2016
f1_keywords:
- C3670
helpviewer_keywords:
- C3670
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
ms.openlocfilehash: 499ef1a8f0638da7693ccdbdc0b02c0d5c86c59b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228935"
---
# <a name="compiler-error-c3670"></a>Erreur du compilateur C3670

'override' : impossible de substituer la méthode de classe de base inaccessible’Method'

Une substitution ne peut avoir lieu que sur une fonction dont le niveau d’accès le rend disponible dans un type dérivé. Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’C3670 :

```cpp
// C3670.cpp
// compile with: /clr /c
public ref class C {
// Uncomment the following line to resolve.
// public:
   virtual void g() { }
};

public ref class D : public C {
public:
   virtual void f() new sealed = C::g {};   // C3670
};
```
