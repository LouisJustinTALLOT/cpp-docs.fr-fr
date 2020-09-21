---
title: Erreur du compilateur C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 59d0e5d5a5f0957f2d73cdb863ccee9a2dd2a026
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743254"
---
# <a name="compiler-error-c2027"></a>Erreur du compilateur C2027

utilisation du type non défini’type'

Un type ne peut pas être utilisé tant qu’il n’est pas défini. Pour résoudre l’erreur, assurez-vous que le type est entièrement défini avant de le référencer.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2027.

```cpp
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

Il est possible de déclarer un pointeur vers un type déclaré, mais non défini. Toutefois, C++ n’autorise pas de référence à un type non défini.

L’exemple suivant génère l’C2027.

```cpp
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```
