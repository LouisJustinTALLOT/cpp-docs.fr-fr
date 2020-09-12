---
title: span, classe (bibliothèque standard C++) | Microsoft Docs
description: Référence d’API pour la classe d’étendue STL (Standard Template Library), qui fournit une vue légère sur une séquence contiguë d’objets.
ms.date: 05/28/2020
f1_keywords:
- span/std::span
- span/std::span::const_pointer
- span/std::span::const_reference
- span/std::span::difference_type
- span/std::span::element_type
- span/std::span::iterator
- span/std::span::pointer
- span/std::span::reference
- span/std::span::reverse_iterator
- span/std::span::size_type
- span/std::span::value_type
- span/std::span::at
- span/std::span::assign
- span/std::span::back
- span/std::span::begin
- span/std::span::data
- span/std::span::empty
- span/std::span::end
- span/std::span::front
- span/std::span::rbegin
- span/std::span::rend
- span/std::span::size
- span/std::span::size_bytes
- span/std::span::operator=
- span/std::span::operator[]
helpviewer_keywords:
- std::span [C++]
- std::span [C++], const_pointer
- std::span [C++], const_reference
- std::span [C++], difference_type
- std::span [C++], element_type
- std::span [C++], iterator
- std::span [C++], pointer
- std::span [C++], reference
- std::span [C++], reverse_iterator
- std::span [C++], size_type
- std::span [C++], value_type
- std::span [C++], assign
- std::span [C++], at
- std::span [C++], back
- std::span [C++], begin
- std::span [C++], data
- std::span [C++], empty
- std::span [C++], end
- std::span [C++], front
- std::span [C++], rbegin
- std::span [C++], rend
- std::span [C++], size
- std::span [C++], size_bytes
ms.openlocfilehash: 297104820f5498e59397db9025aed1675984a060
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039962"
---
# <a name="span-class-c-standard-library"></a>span, classe (bibliothèque standard C++)

Fournit une vue légère sur une séquence contiguë d’objets. Une étendue offre un moyen sûr d’effectuer des itérations et des index dans les objets qui sont réorganisés en mémoire, comme les objets stockés dans un tableau intégré, `std::array` ou `std::vector` .

Si vous accédez généralement à une séquence d’objets dos à dos à l’aide d’un pointeur et d’un index, a `span` est une alternative plus sûre et légère.

