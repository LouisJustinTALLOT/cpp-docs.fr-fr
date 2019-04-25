---
title: Erreur du compilateur C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 8174faed09bdffbdc6974390cceb7c17661eab4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388772"
---
# <a name="compiler-error-c2885"></a>Erreur du compilateur C2885

'classe::identificateur' : pas une valide à l’aide de-déclaration de portée sans classe

Vous avez utilisé un [à l’aide de](../../cpp/using-declaration.md) déclaration de manière incorrecte.

## <a name="example"></a>Exemple

Cette erreur peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : il n’est plus valide pour avoir un `using` déclaration pour un type imbriqué ; vous devez explicitement qualifier chaque référence au type imbriqué, placer le type dans un nom l’espace, ou créer un typedef.

L’exemple suivant génère C2885.

```
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

Si vous utilisez le `using` mot clé avec un membre de classe C++, vous devez définir ce membre à l’intérieur d’une autre classe (une classe dérivée).

L’exemple suivant génère C2885.

```
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