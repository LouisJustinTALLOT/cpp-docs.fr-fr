---
title: '&lt;iterator&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- xutility/std::advance
- xutility/std::back_inserter
- xutility/std::begin
- xutility/std::cbegin
- xutility/std::cend
- xutility/std::distance
- xutility/std::end
- xutility/std::front_inserter
- xutility/std::inserter
- xutility/std::make_checked_array_iterator
- xutility/std::make_move_iterator
- xutility/std::make_unchecked_array_iterator
- xutility/std::next
- xutility/std::prev
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
helpviewer_keywords:
- std::advance [C++]
- std::back_inserter [C++]
- std::begin [C++]
- std::cbegin [C++]
- std::cend [C++]
- std::distance [C++]
- std::end [C++]
- std::front_inserter [C++]
- std::inserter [C++]
- std::make_checked_array_iterator [C++]
- std::make_move_iterator [C++]
- std::make_unchecked_array_iterator [C++]
- std::next [C++]
- std::prev [C++]
ms.openlocfilehash: 69f1007f0c7f587e81313f5de97947410bf243df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874039"
---
# <a name="ltiteratorgt-functions"></a>&lt;iterator&gt;, fonctions

## <a name="advance"></a>l’avance

Incrémente un itérateur d'un nombre spécifié de positions.

```cpp
template <class InputIterator, class Distance>
    void advance(InputIterator& InIt, Distance Off);
```

### <a name="parameters"></a>Paramètres

\ *init*
Itérateur qui doit être incrémenté et qui doit être conforme aux exigences d’un itérateur d’entrée.

*Désactivé*\
Type intégral pouvant être converti en type de différence de l'itérateur et qui spécifie le nombre d'incréments dont la position de l'itérateur doit être avancée.

### <a name="remarks"></a>Notes

La plage d'avance ne doit pas être singulière, là où les itérateurs doivent pouvoir être déréférencés ou au-delà de la fin.

Si le `InputIterator` satisfait aux exigences d’un type d’itérateur bidirectionnel, la valeur *off* peut être négative. Si `InputIterator` est un type d’itérateur d’entrée ou de transfert, la valeur *off* ne doit pas être négative.

La fonction Advance a une complexité constante lorsque `InputIterator` est conforme aux exigences d’un itérateur à accès aléatoire ; dans le cas contraire, elle a une complexité linéaire et est donc potentiellement coûteuse.

### <a name="example"></a>Exemple

```cpp
// iterator_advance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = 1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 4 );
   cout << "LPOS is advanced 4 steps forward to point"
        << " to the fifth element: "
        << *LPOS << "." << endl;

   advance ( LPOS , -3 );
   cout << "LPOS is moved 3 steps back to point to the "
        << "2nd element: " << *LPOS << "." << endl;
}
```

```Output
The list L is: ( 1 2 3 4 5 6 7 8 ).
The iterator LPOS initially points to the first element: 1.
LPOS is advanced 4 steps forward to point to the fifth element: 5.
LPOS is moved 3 steps back to point to the 2nd element: 2.
```

## <a name="back_inserter"></a>back_inserter

Crée un itérateur qui peut insérer des éléments à la fin d'un conteneur spécifié.

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>Paramètres

*_Cont*\
Conteneur dans lequel l’insertion de fin doit être exécutée.

### <a name="return-value"></a>Valeur de retour

`back_insert_iterator` associé à l’objet Container *_Cont*.

### <a name="remarks"></a>Notes

Dans la bibliothèque standard C++, l’argument doit faire référence à l’un des trois conteneurs de séquence ayant la fonction membre `push_back` : [classe deque](../standard-library/deque-class.md), [classe list](../standard-library/list-class.md) ou [classe vector](../standard-library/vector-class.md).

### <a name="example"></a>Exemple

```cpp
// iterator_back_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 3 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;
*backiter = 40;

   // Alternatively, insertions can be done with the
   // back_insert_iterator member function
   back_inserter ( vec ) = 500;
   back_inserter ( vec ) = 600;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 0 1 2 ).
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).
```

## <a name="begin"></a>commencer

Récupère un itérateur sur le premier élément d'un conteneur spécifié.

```cpp
template <class Container>
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>
Ty *begin(Ty (& array)[Size]);
```

### <a name="parameters"></a>Paramètres

*cont*\
Conteneur.

*tableau*\
Tableau d'objets de type `Ty`.

### <a name="return-value"></a>Valeur de retour

