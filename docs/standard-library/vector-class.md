---
title: vector, classe
ms.date: 11/04/2016
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
ms.openlocfilehash: 501f6547378b5461fe314410f54a6cc7d64c1221
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583363"
---
# <a name="vector-class"></a>vector, classe

La classe vector de la bibliothèque standard C++ est une classe de modèle de conteneurs de séquence qui organisent les éléments d’un type donné selon un arrangement linéaire et permettent ainsi un accès aléatoire rapide à n’importe quel élément. Ils doivent être les conteneurs préférés pour une séquence quand les performances de l'accès aléatoire sont une priorité.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>Paramètres

*Type*<br/>
Type de données des éléments à stocker dans le vecteur.

*Allocateur*<br/>
Type qui représente l'objet allocateur stocké qui contient des informations détaillées sur l'allocation et la désallocation de mémoire du vecteur. Cet argument est facultatif et sa valeur par défaut est `allocator<Type>`.

## <a name="remarks"></a>Notes

Les vecteurs gèrent les insertions et suppressions en temps fixe à la fin de la séquence. Ailleurs dans le vecteur, les insertions et suppressions d'éléments doivent s'effectuer en temps linéaire. Le conteneur de [classe deque](../standard-library/deque-class.md) offre de meilleures performances pour les insertions et les suppressions au début et à la fin d’une séquence. Le conteneur de [classe list](../standard-library/list-class.md) est recommandé pour les insertions et suppressions réalisées à tout autre emplacement dans la séquence.

Une réallocation du vecteur se produit quand une fonction membre doit augmenter la taille de la séquence contenue dans l'objet vector au-delà de sa capacité de stockage actuelle. D'autres insertions et suppressions peuvent modifier différentes adresses de stockage dans la séquence. Si cela se produit, les itérateurs ou les références qui pointent vers des parties modifiées dans la séquence deviennent non valides. En l'absence de réallocation, seuls les itérateurs et références situés avant le point d'insertion ou de suppression restent valides.

La [classe vector\<bool>](../standard-library/vector-bool-class.md) est une spécialisation complète de la classe de modèle vector pour les éléments de type booléen ayant un allocateur pour le type sous-jacent utilisé par la spécialisation.

