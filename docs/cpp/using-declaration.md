---
title: à l’aide de la déclaration | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- using declaration
- declaring namespaces, unqualified names in namespaces
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
- declarations [C++], namespaces
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c40a69e9c8d584d91a1b6401ec0da57368641975
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941523"
---
# <a name="using-declaration"></a>déclaration using
La déclaration using introduit un nom dans la région déclarative dans laquelle la déclaration using s’affiche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
using [typename] nested-name-specifier unqualified-id ;  
using declarator-list ;  
```  
  
### <a name="parameters"></a>Paramètres
  
*spécificateur de nom imbriqué*  
    Une séquence d’espace de noms, classe, ou noms d’énumération et opérateurs de résolution de portée ( :), terminée par un opérateur de résolution de portée. Un opérateur de résolution de portée unique peut être utilisé pour introduire un nom à partir de l’espace de noms global. Le mot clé **typename** est facultatif et peut être utilisé pour résoudre des noms dépendants lors de l’introduction dans un modèle de classe à partir d’une classe de base.  
  
*id non qualifié*  
    Non qualifiée id-expression, qui peut être un identificateur, un nom d’opérateur surchargé, un défini par l’utilisateur littéral opérateur ou conversion nom de fonction, un nom de destructeur de classe ou une liste de noms et d’arguments de modèle.  
  
*liste des déclarateurs*  
    Une liste séparée par des virgules de [**typename**] *spécificateur de nom imbriqué* *non qualifié id* déclarateurs, suivies éventuellement d’un bouton de sélection.
    
## <a name="remarks"></a>Notes  
Une déclaration using introduit un nom non qualifié en tant que synonyme pour une entité déclaré ailleurs. Il permet à un nom unique à partir d’un espace de noms spécifique pour être utilisé sans qualification explicite dans la région de déclaration dans laquelle elle apparaît. Il s’agit Contrairement à la [à l’aide de la directive](../cpp/namespaces-cpp.md#using_directives), ce qui permet de *tous les* les noms dans un espace de noms sans qualification. Le **à l’aide de** mot clé est également utilisé pour [alias de type](../cpp/aliases-and-typedefs-cpp.md).  
  
## <a name="example"></a>Exemple  
 Une déclaration using peut être utilisé dans une définition de classe.  
  
```cpp  
// using_declaration1.cpp  
#include <stdio.h>  
class B {  
public:  
   void f(char) {  
      printf_s("In B::f()\n");  
   }  
  
   void g(char) {  
      printf_s("In B::g()\n");  
   }  
};  
  
class D : B {  
public:  
   using B::f;    // B::f(char) is now visible as D::f(char)  
   using B::g;    // B::g(char) is now visible as D::g(char)  
   void f(int) {  
      printf_s("In D::f()\n");  
      f('c');     // Invokes B::f(char) instead of recursing  
   }  
  
   void g(int) {  
      printf_s("In D::g()\n");  
      g('c');     // Invokes B::g(char) instead of recursing  
   }  
};  
  
int main() {  
   D myD;  
   myD.f(1);  
   myD.g('a');  
}  
```  
  
```Output  
In D::f()  
In B::f()  
In B::g()  
```  
  
## <a name="example"></a>Exemple  
Lorsqu’il est utilisé pour déclarer un membre, un à l’aide de déclaration doit faire référence à un membre d’une classe de base.  
  
```cpp  
// using_declaration2.cpp  
#include <stdio.h>  
  
class B {  
public:  
   void f(char) {  
      printf_s("In B::f()\n");  
   }  
  
   void g(char) {  
      printf_s("In B::g()\n");  
   }  
};  
  
class C {  
public:  
   int g();  
};  
  
class D2 : public B {  
public:  
   using B::f;   // ok: B is a base of D2  
   // using C::g;   // error: C isn't a base of D2  
};  
  
int main() {  
   D2 MyD2;  
   MyD2.f('a');  
}  
```  
  
```Output  
In B::f()  
```  
  
## <a name="example"></a>Exemple  
Les membres déclarés à l’aide d’une déclaration peut être référencée à l’aide de qualification explicite. Le `::` préfixe fait référence à l’espace de noms global.  
  
```cpp  
// using_declaration3.cpp  
#include <stdio.h>  
  
void f() {  
   printf_s("In f\n");  
}  
  
namespace A {  
   void g() {  
      printf_s("In A::g\n");  
   }  
}  
  
namespace X {  
   using ::f;   // global f is also visible as X::f  
   using A::g;   // A's g is now visible as X::g 
}  
  
void h() {  
   printf_s("In h\n");  
   X::f();   // calls ::f  
   X::g();   // calls A::g  
}  
  