Les deux premières fonctions de modèle retournent `cont.begin()`. La première fonction est non constante ; la seconde est constante.

La troisième fonction de modèle retourne un *tableau*.

### <a name="example"></a>Exemple

Nous vous recommandons d'utiliser cette fonction de modèle à la place du membre de conteneur `begin()` lorsqu'un comportement plus générique est requis.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <vector>

template <typename C> void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(begin(c), end(c), std::greater<>());
}

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        std::cout << e << " ";
    }

    std::cout << "\n";
}

int main() {
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(v);
    reverse_sort(v);
    print(v);

    std::cout << "--\n";

    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(arr);
    reverse_sort(arr);
    print(arr);
}
```

```Output
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1
--
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1
```

La fonction `reverse_sort` prend en charge des conteneurs de tout type, outre les tableaux standard, car elle appelle la version non-membre de `begin()`. Si `reverse_sort` était codée pour utiliser le membre de conteneur `begin()` :

```cpp
template <typename C>
void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(c.begin(), c.end(), std::greater<>());

}
```

Ensuite, l'envoi d'un tableau à cette fonction générerait l'erreur du compilateur suivante :

```Output
error C2228: left of '.begin' must have class/struct/union
```

## <a name="cbegin"></a>cbegin

Récupère un itérateur const sur le premier élément d'un conteneur spécifié.

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>Paramètres

*cont*\
Conteneur ou initializer_list.

### <a name="return-value"></a>Valeur de retour

Constante `cont.begin()`.

### <a name="remarks"></a>Notes

Cette fonction est compatible avec tous les conteneurs de bibliothèque standard C++ et avec [initializer_list](../standard-library/initializer-list-class.md).

Vous pouvez utiliser cette fonction membre à la place de la fonction de modèle `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement au mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez `Container` comme un conteneur modifiable (non **const**) ou `initializer_list` de tout type prenant en charge `begin()` et `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>CEND

Récupère un itérateur const sur l'élément qui suit le dernier élément dans le conteneur spécifié.

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>Paramètres

*cont*\
Conteneur ou initializer_list.

### <a name="return-value"></a>Valeur de retour

Constante `cont.end()`.

### <a name="remarks"></a>Notes

Cette fonction est compatible avec tous les conteneurs de bibliothèque standard C++ et avec [initializer_list](../standard-library/initializer-list-class.md).

Vous pouvez utiliser cette fonction membre à la place de la fonction de modèle [end()](../standard-library/iterator-functions.md#end) pour garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement au mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez `Container` comme un conteneur modifiable (non **const**) ou `initializer_list` de tout type prenant en charge `end()` et `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="crbegin"></a>crbegin

```cpp
template <class C> constexpr auto crbegin(const C& c) -> decltype(std::rbegin(c));
```

## <a name="crend"></a>crend

```cpp
template <class C> constexpr auto crend(const C& c) -> decltype(std::rend(c));
```

## <a name="data"></a>métadonnée

```cpp
template <class C> constexpr auto data(C& c) -> decltype(c.data());
template <class C> constexpr auto data(const C& c) -> decltype(c.data());
template <class T, size_t N> constexpr T* data(T (&array)[N]) noexcept;
template <class E> constexpr const E* data(initializer_list<E> il) noexcept;
```

## <a name="distance"></a>distance

Détermine le nombre d'incréments entre les positions traitées par deux itérateurs.

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>Paramètres

*premier*\
Premier itérateur dont la distance à partir du deuxième doit être déterminée.

*dernier*\
Deuxième itérateur dont la distance à partir du premier doit être déterminée.

### <a name="return-value"></a>Valeur de retour

Nombre de fois où le *premier* doit être incrémenté jusqu’à ce qu’il soit égal en *dernier*.

### <a name="remarks"></a>Notes

La fonction distance a une complexité constante lorsque `InputIterator` est conforme aux exigences d’un itérateur à accès aléatoire ; dans le cas contraire, elle a une complexité linéaire et est donc potentiellement coûteuse.

### <a name="example"></a>Exemple

```cpp
// iterator_distance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 7 );
   cout << "LPOS is advanced 7 steps forward to point "
        << " to the eighth element: "
        << *LPOS << "." << endl;

   list<int>::difference_type Ldiff ;
   Ldiff = distance ( L.begin ( ) , LPOS );
   cout << "The distance from L.begin( ) to LPOS is: "
        << Ldiff << "." << endl;
}
```

