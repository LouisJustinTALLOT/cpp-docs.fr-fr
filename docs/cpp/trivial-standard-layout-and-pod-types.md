---
title: Trivial, disposition standard et types de littéral POD | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.topic: language-reference
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 33b24c20c93f9bf0160536f5d6149c073c6ca7a5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464011"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Trivial, disposition standard et types de littéral POD

Le terme *disposition* fait référence à la façon dont les membres d’un objet de classe, un struct ou union type sont disposés en mémoire. Dans certains cas, la mise en page est défini par la spécification du langage. Mais lorsqu’une classe ou un struct contient certaines fonctionnalités du langage C++ telles que les classes de base virtuelles, les fonctions virtuelles, les membres avec le contrôle d’accès différents, le compilateur est libre de choisir une disposition. Cette disposition peut varier selon les optimisations sont effectuées et dans de nombreux cas objet peut occuper pas même une zone contiguë de mémoire. Par exemple, si une classe possède des fonctions virtuelles, toutes les instances de cette classe susceptibles de partager une table de fonction virtuelle unique. Ces types sont bien entendu très utiles, mais ils présentent également des limitations. Étant donné que la mise en page n’est pas défini qu’ils ne peuvent pas être passés aux programmes écrits dans d’autres langages, tels que C, et car ils peuvent être non contigus qu’ils ne peut pas être fiable copiés avec des fonctions rapides de bas niveau tels que `memcopy` ou sérialisé sur un réseau.

 Pour activer metaprograms de raisonner sur la pertinence de tout type donné pour les opérations qui dépendent d’une disposition de mémoire particulière ainsi que les programmes C++ et les compilateurs, C ++ 14 introduit trois catégories de simples classes et structs : *trivial*, *disposition standard*, et *POD* ou Plain Old Data. La bibliothèque Standard contient les modèles de fonction `is_trivial<T>`, `is_standard_layout<T>` et `is_pod<T>` qui déterminent si un type donné appartient à une catégorie donnée.

## <a name="trivial-types"></a>Types triviaux

 Quand une classe ou struct en C++ fournie par le compilateur soit explicitement défini par défaut les fonctions membres spéciales, il est un type trivial. Il occupe une zone de mémoire contigus. Il peut avoir des membres avec les spécificateurs d’accès différents. En C++, le compilateur est libre de choisir comment classer les membres dans cette situation. Par conséquent, vous pouvez memcopy ces objets, mais vous ne pouvez pas les utiliser fiable à partir d’un programme C. Un type trivial T peut être copié dans un tableau de char ou unsigned char et copié dans une variable T. Notez qu’en raison des exigences d’alignement, il peut y avoir des octets de remplissage entre les membres de type.

 Les types triviaux ont un constructeur par défaut trivial constructeur de copie trivial, opérateur d’assignation de copie triviaux et destructeur trivial. Dans chaque cas, *trivial* signifie que le constructeur/opérateur/destructeur n’est pas fourni par l’utilisateur et appartient à une classe a

- aucune des fonctions virtuelles ou les classes de base virtuelles,

- aucune classe de base avec un correspondant destructeur non trivial constructeur/opérateur /

- Aucun membre de données de type de classe possédant un correspondant destructeur non trivial constructeur/opérateur /

Les exemples suivants montrent les types triviaux. Dans Trivial2, la présence de la `Trivial2(int a, int b)` constructeur requiert que vous fournissez un constructeur par défaut. Pour le type être considérée comme triviale, vous devez explicitement ce un constructeur par défaut.

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

## <a name="standard-layout-types"></a>Types de mise en forme standard

 Lorsqu’une classe ou un struct ne contient-elle pas de certaines fonctionnalités du langage C++ telles que les fonctions virtuelles qui ne figurent pas dans le langage C, et tous les membres ont le même contrôle d’accès, c’est un type de disposition standard. Il est en mesure de memcopy et la mise en page est suffisamment défini qu’il peut être consommé par des programmes C. Les types de disposition standard peuvent avoir des fonctions membres spéciales définies par l’utilisateur. En outre, les types de disposition standard possèdent ces caractéristiques :

- aucune des fonctions virtuelles ou les classes de base virtuelles

- tous les membres de données non statiques ont le même contrôle d’accès

- tous les membres non statiques de type de classe sont disposition standard

- classes de base sont disposition standard

- ne dispose d’aucune classe de base du même type que le premier membre de données non statiques.

- remplit une des conditions suivantes :

  - Aucun membre de données non statiques dans la classe la plus dérivée et pas plus d’une classe de base avec les membres de données non statiques, ou

  - ne dispose d’aucune classe de base avec des données membres non static

Le code suivant illustre un exemple d’un type de disposition standard :

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

 Les deux dernières exigences peuvent éventuellement être mieux illustrés par code. Dans l’exemple suivant, même si Base est disposition standard, `Derived` n’est pas mise en forme standard, car les deux (la classe la plus dérivée) de l’informatique et `Base` ont des membres de données non statiques :

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

 Dans cet exemple `Derived` est disposition standard, car `Base` ne possède aucun membre de données non statiques :

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

 Dérivée serait également disposition standard si `Base` avait les membres de données et `Derived` avait uniquement des fonctions membres.

## <a name="pod-types"></a>Types POD

 Lorsqu’une classe ou un struct est trivial et disposition standard, il est un type POD (Plain Old Data). La disposition de mémoire des types POD est par conséquent contiguë et chaque membre possède une adresse supérieure que le membre qui a été déclaré avant lui, afin que la copie de l’octet par octet et les e/s binaires peuvent être effectuées sur ces types.  Types scalaires tels qu’int sont également des types POD. Les types POD qui sont des classes peuvent avoir uniquement des types POD en tant que membres de données non statiques.

## <a name="example"></a>Exemple

L’exemple suivant montre les différences entre triviale, disposition standard et les types POD :

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

## <a name="literal_types"></a> Types de littéral

Un type de littéral est un type dont la disposition peut être déterminée au moment de la compilation. Voici les types de littéral disponibles :

- void
- Types scalaires
- Références
- Tableaux de types void, de types scalaires ou de références
- Classe contenant un destructeur trivial, et un ou plusieurs constructeurs constexpr autres que des constructeurs de copie ou de déplacement. Tous les membres de données non statiques et classes de base doivent également être des types de littéral et être non volatiles.

## <a name="see-also"></a>Voir aussi
 [Concepts de base](../cpp/basic-concepts-cpp.md)