La taille d’un `span` peut être définie au moment de la compilation en le spécifiant comme argument de modèle, ou au moment de l’exécution en spécifiant `dynamic_extent` .

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, size_t Extent = dynamic_extent>
class span;
```

### <a name="template-parameters"></a>Paramètres de modèle

`T`\
 Type des éléments de l’étendue.

`Extent`\
 Nombre d’éléments dans l’étendue, s’ils sont spécifiés au moment de la compilation. Sinon,  `std::dynamic_extent` si le nombre d’éléments est spécifié au moment de l’exécution.

[Guide de déduction](#deduction_guides)

## <a name="members"></a>Membres

| **Définitions de types** | **Description** |
|-|-|
| [const_pointer](#pointer) | Type d’un pointeur vers un **`const`** élément. |
| [const_reference](#reference) | Type d’une référence à un **`const`** élément. |
| [difference_type](#difference_type) | Type d'une distance signée entre deux éléments. |
| [element_type](#element_type) | Type d’un élément span. |
| [répétiteur](#iterator) | Type d’un itérateur pour une étendue. |
| [dirigé](#pointer) | Type d'un pointeur vers un élément. |
| [reference](#reference) | Type d'une référence à un élément. |
| [reverse_iterator](#reverse_iterator) | Type d’un itérateur inverse pour une étendue. |
| [size_type](#size_type) | Type pour le résultat de la distance non signée entre deux éléments dans l’étendue. |
| [value_type](#value_type) | Type d’un élément, sans les **`const`** **`volatile`** qualifications. |
| **Constructeurs** | **Description** |
|[répartis](#span)| Construisez un `span`.|
| **Prise en charge des itérateurs** | **Description** |
|[commencer](#begin) | Obtient un itérateur pointant vers le premier élément de l’étendue.|
|[end](#end) | Obtient un itérateur pointant vers la fin de l’étendue. |
|[rbegin](#rbegin) | Obtient un itérateur inverse pointant vers le dernier élément de l’étendue. autrement dit, le début de l’étendue inversée.|
|[rend](#rend) | Obtient un itérateur inverse pointant vers le début de l’étendue. autrement dit, la fin de l’étendue inversée.|
| **Éléments d’accès**| **Description** |
|[Précédent](#back) | Obtient le dernier élément de l’étendue.|
|[data](#data) | Obtient l’adresse du premier élément de l’étendue.|
|[frontal](#front) | Obtient le premier élément de l’étendue.|
|[and\[\]](#op_at) | Accéder à un élément à une position spécifiée.|
| **Observateurs** | **Description** |
|[empty](#empty)| Teste si l’étendue est vide.|
|[size](#size) | Obtient le nombre d’éléments dans l’étendue.|
|[size_bytes](#size_bytes) | Obtient la taille de l’étendue en octets.|
| **Sous-affichages** | **Description**|
| [first](#first_view) | Obtient une sous-étendue à partir du début de l’étendue.|
| [last](#last_view) | Obtient une sous-étendue à partir de l’arrière de l’étendue.|
| [sous-étendue](#sub_view) | Obtient une sous-étendue à partir de n’importe où dans l’étendue.|
| **Opérateurs** | **Description** |
|[span :: Operator =](#op_eq)| Remplacez l’étendue.|
|[span ::, opérateur\[\]](#op_at)| Obtient l’élément à la position spécifiée. |

## <a name="remarks"></a>Remarques

Toutes les `span` fonctions membres ont une complexité constante du temps.

Contrairement `array` `vector` à ou, une étendue n’est pas « propriétaire » des éléments qu’elle contient. Une étendue ne libère pas de stockage pour les éléments qu’elle contient, car elle ne possède pas le stockage pour ces objets.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<span>

**Espace de noms :** std

**Option du compilateur :** [/std : c + + latest](../build/reference/std-specify-language-standard-version.md)

## <a name="spanback"></a><a name="back"></a> `span::back`

Obtient le dernier élément de l’étendue.

```cpp
constexpr reference back() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Référence au dernier élément de l’étendue.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << mySpan.back();
}
```

```Output
2
```

## <a name="spanbegin"></a><a name="begin"></a> `span::begin`

Obtient un itérateur pointant sur le premier élément de l’étendue.

```cpp
constexpr iterator begin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur pointant sur le premier élément de l’étendue.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.begin();
    cout << *i;
}
```

```Output
0
```

## <a name="spandata"></a><a name="data"></a> `span::data`

Obtient un pointeur vers le début des données de l’étendue.

```cpp
constexpr pointer data() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le premier élément stocké dans l’étendue.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    auto i = mySpan.data();
    cout << *i;
}
```

```Output
0
```

## <a name="spandifference_type"></a><a name="difference_type"></a> `span::difference_type`

Nombre d’éléments entre deux éléments dans une étendue.

```cpp
using difference_type = std::ptrdiff_t;
```

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::difference_type distance = mySpan.end() - mySpan.begin();
    cout << distance << std::endl;
}
```

```Output
3
```

## <a name="spanelement_type"></a><a name="element_type"></a> `span::element_type`

Type des éléments de l’étendue.

```cpp
using element_type = T;
```

### <a name="remarks"></a>Remarques

Le type est extrait du paramètre de modèle `T` lors de la création d’une étendue.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::element_type et = mySpan[2];
    cout << et << endl;
}
```

```Output
2
```

## <a name="spanempty"></a><a name="empty"></a> `span::empty`

Indique si l’étendue contient des éléments.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne **`true`** si `this->size() == 0` . Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    bool isEmpty = mySpan.empty(); // isEmpty == false
}
```

## <a name="spanend"></a><a name="end"></a> `span::end`

Obtient un itérateur à la fin de l’étendue.

```cpp
constexpr iterator end() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur pointant juste après la fin de l’étendue.

### <a name="remarks"></a>Remarques

`end` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.

Ne déréférencez pas la valeur retournée par cet itérateur. Utilisez-le pour déterminer si l’itérateur est parvenu au-delà du dernier élément de l’étendue.

### <a name="example"></a>Exemple

```cpp
// Iteration
for (auto it = s1.begin(); it != s1.end(); ++it)
{
    cout << *it;
}
```

## <a name="spanfirst"></a><a name="first_view"></a> `span::first`

Obtient une sous-étendue, prise de l’avant de cette étendue.

```cpp
constexpr auto first(size_type count) const noexcept;
template <size_t count> constexpr auto first() const noexcept;
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre d’éléments à partir de l’avant de cette étendue à placer dans la sous-étendue.  
Le nombre d’éléments est spécifié en tant que paramètre pour le modèle, ou à la fonction, comme illustré ci-dessous.

### <a name="return-value"></a>Valeur de retour

Étendue qui contient `count` les éléments de l’avant de cette étendue.

### <a name="remarks"></a>Remarques