```Output
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).
The iterator LPOS initially points to the first element: -2.
LPOS is advanced 7 steps forward to point  to the eighth element: 12.
The distance from L.begin( ) to LPOS is: 7.
```

## <a name="empty"></a>vidé

```cpp
template <class C> constexpr auto empty(const C& c) -> decltype(c.empty());
template <class T, size_t N> constexpr bool empty(const T (&array)[N]) noexcept;
template <class E> constexpr bool empty(initializer_list<E> il) noexcept;
```

## <a name="end"></a>effet

Récupère un itérateur de l'élément qui suit le dernier élément dans le conteneur spécifié.

```cpp
template <class Container>
auto end(Container& cont)
   -> decltype(cont.end());

template <class Container>
auto end(const Container& cont)
   -> decltype(cont.end());

template <class Ty, class Size>
Ty *end(Ty (& array)[Size]);
```

### <a name="parameters"></a>Paramètres

*cont*\
Conteneur.

*tableau*\
Tableau d'objets de type `Ty`.

### <a name="return-value"></a>Valeur de retour

Les deux premières fonctions de modèle retournent `cont.end()` (la première est non constante et la deuxième est constante).

La troisième fonction de modèle retourne `array + Size`.

### <a name="remarks"></a>Notes

Pour obtenir un exemple de code, consultez [begin](../standard-library/iterator-functions.md#begin).

## <a name="front_inserter"></a>front_inserter

Crée un itérateur qui peut insérer des éléments à l'avant d'un conteneur spécifié.

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>Paramètres

*_Cont*\
Objet conteneur à l’avant duquel un élément est inséré.

### <a name="return-value"></a>Valeur de retour

`front_insert_iterator` associé à l’objet Container *_Cont*.

### <a name="remarks"></a>Notes

Vous pouvez aussi utiliser la fonction membre [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator) de la classe front_insert_iterator.

Dans la bibliothèque standard C++, l’argument doit faire référence à l’un des deux conteneurs de séquence ayant la fonction membre `push_back` : [classe deque](../standard-library/deque-class.md) ou « classe list ».

### <a name="example"></a>Exemple

```cpp
// iterator_front_inserter.cpp
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
      L.push_back ( i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template function to insert an element
   front_insert_iterator< list < int> > Iter(L);
*Iter = 100;

   // Alternatively, you may use the front_insert member function
   front_inserter ( L ) = 200;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( -1 0 1 2 3 4 5 6 7 8 ).
After the front insertions, the list L is:
( 200 100 -1 0 1 2 3 4 5 6 7 8 ).
```

## <a name="inserter"></a>Inserter

Fonction de modèle d’assistance qui vous permet d’utiliser `inserter(_Cont, _Where)` au lieu de `insert_iterator<Container>(_Cont, _Where)`.

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>Paramètres

*_Cont*\
Conteneur auquel de nouveaux éléments doivent être ajoutés.

*_Where*\
Itérateur localisant le point d’insertion.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator)`<Container>(_Cont, _Where)`.

### <a name="example"></a>Exemple

```cpp
// iterator_inserter.cpp
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
   for (i = 2 ; i < 5 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template version to insert an element
   insert_iterator<list <int> > Iter( L, L.begin ( ) );
*Iter = 1;

   // Alternatively, using the member function to insert an element
   inserter ( L, L.end ( ) ) = 500;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( 20 30 40 ).
After the insertions, the list L is:
( 1 20 30 40 500 ).
```

## <a name="make_checked_array_iterator"></a>make_checked_array_iterator

Crée un [checked_array_iterator](../standard-library/checked-array-iterator-class.md) qui peut être utilisé par d’autres algorithmes.

> [!NOTE]
> Cette fonction est une extension Microsoft de la bibliothèque standard C++. Le code implémenté à l’aide de cette fonction ne peut pas être utilisé dans les environnements de build C++ standard qui ne prennent pas en charge cette extension Microsoft.

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Pointeur vers le tableau de destination.

*Taille*\
Taille du tableau de destination.

*Index*\
Index facultatif du tableau.

### <a name="return-value"></a>Valeur de retour

Instance de `checked_array_iterator`.

### <a name="remarks"></a>Notes

La fonction `make_checked_array_iterator` est définie dans l'espace de noms `stdext`.

