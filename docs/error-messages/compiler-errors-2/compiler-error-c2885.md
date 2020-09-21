---
title: Erreur du compilateur C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 1953cb8fb9f80c5c1f967e10583c2b7303075f59
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742669"
---
# <a name="compiler-error-c2885"></a>Erreur du compilateur C2885

'Class :: identifier' : déclaration using non valide au niveau d’une portée sans classe

Vous avez utilisé une déclaration [using](../../cpp/using-declaration.md) de manière incorrecte.

Cette erreur peut être générée en raison du travail de mise en conformité du compilateur pour Visual Studio 2005 : il n’est plus valide d’avoir une **`using`** déclaration à un type imbriqué ; vous devez qualifier explicitement chaque référence que vous apportez au type imbriqué, placer le type dans un espace de noms ou créer un typedef.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2885.

```cpp
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

Si vous utilisez le **`using`** mot clé avec un membre de classe, C++ vous oblige à définir ce membre à l’intérieur d’une autre classe (classe dérivée).

L’exemple suivant génère l’C2885.

```cpp
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```