Utilisez la version de modèle de cette fonction si possible pour valider le `count` au moment de la compilation et pour conserver des informations sur l’étendue, car elle retourne une plage d’étendue fixe.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.first(2);
    cout << "mySpan.first(2): ";
    for (auto& i : first2)
    {
        cout << i;
    }

    cout << "\nmySpan.first<2>: ";
    auto viewSpan = mySpan.first<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.first(2): 01
mySpan.first<2>: 01
```

## <a name="spanfront"></a><a name="front"></a> `span::front`

Obtient le premier élément de l’étendue.

```cpp
constexpr reference front() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Référence au premier élément de l’étendue.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.front();
    cout << i;
}
```

```Output
0
```

## <a name="spaniterator"></a><a name="iterator"></a> `span::iterator`

Type d’un itérateur sur des éléments span.

```cpp
using iterator = implementation-defined-iterator-type;
```

### <a name="remarks"></a>Remarques

Ce type sert d’itérateur sur les éléments d’une étendue.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::iterator it = mySpan.begin();
    cout << *it++ << *it++ << *it;
}
```

```Output
012
```

## <a name="spanlast"></a><a name="last_view"></a> `span::last`

Obtenez une sous-étendue, prise à partir de la fin de cette étendue.

```cpp
constexpr span<element_type, dynamic_extent> last(const size_type count) const noexcept;
template <size_t count> constexpr span<element_type, count> last() const noexcept;
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre d’éléments à partir de la fin de cette étendue à placer dans la sous-étendue.
Le nombre peut être spécifié comme paramètre pour le modèle ou pour la fonction, comme illustré ci-dessous.

### <a name="return-value"></a>Valeur de retour

Étendue contenant les derniers `count` éléments de cette étendue.

### <a name="remarks"></a>Remarques

Utilisez la version de modèle de cette fonction si possible pour valider le `count` au moment de la compilation et pour conserver des informations sur l’étendue, car elle retourne une plage d’étendue fixe.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.last(2);
    cout << "mySpan.last(2): ";
    for (auto& i : last2)
    {
        cout << i;
    }

    cout << "\nmySpan.last<2>: ";
    auto viewSpan = mySpan.last<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.last(2): 12
mySpan.last<2>: 12
```

## <a name="spanoperator"></a><a name="op_at"></a> `span::operator[]`

Obtient l’élément dans l’étendue à une position spécifiée.

```cpp
constexpr reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Paramètres

*décalage*\
Élément de base zéro dans l’étendue à laquelle accéder.

### <a name="return-value"></a>Valeur de retour

Référence à l’élément à l' *offset*de position. Si la position n’est pas valide, le comportement n’est pas défini.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan[1];
}
```

```Output
1
```

## <a name="spanoperator"></a><a name="op_eq"></a> `span::operator=`

Assignez une autre étendue à celle-ci.

```cpp
constexpr span& operator=(const span& other) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*autres*\
Étendue à assigner à celui-ci.

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Remarques

L’assignation effectue une copie superficielle du pointeur de données et de la taille. Une copie superficielle est sécurisée, car `span` n’alloue pas de mémoire pour les éléments qu’elle contient.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    span<int> mySpan2;
    mySpan2 = mySpan;
    for (auto &i : mySpan2)
    {
        cout << it;
    }
}
```

```Output
012
```

## <a name="spanpointer"></a><a name="pointer"></a> `span::pointer`

Types pour un pointeur et un **`const`** pointeur vers un élément span.

```cpp
using pointer = T*;
using const_pointer = const T*;
```

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // pointer
    span<int>::pointer ptr = &mySpan[2];
    *ptr = 9;
    cout << mySpan[2];

    // const pointer
    span<int>::const_pointer cPtr = &mySpan[0];
    // *cPtr = 9; error - const
    cout << *cPtr;
}
```

```Output
90
```

## <a name="spanrbegin"></a><a name="rbegin"></a> `span::rbegin`

Obtient un itérateur inverse pointant vers le dernier élément de cette étendue.

```cpp
constexpr reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur pointant vers le début de l’étendue inversée.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

```Output
210
```

## <a name="spanreference"></a><a name="reference"></a> `span::reference`

Types pour une référence, et une **`const`** référence, à un élément span.