Cette fonction accepte un pointeur brut (qui cause habituellement un problème de débordement de limites) et l’enveloppe dans une classe [checked_array_iterator](../standard-library/checked-array-iterator-class.md) qui effectue une vérification. Cette classe étant marquée comme vérifiée, la bibliothèque standard C++ n’affiche pas d’avertissement. Pour plus d’informations et pour obtenir des exemples de code, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

Dans l’exemple suivant, un [vecteur](../standard-library/vector-class.md) est créé et rempli avec 10 éléments. Le contenu du vecteur est copié dans un tableau à l'aide de l'algorithme de copie, puis `make_checked_array_iterator` est utilisé pour spécifier la destination. Ceci est suivi d'une violation intentionnelle de la vérification des limites, afin de déclencher un échec d'assertion de débogage.

```cpp
// make_checked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_checked_array_iterator
#include <memory> // std::make_unique
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    // Old-school but not exception safe, favor make_unique<int[]>
    // int* dest = new int[dest_size];
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);
    int* dest = updest.get(); // get a raw pointer for the demo

    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    // Add another element to the vector to force an overrun.
    v.push_back(10);
    // The next line causes a debug assertion when it executes.
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));
}
```

## <a name="make_move_iterator"></a>make_move_iterator

Crée un `move iterator` qui contient l’itérateur fourni en tant qu’itérateur `stored`.

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>Paramètres

*_It*\
Itérateur stocké dans le nouvel itérateur de déplacement.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `move_iterator` `<Iterator>(_It)`.

## <a name="make_unchecked_array_iterator"></a>make_unchecked_array_iterator

Crée un [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) qui peut être utilisé par d’autres algorithmes.

> [!NOTE]
> Cette fonction est une extension Microsoft de la bibliothèque standard C++. Le code implémenté à l’aide de cette fonction ne peut pas être utilisé dans les environnements de build C++ standard qui ne prennent pas en charge cette extension Microsoft.

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Pointeur vers le tableau de destination.

### <a name="return-value"></a>Valeur de retour

Instance de `unchecked_array_iterator`.

### <a name="remarks"></a>Notes

La fonction `make_unchecked_array_iterator` est définie dans l'espace de noms `stdext`.

Cette fonction accepte un pointeur brut et l’enveloppe dans une classe qui n’effectue aucune vérification. Outre l’optimisation qui en résulte, cela fait taire les avertissements du compilateur, tels que [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Il s'agit donc d'une méthode ciblée permettant de gérer les avertissements des pointeurs non vérifiés, sans tous les faire taire ou faire l'effort d'une vérification. Pour plus d’informations et pour obtenir des exemples de code, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

Dans l’exemple suivant, un [vecteur](../standard-library/vector-class.md) est créé et rempli avec 10 éléments. Le contenu du vecteur est copié dans un tableau à l'aide de l'algorithme de copie, puis `make_unchecked_array_iterator` est utilisé pour spécifier la destination.

```cpp
// make_unchecked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_unchecked_array_iterator
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    int *dest = new int[dest_size];
    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun will trigger undefined behavior)
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    delete[] dest;
}
```

## <a name="next"></a>Situé

Itère un nombre de fois donné et retourne la nouvelle position de l'itérateur.

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Paramètres

*premier*\
Position actuelle.

*_Off*\
Nombre d’itérations à effectuer.

### <a name="return-value"></a>Valeur de retour

Retourne la nouvelle position de l’itérateur après l’itération *_OFF* fois.

### <a name="remarks"></a>Notes

La fonction de modèle retourne des `next` incrémentées *_OFF* fois

## <a name="prev"></a>PREV

Itère en sens inverse un nombre de fois donné et retourne la nouvelle position de l'itérateur.

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Paramètres

*premier*\
Position actuelle.

*_Off*\
Nombre d’itérations à effectuer.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `next` décrémenté `off` fois.

## <a name="rbegin"></a>rbegin

```cpp
template <class C> constexpr auto rbegin(C& c) -> decltype(c.rbegin());
template <class C> constexpr auto rbegin(const C& c) -> decltype(c.rbegin());
```

## <a name="rend"></a>rend

```cpp
template <class C> constexpr auto rend(C& c) -> decltype(c.rend());
template <class C> constexpr auto rend(const C& c) -> decltype(c.rend());
```

## <a name="size"></a>corps

```cpp
template <class C> constexpr auto size(const C& c) -> decltype(c.size());
template <class T, size_t N> constexpr size_t size(const T (&array)[N]) noexcept;
```
