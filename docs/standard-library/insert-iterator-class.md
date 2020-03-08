---
title: insert_iterator, classe
ms.date: 11/04/2016
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
ms.openlocfilehash: 15041e21b53c29aedda831fd73b37a65e57a3680
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874040"
---
# <a name="insert_iterator-class"></a>insert_iterator, classe

Décrit un adaptateur d’itérateur qui répond aux exigences d’un itérateur de sortie. Elle insère, plutôt que remplace, des éléments dans une séquence et fournit ainsi une sémantique différente de la sémantique de remplacement fournie par les itérateurs de la séquence C++ et les conteneurs associatifs. La classe `insert_iterator` est mise en modèle sur le type de conteneur qui est adapté.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>Paramètres

\ de *conteneur*
Type de conteneur dans lequel des éléments doivent être insérés par un `insert_iterator`.

## <a name="remarks"></a>Notes

Le conteneur de type `Container` doit satisfaire les exigences d’un conteneur de taille variable et avoir une fonction membre Insert à deux arguments où les paramètres sont de type `Container::iterator` et `Container::value_type` et qui retourne un `Container::iterator`de type. La séquence de bibliothèque standard C++ et les conteneurs associatifs triés sont conformes à ces exigences et peuvent être adaptés pour être utilisés avec des objets `insert_iterator`. Pour les conteneurs associatifs, l’argument de position est traité comme un indice, lequel peut améliorer ou dégrader les performances selon sa qualité. Un `insert_iterator` doit toujours être initialisé avec son conteneur.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[insert_iterator](#insert_iterator)|Construit un `insert_iterator` qui insère un élément à une position spécifiée dans un conteneur.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[container_type](#container_type)|Type qui représente le conteneur dans lequel une insertion générale doit être effectuée.|
|[reference](#reference)|Type qui fournit une référence à un élément dans une séquence contrôlée par le conteneur associé.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator*](#op_star)|Opérateur de suppression de référence servant à implémenter l’expression de l’itérateur de sortie * `i` = `x` pour une insertion générale.|
|[operator++](#op_add_add)|Incrémente le `insert_iterator` à l'emplacement suivant où une valeur peut être stockée.|
|[operator=](#op_eq)|Opérateur d’assignation servant à implémenter l’expression de l’itérateur de sortie * `i` = `x` pour une insertion générale.|

## <a name="requirements"></a>Spécifications

**En-tête** : \<iterator>

**Espace de noms :** std

## <a name="container_type"></a>  insert_iterator::container_type

Type qui représente le conteneur dans lequel une insertion générale doit être effectuée.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *Container*.

### <a name="example"></a>Exemple

```cpp
// insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   insert_iterator<list<int> >::container_type L2 = L1;
   inserter ( L2, L2.end ( ) ) = 20;
   inserter ( L2, L2.end ( ) ) = 10;
   inserter ( L2, L2.begin ( ) ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 20 10 ).
*/
```

## <a name="insert_iterator"></a>  insert_iterator::insert_iterator

Construit un `insert_iterator` qui insère un élément à une position spécifiée dans un conteneur.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>Paramètres

*_Cont*\
Conteneur dans lequel `insert_iterator` doit insérer des éléments.

*_It*\
Position de l’insertion.

### <a name="remarks"></a>Notes

Tous les conteneurs ont leur fonction membre d’insertion appelée par `insert_iterator`. Pour les conteneurs associatifs, la position du paramètre est simplement une suggestion. La fonction d’insertion fournit un moyen pratique pour insérer des valeurs.

### <a name="example"></a>Exemple

```cpp
// insert_iterator_insert_iterator.cpp
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
   for (i = 1 ; i < 4 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   inserter ( L, L.begin ( ) ) = 2;

   // Alternatively, you may use the template version
   insert_iterator< list < int> > Iter(L, L.end ( ) );
*Iter = 300;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( 10 20 30 ).
After the insertions, the list L is:
( 2 10 20 30 300 ).
*/
```

## <a name="op_star"></a>  insert_iterator::operator*

Supprime la référence à l’itérateur d’insertion retournant l’élément traité.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne la valeur de l’élément ciblé.

### <a name="remarks"></a>Notes

Utilisé pour implémenter l’expression d’itérateur de sortie **\*Iter** = **value**. Si `Iter` est un itérateur qui traite un élément dans une séquence,\***valeur** de l' **ITER** = remplace cet élément par la valeur et ne modifie pas le nombre total d’éléments dans la séquence.

### <a name="example"></a>Exemple

```cpp
// insert_iterator_op_deref.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="op_add_add"></a>  insert_iterator::operator++

Incrémente le `insert_iterator` à l'emplacement suivant où une valeur peut être stockée.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>Paramètres

`insert_iterator` qui traite l’emplacement suivant où une valeur peut être stockée.

### <a name="remarks"></a>Notes

Les opérateurs de préincrémentation et de postincrémentation retournent le même résultat.

### <a name="example"></a>Exemple

```cpp
// insert_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 5 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   insert_iterator<vector<int> > ii ( vec, vec.begin ( ) );
*ii = 30;
   ii++;
*ii = 40;
   ii++;
*ii = 50;

   cout << "After the insertions, the vector vec becomes:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The vector vec is:
( 1 2 3 4 ).
After the insertions, the vector vec becomes:
( 30 40 50 1 2 3 4 ).
*/
```

## <a name="op_eq"></a>  insert_iterator::operator=

Insère une valeur dans le conteneur et retourne l’itérateur mis à jour pour pointer vers le nouvel élément.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>Paramètres

\ *Val*
Valeur à assigner au conteneur.

### <a name="return-value"></a>Valeur de retour

Référence à l’élément inséré dans le conteneur.

### <a name="remarks"></a>Notes

Le premier opérateur de membre évalue

`Iter = container->insert(Iter, val)`;

`++Iter;`

puis retourne `*this`.

Le deuxième opérateur de membre évalue

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

puis retourne `*this`.

### <a name="example"></a>Exemple

```cpp
// insert_iterator_op_assign.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="reference"></a>  insert_iterator::reference

Type qui fournit une référence à un élément dans une séquence contrôlée par le conteneur associé.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence à un élément de la séquence contrôlée par le conteneur associé.

### <a name="example"></a>Exemple

```cpp
// insert_iterator_container_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   insert_iterator<list<int> > iivIter( L , L.begin ( ) );
*iivIter = 10;
*iivIter = 20;
*iivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++ )
      cout << *LIter << " ";
   cout << ")." << endl;

   insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*/
```

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ Standard](../standard-library/cpp-standard-library-reference.md)
