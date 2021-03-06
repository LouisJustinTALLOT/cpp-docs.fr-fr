---
description: 'En savoir plus sur : classe front_insert_iterator'
title: front_insert_iterator, classe
ms.date: 11/04/2016
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
ms.openlocfilehash: 79690f51ce108357a6131c6ab811cee23c6c4529
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324276"
---
# <a name="front_insert_iterator-class"></a>front_insert_iterator, classe

Décrit un adaptateur d’itérateur qui répond aux exigences d’un itérateur de sortie. Elle insère, plutôt que remplace, des éléments du début d'une séquence et fournit ainsi une sémantique différente de la sémantique de remplacement fournie par les itérateurs des conteneurs de la séquence C++. La classe `front_insert_iterator` est mise en modèle d'après le type de conteneur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>Paramètres

*Conteneur*\
Type de conteneur au début duquel des éléments doivent être insérés par un `front_insert_iterator`.

## <a name="remarks"></a>Notes

Le conteneur doit répondre aux exigences d’une insertion de début de séquence où il est possible d’insérer des éléments au début de la séquence dans le temps fixe amorti. Les conteneurs de séquence de bibliothèque C++ Standard définis par la [classe deque](../standard-library/deque-class.md) et la [classe list](../standard-library/list-class.md) fournissent la fonction membre `push_front` nécessaire et répondent à ces exigences. En revanche, les conteneurs de séquence définis par la [classe vector](../standard-library/vector-class.md) ne répondent pas à ces exigences et ne peuvent pas être adaptés pour être utilisés avec des `front_insert_iterator`. Un `front_insert_iterator` doit toujours être initialisé avec son conteneur.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|Crée un itérateur qui peut insérer des éléments au début d'un objet conteneur spécifié.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[container_type](#container_type)|Type qui représente le conteneur dans lequel une insertion de début doit être effectuée.|
|[reference](#reference)|Type qui fournit une référence à un élément dans une séquence contrôlée par le conteneur associé.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[and](#op_star)|Opérateur de suppression de référence utilisé pour implémenter l’expression \* `i`  =  `x` d’itérateur de sortie pour une insertion de début.|
|[opérateur + +](#op_add_add)|Incrémente le `front_insert_iterator` à l'emplacement suivant où une valeur peut être stockée.|
|[opérateur =](#op_eq)|Opérateur d’assignation utilisé pour implémenter l’expression \* `i`  =  `x` d’itérateur de sortie pour une insertion devant.|

## <a name="requirements"></a>Spécifications

**En-tête**: \<iterator>

**Espace de noms :** std

## <a name="front_insert_iteratorcontainer_type"></a><a name="container_type"></a> front_insert_iterator :: container_type

Type qui représente le conteneur dans lequel une insertion de début doit être effectuée.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *Container*.

### <a name="example"></a>Exemple

```cpp
// front_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> >::container_type L2 = L1;
   front_inserter ( L2 ) = 20;
   front_inserter ( L2 ) = 10;
   front_inserter ( L2 ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 10 20 ).
*/
```

## <a name="front_insert_iteratorfront_insert_iterator"></a><a name="front_insert_iterator"></a> front_insert_iterator :: front_insert_iterator

Crée un itérateur qui peut insérer des éléments au début d'un objet conteneur spécifié.

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Paramètres

*_Cont*\
Objet de conteneur dans lequel `front_insert_iterator` doit insérer des éléments.

### <a name="return-value"></a>Valeur renvoyée

`front_insert_iterator` pour l’objet conteneur du paramètre.

### <a name="example"></a>Exemple

```cpp
// front_insert_iterator_front_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   front_inserter ( L ) = 20;

   // Alternatively, one may use the template function
   front_insert_iterator< list < int> > Iter(L);
*Iter = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_star"></a> front_insert_iterator ::, opérateur\*

Supprime la référence à l’itérateur d’insertion retournant l’élément ciblé.

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Valeur renvoyée

La fonction membre retourne la valeur de l’élément ciblé.

### <a name="remarks"></a>Notes

Utilisé pour implémenter la valeur d' **\* ITER** de l’expression d’itérateur de sortie  =  . Si `Iter` est un itérateur qui traite un élément dans une séquence, la **\***  =  **valeur** d’ITER remplace cet élément par la valeur et ne modifie pas le nombre total d’éléments dans la séquence.

### <a name="example"></a>Exemple

```cpp
// front_insert_iterator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   front_insert_iterator< list < int> > Iter(L);
*Iter = 20;

   // Alternatively, you may use
   front_inserter ( L ) = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_add_add"></a> front_insert_iterator :: Operator + +

Incrémente le `back_insert_iterator` à l'emplacement suivant où une valeur peut être stockée.

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Valeur renvoyée

`front_insert_iterator` qui cible l’emplacement suivant où une valeur peut être stockée.

### <a name="remarks"></a>Notes

Les opérateurs de préincrémentation et de postincrémentation retournent le même résultat.

### <a name="example"></a>Exemple

```cpp
// front_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_eq"></a> front_insert_iterator :: Operator =

Ajoute (push) une valeur au début du conteneur.

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Valeur à assigner au conteneur.

### <a name="return-value"></a>Valeur renvoyée

Référence au dernier élément inséré au début du conteneur.

### <a name="remarks"></a>Notes

Le premier opérateur membre évalue `container.push_front( val)` , puis retourne **`*this`** .

Le deuxième opérateur membre évalue

`container->push_front((typename Container::value_type&&) val)`,

retourne ensuite **`*this`** .

### <a name="example"></a>Exemple

```cpp
// front_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratorreference"></a><a name="reference"></a> front_insert_iterator :: référence

Type qui fournit une référence à un élément dans une séquence contrôlée par le conteneur associé.

```cpp
typedef typename Container::reference reference;
```

### <a name="example"></a>Exemple

```cpp
// front_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   front_insert_iterator<list<int> > fiivIter( L );
*fiivIter = 10;
*fiivIter = 20;
*fiivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)
      cout << *LIter << " ";
   cout << ")." << endl;

   front_insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*/
```

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