La [classe de référence vector\<bool>](../standard-library/vector-bool-class.md#reference_class) est une classe imbriquée dont les objets peuvent fournir des références aux éléments (sur un octet) d’un objet vector\<bool>.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[vector](#vector)|Construit un vecteur de taille spécifique ou contenant des éléments de valeurs spécifiques, ou contenant un objet `allocator` spécifique, ou comme copie d'un autre vecteur.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` pour l'objet vector.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur à accès aléatoire qui peut lire un élément **const** dans un vecteur.|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur vers un élément **const** dans un vecteur.|
|[const_reference](#const_reference)|Type qui fournit une référence à un élément **const** stocké dans un vecteur pour la lecture et l’exécution des opérations **const**.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur d’accès aléatoire pouvant lire tout élément **const** dans le vecteur.|
|[difference_type](#difference_type)|Type qui fournit la différence entre les adresses de deux éléments dans un vecteur.|
|[iterator](#iterator)|Type qui fournit un itérateur à accès aléatoire pour lire ou modifier un élément dans un vecteur.|
|[pointer](#pointer)|Type qui fournit un pointeur vers un élément d'un vecteur.|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans un vecteur.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur à accès aléatoire pouvant lire ou modifier un élément d'un vecteur inversé.|
|[size_type](#size_type)|Type qui compte le nombre d'éléments dans un vecteur.|
|[value_type](#value_type)|Type représentant le type de données stockées dans un vecteur.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[assign](#assign)|Efface un tableau et copie les éléments spécifiés dans le vecteur vide.|
|[at](#at)|Retourne une référence à l'élément à un emplacement spécifié dans le vecteur.|
|[back](#back)|Retourne une référence au dernier élément du vecteur.|
|[begin](#begin)|Retourne un itérateur à accès aléatoire pointant vers le premier élément dans le vecteur.|
|[capacity](#capacity)|Retourne le nombre d'éléments que le vecteur peut contenir sans avoir à allouer plus de stockage.|
|[cbegin](#cbegin)|Retourne un itérateur const à accès aléatoire pointant vers le premier élément du vecteur.|
|[cend](#cend)|Retourne un itérateur const à accès aléatoire qui pointe juste après la fin du vecteur.|
|[crbegin](#crbegin)|Retourne un itérateur const qui pointe vers le premier élément d'un vecteur inversé.|
|[crend](#crend)|Retourne un itérateur const qui pointe vers la fin d'un vecteur inversé.|
|[clear](#clear)|Supprime les éléments du vecteur.|
|[data](#data)|Retourne un pointeur vers le premier élément du vecteur.|
|[emplace](#emplace)|Insère un élément construit sur place à la position spécifiée dans le vecteur.|
|[emplace_back](#emplace_back)|Ajoute un élément construit sur place à la fin du vecteur.|
|[empty](#empty)|Teste si le conteneur vecteur est vide.|
|[end](#end)|Retourne un itérateur à accès aléatoire qui pointe vers la fin du vecteur.|
|[erase](#erase)|Supprime un élément ou une plage d'éléments aux positions spécifiées dans le vecteur.|
|[front](#front)|Retourne une référence au premier élément du vecteur.|
|[get_allocator](#get_allocator)|Retourne un objet à la classe `allocator` utilisée par un vecteur.|
|[insert](#insert)|Insère un ou plusieurs éléments à la position spécifiée dans le vecteur.|
|[max_size](#max_size)|Retourne la longueur maximale autorisée du vecteur.|
|[pop_back](#pop_back)|Supprime l'élément à la fin du vecteur.|
|[push_back](#push_back)|Ajoute un élément à la fin du vecteur.|
|[rbegin](#rbegin)|Retourne un itérateur pointant vers le premier élément d'un vecteur inverse.|
|[rend](#rend)|Retourne un itérateur qui pointe vers la fin d'un vecteur inversé.|
|[reserve](#reserve)|Réserve une taille de stockage minimale pour un vecteur.|
|[resize](#resize)|Spécifie une nouvelle taille pour un vecteur.|
|[shrink_to_fit](#shrink_to_fit)|Ignore la capacité excédentaire.|
|[size](#size)|Retourne le nombre d'éléments figurant dans le vecteur.|
|[swap](#swap)|Échange les éléments de deux vecteurs.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator&#91;&#93;](#op_at)|Retourne une référence à l'élément de vecteur à un emplacement spécifié.|
|[operator=](#op_eq)|Remplace les éléments du vecteur par une copie d'un autre vecteur.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<vector>

**Espace de noms :** std

## <a name="allocator_type"></a>  vector::allocator_type

Type représentant la classe allocator pour l'objet vecteur.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Notes

`allocator_type` est un synonyme du paramètre de modèle `Allocator`.

### <a name="example"></a>Exemple

Consultez l’exemple de [get_allocator](#get_allocator) pour obtenir un exemple qui utilise `allocator_type`.

## <a name="assign"></a>  vector::assign

Efface un tableau et copie les éléments spécifiés dans le vecteur vide.

```cpp
void assign(size_type Count, const Type& Val);
void assign(initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Paramètres

*Premier*<br/>
Position du premier élément dans la plage d'éléments à copier.

*Dernière*<br/>
Position du premier élément suivant la fin de la plage d'éléments à copier.

*Nombre*<br/>
Nombre de copies d'un élément inséré dans le vecteur.

*Val*<br/>
Valeur de l'élément inséré dans le vecteur.

*IList*<br/>
initializer_list qui contient les éléments à insérer.

### <a name="remarks"></a>Notes

Après avoir supprimé les éléments existants dans un vecteur, assign insère la plage d'éléments spécifiée du vecteur d'origine dans un vecteur, ou insère des copies d'un nouvel élément ayant la valeur spécifiée dans un vecteur.

### <a name="example"></a>Exemple

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}

```

## <a name="at"></a>  vector::at

Retourne une référence à l'élément à un emplacement spécifié dans le vecteur.

```cpp
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```

### <a name="parameters"></a>Paramètres

*_Pos*<br/>
Valeur de l'indice ou de la position de l'élément à référencer dans le vecteur.

### <a name="return-value"></a>Valeur de retour

Référence à l’élément en indice dans l’argument. Si `_Off` est supérieure à la taille du vecteur, `at` lève une exception.

### <a name="remarks"></a>Notes

Si la valeur de retour de `at` est assignée à `const_reference`, il est impossible de modifier l'objet de vecteur. Si la valeur de retour de `at` est assignée à `reference`, l’objet vector peut être modifié.

### <a name="example"></a>Exemple

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>  vector::back

Retourne une référence au dernier élément du vecteur.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Valeur de retour

Dernier élément du vecteur. Si le vecteur est vide, la valeur de retour n'est pas définie.

### <a name="remarks"></a>Notes

Si la valeur de retour de `back` est assignée à `const_reference`, il est impossible de modifier l'objet de vecteur. Si la valeur de retour de `back` est assignée à `reference`, l’objet vector peut être modifié.

En cas de compilation avec [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous essayez d’accéder à un élément dans un vecteur vide.  Pour plus d'informations, voir [Checked Iterators](../standard-library/checked-iterators.md) .

### <a name="example"></a>Exemple

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a>  vector::begin

Retourne un itérateur à accès aléatoire pointant vers le premier élément dans le vecteur.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur à accès aléatoire qui traite le premier élément dans l’objet `vector` ou l’emplacement suivant un objet `vector` vide. Vous devez toujours comparer la valeur retournée avec [vector::end](#end) pour vous assurer de sa validité.

### <a name="remarks"></a>Notes

Si la valeur de retour de `begin` est assignée à [vector::const_iterator](#const_iterator), l’objet `vector` ne peut pas être modifié. Si la valeur de retour de `begin` est assignée à [vector::iterator](#iterator), l’objet `vector` peut être modifié.

### <a name="example"></a>Exemple

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
    *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a>  vector::capacity

Retourne le nombre d'éléments que le vecteur peut contenir sans avoir à allouer plus de stockage.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur actuelle du stockage alloué pour le vecteur.

### <a name="remarks"></a>Notes

La fonction membre [resize](#resize) sera plus efficace si une mémoire suffisante est allouée pour répondre à ses besoins. Utilisez la fonction membre [reserve](#reserve) pour spécifier la quantité de mémoire allouée.

### <a name="example"></a>Exemple

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a>  vector::cbegin

Retourne un **const** itérateur qui traite le premier élément dans la plage.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Un **const** itérateur à accès aléatoire qui pointe vers le premier élément de la plage ou l’emplacement juste après la fin d’une plage vide (pour une plage vide, `cbegin() == cend()`).

### <a name="remarks"></a>Notes

Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez `Container` à être modifiable (non - **const**) conteneur quelconque qui prend en charge `begin()` et `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  vector::cend

Retourne un **const** itérateur qui traite l’emplacement juste après le dernier élément dans une plage.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

Un **const** itérateur à accès aléatoire qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Notes

`cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez `Container` à être modifiable (non - **const**) conteneur quelconque qui prend en charge `end()` et `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="clear"></a>  vector::clear

Supprime les éléments du vecteur.

```cpp
void clear();
```

### <a name="example"></a>Exemple

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a>  vector::const_iterator

Type qui fournit un itérateur à accès aléatoire qui peut lire un élément **const** dans un vecteur.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_iterator` ne peut pas être utilisé pour changer la valeur d'un élément.

### <a name="example"></a>Exemple

Consultez l’exemple [back](#back) illustrant l’utilisation de `const_iterator`.

## <a name="const_pointer"></a>  vector::const_pointer

Type qui fournit un pointeur vers un élément **const** dans un vecteur.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Notes

Un type `const_pointer` ne peut pas être utilisé pour changer la valeur d'un élément.

Un [itérateur](#iterator) est généralement utilisé pour fournir un accès à un élément de vecteur.

## <a name="const_reference"></a>  vector::const_reference

Type qui fournit une référence à un élément **const** stocké dans un vecteur pour la lecture et l’exécution des opérations **const**.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Notes

Un type `const_reference` ne peut pas être utilisé pour changer la valeur d'un élément.

### <a name="example"></a>Exemple

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>  vector::const_reverse_iterator

Type qui fournit un itérateur d’accès aléatoire pouvant lire tout élément **const** dans le vecteur.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_reverse_iterator` ne peut pas modifier la valeur d’un élément. Il sert à itérer au sein du vecteur dans l’ordre inverse.

### <a name="example"></a>Exemple

Consultez [rbegin](#rbegin) pour obtenir un exemple montrant comment déclarer et utiliser un itérateur.

## <a name="crbegin"></a>  vector::crbegin

Retourne un itérateur const qui pointe vers le premier élément d'un vecteur inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Un itérateur const inverse à accès aléatoire qui traite le premier élément d’un objet [vector](../standard-library/vector-class.md) inversé (ou qui traite ce qui était le dernier élément de l’objet `vector` non inversé).

### <a name="remarks"></a>Notes

Avec la valeur de retour `crbegin`, l'objet `vector` ne peut pas être changé.

### <a name="example"></a>Exemple

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a>  vector::crend

Retourne un itérateur const qui traite l’emplacement qui suit le dernier élément d’un vecteur inversé.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur const inverse à accès aléatoire qui traite l’emplacement qui suit le dernier élément d’un objet [vector](../standard-library/vector-class.md) inversé (emplacement qui précédait le premier élément dans l’objet `vector` non inversé).

### <a name="remarks"></a>Notes

`crend` est utilisé avec un objet `vector` inversé comme [vector::cend](#cend) est utilisé avec un objet `vector`.

Avec la valeur de retour de `crend` (convenablement décrémentée), l’objet `vector` ne peut pas être modifié.

`crend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de son objet `vector`.

La valeur retournée par `crend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

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

## <a name="data"></a>  vector::data

Retourne un pointeur vers le premier élément du vecteur.

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le premier élément de l’objet [vector](../standard-library/vector-class.md) ou vers l’emplacement suivant un objet `vector` vide.

### <a name="example"></a>Exemple

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1 ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1 ptr = c1.data();
    *c1 ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1 ptr++)
    {
        cout << " " << *c1 ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a>  vector::difference_type

Type qui fournit la différence entre deux itérateurs qui font référence aux éléments d'un même vecteur.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Notes

Un `difference_type` peut également être décrit comme le nombre d’éléments entre deux pointeurs, car un pointeur vers un élément contient son adresse.

Un [itérateur](#iterator) est généralement utilisé pour fournir un accès à un élément de vecteur.

### <a name="example"></a>Exemple

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

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

## <a name="emplace"></a>  vector::emplace

Insère un élément construit sur place à la position spécifiée dans le vecteur.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*_WHERE*|Position dans l’objet [vector](../standard-library/vector-class.md) où le premier élément est inséré.|
|*Val*|Valeur de l'élément inséré dans le `vector`.|

### <a name="return-value"></a>Valeur de retour

La fonction retourne un itérateur qui pointe vers la position où le nouvel élément a été inséré dans le `vector`.

### <a name="remarks"></a>Notes

Toute opération d’insertion peut s’avérer coûteuse. Consultez [vector, classe](../standard-library/vector-class.md) pour en savoir plus sur les performances de `vector`.

### <a name="example"></a>Exemple

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

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

## <a name="emplace_back"></a>  vector::emplace_back

Ajoute un élément construit sur place à la fin du vecteur.

```cpp
template <class... Types>
void emplace_back(Types&&... _Args);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Args*|Arguments de constructeur. Selon les arguments fournis, la fonction déduit la surcharge de constructeur à appeler.|

### <a name="example"></a>Exemple

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}

```

## <a name="empty"></a>  vector::empty

Teste si le vecteur est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le vecteur est vide ; **false** si le vecteur n’est pas vide.

### <a name="example"></a>Exemple

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a>  vector::end

Retourne l'itérateur past-the-end.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur past-the-end du vecteur. Si le vecteur est vide, `vector::end() == vector::begin()`.

### <a name="remarks"></a>Notes

Si la valeur de retour de `end` est affectée à une variable de type `const_iterator`, l’objet vector ne peut pas être modifié. Si la valeur de retour de `end` est affectée à une variable de type `iterator`, l’objet vector peut être modifié.

### <a name="example"></a>Exemple

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a>  vector::erase

Supprime un élément ou une plage d'éléments aux positions spécifiées dans le vecteur.

```cpp
iterator erase(
    const_iterator _Where);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*_WHERE*|Position de l'élément à supprimer du vecteur.|
|*first*|Position du premier élément supprimé du vecteur.|
|*last*|Position juste après le dernier élément supprimé du vecteur.|

### <a name="return-value"></a>Valeur de retour

Itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou pointeur vers la fin du vecteur si aucun élément de ce genre n'existe.

### <a name="example"></a>Exemple

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a>  vector::front

Retourne une référence au premier élément du vecteur.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Valeur de retour

Référence au premier élément du vecteur. Si le vecteur est vide, la valeur de retour n'est pas définie.

### <a name="remarks"></a>Notes

Si la valeur de retour de `front` est assignée à `const_reference`, il est impossible de modifier l'objet de vecteur. Si la valeur de retour de `front` est assignée à un objet **reference**, l’objet vector peut être modifié.

En cas de compilation avec [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous essayez d’accéder à un élément dans un vecteur vide.  Pour plus d'informations, voir [Checked Iterators](../standard-library/checked-iterators.md) .

### <a name="example"></a>Exemple

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a>  vector::get_allocator

Retourne une copie de l’objet allocateur utilisé pour construire le vecteur.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Allocateur utilisé par le vecteur.

### <a name="remarks"></a>Notes

Les allocateurs de la classe vector spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de la bibliothèque standard C++ suffisent à satisfaire la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a>  vector::insert

Insère un élément, un certain nombre d'éléments ou une plage d'éléments à la position spécifiée dans le vecteur.

```cpp
iterator insert(
    const_iterator _Where,
    const Type& val);

iterator insert(
    const_iterator _Where,
    Type&& val);

void insert(
    const_iterator _Where,
    size_type count,
    const Type& val);

template <class InputIterator>
void insert(
    const_iterator _Where,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*_WHERE*|Position dans le vecteur où le premier élément est inséré.|
|*Val*|Valeur de l'élément inséré dans le vecteur.|
|*count*|Nombre d'éléments insérés dans le vecteur.|
|*first*|Position du premier élément de la plage d'éléments à copier.|
|*last*|Position du premier élément au-delà de la plage d'éléments à copier.|

### <a name="return-value"></a>Valeur de retour

Les deux premières fonctions `insert` retournent un itérateur qui pointe vers la position où le nouvel élément a été inséré dans le vecteur.

### <a name="remarks"></a>Notes

Comme condition préalable, *première* et *dernière* ne doit pas être itérateurs dans le vecteur, ou le comportement est indéfini. Toute opération d’insertion peut s’avérer coûteuse. Consultez [vector, classe](../standard-library/vector-class.md) pour en savoir plus sur les performances de `vector`.

### <a name="example"></a>Exemple

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( )+1, v1.begin( )+2, v1.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      vector < vector <int> >::iterator Iter;
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a>  vector::iterator

Type qui fournit un itérateur à accès aléatoire pour lire ou modifier un élément dans un vecteur.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Notes

Vous pouvez utiliser un type **iterator** pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Consultez l’exemple de [begin](#begin).

## <a name="max_size"></a>  vector::max_size

Retourne la longueur maximale autorisée du vecteur.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur maximale autorisée du vecteur.

### <a name="example"></a>Exemple

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="op_at"></a>  vector::operator[]

Retourne une référence à l'élément de vecteur à un emplacement spécifié.

```cpp
reference operator[](size_type Pos);

const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*points de vente*|Position de l'élément de vecteur.|

### <a name="return-value"></a>Valeur de retour

Si la position spécifiée est supérieure ou égale à la taille du conteneur, le résultat est non défini.

### <a name="remarks"></a>Notes

Si la valeur de retour de `operator[]` est assignée à `const_reference`, il est impossible de modifier l'objet de vecteur. Si la valeur de retour de `operator[]` est assignée à une référence, l'objet de vecteur peut être modifié.

En cas de compilation avec [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous essayez d’accéder à un élément en dehors des limites du vecteur.  Pour plus d'informations, voir [Checked Iterators](../standard-library/checked-iterators.md) .

### <a name="example"></a>Exemple

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="op_eq"></a>  vector::operator=

Remplace les éléments du vecteur par une copie d'un autre vecteur.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*right*|L’objet [vector](../standard-library/vector-class.md) copié dans `vector`.|

### <a name="remarks"></a>Notes

Après avoir supprimé les éléments existants dans un `vector`, `operator=` copie ou déplace le contenu de *droit* dans le `vector`.

### <a name="example"></a>Exemple

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  vector::pointer

Type qui fournit un pointeur vers un élément d'un vecteur.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Notes

Un type **pointer** peut être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
    using namespace std;
    vector<int> v;
    v.push_back( 11 );
    v.push_back( 22 );

    vector<int>::pointer ptr = &v[0];
    cout << *ptr << endl;
    ptr++;
    cout << *ptr << endl;
    *ptr = 44;
    cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a>  vector::pop_back

Supprime l'élément à la fin du vecteur.

```cpp
void pop_back();
```

### <a name="remarks"></a>Notes

Pour obtenir un exemple de code, consultez [vector::push_back()](#push_back).

## <a name="push_back"></a>  vector::push_back

Ajoute un élément à la fin du vecteur.

```cpp
void push_back(const T& Val);

void push_back(T&& Val);
```

### <a name="parameters"></a>Paramètres

*Val*<br/>
Valeur à affecter à l'élément ajouté à la fin du vecteur.

### <a name="example"></a>Exemple

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a>  vector::rbegin

Retourne un itérateur pointant vers le premier élément d'un vecteur inverse.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Un itérateur inverse à accès aléatoire qui traite le premier élément d’un vecteur inversé (ou qui traite ce qui était le dernier élément du vecteur non inversé).

### <a name="remarks"></a>Notes

Si la valeur de retour de `rbegin` est assignée à `const_reverse_iterator`, il est impossible de modifier l'objet de vecteur. Si la valeur de retour de `rbegin` est assignée à `reverse_iterator`, l’objet vector peut être modifié.

### <a name="example"></a>Exemple

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a>  vector::reference

Type qui fournit une référence à un élément stocké dans un vecteur.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Exemple

Consultez [at](#at) pour obtenir un exemple d’utilisation de **reference** dans la classe vector.

## <a name="rend"></a>  vector::rend

Retourne un itérateur qui traite l’emplacement suivant le dernier élément d’un vecteur inversé.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Valeur de retour

Itérateur inverse à accès aléatoire qui traite l’emplacement qui suit le dernier élément d’un vecteur inversé (emplacement qui précédait le premier élément dans le vecteur non inversé).

### <a name="remarks"></a>Notes

`rend` est utilisé avec un vecteur inversé tout comme [end](#end) est utilisé avec un vecteur.

Si la valeur de retour de `rend` est assignée à `const_reverse_iterator`, l’objet vector ne peut pas être modifié. Si la valeur de retour de `rend` est assignée à `reverse_iterator`, l’objet vector peut être modifié.

`rend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de son tableau.

La valeur retournée par `rend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

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

## <a name="reserve"></a>  vector::reserve

Réserve une taille de stockage minimale pour un vecteur, en allouant plus d'espace si nécessaire.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>Paramètres

*count*<br/>
Taille de stockage minimale à allouer pour le vecteur.

### <a name="example"></a>Exemple

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a>  vector::resize

Spécifie une nouvelle taille pour un vecteur.

```cpp
void resize(size_type Newsize);
void resize(size_type Newsize, Type Val);
```

### <a name="parameters"></a>Paramètres

*NewSize*<br/>
Nouvelle taille du vecteur.

*Val*<br/>
Valeur d'initialisation des nouveaux éléments ajoutés au vecteur si la nouvelle taille est supérieure à la taille d'origine. Si la valeur est omise, les nouveaux objets utilisent leur constructeur par défaut.

### <a name="remarks"></a>Notes

Si la taille du conteneur est inférieure à la taille demandée, *Newsize*, éléments sont ajoutés au vecteur jusqu'à ce qu’il atteigne la taille demandée. Si la taille du conteneur est supérieure à la taille demandée, les éléments le plus proche de la fin du conteneur sont supprimés jusqu'à ce que le conteneur atteigne la taille *Newsize*. Si la taille actuelle du conteneur est égale à la taille demandée, aucune action n'est effectuée.

[size](#size) reflète la taille actuelle du vecteur.

### <a name="example"></a>Exemple

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

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

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a>  vector::reverse_iterator

Type qui fournit un itérateur à accès aléatoire pouvant lire ou modifier un élément d'un vecteur inversé.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `reverse_iterator` est utilisé pour itérer le vecteur dans l'ordre inverse.

### <a name="example"></a>Exemple

Consultez l’exemple de [rbegin](#rbegin).

## <a name="shrink_to_fit"></a>  vector::shrink_to_fit

Ignore la capacité excédentaire.

```cpp
void shrink_to_fit();
```

### <a name="example"></a>Exemple

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a>  vector::size

Retourne le nombre d'éléments figurant dans le vecteur.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur actuelle du vecteur.

### <a name="example"></a>Exemple

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a>  vector::size_type

Type qui compte le nombre d'éléments dans un vecteur.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [capacity](#capacity).

## <a name="swap"></a>  vector::swap

Échange les éléments de deux vecteurs.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Un vecteur qui fournit les éléments à échanger ou un vecteur dont les éléments doivent être échangés avec ceux du vecteur *gauche*.

*left*<br/>
Un vecteur dont les éléments doivent être échangés avec ceux du vecteur *droit*.

### <a name="example"></a>Exemple

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a>  vector::value_type

Type représentant le type de données stockées dans un vecteur.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Notes

`value_type` est un synonyme du paramètre de modèle `Type`.

### <a name="example"></a>Exemple

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a>  vector::vector

Construit un vecteur de taille spécifique ou contenant des éléments de valeurs spécifiques, ou contenant un allocateur spécifique, ou comme copie complète ou partielle d'un autre vecteur.

```cpp
vector();
explicit vector(const Allocator& Al);
explicit vector(size_type Count);
vector(size_type Count, const Type& Val);
vector(size_type Count, const Type& Val, const Allocator& Al);

vector(const vector& Right);
vector(vector&& Right);
vector(initializer_list<Type> IList, const _Allocator& Al);

template <class InputIterator>
vector(InputIterator First, InputIterator Last);
template <class InputIterator>
vector(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Al*|Classe allocator à utiliser avec cet objet. [get_allocator](#get_allocator) retourne la classe allocator de l’objet.|
|*Nombre*|Nombre d'éléments figurant dans le vecteur construit.|
|*Val*|Valeur des éléments contenus dans le vecteur construit.|
|*Droite*|Vecteur dont le vecteur construit doit être une copie.|
|*Premier*|Position du premier élément dans la plage d'éléments à copier.|
|*Dernière*|Position du premier élément suivant la fin de la plage d'éléments à copier.|
|*IList*|Objet initializer_list contenant les éléments à copier.|

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet allocateur (*Al*) et initialisent le vecteur.

Les deux premiers constructeurs spécifient un vecteur initial vide. Le deuxième spécifie explicitement le type d’allocateur (*Al*) à utiliser.

Le troisième constructeur spécifie une répétition d’un nombre spécifié (*nombre*) d’éléments de la valeur par défaut pour la classe `Type`.

Les quatrième et cinquième constructeurs spécifient une répétition des (*nombre*) éléments ayant la valeur *Val*.

Le sixième constructeur spécifie une copie du vecteur *droite*.

Le septième constructeur déplace le vecteur *droite*.

Le huitième constructeur utilise initializer_list pour spécifier les éléments.

Les neuvième et dixième constructeurs copient la plage [ `First`, `Last`) du vecteur.

### <a name="example"></a>Exemple

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}

```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
