---
title: Erreur du compilateur C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 7236cb75aef4250440a1e992415df07fb5b7da3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757174"
---
# <a name="compiler-error-c3797"></a>Erreur du compilateur C3797

'override' : la déclaration d’événement ne peut pas avoir de spécificateur de substitution (doit être placé sur les méthodes Add/Remove/Raise de l’événement à la place)

Vous ne pouvez pas substituer un événement trivial (un événement sans méthode d’accesseur explicitement défini) par un autre événement trivial. L’événement de substitution doit définir son comportement avec les fonctions d’accesseur.

Pour plus d’informations, consultez [Event](../../extensions/event-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3797.

```cpp
// C3797.cpp
// compile with: /clr /c
delegate void MyDel();

ref class Class1 {
public:
   virtual event MyDel ^ E;
};

ref class Class2 : public Class1 {
public:
   virtual event MyDel ^ E override;   // C3797
};

// OK
ref class Class3 : public Class1 {
public:
   virtual event MyDel ^ E {
      void add(MyDel ^ d) override {}
      void remove(MyDel ^ d) override {}
   }
};
```
