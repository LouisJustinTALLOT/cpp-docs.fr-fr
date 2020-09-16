---
title: Avertissement du compilateur (niveau 1) C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: 6db814e405c0b13cdf40fc81a1f23c6d59fd5f00
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684662"
---
# <a name="compiler-warning-level-1-c4488"></a>Avertissement du compilateur (niveau 1) C4488

'fonction' : requiert le mot clé’keyword’pour implémenter la méthode d’interface’interface_method'

Une classe doit implémenter tous les membres d’une interface dont elle hérite directement. Un membre implémenté doit avoir une accessibilité publique et doit être marqué comme virtuel.

## <a name="examples"></a>Exemples

C4488 peut se produire si un membre implémenté n’est pas public. L’exemple suivant génère l’C4488.

```cpp
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

C4488 peut se produire si un membre implémenté n’est pas marqué comme Virtual. L’exemple suivant génère l’C4488.

```cpp
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```
