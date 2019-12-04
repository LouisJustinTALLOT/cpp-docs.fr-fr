---
title: Erreur du compilateur C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 62cf208d9d0025afba06d32a15b9a1e50777c473
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750999"
---
# <a name="compiler-error-c2027"></a>Erreur du compilateur C2027

utilisation du type non défini’type'

Un type ne peut pas être utilisé tant qu’il n’est pas défini. Pour résoudre l’erreur, assurez-vous que le type est entièrement défini avant de le référencer.

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

Il est possible de déclarer un pointeur vers un type déclaré, mais non défini. Mais C++ n’autorise pas une référence à un type non défini.

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
