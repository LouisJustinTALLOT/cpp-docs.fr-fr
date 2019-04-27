---
title: Avertissement du compilateur (niveau 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 8020103e8e20bf1a5e955cbfdfafc6a328b439e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221031"
---
# <a name="compiler-warning-level-4-c4516"></a>Avertissement du compilateur (niveau 4) C4516

'class::symbol' : déclarations d’accès sont déconseillées ; déclarations using de membres constituent un meilleur choix

Le comité C++ ANSI a déclaré des déclarations d’accès (modification d’accès d’un membre dans une classe dérivée sans le [à l’aide de](../../cpp/using-declaration.md) mot clé) à être obsolètes. Déclarations d’accès ne peuvent pas pris en charge par les versions futures de C++.

L’exemple suivant génère C4516 :

```
// C4516.cpp
// compile with: /W4
class A
{
public:
   void x(char);
};

class B : protected A
{
public:
   A::x;  // C4516 on access-declaration
   // use the following line instead
   // using A::x; // using-declaration, ok
};

int main()
{
}
```