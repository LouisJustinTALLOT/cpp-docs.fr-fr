---
title: Résolution de nom pour les noms déclarés localement
ms.date: 11/04/2016
ms.assetid: 743b88f3-de11-48f4-ae83-931449ea3886
ms.openlocfilehash: 91ed065a6c8aca6c7f740f0236cb13c8133fc96f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345917"
---
# <a name="name-resolution-for-locally-declared-names"></a>Résolution de nom pour les noms déclarés localement

Le nom du modèle lui-même peut être qualifié avec ou sans les arguments template. Dans la portée d'un modèle de classe, le nom lui-même fait référence au modèle. Dans la portée d'une spécialisation de modèle ou d'une spécialisation partielle, le nom seul fait référence à la spécialisation ou la spécialisation partielle. D'autres spécialisations ou spécialisations partielles du modèle peuvent également être référencées, avec les arguments template appropriés.

## <a name="example"></a>Exemple

Le code suivant indique que le A du nom du modèle de classe est interprété différemment dans la portée d'une spécialisation ou de spécialisation partielle.

```cpp
// template_name_resolution3.cpp
// compile with: /c
template <class T> class A {
   A* a1;   // A refers to A<T>
   A<int>* a2;  // A<int> refers to a specialization of A.
   A<T*>* a3;   // A<T*> refers to the partial specialization A<T*>.
};

template <class T> class A<T*> {
   A* a4; // A refers to A<T*>.
};

template<> class A<int> {
   A* a5; // A refers to A<int>.
};
```

## <a name="example"></a>Exemple

Dans le cas d'un conflit au niveau du nom entre un paramètre de modèle et un autre objet, le paramètre de modèle peut ou ne peut pas être masqué. Les règles suivantes vous aideront à déterminer la priorité.

Le paramètre de modèle est dans la portée à partir du point où il apparaît la première fois, jusqu'à la fin de la classe ou du modèle de fonction. Si le nom s'affiche à nouveau dans la liste d'arguments template ou dans la liste de classes de base, il fait référence au même type. En C++ standard, aucun autre nom identique au paramètre de modèle ne peut être déclaré dans la même portée. Une extension Microsoft permet de redéfinir le paramètre de modèle dans la portée du modèle. L'exemple suivant montre l'utilisation du paramètre de modèle dans la spécification de base d'un modèle de classe.

```cpp
// template_name_resolution4.cpp
// compile with: /EHsc
template <class T>
class Base1 {};

template <class T>
class Derived1 : Base1<T> {};

int main() {
   // Derived1<int> d;
}
```

## <a name="example"></a>Exemple

Lorsque vous définissez les fonctions membres d'un modèle en-dehors du modèle de classe, un nom de paramètre de modèle différent peut être utilisé. Si la définition de la fonction membre de modèle utilise un nom différent de celui utilisé par la déclaration pour le paramètre de modèle et si le nom utilisé dans la définition est en conflit avec un autre membre de la déclaration, le membre de la déclaration de modèle est prioritaire.

```cpp
// template_name_resolution5.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T> class C {
public:
   struct Z {
      Z() { cout << "Z::Z()" << endl; }
   };
   void f();
};

template <class Z>
void C<Z>::f() {
   // Z refers to the struct Z, not to the template arg;
   // Therefore, the constructor for struct Z will be called.
   Z z;
}

int main() {
   C<int> c;
   c.f();
}
```

```Output
Z::Z()
```

## <a name="example"></a>Exemple

Lors de la définition d’une fonction modèle ou d’une fonction membre en dehors de l’espace de noms dans lequel le modèle a été déclaré, l’argument template a priorité sur les noms des autres membres de l’espace de noms.

```cpp
// template_name_resolution6.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

namespace NS {
   void g() { cout << "NS::g" << endl; }

   template <class T> struct C {
      void f();
      void g() { cout << "C<T>::g" << endl; }
   };
};

template <class T>
void NS::C<T>::f() {
   g(); // C<T>::g, not NS::g
};

int main() {
   NS::C<int> c;
   c.f();
}
```

```Output
C<T>::g
```

## <a name="example"></a>Exemple

Dans les définitions qui sont en dehors de la déclaration de la classe de modèle, si une classe de modèle a une classe de base qui ne dépend pas d’un argument template et si la classe de base ou un de ses membres porte le même nom qu’un argument template, la classe de base ou le nom de membre masque l’argument template.

```cpp
// template_name_resolution7.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct B {
   int i;
   void print() { cout << "Base" << endl; }
};

template <class T, int i> struct C : public B {
   void f();
};

template <class B, int i>
void C<B, i>::f() {
   B b;   // Base class b, not template argument.
   b.print();
   i = 1; // Set base class's i to 1.
}

int main() {
   C<int, 1> c;
   c.f();
   cout << c.i << endl;
}
```

```Output
Base
1
```

## <a name="see-also"></a>Voir aussi

[Résolution de noms](../cpp/templates-and-name-resolution.md)