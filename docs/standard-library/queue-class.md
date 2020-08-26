---
title: queue, classe
ms.date: 11/04/2016
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
ms.openlocfilehash: e0bfa4ab037b52b237bd674d5f705de4e9699383
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832605"
---
# <a name="queue-class"></a>queue, classe

Classe d’adaptateur de conteneur de modèle qui fournit une restriction de fonctionnalité pour un certain type de conteneur sous-jacent, limitant l’accès aux éléments à l’arrière ou à l’avant. Les éléments peuvent être ajoutés à l’arrière ou supprimés à l’avant, et être inspectés aux extrémités de l’objet queue.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Paramètres

*Entrer*\
Type de données des éléments à stocker dans la classe queue

*Conteneur*\
Type du conteneur sous-jacent utilisé pour implémenter la classe queue.

## <a name="remarks"></a>Notes

Les éléments de la classe `Type` stipulés dans le premier paramètre de modèle d’un objet de file d’attente sont synonymes de [Value_type](#value_type) et doivent correspondre au type d’élément dans la classe de conteneur sous-jacente `Container` stipulée par le deuxième paramètre de modèle. `Type`Doit être assignable, afin qu’il soit possible de copier des objets de ce type et d’assigner des valeurs aux variables de ce type.

Les classes de conteneur sous-jacentes appropriées pour la file d’attente incluent [deque](../standard-library/deque-class.md) et [List](../standard-library/list-class.md), ou tout autre conteneur de séquences qui prend en charge les opérations de,, `front` `back` `push_back` et `pop_front` . La classe de conteneur sous-jacent est encapsulée dans l'adaptateur de conteneur, qui expose seulement l'ensemble limité de fonctions membres du conteneur de séquence comme une interface publique.

Les objets de file d’attente sont comparables si et seulement si les éléments de la classe `Type` sont comparables à l’égalité, et sont moins comparables si et seulement si les éléments de la classe `Type` sont moins comparables.

Il y a trois types d’adaptateurs de conteneur définis dans la bibliothèque standard C++ : stack, queue et priority_queue. Chaque type limite les fonctionnalités d’une classe de conteneur sous-jacent pour fournir une interface contrôlée de façon précise à une structure de données standard.

- La [classe Stack](../standard-library/stack-class.md) prend en charge une structure de données LIFO (dernier entré, premier sorti). Une bonne analogie à avoir à l'esprit est celle d'une pile d'assiettes. Les éléments (les assiettes) peuvent être insérés, inspectés ou supprimés seulement à partir du haut de la pile, qui est le dernier élément à la fin du conteneur de base. La restriction qui fait que seul l'élément du haut est accessible est la raison de l'utilisation de la classe stack.

- La classe queue prend en charge une structure de données FIFO (premier entré, premier sorti). Une bonne analogie à avoir à l'esprit est celle de personnes faisant la file pour un employé de banque. Les éléments (les personnes) peuvent être ajoutés à l'arrière de la file et ils sont supprimés de l'avant de la file. Le début et la fin d'une file peuvent être inspectés. L’utilisation de la classe queue s’explique par cette limitation qui fait que seuls les éléments à l’avant et à l’arrière sont accessibles de cette façon.

- La [classe priority_queue](../standard-library/priority-queue-class.md) trie ses éléments pour que l’élément le plus grand soit toujours en haut. Elle prend en charge l'insertion d'un élément, et l'inspection et la suppression de l'élément du haut. Une bonne analogie à avoir à l'esprit est celle de personnes faisant la file, classées selon leur âge, leur taille ou un autre critère.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[mis](#queue)|Construit un objet `queue` qui est vide ou qui est une copie de l'objet conteneur de base.|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|[container_type](#container_type)|Type qui fournit le conteneur de base à adapter par l’objet `queue`.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `queue`.|
|[value_type](#value_type)|Type qui représente le type d'objet stocké en tant qu'élément dans un objet `queue`.|

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[Précédent](#back)|Retourne une référence au dernier élément (ajouté le plus récemment) à l’arrière de l’objet `queue`.|
|[empty](#empty)|Vérifie si l'objet `queue` est vide.|
|[frontal](#front)|Retourne une référence au premier élément à l’avant de l’objet `queue`.|
|[roulant](#pop)|Supprime un élément à l’avant de l’objet `queue`.|
|[push](#push)|Ajoute un élément à l’arrière de l’objet `queue`.|
|[size](#size)|Retourne le nombre d'éléments d'un `queue`.|

## <a name="back"></a><a name="back"></a> Précédent

Retourne une référence au dernier élément (ajouté le plus récemment) à l’arrière de l’objet queue.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Valeur renvoyée

Dernier élément de l’objet queue. Si l’objet queue est vide, la valeur de retour n’est pas définie.

### <a name="remarks"></a>Notes

Si la valeur de retour de `back` est assignée à une `const_reference`, l’objet queue ne peut pas être modifié. Si la valeur de retour de `back` est assignée à `reference` , l’objet de file d’attente peut être modifié.

En cas de compilation avec [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous essayez d’accéder à un élément dans un objet queue vide.  Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md) .

### <a name="example"></a>Exemple

```cpp
// queue_back.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 11 );

   int& i = q1.back( );
   const int& ii = q1.front( );

   cout << "The integer at the back of queue q1 is " << i
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << ii
        << "." << endl;
}
```

## <a name="container_type"></a><a name="container_type"></a> container_type

Type qui fournit le conteneur de base à adapter.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Container`. Deux classes de conteneur de séquence de la bibliothèque standard C++, la classe list et la classe deque par défaut, remplissent les conditions pour être utilisées comme conteneur de base d’un objet queue. Les types définis par l’utilisateur peuvent également être utilisés s’ils remplissent les conditions.

Pour plus d’informations sur `Container`, consultez la section Notes de la rubrique [queue, classe](../standard-library/queue-class.md).

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `container_type`, consultez l’exemple [queue](#queue).

## <a name="empty"></a><a name="empty"></a> vidé

Teste si un objet queue est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la file d’attente est vide ; **`false`** si la file d’attente n’est pas vide.

### <a name="example"></a>Exemple

```cpp
// queue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The queue q1 is empty." << endl;
   else
      cout << "The queue q1 is not empty." << endl;

   if ( q2.empty( ) )
      cout << "The queue q2 is empty." << endl;
   else
      cout << "The queue q2 is not empty." << endl;
}
```

```Output
The queue q1 is not empty.
The queue q2 is empty.
```

## <a name="front"></a><a name="front"></a> frontal

Retourne une référence au premier élément à l’avant de l’objet queue.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Valeur renvoyée

Premier élément de l’objet queue. Si l’objet queue est vide, la valeur de retour n’est pas définie.

### <a name="remarks"></a>Notes

Si la valeur de retour de `front` est assignée à une `const_reference`, l’objet queue ne peut pas être modifié. Si la valeur de retour de `front` est assignée à `reference` , l’objet de file d’attente peut être modifié.

La fonction membre retourne un `reference` au premier élément de la séquence contrôlée, qui ne doit pas être vide.

En cas de compilation avec [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous essayez d’accéder à un élément dans un objet queue vide.  Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md) .

### <a name="example"></a>Exemple

```cpp
// queue_front.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main() {
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   int& ii = q1.back( );
   int& iii = q1.front( );

   cout << "The integer at the back of queue q1 is " << ii
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << iii
        << "." << endl;
}
```

## <a name="pop"></a><a name="pop"></a> roulant

Supprime un élément à l’avant de l’objet queue.

```cpp
void pop();
```

### <a name="remarks"></a>Notes

L’objet queue ne doit pas être vide pour appliquer la fonction membre. Le haut de l’objet queue correspond à la position occupée par l’élément ajouté le plus récemment et au dernier élément à la fin du conteneur.

### <a name="example"></a>Exemple

```cpp
// queue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;

   q1.pop( );

   i = q1.size( );
   cout << "After a pop the queue length is "
        << i << "." << endl;

   i = q1. front ( );
   cout << "After a pop, the element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
After a pop the queue length is 2.
After a pop, the element at the front of the queue is 20.
```

## <a name="push"></a><a name="push"></a> souleve

Ajoute un élément à l’arrière de l’objet queue.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Élément ajouté à l’arrière de l’objet queue.

### <a name="remarks"></a>Notes

L’arrière de l’objet queue correspond à la position occupée par l’élément ajouté le plus récemment et au dernier élément à la fin du conteneur.

### <a name="example"></a>Exemple

```cpp
// queue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
```

## <a name="queue"></a>File d'attente <a name="queue"></a>

Construit un objet queue qui est vide ou qui est une copie d’un objet conteneur de base.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
**`const`** Conteneur dont la file d’attente construite doit être une copie.

### <a name="remarks"></a>Notes

deque est le conteneur de base par défaut pour l’objet queue. Vous pouvez également spécifier list comme conteneur de base, mais vous ne pouvez pas spécifier vector, qui n’a pas la fonction membre `pop_front` exigée.

### <a name="example"></a>Exemple

```cpp
// queue_queue.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queue with default deque base container
   queue <char> q1;

   // Explicitly declares a queue with deque base container
   queue <char, deque<char> > q2;

   // These lines don't cause an error, even though they
   // declares a queue with a vector base container
   queue <int, vector<int> > q3;
   q3.push( 10 );
   // but the following would cause an error because vector has
   // no pop_front member function
   // q3.pop( );

   // Declares a queue with list base container
   queue <int, list<int> > q4;

   // The second member function copies elements from a container
   list<int> li1;
   li1.push_back( 1 );
   li1.push_back( 2 );
   queue <int, list<int> > q5( li1 );
   cout << "The element at the front of queue q5 is "
        << q5.front( ) << "." << endl;
   cout << "The element at the back of queue q5 is "
        << q5.back( ) << "." << endl;
}
```

```Output
The element at the front of queue q5 is 1.
The element at the back of queue q5 is 2.
```

## <a name="size"></a><a name="size"></a> corps

Retourne le nombre d’éléments figurant dans l’objet queue.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur actuelle de l’objet queue.

### <a name="example"></a>Exemple

```cpp
// queue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2;
   queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The queue length is now " << i << "." << endl;
}
```

```Output
The queue length is 1.
The queue length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Type entier non signé qui peut représenter le nombre d’éléments dans un objet queue.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du `size_type` pour le conteneur de base adapté par la classe queue.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `size_type`, consultez l’exemple [queue::front](#front).

## <a name="value_type"></a><a name="value_type"></a> value_type

Type qui représente le type d’objet stocké comme élément dans une classe queue.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du `value_type` pour le conteneur de base adapté par la classe queue.

### <a name="example"></a>Exemple

```cpp
// queue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   queue<int> q1;
   q1.push(AnInt);
   cout << "The element at the front of the queue is "
        << q1.front( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the front of the queue is 69.
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
