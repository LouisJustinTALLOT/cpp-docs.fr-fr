---
title: Erreur du compilateur C2253
ms.date: 11/04/2016
f1_keywords:
- C2253
helpviewer_keywords:
- C2253
ms.assetid: bd6445ae-b2c1-4669-9657-a8f4acf80b16
ms.openlocfilehash: 847c37c6ae5edf14205d3d46ca624a572c8d6b6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397559"
---
# <a name="compiler-error-c2253"></a>Erreur du compilateur C2253

'fonction' : spécificateur pure ou abstraite spécificateur de substitution uniquement autorisé sur une fonction virtuelle

Une fonction non virtuelle est spécifiée comme pure `virtual`.

L’exemple suivant génère l’erreur C2253 :

```
// C2253.cpp
// compile with: /c
class A {
public:
   void func1() = 0;   // C2253 not virtual
   virtual void func2() = 0;   // OK
};
```

L’exemple suivant génère l’erreur C2253 :

```
// C2253_2.cpp
// compile with: /clr /c
ref struct A {
   property int Prop_3 {
      int get() abstract;   // C2253
      // try the following line instead
      // virtual int get() abstract;

      void set(int i) abstract;   // C2253
      // try the following line instead
      // virtual void set(int i) abstract;
   }
};
```