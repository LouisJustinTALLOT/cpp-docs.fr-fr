---
title: Avertissement du compilateur (niveau 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 47e278bbc69b972f6acc391d6b3278ab8d159c08
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990706"
---
# <a name="compiler-warning-level-4-c4516"></a>Avertissement du compilateur (niveau 4) C4516

'Class :: Symbol' : les déclarations d’accès sont déconseillées ; les déclarations using de membre offrent une meilleure alternative

Le Comité C++ ANSI a déclaré des déclarations d’accès (en modifiant l’accès d’un membre dans une classe dérivée sans le mot clé [using](../../cpp/using-declaration.md) ) pour qu’il soit obsolète. Les déclarations d’accès peuvent ne pas être prises en C++charge par les futures versions de.

L’exemple suivant génère l’C4516 :

```cpp
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
