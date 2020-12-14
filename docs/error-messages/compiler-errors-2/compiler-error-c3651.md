---
description: 'En savoir plus sur : erreur du compilateur C3651'
title: Erreur du compilateur C3651
ms.date: 11/04/2016
f1_keywords:
- C3651
helpviewer_keywords:
- C3651
ms.assetid: a03e692e-c219-4654-9827-8415cfa5a22d
ms.openlocfilehash: 03845059c1c99db7a228d2678148f768cb2e2c1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203716"
---
# <a name="compiler-error-c3651"></a>Erreur du compilateur C3651

'membre' : ne peut pas être utilisé comme substitution explicite, doit être membre d’une classe de base

Une substitution explicite a été spécifiée, mais la fonction en cours de substitution était dans un type qui n’est pas un type de base.

Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’C3651 :

```cpp
// C3651.cpp
// compile with: /clr /c
ref class C {
public:
   virtual void func2();
};

ref class Other {
public:
   virtual void func();
};

ref class D : public C {
public:
   virtual void func() new sealed = Other::func;   // C3651
   virtual void func2() new sealed = C::func2;   // OK
};
```
