---
title: Erreur du compilateur C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 9b6b7bb54d5dce48dc6fce517eb0c909b0284da2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233442"
---
# <a name="compiler-error-c2885"></a>Erreur du compilateur C2885

'Class :: identifier' : déclaration using non valide au niveau d’une portée sans classe

Vous avez utilisé une déclaration [using](../../cpp/using-declaration.md) de manière incorrecte.

## <a name="example"></a>Exemple

Cette erreur peut être générée en raison du travail de mise en conformité du compilateur pour Visual Studio 2005 : il n’est plus valide d’avoir une **`using`** déclaration à un type imbriqué ; vous devez qualifier explicitement chaque référence que vous apportez au type imbriqué, placer le type dans un espace de noms ou créer un typedef.

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

## <a name="example"></a>Exemple

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
