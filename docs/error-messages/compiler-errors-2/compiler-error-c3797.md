---
title: Erreur du compilateur C3797 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3797
dev_langs:
- C++
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ac1ded1c95f7e8bea9598e468010c75d8bd917a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033418"
---
# <a name="compiler-error-c3797"></a>Erreur du compilateur C3797

'override' : déclaration d’événement ne peut pas avoir de spécificateur de substitution (doit être sur les méthodes d’ajout/remove/raise event à la place)

Vous ne pouvez pas remplacer un événement trivial (un événement sans méthodes d’accesseur explicitement définie) avec un autre événement trivial. L’événement de substitution doit définir son comportement avec des fonctions d’accesseur.

Pour plus d’informations, consultez [événement](../../windows/event-cpp-component-extensions.md).

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