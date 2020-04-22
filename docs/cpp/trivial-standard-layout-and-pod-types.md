---
title: Types triviaux, à disposition standard, POD et littéraux
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 6fe237386e63fcdd96621edabf2b0b66ce72e4f8
ms.sourcegitcommit: 435133128b18cdd02d33d929b16c33e7ec40e9eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81664132"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Types triviaux, à disposition standard, POD et littéraux

Le terme *disposition* fait référence à la façon dont les membres d’un objet de classe, d’un struct ou d’un type union sont organisés dans la mémoire. Dans certains cas, la disposition est bien définie par la spécification du langage. Toutefois, quand une classe ou un struct contiennent certaines fonctionnalités du langage C++, comme des classes de base virtuelles, des fonctions virtuelles, des membres avec un contrôle d’accès différent, le compilateur est libre de choisir une disposition. Cette disposition peut varier selon les optimisations qui sont apportées. Dans de nombreux cas, l’objet peut même ne pas occuper une zone contiguë de mémoire. Par exemple, si une classe a des fonctions virtuelles, toutes les instances de cette classe partagent probablement une seule table de fonctions virtuelles. Ces types sont très utiles, mais ils présentent également des limites. Étant donné que la disposition n’est pas définie, ils ne peuvent pas être passés aux programmes écrits dans d’autres langages, comme C, et parce qu’ils risquent de ne pas être contigus, ils ne peuvent pas non plus être copiés de façon fiable avec des fonctions rapides de bas niveau comme `memcopy`, ni sérialisés sur un réseau.

Pour activer les compilateurs, ainsi que les programmes et métaprogrammes C++, afin qu’un type donné reste adapté aux opérations qui dépendent d’une disposition de mémoire particulière, C++14 a introduit trois catégories de classes et de structs simples : *trivial*, *disposition standard* et *POD* ou Plain Old Data. La bibliothèque Standard contient les modèles de fonction `is_trivial<T>`, `is_standard_layout<T>` et `is_pod<T>` qui déterminent si un type donné appartient à une catégorie donnée.

## <a name="trivial-types"></a>Types triviaux

Quand une classe ou un struct dans C++ a des fonctions membres spéciales définies explicitement par défaut ou fournies par le compilateur, il s’agit d’un type trivial. Il occupe une zone de mémoire contiguë. Il peut avoir des membres avec des spécificateurs d’accès différents. Dans C++, le compilateur est libre de choisir comment classer les membres dans ce cas. Par conséquent, vous pouvez utiliser memcopy pour copier ces objets, mais vous ne pouvez pas les consommer de façon fiable dans un programme C. Un type trivial T peut être copié dans un tableau de caractères ou de caractères non signés, puis copié sans problème dans une variable T. Notez qu’en raison des conditions d’alignement, il peut y avoir des octets de remplissage entre les membres de type.

Les types triviaux ont un constructeur par défaut trivial, un constructeur de copie trivial, un opérateur d’attribution de copie trivial et un destructeur trivial. Dans chaque cas, *trivial* signifie que le constructeur/opérateur/destructeur n’est pas fourni par l’utilisateur et appartient à une classe qui n’a

- aucune fonction virtuelle, aucune classe de base virtuelle,

- aucune classe de base avec un constructeur/opérateur/destructeur non trivial correspondant

- aucun membre de données de type de classe avec un constructeur/opérateur/destructeur non trivial correspondant

Les exemples suivants montrent des types triviaux. Dans Trivial2, la présence du constructeur `Trivial2(int a, int b)` vous demande de fournir un constructeur par défaut. Pour que le type soit considéré comme trivial, vous devez définir explicitement ce constructeur comme constructeur par défaut.

```cpp
struct Trivial
{
   int i;
private:
   int j;
};

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>Types de disposition standard

Quand une classe ou un struct ne contiennent pas certaines fonctionnalités du langage C++ (comme des fonctions virtuelles) qui ne figurent pas dans le langage C, et que tous les membres ont le même contrôle d’accès, il s’agit d’un type à disposition standard. Il peut utiliser memcopy et la disposition est suffisamment définie pour être consommée par des programmes C. Les types de disposition standard peuvent avoir des fonctions membres spéciales définies par l’utilisateur. Par ailleurs, les types de disposition standard ont ces caractéristiques :

- aucune fonction virtuelle ni aucune classe de base virtuelle

- tous les membres de données non statiques ont le même contrôle d’accès

- tous les membres non statiques de type de classe sont à disposition standard

- toutes les classes de base sont à disposition standard

- aucune classe de base du même type que le premier membre de données non statique.

- remplit l’une des conditions suivantes :

  - aucun membre de données non statique dans la classe la plus dérivée et pas plus d’une classe de base avec des membres de données non statiques, ou

  - aucune classe de base avec des membres de données non statiques

Le code suivant montre un exemple d’un type à disposition standard :

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

Les deux dernières conditions peuvent éventuellement être mieux illustrées avec du code. Dans l’exemple suivant, même si Base est à disposition standard, `Derived` n’est pas à disposition standard, car les deux (la classe la plus dérivée) et `Base` ont des membres de données non statiques :

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

Dans cet exemple, `Derived` est à disposition standard, car `Base` n’a aucun membre de données non statique :

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

Derived serait également à disposition standard si `Base` avait des membres de données et si `Derived` avait uniquement des fonctions membres.

## <a name="pod-types"></a>Types POD

Quand une classe ou un struct sont à la fois triviaux et à disposition standard, il s’agit d’un type POD (Plain Old Data). La disposition en mémoire des types POD est par conséquent contiguë et chaque membre a une adresse supérieure à celle du membre qui a été déclaré avant lui, afin que les copies octet pour octet et les E/S binaires puissent être effectuées sur ces types.  Les types scalaires comme int sont également des types POD. Les types POD qui sont des classes peuvent avoir uniquement des types POD comme membres de données non statiques.

## <a name="example"></a>Exemple

L’exemple suivant montre les différences entre les types triviaux, à disposition standard et POD :

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
   int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
{
   int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal-types"></a><a name="literal_types"></a> Types littéraux

Un type de littéral est un type dont la disposition peut être déterminée au moment de la compilation. Voici les types de littéral disponibles :

- void
- Types scalaires
- references
- Tableaux de types void, de types scalaires ou de références
- Classe contenant un destructeur trivial, et un ou plusieurs constructeurs constexpr autres que des constructeurs de copie ou de déplacement. Tous les membres de données non statiques et classes de base doivent également être des types de littéral et être non volatiles.

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)
