---
title: Erreur du compilateur C2931
ms.date: 11/04/2016
f1_keywords:
- C2931
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
ms.openlocfilehash: 03c5c1865343afdc0fd7a67ce393c7e1a5d2966f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757694"
---
# <a name="compiler-error-c2931"></a>Erreur du compilateur C2931

'class' : type-class-id redéfini en tant que fonction membre d’'identifier'

Vous ne pouvez pas utiliser une classe ou un modèle générique en tant que fonction membre d’une autre classe.

Cette erreur peut se produire si des accolades sont appariées incorrectement.

L’exemple suivant génère l’erreur C2931 :

```cpp
// C2931.cpp
// compile with: /c
template<class T>
struct TC { };
struct MyStruct {
   void TC<int>();   // C2931
};

struct TC2 { };
struct MyStruct2 {
   void TC2();
};
```

L’erreur C2931 peut également se produire lors de l’utilisation de génériques.

```cpp
// C2931b.cpp
// compile with: /clr /c
generic<class T> ref struct GC {};
struct MyStruct {
   void GC<int>();   // C2931
   void GC2();   // OK
};
```