int main() {  
   h();  
}  
```  
  
```Output  
In h  
In f  
In A::g  
```  
  
## <a name="example"></a>Exemple  
Lors d’un à l’aide de la déclaration est effectuée, le synonyme créé par la déclaration fait uniquement référence aux définitions qui sont valides au moment à l’aide de la déclaration. Définitions ajoutées à un espace de noms après l’utilisation de déclaration ne sont pas synonymes valides.  
  
Un nom défini par un **à l’aide de** déclaration est un alias pour son nom d’origine. Il n’affecte pas le type, d’une liaison ou d’autres attributs de la déclaration d’origine.  
  
```cpp  
// post_declaration_namespace_additions.cpp  
// compile with: /c  
namespace A {  
   void f(int) {}  
}  
  
using A::f;   // f is a synonym for A::f(int) only  
  
namespace A {  
   void f(char) {}  
}  
  
void f() {  
   f('a');   // refers to A::f(int), even though A::f(char) exists  
}  
  
void b() {  
   using A::f;   // refers to A::f(int) AND A::f(char)  
   f('a');   // calls A::f(char);  
}  
```  
  
## <a name="example"></a>Exemple  
En ce qui concerne les fonctions dans les espaces de noms, si un ensemble de déclarations locales et à l’aide de déclarations pour bénéficient d’un nom unique dans une région déclarative, elles doivent toutes faire référence à la même entité, ou ils doivent tous faire référence aux fonctions.  
  
```cpp  
// functions_in_namespaces1.cpp  
// C2874 expected  
namespace B {  
    int i;  
    void f(int);  
    void f(double);  
}  
  
void g() {  
    int i;  
    using B::i;   // error: i declared twice  
    void f(char);  
    using B::f;   // ok: each f is a function  
}  
```  
  
 Dans l’exemple ci-dessus, le `using B::i` instruction provoque une seconde `int i` doivent être déclarées dans le `g()` (fonction). Le `using B::f` instruction n’est pas en conflit avec le `f(char)` fonctionner, car les noms des fonctions introduites par `B::f` ont différents types de paramètres.  
  
## <a name="example"></a>Exemple  
 Une déclaration de fonction locale ne peut pas avoir le même nom et le type en tant que fonction introduite à l’aide de déclaration. Exemple :  
  
```cpp  
// functions_in_namespaces2.cpp  
// C2668 expected  
namespace B {  
    void f(int);  
    void f(double);  
}  
  
namespace C {  
    void f(int);  
    void f(double);  
    void f(char);  
}  
  
void h() {  
    using B::f;          // introduces B::f(int) and B::f(double)  
    using C::f;          // C::f(int), C::f(double), and C::f(char)  
    f('h');              // calls C::f(char)  
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?  
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)  
}  
```  
  
## <a name="example"></a>Exemple  
 En ce qui concerne l’héritage, lors d’un à l’aide de déclaration introduit un nom à partir d’une classe de base dans une étendue de la classe dérivée, les fonctions membres dans les fonctions de membre virtuel de remplacement de classe dérivée avec les mêmes types de nom et l’argument dans la classe de base.  
  
```cpp  
// using_declaration_inheritance1.cpp  
#include <stdio.h>  
struct B {  
   virtual void f(int) {  
      printf_s("In B::f(int)\n");  
   }  
  
   virtual void f(char) {  
      printf_s("In B::f(char)\n");  
   }  
  
   void g(int) {  
      printf_s("In B::g\n");  
   }  
  
   void h(int);  
};  
  
struct D : B {  
   using B::f;  
   void f(int) {   // ok: D::f(int) overrides B::f(int)  
      printf_s("In D::f(int)\n");  
   }  
  
   using B::g;  
   void g(char) {   // ok: there is no B::g(char)  
      printf_s("In D::g(char)\n");  
   }  
  
   using B::h;  
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)  
};  
  
void f(D* pd) {  
   pd->f(1);     // calls D::f(int)  
   pd->f('a');   // calls B::f(char)  
   pd->g(1);     // calls B::g(int)  
   pd->g('a');   // calls D::g(char)  
}  
  
int main() {  
   D * myd = new D();  
   f(myd);  
}  
```  
  
```Output  
In D::f(int)  
In B::f(char)  
In B::g  
In D::g(char)  
```  
  
## <a name="example"></a>Exemple  
Toutes les instances d’un nom mentionné dans un à l’aide de la déclaration doit être accessible. En particulier, si une classe dérivée utilise une à l’aide de déclaration d’accéder à un membre de classe de base, le nom du membre doit être accessible. Si le nom est celui d’une fonction membre surchargé, puis toutes les fonctions nommées doivent être accessibles.  
  
Pour plus d’informations sur l’accessibilité des membres, consultez [contrôle d’accès de membre](../cpp/member-access-control-cpp.md).  
  
```cpp  
// using_declaration_inheritance2.cpp  
// C2876 expected  
class A {  
private:  
   void f(char);  
public:  
   void f(int);  
protected:  
   void g();  
};  
  
class B : public A {  
   using A::f;   // C2876: A::f(char) is inaccessible  
public:  
   using A::g;   // B::g is a public synonym for A::g  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Espaces de noms](../cpp/namespaces-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)