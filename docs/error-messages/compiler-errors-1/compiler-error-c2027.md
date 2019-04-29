---
title: Erreur du compilateur C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 3f3fac9d5410595fe5653e257d97d2fd7c858545
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303487"
---
# <a name="compiler-error-c2027"></a>Erreur du compilateur C2027

utilisation du type non défini 'type'

Un type ne peut pas être utilisé jusqu'à ce qu’il est défini. Pour résoudre cette erreur, assurez-vous que le type est entièrement défini avant de le référencer.

## <a name="example"></a>Exemple

L’exemple suivant génère C2027.

```
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

Il est possible de déclarer un pointeur vers un type déclaré mais non défini.  Mais Visual C++ n’autorise pas une référence à un type non défini.

L’exemple suivant génère C2027.

```
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