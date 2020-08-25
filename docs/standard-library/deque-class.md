---
title: deque, classe
ms.date: 11/04/2016
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
ms.openlocfilehash: 1edcabf526d0f3aa2ba52ba3fd0fc656c5ae6b9c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838542"
---
# <a name="deque-class"></a>deque, classe

Organise les éléments d'un type en un arrangement linéaire et, comme un vecteur, permet un accès aléatoire rapide à n'importe quel élément, ainsi que l'insertion et la suppression efficace à l'arrière du conteneur. Cependant, contrairement à un vecteur, la classe `deque` prend également en charge l'insertion et la suppression efficace à l'avant du conteneur.

## <a name="syntax"></a>Syntaxe

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>Paramètres

*Entrer*\
Type de données de l'élément à stocker dans la file d'attente à deux extrémités.

*Allocateur*\
Type qui représente l'objet allocateur stocké qui contient des informations sur l'allocation et la désallocation de mémoire de la file d'attente à deux extrémités. Cet argument est facultatif et sa valeur par défaut est **Allocator \<Type> **.

## <a name="remarks"></a>Notes

Le choix du type de conteneur doit être basé en général sur le type de la recherche et de l'insertion requis par l'application. Les [vecteurs](../standard-library/vector-class.md) doivent être le conteneur préféré pour la gestion d’une séquence quand l’accès aléatoire à un élément est primordial, et que des insertions ou des suppressions d’éléments sont nécessaires seulement à la fin d’une séquence. Les performances du conteneur de liste sont meilleures quand des insertions et des suppressions efficaces (en temps constant) sont primordiales à n’importe quel emplacement de la séquence. Ces opérations au milieu de la séquence nécessitent des copies et des affectations d'éléments proportionnellement au nombre d'éléments de la séquence (délai linéaire).

La réallocation de la file d'attente à deux extrémités se produit quand une fonction membre doit insérer ou effacer des éléments de la séquence :

