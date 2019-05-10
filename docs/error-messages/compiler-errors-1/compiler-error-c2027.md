---
title: Erreur du compilateur C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 901e9b791616c5684b352c1fda7687f67b895d9c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447371"
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

Il est possible de déclarer un pointeur vers un type déclaré mais non défini. Mais C++ n’autorise pas une référence à un type non défini.

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