```cpp
using reference = T&;
using const_reference = const T&;
```

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // reference
    span<int>::reference ref = mySpan[0];
    ref = 9;
    cout << mySpan[0];
    // const reference
    span<int>::const_reference cRef = mySpan[1];
    // cRef = 9; error because const
    cout << cRef;
}
```

```Output
91
```

## <a name="spanrend"></a><a name="rend"></a> `span::rend`

Obtenez un itérateur à accès aléatoire qui pointe juste après la fin de l’étendue inversée.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur inverse de l’espace réservé qui suit le dernier élément de l’étendue inversée ; autrement dit, l’espace réservé avant le premier élément de l’étendue non inversée.

### <a name="remarks"></a>Remarques

`rend` est utilisé avec une étendue inversée comme [span :: end](#end) est utilisé avec une étendue. Utilisez-le pour déterminer si un itérateur inversé a atteint la fin de son étendue.

La valeur retournée par `rend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

## <a name="spanreverse_iterator"></a><a name="reverse_iterator"></a> `span::reverse_iterator`

Type d’un itérateur inverse pour une étendue.

```cpp
using reverse_iterator = std::reverse_iterator<iterator>;
```

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::reverse_iterator rIt = mySpan.rbegin();
    cout << *rIt++ << *rIt++ << *rIt;
}
```

```Output
210
```

## <a name="spansize"></a><a name="size"></a> `span::size`

Obtient le nombre d’éléments dans l’étendue.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans l’étendue.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size();
}
```

```Output
3
```

## <a name="spansize_bytes"></a><a name="size_bytes"></a> `span::size_bytes`

Obtient la taille des éléments dans l’étendue, en octets.

```cpp
constexpr size_type size_bytes() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’octets que tous les éléments de l’étendue occupent ; autrement dit, `sizeof(element_type)` multiplié par le nombre d’éléments dans l’étendue.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size_bytes(); // 3 elements * 4 (size of an int)
}
```

```Output
12
```

## <a name="spansize_type"></a><a name="size_type"></a> `span::size_type`

Type non signé, approprié pour stocker le nombre d’éléments dans une étendue.

```cpp
using size_type = size_t;
```

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::size_type szType = mySpan.size();
    cout << szType;
}
```

```Output
3
```

## <a name="spanspan"></a><a name="span"></a> `span::span`

`span` constructeurs.

```cpp
constexpr span() noexcept
requires (Extent == 0 || Extent == dynamic_extent) = default;

template <class It>
constexpr explicit(Extent != dynamic_extent)
span(It first, size_type count) noexcept

template <class It, class End>
constexpr explicit(Extent != dynamic_extent)
span(It first, End last) noexcept(noexcept(last - first))

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<T (*)[], T (*)[]>
constexpr span(array<T, N>& arr) noexcept

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<const T (*)[], T (*)[]>
constexpr span(const array<T, N>& arr) noexcept

template <size_t N>
requires (Extent == dynamic_extent || Extent == N)
constexpr span(type_identity_t<T> (&arr)[N]) noexcept

template <class R>
constexpr explicit(Extent != dynamic_extent)
span(R&& r)

// default copy ctor
constexpr span(const span& other) noexcept = default;

// converting  ctor
template <class T, size_t OtherExtent>
requires (Extent == dynamic_extent || OtherExtent == dynamic_extent ||
              Extent == OtherExtent) && is_convertible_v<T (*)[], T (*)[]>
constexpr explicit(Extent != dynamic_extent && OtherExtent == dynamic_extent)
span(const span<T, OtherExtent>& other) noexcept
```

### <a name="parameters"></a>Paramètres

*arr*\
Construit une étendue à partir d’un tableau.

*saut*\
Nombre d’éléments qui seront dans l’étendue.

*premier*\
Itérateur vers le premier élément de l’étendue.

*famille*\
Itérateur à juste après le dernier élément de l’étendue.

*N*\
Nombre d’éléments qui seront dans l’étendue.

*autres*\
Effectuez une copie de cette étendue.

*r*\
Construit une étendue à partir de cette plage.

### <a name="remarks"></a>Remarques

Une étendue ne libère pas de stockage pour les éléments de l’étendue, car elle ne possède pas le stockage des objets qu’elle contient.

|Constructeur  | Description  |
|---------|---------|
|`span()` | Construit une étendue vide. Pris en compte uniquement pendant la résolution de surcharge lorsque le paramètre de modèle `Extent` est `0` ou `dynamic_extent` .|
|`span(It first, size_type count)` | Construit une étendue à partir des premiers `count` éléments de Iterator `first` .  Pris en compte uniquement pendant la résolution de surcharge lorsque le paramètre de modèle `Extent` n’est pas `dynamic_extent` . |
|`span(It first, End last)` | Construit une étendue à partir des éléments de l’itérateur `first` jusqu’à ce que la fin `last` soit atteinte. Pris en compte uniquement pendant la résolution de surcharge lorsque le paramètre de modèle `Extent` n’est pas `dynamic_extent` . `It` doit être `contiguous_iterator` .  |
|`span(array<T, N>& arr) noexcept;`<br /><br />`span(const array<T, N>& arr) noexcept;`<br /><br />`span(type_identity_t<element_type> (&arr)[N]) noexcept;` |  Construit une étendue à partir d' `N` éléments du tableau spécifié. Pris en compte uniquement pendant la résolution de surcharge lorsque le paramètre `Extent` de modèle est `dynamic_extent` ou est égal à `N` . |
|`span(R&& r)` |  Construisez une étendue à partir d’une plage. Participe uniquement à la résolution de surcharge si le paramètre de modèle `Extent` n’est pas `dynamic_extent` .|
|`span(const span& other)` |  Constructeur de copie généré par le compilateur. Une copie superficielle du pointeur de données est sécurisée, car l’étendue n’alloue pas la mémoire pour contenir les éléments. |
|`span(const span<OtherElementType, OtherExtent>& s) noexcept;` | Conversion du constructeur : construit une étendue à partir d’une autre étendue. Participe uniquement à la résolution de surcharge si le `Extent` paramètre `dynamic_extent` de modèle est, ou `N` est `dynamic_extent` ou est égal à `Extent` .|

### <a name="example"></a>Exemple

```cpp
#include <span>

