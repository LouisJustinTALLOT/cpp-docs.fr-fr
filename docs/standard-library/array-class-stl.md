---
title: array, classe (Bibliothèque C++ Standard)| Microsoft Docs
ms.date: 11/13/2019
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
ms.openlocfilehash: a6cda0f0c66624158f7c2abfeabb5f54678d21b0
ms.sourcegitcommit: 7b12cc4a4d3fcb261d67420fc3dd18652730008f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82643641"
---
# <a name="array-class-c-standard-library"></a>array, classe (Bibliothèque C++ standard)

Décrit un objet qui contrôle une séquence de longueur `N` constituée d'éléments de type `Ty`. La séquence est stockée comme tableau de `Ty`, contenu dans l'objet `array<Ty, N>`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|`Ty`|Type d’un élément.|
|`N`|Nombre d'éléments.|

## <a name="members"></a>Membres

|Définition de types|Description|
|-|-|
|[const_iterator](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|
|[const_pointer](#const_pointer)|Type d'un pointeur constant vers un élément.|
|[const_reference](#const_reference)|Type d'une référence constante à un élément.|
|[const_reverse_iterator](#const_reverse_iterator)|Type d'un itérateur inserve constant pour la séquence contrôlée.|
|[difference_type](#difference_type)|Type d'une distance signée entre deux éléments.|
|[répétiteur](#iterator)|Type d'un itérateur pour la séquence contrôlée.|
|[pointeur](#pointer)|Type d'un pointeur vers un élément.|
|[reference](#reference)|Type d'une référence à un élément.|
|[reverse_iterator](#reverse_iterator)|Type d'un itérateur inverse pour la séquence contrôlée.|
|[size_type](#size_type)|Type d'une distance non signée entre deux éléments.|
|[value_type](#value_type)|Type d’un élément.|

|Fonction membre|Description|
|-|-|
|[array](#array)|Construit un objet tableau.|
|[assign](#assign)|Périmé. Utilisez `fill`.) Remplace tous les éléments.|
|[at](#at)|Accède à un élément à une position spécifiée.|
|[Précédent](#back)|Accède au dernier élément.|
|[commencer](#begin)|Désigne le début de la séquence contrôlée.|
|[cbegin](#cbegin)|Retourne un itérateur const à accès aléatoire pointant vers le premier élément du tableau.|
|[cend](#cend)|Retourne un itérateur à accès aléatoire qui pointe juste après la fin du tableau.|
|[crbegin](#crbegin)|Retourne un itérateur const qui traite le premier élément d'un tableau inversé.|
|[crend](#crend)|Retourne un itérateur const qui pointe vers la fin d'un tableau inversé.|
|[data](#data)|Obtient l'adresse du premier élément.|
|[empty](#empty)|Vérifie la présence d'éléments.|
|[end](#end)|Désigne la fin de la séquence contrôlée.|
|[complète](#fill)|Remplace tous les éléments par une valeur spécifiée.|
|[frontal](#front)|Accède au premier élément.|
|[max_size](#max_size)|Compte le nombre d'éléments.|
|[rbegin](#rbegin)|Désigne le début de la séquence contrôlée inverse.|
|[rend](#rend)|Désigne la fin de la séquence contrôlée inverse.|
|[size](#size)|Compte le nombre d'éléments.|
|[swap](#swap)|Échange le contenu de deux conteneurs.|

|Opérateur|Description|
|-|-|
|[Array :: Operator =](#op_eq)|Remplace la séquence contrôlée.|
|[Array ::, opérateur\[\]](#op_at)|Accède à un élément à une position spécifiée.|

## <a name="remarks"></a>Notes 

Le type a un constructeur par défaut `array()` et un opérateur d'assignation par défaut `operator=`, et il satisfait aux conditions requises pour un `aggregate`. Par conséquent, les objets de type `array<Ty, N>` peuvent être initialisés à l'aide d'un initialiseur d'agrégat. Par exemple,

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

crée l'objet `ai` qui contient quatre valeurs entières, initialise les trois premiers éléments respectivement aux valeurs 1, 2 et 3, et initialise le quatrième élément à la valeur 0.

## <a name="requirements"></a>Spécifications

**En-tête :** \<array>

**Espace de noms :** std

## <a name="arrayarray"></a><a name="array"></a>Tableau :: tableau

Construit un objet tableau.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet ou plage à insérer.

### <a name="remarks"></a>Notes 

Le constructeur par défaut `array()` laisse la séquence contrôlée non initialisée (ou initialisée par défaut). Vous l’utilisez pour spécifier une séquence contrôlée non initialisée.

`array(const array& right)` Le constructeur de copie initialise la séquence contrôlée avec la séquence [*Right*`.begin()`, *Right*`.end()`). Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet tableau *right*.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    typedef std::array<int, 4> Myarray;

    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1(c0);

    // display contents " 0 1 2 3"
    for (const auto& it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arrayassign"></a><a name="assign"></a>Tableau :: assign

Obsolète dans C++11, remplacé par [fill](#fill). Remplace tous les éléments.

## <a name="arrayat"></a><a name="at"></a>Array :: at

Accède à un élément à une position spécifiée.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Paramètres

*préférable*\
Position de l'élément auquel accéder.

### <a name="remarks"></a>Notes 

Les fonctions membres retournent une référence à l’élément de la séquence contrôlée à la position *off*. Si cet emplacement n'est pas valide, la fonction lève un objet de classe `out_of_range`.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
}
```

## <a name="arrayback"></a><a name="back"></a>Tableau :: précédent

Accède au dernier élément.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Notes 

Les fonctions membres retournent une référence au dernier élément de la séquence contrôlée qui ne doit pas être vide.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraybegin"></a><a name="begin"></a>Tableau :: Begin

Désigne le début de la séquence contrôlée.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Notes 

Les fonctions membres retournent un itérateur d'accès aléatoire qui pointe vers le premier élément de la séquence (ou juste après la fin d'une séquence vide).

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arraycbegin"></a><a name="cbegin"></a>Tableau :: cbegin

Retourne un itérateur **const** qui traite le premier élément de la plage.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur **const** à accès aléatoire qui pointe vers le premier élément de la plage, ou vers l’emplacement situé juste après la fin d’une plage vide (pour une plage vide `cbegin() == cend()`,).

### <a name="remarks"></a>Notes 

Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. `Container` Dans l’exemple, considérez qu’il s’agit d’un conteneur modifiable (non **const**) de tout `begin()` type `cbegin()`qui prend en charge et.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="arraycend"></a><a name="cend"></a>Tableau :: CEND

Retourne un itérateur **const** qui traite l’emplacement juste après le dernier élément d’une plage.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur d'accès aléatoire qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Notes 

`cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. `Container` Dans l’exemple, considérez qu’il s’agit d’un conteneur modifiable (non **const**) de tout `end()` type `cend()`qui prend en charge et.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="arrayconst_iterator"></a><a name="const_iterator"></a>Tableau :: const_iterator

Type d'un itérateur constant pour la séquence contrôlée.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Notes 

Le type décrit un objet pouvant servir d’itérateur d’accès aléatoire constant pour la séquence contrôlée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::const_iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="arrayconst_pointer"></a><a name="const_pointer"></a>Tableau :: const_pointer

Type d'un pointeur constant vers un élément.

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Notes 

Le type décrit un objet pouvant servir de pointeur constant vers des éléments de la séquence.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayconst_reference"></a><a name="const_reference"></a>Tableau :: const_reference

Type d'une référence constante à un élément.

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Notes 

Le type décrit un objet pouvant servir de référence constante à un élément de la séquence contrôlée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>Tableau :: const_reverse_iterator

Type d'un itérateur inserve constant pour la séquence contrôlée.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Notes 

Le type décrit un objet pouvant servir d’itérateur inverse constant pour la séquence contrôlée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraycrbegin"></a><a name="crbegin"></a>Tableau :: crbegin

Retourne un itérateur const qui traite le premier élément d'un tableau inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur à accès aléatoire inversé const qui traite le premier élément d'un tableau inversé (ou qui traite ce qui était le dernier élément du tableau non inversé).

### <a name="remarks"></a>Notes 

Avec la valeur de retour `crbegin`, l'objet de tableau ne peut pas être changé.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="arraycrend"></a><a name="crend"></a>Tableau :: crend

Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un tableau inversé.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur d'accès aléatoire inversé const qui traite l'emplacement qui suit le dernier élément d'un tableau inversé (emplacement qui précédait le premier élément dans le tableau non inversé).

### <a name="remarks"></a>Notes 

`crend` est utilisé avec un tableau inversé de la même manière que [array::cend](#cend) est utilisé avec un tableau.

Avec la valeur de retour de `crend` (convenablement décrémentée), l'objet de tableau ne peut pas être modifié.

`crend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de son tableau.

La valeur retournée par `crend` ne doit pas être déréférencée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="arraydata"></a><a name="data"></a>Tableau ::d ATA

Obtient l'adresse du premier élément.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Notes 

Les fonctions membres retournent l’adresse du premier élément de la séquence contrôlée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arraydifference_type"></a><a name="difference_type"></a>Tableau ::d ifference_type

Type d'une distance signée entre deux éléments.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Notes 

Le type d'entier signé décrit un objet qui peut représenter la différence entre les adresses de deux éléments quelconques dans la séquence contrôlée. Il est synonyme du type `std::ptrdiff_t`.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
-4
```

## <a name="arrayempty"></a><a name="empty"></a>Tableau :: Empty

Vérifie l'absence d'éléments.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Notes 

La fonction membre retourne true uniquement si `N == 0`.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

    // display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
false
true
```

## <a name="arrayend"></a><a name="end"></a>Tableau :: fin

Désigne la fin de la séquence contrôlée.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Notes 

Les fonctions membres retournent un itérateur d'accès aléatoire qui pointe juste après la fin de la séquence.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arrayfill"></a><a name="fill"></a>Tableau :: remplissage

Efface un tableau et copie les éléments spécifiés dans le tableau vide.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*multiples*|Valeur de l'élément inséré dans le tableau.|

### <a name="remarks"></a>Notes 

`fill` remplace chaque élément du tableau par la valeur spécifiée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

int main()
{
    using namespace std;
    array<int, 2> v1 = { 1, 2 };

    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;

    v1.fill(3);
    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;
}
```

## <a name="arrayfront"></a><a name="front"></a>Array :: front

Accède au premier élément.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Notes 

Les fonctions membres retournent une référence au premier élément de la séquence contrôlée qui ne doit pas être vide.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayiterator"></a><a name="iterator"></a>Tableau :: Iterator

Type d'un itérateur pour la séquence contrôlée.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Notes 

Le type décrit un objet pouvant servir d'itérateur à accès aléatoire pour la séquence contrôlée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3

it2: 0
```

## <a name="arraymax_size"></a><a name="max_size"></a>Tableau :: max_size

Compte le nombre d'éléments.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Notes 

La fonction membre retourne `N`.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arrayoperator"></a><a name="op_at"></a>Array :: Operator []

Accède à un élément à une position spécifiée.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Paramètres

*préférable*\
Position de l'élément auquel accéder.

### <a name="remarks"></a>Notes 

Les fonctions membres retournent une référence à l’élément de la séquence contrôlée à la position *off*. Si cette position n'est pas valide, le comportement est indéfini.

Une fonction d' [extraction](array-functions.md#get) non membre est également disponible pour obtenir une référence à un élément d’un **tableau**.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
1 3
```

## <a name="arrayoperator"></a><a name="op_eq"></a>Array :: Operator =

Remplace la séquence contrôlée.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Conteneur à copier.

### <a name="remarks"></a>Notes 

L’opérateur membre assigne chaque élément de *droite* à l’élément correspondant de la séquence contrôlée, puis retourne `*this`. Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *Right*.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

    // display copied contents " 0 1 2 3"
        // display contents " 0 1 2 3"
    for (auto it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arraypointer"></a><a name="pointer"></a>Tableau ::p ointer

Type d'un pointeur vers un élément.

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Notes 

Le type décrit un objet pouvant servir de pointeur vers des éléments de la séquence.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayrbegin"></a><a name="rbegin"></a>Tableau :: rbegin

Désigne le début de la séquence contrôlée inverse.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Notes 

Les fonctions membres retournent un itérateur inverse qui pointe juste après la fin de la séquence contrôlée. Par conséquent, il désigne le début de la séquence inverse.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arrayreference"></a><a name="reference"></a>Array :: Reference

Type d'une référence à un élément.

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Notes 

Le type décrit un objet qui peut servir de référence à un élément de la séquence contrôlée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayrend"></a><a name="rend"></a>Tableau :: rend

Désigne la fin de la séquence contrôlée inverse.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Notes 

Les fonctions membres retournent un itérateur inverse qui pointe vers le premier élément de la séquence (ou juste après la fin d'une séquence vide). Par conséquent, il désigne la fin de la séquence inverse.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayreverse_iterator"></a><a name="reverse_iterator"></a>Tableau :: reverse_iterator

Type d'un itérateur inverse pour la séquence contrôlée.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Notes 

Le type décrit un objet pouvant servir d’itérateur inverse pour la séquence contrôlée.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraysize"></a><a name="size"></a>Array :: Size

Compte le nombre d'éléments.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Notes 

La fonction membre retourne `N`.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arraysize_type"></a><a name="size_type"></a>Tableau :: size_type

Type d’une distance non signée entre deux éléments.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Notes 

Le type d'entier non signé décrit un objet qui peut représenter la longueur de n'importe quelle séquence contrôlée. Il est synonyme du type `std::size_t`.

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arrayswap"></a><a name="swap"></a>Array :: swap

Échange le contenu de ce tableau avec un autre tableau.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Tableau avec lequel échanger le contenu.

### <a name="remarks"></a>Notes 

La fonction membre échange les séquences contrôlées entre `*this` et *Right*. Il effectue un nombre d’assignations d’élément et d’appels de constructeur proportionnel à `N`.

Une fonction d' [échange](array-functions.md#swap) non membre est également disponible pour échanger deux instances de **tableau** .

### <a name="example"></a> Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="arrayvalue_type"></a><a name="value_type"></a>Tableau :: value_type

Type d’un élément.

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Notes 

Le type est un synonyme du paramètre de modèle `Ty`.

### <a name="example"></a>Exemple

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        Myarray::value_type val = it;
        std::cout << " " << val;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>Voir aussi

[\<Tableau>](../standard-library/array.md)
