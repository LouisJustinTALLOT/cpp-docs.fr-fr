---
title: Erreur du compilateur C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: 1920af8873578c63ab768dae4bcdf4d91fe7cd57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164811"
---
# <a name="compiler-error-c2668"></a>Erreur du compilateur C2668

'fonction' : appel ambigu à une fonction surchargée

L’appel de fonction surchargée spécifié n’a pas pu être résolu. Voulez-vous convertir explicitement un ou plusieurs des paramètres réels.

Vous pouvez également obtenir cette erreur à l’aide du modèle. Si, dans la même classe, vous avez une fonction membre régulière et une fonction membre basé sur un modèle avec la même signature, celui qui est basé sur un modèle doit figurer en premier. Il s’agit d’une limitation de l’implémentation actuelle de Visual C++.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2668 :

```cpp
// C2668.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};

void func( X, X ){}
void func( A, B ){}
D d;
int main() {
   func( d, d );   // C2668 D has an A, B, and X
   func( (X)d, (X)d );   // OK, uses func( X, X )
}
```

## <a name="example"></a>Exemple

Une autre façon de résoudre cette erreur est avec un [à l’aide de la déclaration](../../cpp/using-declaration.md):

```cpp
// C2668b.cpp
// compile with: /EHsc /c
// C2668 expected
#include <iostream>
class TypeA {
public:
   TypeA(int value) {}
};

class TypeB {
   TypeB(int intValue);
   TypeB(double dbValue);
};

class TestCase {
public:
   void AssertEqual(long expected, long actual, std::string
                    conditionExpression = "");
};

class AppTestCase : public TestCase {
public:
   // Uncomment the following line to resolve.
   // using TestCase::AssertEqual;
   void AssertEqual(const TypeA expected, const TypeA actual,
                    std::string conditionExpression = "");
   void AssertEqual(const TypeB expected, const TypeB actual,
                    std::string conditionExpression = "");
};

class MyTestCase : public AppTestCase {
   void TestSomething() {
      int actual = 0;
      AssertEqual(0, actual, "Value");
   }
};
```

## <a name="example"></a>Exemple

Cette erreur peut également être due à la mise en conformité du compilateur pour Visual Studio .NET 2003 : conversion ambiguë sur un cast de la constante 0.

Conversion sur un cast à l’aide de la constante 0 est ambiguë puisqu’elle nécessite une conversion en type long et au void *. Pour résoudre cette erreur, effectuez un cast de 0 au type de paramètre de la fonction, qu'il est utilisé afin qu’aucune conversion se déroulent (ce code sera valide dans les versions de Visual Studio .NET 2003 et Visual Studio .NET de Visual C++).

```cpp
// C2668c.cpp
#include "stdio.h"
void f(long) {
   printf_s("in f(long)\n");
}
void f(void*) {
   printf_s("in f(void*)\n");
}
int main() {
   f((int)0);   // C2668

   // OK
   f((long)0);
   f((void*)0);
}
```

## <a name="example"></a>Exemple

Cette erreur peut se produire parce que la bibliothèque CRT a maintenant des formes flottante et double de toutes les fonctions mathématiques.

```cpp
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

## <a name="example"></a>Exemple

Cette erreur peut se produire, car le pow (int, int) a été supprimé de math.h dans le CRT.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Exemple

Ce code réussit dans Visual Studio 2015, mais échoue dans Visual Studio 2017 et versions ultérieures avec l’erreur C2668. Dans Visual Studio 2015, le compilateur traitait à tort copy-list-initialization de la même façon que l’instruction copy-initialization ordinaire ; il envisageait uniquement de convertir les constructeurs pour résoudre la surcharge.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```