---
title: déclaration using
ms.date: 11/04/2016
helpviewer_keywords:
- using declaration
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
ms.openlocfilehash: d762ea36e83d2384b7bb50c2914f6a634c134d15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187841"
---
# <a name="using-declaration"></a>déclaration using

La Déclaration **using** introduit un nom dans la région déclarative dans laquelle la déclaration using s’affiche.

## <a name="syntax"></a>Syntaxe

```
using [typename] nested-name-specifier unqualified-id ;
using declarator-list ;
```

### <a name="parameters"></a>Paramètres

*Nested-Name-specifier* Séquence de noms d’espaces de noms, de classes ou d’énumération et d’opérateurs de résolution de portée ( ::), terminée par un opérateur de résolution de portée. Un opérateur de résolution de portée unique peut être utilisé pour introduire un nom à partir de l’espace de noms global. Le mot clé **TypeName** est facultatif et peut être utilisé pour résoudre des noms dépendants lorsqu’il est introduit dans un modèle de classe à partir d’une classe de base.

*ID non qualifié* Une expression d’ID non qualifiée, qui peut être un identificateur, un nom d’opérateur surchargé, un opérateur de littéral défini par l’utilisateur ou un nom de fonction de conversion, un nom de destructeur de classe ou un nom de modèle et une liste d’arguments.

*déclarateur-liste* Liste séparée par des virgules des déclarateurs *Unqualified-ID Unqualified* - *Name-specifier* [**TypeName**], suivi éventuellement d’un point de suspension.

## <a name="remarks"></a>Notes

Une déclaration using introduit un nom non qualifié comme synonyme d’une entité déclarée ailleurs. Il permet d’utiliser un seul nom d’un espace de noms spécifique sans qualification explicite dans la région de la déclaration dans laquelle il apparaît. Cela diffère de la [directive using](../cpp/namespaces-cpp.md#using_directives), qui permet d’utiliser *tous* les noms d’un espace de noms sans qualification. Le mot clé **using** est également utilisé pour les [alias de type](../cpp/aliases-and-typedefs-cpp.md).

## <a name="example"></a>Exemple

Une déclaration using peut être utilisée dans une définition de classe.

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

Lorsqu’elle est utilisée pour déclarer un membre, une déclaration using doit faire référence à un membre d’une classe de base.

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

Les membres déclarés à l’aide d’une déclaration using peuvent être référencés à l’aide d’une qualification explicite. Le préfixe `::` fait référence à l’espace de noms global.

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

Quand une déclaration using est effectuée, le synonyme créé par la déclaration fait référence uniquement aux définitions qui sont valides au point de la déclaration using. Les définitions ajoutées à un espace de noms après la déclaration using ne sont pas des synonymes valides.

Un nom défini par une déclaration **using** est un alias pour son nom d’origine. Elle n’affecte pas le type, la liaison ou d’autres attributs de la déclaration d’origine.

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

En ce qui concerne les fonctions dans les espaces de noms, si un ensemble de déclarations locales et l’utilisation de déclarations pour un même nom sont fournies dans une région déclarative, elles doivent toutes faire référence à la même entité, ou elles doivent toutes faire référence à des fonctions.

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

Dans l’exemple ci-dessus, l’instruction `using B::i` entraîne la déclaration d’une deuxième `int i` dans la fonction `g()`. L’instruction `using B::f` n’est pas en conflit avec la fonction `f(char)`, car les noms de fonctions introduits par `B::f` ont des types de paramètres différents.

## <a name="example"></a>Exemple

Une déclaration de fonction locale ne peut pas avoir le même nom et le même type qu’une fonction introduite à l’aide d’une déclaration. Par exemple :

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

En ce qui concerne l’héritage, quand une déclaration using introduit un nom d’une classe de base dans une portée de classe dérivée, les fonctions membres dans la classe dérivée remplacent les fonctions membres virtuelles avec les mêmes types de noms et d’arguments dans la classe de base.

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

Toutes les instances d’un nom mentionné dans une déclaration using doivent être accessibles. En particulier, si une classe dérivée utilise une déclaration using pour accéder à un membre d’une classe de base, le nom du membre doit être accessible. Si le nom est celui d’une fonction membre surchargée, toutes les fonctions nommées doivent être accessibles.

Pour plus d’informations sur l’accessibilité des membres, consultez [member-Access Control](../cpp/member-access-control-cpp.md).

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

[Espaces de noms](../cpp/namespaces-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
