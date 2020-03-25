---
title: Erreur du compilateur C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: f59cb33bed15847ed1a7a2dbe99ea030babf3337
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177155"
---
# <a name="compiler-error-c2668"></a>Erreur du compilateur C2668

'fonction' : appel ambigu à une fonction surchargée

L’appel de fonction surchargé spécifié n’a pas pu être résolu. Vous pouvez effectuer un cast explicite d’un ou plusieurs des paramètres réels.

Vous pouvez également recevoir cette erreur par le biais de l’utilisation d’un modèle. Si, dans la même classe, vous avez une fonction membre standard et une fonction membre basée sur un modèle avec la même signature, le modèle doit être en premier. Il s’agit d’une limitation de l’implémentation actuelle C++de Visual.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2668 :

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

Une autre façon de résoudre cette erreur consiste à [utiliser une déclaration using](../../cpp/using-declaration.md):

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

Cette erreur peut également être générée en raison du travail de conformité du compilateur pour Visual Studio .NET 2003 : conversion ambiguë sur un cast de constante 0.

La conversion sur un cast à l’aide de la constante 0 est ambiguë puisque int requiert une conversion de long et de void *. Pour résoudre cette erreur, effectuez un cast de 0 vers le type exact du paramètre de fonction pour lequel il est utilisé afin qu’aucune conversion ne doive avoir lieu (ce code sera valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++).

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

Cette erreur peut se produire parce que la bibliothèque CRT a désormais des formes float et double de toutes les fonctions mathématiques.

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

Cette erreur peut se produire car Pow (int, int) a été supprimé de Math. h dans le CRT.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Exemple

Ce code réussit dans Visual Studio 2015 mais échoue dans Visual Studio 2017 et versions ultérieures avec C2668. Dans Visual Studio 2015, le compilateur traitait à tort copy-list-initialization de la même façon que l’instruction copy-initialization ordinaire ; il envisageait uniquement de convertir les constructeurs pour résoudre la surcharge.

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