using namespace std;

int main()
{
    const int MAX=10;

    int x[MAX];
    for (int i = 0; i < MAX; i++)
    {
        x[i] = i;
    }

    span<int, MAX> span1{ x }; // fixed-size span: compiler error if size of x doesn't match template argument MAX
    span<int> span2{ x }; // size is inferred from x
    span<const int> span3 = span2; // converting constructor
    span<int> span4( span2 ); // copy constructor
}
```

## <a name="spansubspan"></a><a name="sub_view"></a> `span::subspan`

Obtient une sous-étendue de cette étendue.

```cpp
constexpr auto subspan(size_type offset, size_type count = dynamic_extent) const noexcept;

template <size_t offset, size_t count = dynamic_extent>
constexpr auto subspan() const noexcept
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre d’éléments à placer dans la sous-étendue. Si `count` a `dynamic_extent` la valeur (valeur par défaut), la sous-étendue est prise de `offset` jusqu’à la fin de cette étendue.

*décalage*\
Emplacement dans cette étendue pour démarrer la sous-étendue.

### <a name="return-value"></a>Valeur de retour

Étendue commençant à `offset` dans cette étendue. Contient des `count` éléments.

### <a name="remarks"></a>Remarques

Une version de modèle de cette fonction est disponible et vérifie le nombre au moment de la compilation, qui conserve les informations sur l’étendue en retournant une étendue d’étendue fixe.

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << "mySpan.subspan(1,2): ";
    for (auto& i : mySpan.subspan(1,2))
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1,2>: ";
    for (auto& i : mySpan.subspan<1,2>())
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1>: ";
    for (auto& i : mySpan.subspan<1>)
    {
        cout << i;
    }
}
```

```Output
mySpan.subspan(1,2): 12
mySpan.subspan<1,2>: 12
mySpan.subspan<1>: 12
```

## <a name="spanvalue_type"></a><a name="value_type"></a> `span::value_type`

Type de l’élément dans l’étendue, sans les **`const`** **`volatile`** qualifications ou.

```cpp
using value_type = std::remove_cv_t<T>;
```

### <a name="example"></a>Exemple

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::value_type vType = mySpan[2];
    cout << vType;
}
```

```Output
2
```

## <a name="deduction-guides"></a><a name="deduction_guides"></a> Guides de déduction

Les guides de déduction suivants sont fournis pour span.

```cpp
// Allows the extent to be deduced from std::array and C++ built-in arrays

template <class T, size_t Extent>
span(T (&)[Extent]) -> span<T, Extent>;

template <class T, size_t Size>
span(array<T, Size>&) -> span<T, Size>;

template <class T, size_t Size>
span(const array<T, Size>&) -> span<const T, Size>;

// Allows the element type to be deduced from the iterator and the end of the span.
// The iterator must be contiguous

template <contiguous_iterator It, class End>
span(It, End) -> span<remove_reference_t<iter_reference_t<It>>>;

// Allows the element type to be deduced from a range.
// The range must be contiguous

template <ranges::contiguous_range Rng>
span(Rng &&) -> span<remove_reference_t<ranges::range_reference_t<Rng>>>;
```

## <a name="see-also"></a>Voir aussi

[\<span>](../standard-library/span.md)  
[Comment utiliser la déduction d’argument de modèle de classe](https://devblogs.microsoft.com/cppblog/how-to-use-class-template-argument-deduction/)
