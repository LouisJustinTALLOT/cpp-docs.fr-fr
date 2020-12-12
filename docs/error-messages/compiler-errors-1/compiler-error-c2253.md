---
description: 'En savoir plus sur : erreur du compilateur C2253'
title: Erreur du compilateur C2253
ms.date: 11/04/2016
f1_keywords:
- C2253
helpviewer_keywords:
- C2253
ms.assetid: bd6445ae-b2c1-4669-9657-a8f4acf80b16
ms.openlocfilehash: 7401e9a25382f635ec076e9d84b02e58935bbddd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134782"
---
# <a name="compiler-error-c2253"></a>Erreur du compilateur C2253

'fonction' : spécificateur pure ou spécificateur de substitution abstrait uniquement autorisé sur une fonction virtuelle

Une fonction non virtuelle est spécifiée comme pure **`virtual`** .

L’exemple suivant génère l’C2253 :

```cpp
// C2253.cpp
// compile with: /c
class A {
public:
   void func1() = 0;   // C2253 not virtual
   virtual void func2() = 0;   // OK
};
```

L’exemple suivant génère l’C2253 :

```cpp
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
