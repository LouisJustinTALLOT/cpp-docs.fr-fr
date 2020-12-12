---
description: 'En savoir plus sur : erreur du compilateur C2027'
title: Erreur du compilateur C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 131362f2caa8da80865a9601d87cfe3a5e7ab3b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175545"
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
