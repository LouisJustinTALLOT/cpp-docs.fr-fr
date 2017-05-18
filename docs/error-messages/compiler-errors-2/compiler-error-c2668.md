---
title: Erreur du compilateur C2668 | Documents Microsoft
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2668
dev_langs:
- C++
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: b790beb88de009e1c7161f3c9af6b3e21c22fd8e
ms.openlocfilehash: 6bb1dc7c1dbf26a4ff8ec25a46fe7128e0fb6aa8
ms.contentlocale: fr-fr
ms.lasthandoff: 03/29/2017

---
# <a name="compiler-error-c2668"></a>Erreur du compilateur C2668
'fonction' : appel ambigu à une fonction surchargée  
  
 L’appel de fonction surchargée spécifié n’a pas pu être résolu. Voulez-vous convertir explicitement un ou plusieurs des paramètres réels.  
  
 Vous pouvez également obtenir cette erreur via l’utilisation du modèle. Si, dans la même classe, vous disposez d’une fonction membre régulière et une fonction membre basé sur un modèle avec la même signature, celle basée sur un modèle doit figurer en premier. Il s’agit d’une limitation de l’implémentation actuelle de Visual C++.  
  
 Consultez l’article Q240869 de la Base de connaissances Microsoft pour plus d’informations sur le classement partiel des modèles de fonction.  
  
 Si vous générez un projet ATL contenant un objet COM prenant en charge `ISupportErrorInfo`, consultez l’article Q243298 de la Base de connaissances.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2668 :  
  
```  
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
 Une autre façon de résoudre cette erreur est un [à l’aide de la déclaration](../../cpp/using-declaration.md):  
  
```  
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
  
 Conversion sur un cast à l’aide de la constante 0 est ambiguë puisqu’elle nécessite une conversion en type long et au void *. Pour résoudre cette erreur, un cast de 0 au type du paramètre de fonction qu'il est utilisé afin qu’aucune conversion soit effectuée (ce code sera valide dans les versions de Visual Studio .NET 2003 et Visual Studio .NET de Visual C++).  
  
```  
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
 Cette erreur peut se produire parce que la bibliothèque CRT a maintenant des formes flottante et doubles de toutes les fonctions mathématiques.  
  
```  
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
 Cette erreur peut se produire parce que pow (int, int) a été supprimé de math.h dans la bibliothèque CRT.  
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```

## <a name="example"></a>Exemple  
Ce code réussit dans Visual Studio 2015, mais échoue dans Visual Studio 2017 et versions ultérieures avec C2668. Dans Visual Studio 2015, le compilateur traitait à tort copy-list-initialization de la même façon que l’instruction copy-initialization ordinaire ; il envisageait uniquement de convertir les constructeurs pour résoudre la surcharge. 

```
C++
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