- Si un élément est inséré dans une séquence vide ou si un élément est effacé pour laisser une séquence vide, les itérateurs précédemment retournés par [begin](#begin) et [end](#end) deviennent non valides.

- Si un élément est inséré à la première position de la file d'attente à deux extrémités, tous les itérateurs, mais aucune des références, désignant les éléments existants deviennent non valides.

- Si un élément est inséré à la fin de la file d’attente à deux extrémités, [end](#end) et tous les itérateurs, mais aucune des références, désignant les éléments existants deviennent non valides.

- Si un élément est effacé à l'avant de la file d'attente à deux extrémités, seul cet itérateur et les références à l'élément effacé deviennent non valides.

- Si le dernier élément est effacé de la fin de la file d'attente à deux extrémités, seul cet itérateur vers l'élément final et les références à l'élément effacé deviennent non valides.

Dans le cas contraire, l'insertion ou la suppression d'un élément invalide tous les itérateurs et toutes les références.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[deque](#deque)|Construit un objet `deque`. Plusieurs constructeurs sont fournis pour configurer le contenu du nouveau `deque` de différentes façons : vide ; chargé avec un nombre spécifié d’éléments vides ; contenu déplacé ou copié à partir d’un autre `deque` ; contenu copié ou déplacé à l’aide d’un itérateur ; et un élément copié dans les `deque` `count` heures. Certains constructeurs permettent l'utilisation d'un `allocator` personnalisé pour créer des éléments.|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` pour l'objet `deque`.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur à accès aléatoire qui peut accéder et lire des éléments dans le `deque` en tant que **`const`**|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur vers un élément d'une `deque` en tant que `const.`.|
|[const_reference](#const_reference)|Type qui fournit une référence à un élément d'une  `deque` pour la lecture et d'autres opérations en tant que `const.`.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur à accès aléatoire qui peut accéder aux éléments du en tant que et les lire `deque` **`const`** . La file d'attente à deux extrémités est affichée dans l'ordre inverse. Pour plus d’informations, consultez [reverse_iterator, classe](../standard-library/reverse-iterator-class.md)|
|[difference_type](#difference_type)|Type qui fournit la différence entre deux itérateurs à accès aléatoire qui référencent des éléments de la même `deque`.|
|[répétiteur](#iterator)|Type qui fournit un itérateur à accès aléatoire qui peut lire ou modifier tout élément d'une `deque`.|
|[dirigé](#pointer)|Type qui fournit un pointeur vers un élément d'un objet `deque`.|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans un `deque`.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur à accès aléatoire qui peut lire ou modifier un élément d'une `deque`. La file d'attente à deux extrémités est affichée dans l'ordre inverse.|
|[size_type](#size_type)|Type qui compte le nombre d'éléments d'une `deque`.|
|[value_type](#value_type)|Type qui représente le type de données stocké dans un `deque`.|

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[assign](#assign)|Efface les éléments d'une `deque` et copie une nouvelle séquence d'éléments vers la `deque` cible.|
|[at](#at)|Retourne une référence à l'élément à un emplacement spécifié dans la `deque`.|
|[Précédent](#back)|Retourne une référence au dernier élément de la `deque`.|
|[commencer](#begin)|Retourne un itérateur à accès aléatoire pointant vers le premier élément de la `deque`.|
|[cbegin](#cbegin)|Retourne un itérateur const vers le premier élément de la `deque`.|
|[cend](#cend)|Retourne un itérateur à accès aléatoire **`const`** qui pointe juste après la fin de `deque` .|
|[clear](#clear)|Efface tous les éléments d'un `deque`.|
|[crbegin](#crbegin)|Retourne un itérateur const à accès aléatoire pointant vers le premier élément d'une `deque` affichée en ordre inverse.|
|[crend](#crend)|Retourne un itérateur const à accès aléatoire pointant vers le premier élément d'une `deque` affichée en ordre inverse.|
|[emplace](#emplace)|Insère un élément construit sur place à la position spécifiée dans la `deque`.|
|[emplace_back](#emplace_back)|Ajoute un élément construit sur place à la fin de la `deque`.|
|[emplace_front](#emplace_front)|Ajoute un élément construit sur place au début de la `deque`.|
|[empty](#empty)|Retourne **`true`** si le `deque` contient zéro élément et **`false`** s’il contient un ou plusieurs éléments.|
|[end](#end)|Retourne un itérateur à accès aléatoire qui pointe juste après la fin de la `deque`.|
|[erase](#erase)|Supprime un élément ou une plage d'éléments aux positions spécifiées d'une `deque`.|
|[frontal](#front)|Retourne une référence au premier élément d'une `deque`.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` qui est utilisé pour construire le `deque`.|
|[insert](#insert)|Insère un élément, plusieurs éléments ou une plage d'éléments dans la `deque` à une position spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale possible de la `deque`.|
|[pop_back](#pop_back)|Efface l'élément à la fin de la `deque`.|
|[pop_front](#pop_front)|Efface l'élément au début de la `deque`.|
|[push_back](#push_back)|Ajoute un élément à la fin de la `deque`.|
|[push_front](#push_front)|Ajoute un élément au début de la `deque`.|
|[rbegin](#rbegin)|Retourne un itérateur à accès aléatoire vers le premier élément d'une `deque` inversée.|
|[rend](#rend)|Retourne un itérateur qui pointe juste après le dernier élément d'une `deque` inversée.|
|[redimensionner](#resize)|Spécifie une nouvelle taille pour un objet `deque`.|
|[shrink_to_fit](#shrink_to_fit)|Ignore la capacité excédentaire.|
|[size](#size)|Retourne le nombre d'éléments d'un `deque`.|
|[swap](#swap)|Échange les éléments de deux `deque`.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[operator&#91;&#93;](#op_at)|Retourne une référence à l'élément d'un objet `deque` à une position spécifiée.|
|[opérateur =](#op_eq)|Remplace les éléments de l'objet `deque` par une copie d'un autre objet `deque`.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

Type représentant la classe allocator pour l’objet de file d’attente à deux extrémités.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Notes

`allocator_type` est un synonyme du paramètre de modèle `Allocator`.

### <a name="example"></a>Exemple

Consultez l’exemple de [get_allocator](#get_allocator).

## <a name="assign"></a><a name="assign"></a> assignés

Efface les éléments d’une file d’attente à deux extrémités et copie un nouvel ensemble d’éléments dans la file d’attente à deux extrémités cible.

```cpp
template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);

void assign(
    size_type Count,
    const Type& Val);

void assign(initializer_list<Type> IList);
```

### <a name="parameters"></a>Paramètres

*Premier*\
Position du premier élément de la plage d’éléments à copier à partir de la file d’attente à deux extrémités de l’argument.

*Famille*\
Position du premier élément après la plage d’éléments à copier à partir de la file d’attente à deux extrémités de l’argument.

*Saut*\
Nombre de copies d’un élément inséré dans la file d’attente à deux extrémités.

*Multiples*\
Valeur de l’élément inséré dans la file d’attente à deux extrémités.

*IList*\
Initializer_list inséré dans la file d’attente à deux extrémités.

### <a name="remarks"></a>Notes

Après avoir effacé les éléments existants dans la file d’attente à deux extrémités cible, `assign` insère une plage d’éléments spécifiée à partir de la file d’attente à deux extrémités d’origine ou d’une autre file d’attente à deux extrémités dans la file d’attente à deux extrémités cible, ou insère des copies d’un nouvel élément d’une valeur spécifiée dans la file d’attente à deux extrémités cible.

### <a name="example"></a>Exemple

```cpp
// deque_assign.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <initializer_list>

int main()
{
    using namespace std;
    deque <int> c1, c2;
    deque <int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    deque<int> d1{ 1, 2, 3, 4 };
    initializer_list<int> iList{ 5, 6, 7, 8 };
    d1.assign(iList);

    cout << "d1 = ";
    for (int i : d1)
        cout << i;
    cout << endl;

    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;
}
```

```Output
d1 = 5678c1 =102030c1 =5060c1 =4444444
```

## <a name="at"></a><a name="at"></a> à

Retourne une référence à l’élément à un emplacement spécifié dans la file d’attente à deux extrémités.

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>Paramètres

*imprim*\
Indice (ou numéro de position) de l’élément à référencer dans la file d’attente à deux extrémités.

### <a name="return-value"></a>Valeur renvoyée

Si *pos* est supérieur à la taille de deque, `at` lève une exception.

### <a name="return-value"></a>Valeur renvoyée

Si la valeur de retour de `at` est assignée à `const_reference`, l’objet de file d’attente à deux extrémités ne peut pas être modifié. Si la valeur de retour de `at` est assignée à `reference`, l’objet de file d’attente à deux extrémités peut être modifié.

### <a name="example"></a>Exemple

```cpp
// deque_at.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int& i = c1.at( 0 );
   int& j = c1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a><a name="back"></a> Précédent

Retourne une référence au dernier élément de la file d’attente à deux extrémités.

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le dernier élément de la file d’attente à deux extrémités. Si la file d’attente à deux extrémités est vide, la valeur de retour n’est pas définie.

### <a name="remarks"></a>Notes

Si la valeur de retour de `back` est assignée à `const_reference`, l’objet de file d’attente à deux extrémités ne peut pas être modifié. Si la valeur de retour de `back` est assignée à `reference`, l’objet de file d’attente à deux extrémités peut être modifié.

En cas de compilation avec [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous essayez d’accéder à un élément d’une file d’attente à deux extrémités vide.  Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md) .

### <a name="example"></a>Exemple

```cpp
// deque_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a><a name="begin"></a> commencer

Retourne un itérateur ciblant le premier élément de la file d’attente à deux extrémités.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’accès aléatoire ciblant le premier élément dans la file d’attente à deux extrémités ou l’emplacement suivant une file d’attente à deux extrémités vide.

### <a name="remarks"></a>Notes

Si la valeur de retour de `begin` est assignée à `const_iterator`, l’objet de file d’attente à deux extrémités ne peut pas être modifié. Si la valeur de retour de `begin` est assignée à `iterator` , l’objet deque peut être modifié.

### <a name="example"></a>Exemple

```cpp
// deque_begin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

Retourne un **`const`** itérateur qui traite le premier élément de la plage.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`const`** Itérateur à accès aléatoire qui pointe vers le premier élément de la plage, ou vers l’emplacement situé juste après la fin d’une plage vide (pour une plage vide, `cbegin() == cend()` ).

### <a name="remarks"></a>Notes

Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `begin()` et `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> CEND

Retourne un **`const`** itérateur qui traite l’emplacement juste après le dernier élément d’une plage.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur d'accès aléatoire qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Notes

`cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `end()` et `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="clear"></a><a name="clear"></a> effacé

Efface tous les éléments d’une file d’attente à deux extrémités.

```cpp
void clear();
```

### <a name="example"></a>Exemple

```cpp
// deque_clear.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the deque is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the deque is initially 3
The size of the deque after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Type qui fournit un itérateur à accès aléatoire qui peut accéder à un **`const`** élément dans le deque et le lire.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_iterator` ne peut pas être utilisé pour changer la valeur d'un élément.

### <a name="example"></a>Exemple

Consultez l’exemple de [back](#back).

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Fournit un pointeur vers un **`const`** élément d’un deque.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Notes

Un type `const_pointer` ne peut pas être utilisé pour changer la valeur d'un élément. Un [itérateur](#iterator) est généralement utilisé pour accéder à un élément d’une file d’attente à deux extrémités.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Type qui fournit une référence à un **`const`** élément stocké dans un deque pour la lecture et l’exécution d' **`const`** opérations.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Notes

Un type `const_reference` ne peut pas être utilisé pour changer la valeur d'un élément.

### <a name="example"></a>Exemple

```cpp
// deque_const_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const deque <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

Type qui fournit un itérateur à accès aléatoire qui peut lire n’importe quel **`const`** élément dans le deque.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_reverse_iterator` ne peut pas modifier la valeur d’un élément. Il sert à itérer au sein de la file d’attente à deux extrémités dans l’ordre inverse.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [rbegin](#rbegin) pour savoir comment déclarer et utiliser un itérateur.

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

Retourne un itérateur const vers le premier élément d’une file d’attente à deux extrémités inversée.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur const inverse d’accès aléatoire qui cible le premier élément d’une classe [deque](../standard-library/deque-class.md) inversée ou l’élément qui était le dernier dans la classe `deque` non inversée.

### <a name="remarks"></a>Notes

Avec la valeur de retour `crbegin`, l'objet `deque` ne peut pas être changé.

### <a name="example"></a>Exemple

```cpp
// deque_crbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator v1_Iter;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of deque is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed deque is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of deque is 1.
The first element of the reversed deque is 2.
```

## <a name="crend"></a><a name="crend"></a> crend

Retourne un itérateur const qui cible l’emplacement qui suit le dernier élément d’une file d’attente à deux extrémités inversée.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur const inversé d’accès aléatoire qui cible l’emplacement qui suit le dernier élément d’une classe [deque](../standard-library/deque-class.md) inversée (emplacement qui précédait le premier élément dans la file d’attente à deux extrémités non inversée).

### <a name="remarks"></a>Notes

`crend` est utilisé avec un `deque` inversé comme [array::cend](../standard-library/array-class-stl.md#cend) est utilisé avec un `deque`.

Avec la valeur de retour de `crend` (convenablement décrémentée), l’objet `deque` ne peut pas être modifié.

`crend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de sa file d’attente à deux extrémités.

La valeur retournée par `crend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// deque_crend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="deque"></a><a name="deque"></a> deque

Construit une file d’attente à deux extrémités de taille spécifique ou contenant des éléments de valeur spécifique, ou contenant un allocateur spécifique, ou comme copie complète ou partielle d’une autre file d’attente à deux extrémités.

```cpp
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,
    const Type& Val,
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>
deque(
   InputIterator First,
   InputIterator Last,
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

*&*\
Classe allocator à utiliser avec cet objet.

*Saut*\
Nombre d’éléments de la file d’attente à deux extrémités construite.

*Multiples*\
Valeur des éléments de la file d’attente à deux extrémités construite.

*Oui*\
File d’attente à deux extrémités dont la file d’attente à deux extrémités construite doit être une copie.

*Premier*\
Position du premier élément dans la plage d'éléments à copier.

*Famille*\
Position du premier élément suivant la fin de la plage d'éléments à copier.

*IList*\
Initializer_list à copier.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet allocateur (*al*) et initialisent le deque.

Les deux premiers constructeurs spécifient un deque initial vide ; le deuxième spécifie également le type d’allocateur ( `_Al` ) à utiliser.

Le troisième constructeur spécifie une répétition d'un nombre donné (`count`) d'éléments de la valeur par défaut pour la classe `Type`.

Les quatrième et cinquième constructeurs spécifient une répétition des éléments (*Count*) de la valeur `val` .

Le sixième constructeur spécifie une copie du *droit*deque.

Les septième et huitième constructeurs copient la plage `[First, Last)` d’une file d’attente à deux extrémités.

Le septième constructeur déplace le deque vers la *droite*.

Le huitième constructeur copie le contenu d’un initializer_list.

Aucun des constructeurs n'effectue de réallocations temporaires.

### <a name="example"></a>Exemple

```cpp
/ compile with: /EHsc
#include <deque>
#include <iostream>
#include <forward_list>

int main()
{
    using namespace std;

    forward_list<int> f1{ 1, 2, 3, 4 };

    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });

    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1(3);

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2(5, 2);

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3(3, 1, c2.get_allocator());

    // Create a copy, deque c4, of deque c2
    deque <int> c4(c2);

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    deque <int> c5(c4.begin(), c4_Iter);

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

    initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for (int i : c1)
        cout << i << " ";
    cout << endl;

    cout << "c2 = ";
    for (int i : c2)
        cout << i << " ";
    cout << endl;

    cout << "c3 = ";
    for (int i : c3)
        cout << i << " ";
    cout << endl;

    cout << "c4 = ";
    for (int i : c4)
        cout << i << " ";
    cout << endl;

    cout << "c5 = ";
    for (int i : c5)
        cout << i << " ";
    cout << endl;

    cout << "c6 = ";
    for (int i : c6)
        cout << i << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7(move(c6));
    deque <int>::iterator c7_Iter;

    cout << "c7 =";
    for (int i : c7)
        cout << i << " ";
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    for (int i : c9)
        cout << i << " ";
    cout << endl;

    int x = 3;
}
// deque_deque.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
    using namespace std;
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1( 3 );

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2( 5, 2 );

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3( 3, 1, c2.get_allocator( ) );

    // Create a copy, deque c4, of deque c2
    deque <int> c4( c2 );

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin( );
    c4_Iter++;
    c4_Iter++;
    deque <int> c5( c4.begin( ), c4_Iter );

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin( );
   c4_Iter++;
   c4_Iter++;
   c4_Iter++;
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

        initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
        cout << *c1_Iter << " ";
    cout << endl;

    cout << "c2 = ";
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
        cout << *c2_Iter << " ";
    cout << endl;

    cout << "c3 = ";
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
        cout << *c3_Iter << " ";
    cout << endl;

    cout << "c4 = ";
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )
        cout << *c4_Iter << " ";
    cout << endl;

    cout << "c5 = ";
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )
        cout << *c5_Iter << " ";
    cout << endl;

    cout << "c6 = ";
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )
        cout << *c6_Iter << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7( move(c6) );
    deque <int>::iterator c7_Iter;

    cout << "c7 =" ;
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )
        cout << " " << *c7_Iter;
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    or (int i : c9)
        cout << i << " ";
    cout << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Type qui fournit la différence entre deux itérateurs qui font référence aux éléments d’une même file d’attente à deux extrémités.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Notes

Un `difference_type` peut également représenter le nombre d'éléments entre deux pointeurs.

### <a name="example"></a>Exemple

```cpp
// deque_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <deque>
#include <algorithm>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   deque <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

Insère un élément construit sur place à la position spécifiée dans la file d’attente à deux extrémités.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Paramètres

*_Where*\
Position dans la classe [deque](../standard-library/deque-class.md) où le premier élément est inséré.

*multiples*\
Valeur de l'élément inséré dans le `deque`.

### <a name="return-value"></a>Valeur renvoyée

La fonction retourne un itérateur qui pointe vers la position où le nouvel élément a été inséré dans la file d’attente à deux extrémités.

### <a name="remarks"></a>Notes

Une opération d’insertion peut s’avérer coûteuse. Consultez `deque` pour en savoir plus sur les performances de `deque`.

### <a name="example"></a>Exemple

```cpp
// deque_emplace.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a><a name="emplace_back"></a> emplace_back

Ajoute un élément construit sur place à la fin de la file d’attente à deux extrémités.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Élément ajouté à la fin de la classe [deque](../standard-library/deque-class.md).

### <a name="example"></a>Exemple

```cpp
// deque_emplace_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_back( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

Ajoute un élément construit sur place à la fin de la file d’attente à deux extrémités.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Élément ajouté au début de [deque](../standard-library/deque-class.md).

### <a name="example"></a>Exemple

```cpp
// deque_emplace_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_front( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="empty"></a><a name="empty"></a> vidé

Vérifie si une file d’attente à deux extrémités est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le deque est vide ; **`false`** si le deque n’est pas vide.

### <a name="example"></a>Exemple

```cpp
// deque_empty.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The deque is empty." << endl;
   else
      cout << "The deque is not empty." << endl;
}
```

```Output
The deque is not empty.
```

## <a name="end"></a><a name="end"></a> effet

Retourne un itérateur qui cible l’emplacement suivant le dernier élément d’une file d’attente à deux extrémités.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’accès aléatoire qui cible l’emplacement suivant le dernier élément d’une file d’attente à deux extrémités. Si la file d’attente à deux extrémités est vide, deque::end == deque::begin.

### <a name="remarks"></a>Notes

`end` est utilisé pour déterminer si un itérateur a atteint la fin de son deque.

### <a name="example"></a>Exemple

```cpp
// deque_end.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
   *c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // deque <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The deque is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The deque is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> effacer

Supprime un élément ou une plage d’éléments d’une file d’attente à deux extrémités, aux positions spécifiées.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Paramètres

*_Where*\
Position de l’élément à supprimer de la file d’attente à deux extrémités.

*premier*\
Position du premier élément supprimé de la file d’attente à deux extrémités.

*famille*\
Position juste après le dernier élément supprimé de la file d’attente à deux extrémités.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’accès aléatoire qui désigne le premier élément restant après tous les éléments supprimés, ou pointeur vers la fin de la file d’attente à deux extrémités si aucun élément de ce genre n’existe.

### <a name="remarks"></a>Notes

`erase` ne lève jamais d’exception.

### <a name="example"></a>Exemple

```cpp
// deque_erase.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial deque is: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the deque becomes:  ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, deque becomes: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
}
```

```Output
The initial deque is: 10 20 30 40 50
After erasing the first element, the deque becomes:  20 30 40 50
After erasing all elements but the first, deque becomes: 20
```

## <a name="front"></a><a name="front"></a> frontal

Retourne une référence au premier élément d’une file d’attente à deux extrémités.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Valeur renvoyée

Si la file d’attente à deux extrémités est vide, la valeur de retour n’est pas définie.

### <a name="remarks"></a>Notes

Si la valeur de retour de `front` est assignée à `const_reference`, l’objet de file d’attente à deux extrémités ne peut pas être modifié. Si la valeur de retour de `front` est assignée à `reference`, l’objet de file d’attente à deux extrémités peut être modifié.

En cas de compilation avec [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous essayez d’accéder à un élément d’une file d’attente à deux extrémités vide.  Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md) .

### <a name="example"></a>Exemple

```cpp
// deque_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.front( );
   const int& ii = c1.front( );

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The second integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Retourne une copie de l’objet allocateur utilisé pour construire la file d’attente à deux extrémités.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valeur renvoyée

Allocateur utilisé par la file d’attente à deux extrémités.

### <a name="remarks"></a>Notes

Les allocateurs de la classe de file d’attente à deux extrémités spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de la bibliothèque standard C++ sont suffisants pour la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// deque_get_allocator.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   deque <int> c1;
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   deque <int> c3( c1.get_allocator( ) );

   deque <int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> Insérer

Insère un élément, un nombre d’éléments ou une plage d’éléments dans la file d’attente à deux extrémités à la position spécifiée.

```cpp
iterator insert(
    const_iterator Where,
    const Type& Val);

iterator insert(
    const_iterator Where,
    Type&& Val);

void insert(
    iterator Where,
    size_type Count,
    const Type& Val);

template <class InputIterator>
void insert(
    iterator Where,
    InputIterator First,
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>
IList);
```

### <a name="parameters"></a>Paramètres

*Cela*\
Position dans la file d’attente à deux extrémités cible où le premier élément est inséré.

*Multiples*\
Valeur de l’élément inséré dans la file d’attente à deux extrémités.

*Saut*\
Nombre d’éléments insérés dans la file d’attente à deux extrémités.

*Premier*\
Position du premier élément de la plage d’éléments dans la file d’attente à deux extrémités de l’argument à copier.

*Famille*\
Position du premier élément après la plage d’éléments dans la file d’attente à deux extrémités de l’argument à copier.

*IList*\
initializer_list des éléments à insérer.

### <a name="return-value"></a>Valeur renvoyée

Les deux premières fonctions d’insertion retournent un itérateur qui pointe vers la position où le nouvel élément a été inséré dans la file d’attente à deux extrémités.

### <a name="remarks"></a>Notes

Une opération d’insertion peut être coûteuse.

## <a name="iterator"></a><a name="iterator"></a> répétiteur

Type qui fournit un itérateur d’accès aléatoire pour lire ou modifier un élément dans une file d’attente à deux extrémités.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Notes

Un type `iterator` peut être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Consultez l’exemple de [begin](#begin).

## <a name="max_size"></a><a name="max_size"></a> max_size

Retourne la longueur maximale de la file d’attente à deux extrémités.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur maximale possible de la file d’attente à deux extrémités.

### <a name="example"></a>Exemple

```cpp
// deque_max_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   i = c1.max_size( );
   cout << "The maximum possible length of the deque is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_at"></a> [], opérateur

Retourne une référence à l’élément d’une file d’attente à deux extrémités à une position spécifiée.

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>Paramètres

*imprim*\
Position de l’élément de file d’attente à deux extrémités à référencer.

### <a name="return-value"></a>Valeur renvoyée

Référence à l’élément dont la position est spécifiée dans l’argument. Si la position spécifiée est supérieure à la taille de la file d’attente à deux extrémités, le résultat n’est pas défini.

### <a name="remarks"></a>Notes

Si la valeur de retour de `operator[]` est assignée à `const_reference`, l’objet de file d’attente à deux extrémités ne peut pas être modifié. Si la valeur de retour de `operator[]` est assignée à `reference`, l’objet de file d’attente à deux extrémités peut être modifié.

En cas de compilation avec [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous essayez d’accéder à un élément en dehors des limites de la file d’attente à deux extrémités.  Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md) .

### <a name="example"></a>Exemple

```cpp
// deque_op_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   cout << "The first integer of c1 is " << c1[0] << endl;
   int& i = c1[1];
   cout << "The second integer of c1 is " << i << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 20
```

## <a name="operator"></a><a name="op_eq"></a> opérateur =

Remplace les éléments de cette file d’attente à deux extrémités par les éléments d’une autre file d’attente à deux extrémités.

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
File d’attente à deux extrémités qui fournit le nouveau contenu.

### <a name="remarks"></a>Notes

La première substitution copie les éléments vers ce deque à partir de la *droite*, la source de l’assignation. Le deuxième remplacement déplace les éléments vers ce deque à partir de la *droite*.

Les éléments contenus dans cette file d’attente à deux extrémités avant l’exécution de l’opérateur sont supprimés.

### <a name="example"></a>Exemple

```cpp
// deque_operator_as.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
using namespace std;

typedef deque<int> MyDeque;

template<typename MyDeque> struct S;

template<typename MyDeque> struct S<MyDeque&> {
  static void show( MyDeque& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
    cout << endl;
  }
};

template<typename MyDeque> struct S<MyDeque&&> {
  static void show( MyDeque&& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
cout << " via unnamed rvalue reference " << endl;
  }
};

int main( )
{
   MyDeque d1, d2;

   d1.push_back(10);
   d1.push_back(20);
   d1.push_back(30);
   d1.push_back(40);
   d1.push_back(50);

   cout << "d1 = " ;
   S<MyDeque&>::show( d1 );

   d2 = d1;
   cout << "d2 = ";
   S<MyDeque&>::show( d2 );

   cout << "     ";
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );
}
```

## <a name="pointer"></a>Pointeur <a name="pointer"></a>

Fournit un pointeur vers un élément dans une classe [deque](../standard-library/deque-class.md).

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Notes

Un type `pointer` peut être utilisé pour modifier la valeur d’un élément. Un [itérateur](#iterator) est généralement utilisé pour accéder à un élément d’une file d’attente à deux extrémités.

## <a name="pop_back"></a><a name="pop_back"></a> pop_back

Supprime l’élément à la fin de la file d’attente à deux extrémités.

```cpp
void pop_back();
```

### <a name="remarks"></a>Notes

Le dernier élément ne doit pas être vide. `pop_back` ne lève jamais d’exception.

### <a name="example"></a>Exemple

```cpp
// deque_pop_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the deque, the "
      "last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the deque, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

Supprime l’élément au début de la file d’attente à deux extrémités.

```cpp
void pop_front();
```

### <a name="remarks"></a>Notes

Le premier élément ne doit pas être vide. `pop_front` ne lève jamais d’exception.

### <a name="example"></a>Exemple

```cpp
// deque_pop_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the "
      "deque, the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the deque, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> push_back

Ajoute un élément à la fin de la file d’attente à deux extrémités.

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Élément ajouté à la fin de la file d’attente à deux extrémités.

### <a name="remarks"></a>Notes

Si une exception est levée, la file d’attente à deux extrémités n’est pas modifiée et l’exception est levée de nouveau.

## <a name="push_front"></a><a name="push_front"></a> push_front

Ajoute un élément au début de la file d’attente à deux extrémités.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Élément ajouté au début de la file d’attente à deux extrémités.

### <a name="remarks"></a>Notes

Si une exception est levée, la file d’attente à deux extrémités n’est pas modifiée et l’exception est levée de nouveau.

### <a name="example"></a>Exemple

```cpp
// deque_push_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a deque of strings
   deque <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

Retourne un itérateur vers le premier élément d’une file d’attente à deux extrémités inversée.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur inverse d’accès aléatoire qui cible le premier élément d’une file d’attente à deux extrémités inversée ou l’élément qui était le dernier dans la file d’attente à deux extrémités non inversée.

### <a name="remarks"></a>Notes

`rbegin` est utilisé avec une file d’attente à deux extrémités inversée, de la même manière que [begin](#begin) est utilisé avec une file d’attente à deux extrémités.

Si la valeur de retour de `rbegin` est assignée à `const_reverse_iterator`, l’objet de file d’attente à deux extrémités ne peut pas être modifié. Si la valeur de retour de `rbegin` est assignée à `reverse_iterator`, l’objet de file d’attente à deux extrémités peut être modifié.

`rbegin` peut servir à itérer au sein d’une file d’attente à deux extrémités vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// deque_rbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rbegin( );
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;

   cout << "The deque contains the elements: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << "in that order.";
   cout << endl;

   // rbegin can be used to iterate through a deque in reverse order
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rbegin( );
   *c1_rIter = 40;  // This would have caused an error if a
                    // const_reverse iterator had been declared as
                    // noted above
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;
}
```

```Output
Last element in the deque is 30.
The deque contains the elements: 10 20 30 in that order.
The reversed deque is: 30 20 10
Last element in deque is now 40.
```

## <a name="reference"></a><a name="reference"></a> faire

Type qui fournit une référence à un élément stocké dans une file d’attente à deux extrémités.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Exemple

```cpp
// deque_reference.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="rend"></a><a name="rend"></a> rend

Retourne un itérateur qui cible l’emplacement suivant le dernier élément d’une file d’attente à deux extrémités inversée.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur inversé d’accès aléatoire qui cible l’emplacement qui suit le dernier élément d’une file d’attente à deux extrémités inversée (emplacement qui précédait le premier élément dans la file d’attente à deux extrémités non inversée).

### <a name="remarks"></a>Notes

`rend` est utilisé avec une file d’attente à deux extrémités inversée, de la même manière que [end](#end) est utilisé avec une file d’attente à deux extrémités.

Si la valeur de retour de `rend` est assignée à `const_reverse_iterator`, l’objet de file d’attente à deux extrémités ne peut pas être modifié. Si la valeur de retour de `rend` est assignée à `reverse_iterator`, l’objet de file d’attente à deux extrémités peut être modifié.

`rend` peut être utilisé pour déterminer si un itérateur inverse a atteint la fin de sa file d’attente à deux extrémités.

La valeur retournée par `rend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// deque_rend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;
   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --; // Decrementing a reverse iterator moves it forward
                // in the deque (to point to the first element here)
   cout << "The first element in the deque is: " << *c1_rIter << endl;

   cout << "The deque is: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << endl;

   // rend can be used to test if an iteration is through all of
   // the elements of a reversed deque
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--; // Decrementing the reverse iterator moves it backward
               // in the reversed deque (to the last element here)
   *c1_rIter = 40; // This modification of the last element would
                   // have caused an error if a const_reverse
                   // iterator had been declared (as noted above)
   cout << "The modified reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;
}
```

```Output
The first element in the deque is: 10
The deque is: 10 20 30
The reversed deque is: 30 20 10
The modified reversed deque is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> redimensionner

Spécifie une nouvelle taille pour une file d’attente à deux extrémités.

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Paramètres

*_Newsize*\
Nouvelle taille de la file d’attente à deux extrémités.

*multiples*\
Valeur des nouveaux éléments à ajouter à la file d’attente à deux extrémités si la nouvelle taille est supérieure à la taille d’origine. Si la valeur est omise, la valeur par défaut pour la classe est assignée aux nouveaux éléments.

### <a name="remarks"></a>Notes

Si la taille du deque est inférieure à la taille demandée, *_Newsize*, les éléments sont ajoutés au deque jusqu’à ce qu’il atteigne la taille demandée.

Si la taille de deque est supérieure à la taille demandée, les éléments les plus proches de la fin du deque sont supprimés jusqu’à ce que le deque atteigne la taille *_Newsize*.

Si la taille actuelle de la file d’attente à deux extrémités est égale à la taille demandée, aucune action n’est effectuée.

[size](#size) reflète la taille actuelle de la file d’attente à deux extrémités.

### <a name="example"></a>Exemple

```cpp
// deque_resize.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is: 4
The value of the last element is 40
The size of c1 is now: 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

Type qui fournit un itérateur d’accès aléatoire pour lire ou modifier un élément d’une file d’attente à deux extrémités inversée.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `reverse_iterator` est utilisé pour itérer au sein de la file d’attente à deux extrémités.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à rbegin.

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> shrink_to_fit

Ignore la capacité excédentaire.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Notes

Il n’existe aucun moyen portable de déterminer si `shrink_to_fit` réduit le stockage utilisé par une classe [deque](../standard-library/deque-class.md).

### <a name="example"></a>Exemple

```cpp
// deque_shrink_to_fit.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   //deque <int>::iterator Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
   v1.shrink_to_fit();
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
}
```

```Output
Current size of v1 = 1
Current size of v1 = 1
```

## <a name="size"></a><a name="size"></a> corps

Retourne le nombre d’éléments de la file d’attente à deux extrémités.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur actuelle de la file d’attente à deux extrémités.

### <a name="example"></a>Exemple

```cpp
// deque_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   c1.push_back( 1 );
   i = c1.size( );
   cout << "The deque length is " << i << "." << endl;

   c1.push_back( 2 );
   i = c1.size( );
   cout << "The deque length is now " << i << "." << endl;
}
```

```Output
The deque length is 1.
The deque length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Type qui compte le nombre d’éléments dans une file d’attente à deux extrémités.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [size](#size).

## <a name="swap"></a><a name="swap"></a> échange

Échange les éléments de deux classes deque.

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
File d’attente à deux extrémités qui fournit les éléments à échanger ou file d’attente à deux extrémités dont les éléments doivent être échangés avec ceux de la file d’attente à deux extrémités `left`.

*gauche*\
Deque dont les éléments doivent être échangés avec ceux du *droit*deque.

### <a name="example"></a>Exemple

```cpp
// deque_swap.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2, c3;
   deque <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap<>(c1, c2);
   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original deque c1 is: 1 2 3
After swapping with c2, deque c1 is: 10 20
After swapping with c3, deque c1 is: 100
After swapping with c2, deque c1 is: 1 2 3
```

## <a name="value_type"></a><a name="value_type"></a> value_type

Type qui représente le type de données stocké dans une file d’attente à deux extrémités.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Notes

`value_type` est un synonyme du paramètre de modèle `Type`.

### <a name="example"></a>Exemple

```cpp
// deque_value_type.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
int main( )
{
   using namespace std;
   deque<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
