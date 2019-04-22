---
title: Erreur du compilateur C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 76206cdffce3f551ff472cbd83df486eb41ae80b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776170"
---
# <a name="compiler-error-c3797"></a>Erreur du compilateur C3797

'override' : déclaration d’événement ne peut pas avoir de spécificateur de substitution (doit être sur les méthodes d’ajout/remove/raise event à la place)

Vous ne pouvez pas remplacer un événement trivial (un événement sans méthodes d’accesseur explicitement définie) avec un autre événement trivial. L’événement de substitution doit définir son comportement avec des fonctions d’accesseur.

Pour plus d’informations, consultez [événement](../../extensions/event-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3797.

```
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