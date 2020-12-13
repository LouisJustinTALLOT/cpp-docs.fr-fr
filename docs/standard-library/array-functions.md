---
description: En savoir plus sur &lt; les &gt; fonctions de tableau
title: '&lt;array&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- array/std::array::get
- array/std::get
- array/std::swap
ms.assetid: e0700a33-a833-4655-8735-16e71175efc8
helpviewer_keywords:
- std::array [C++], get
- std::get [C++]
- std::swap [C++]
ms.openlocfilehash: b2f6cd72c5f82f36914f96dee6924654a96a9fc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149550"
---
# <a name="ltarraygt-functions"></a>&lt;array&gt;, fonctions

L' \<array> en-tête comprend deux fonctions non membres, `get` et `swap` , qui opèrent sur des objets de **tableau** .

[Télécharger](#get)\
[swap](#swap)

## <a name="get"></a><a name="get"></a> Télécharger

Retourne une référence à l’élément spécifié du tableau.

```cpp
template <int Index, class T, size_t N>
constexpr T& get(array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr const T& get(const array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr T&& get(array<T, N>&& arr) noexcept;
```

### <a name="parameters"></a>Paramètres

*Index*\
Décalage de l’élément.

*T*\
Type d’un élément.

*N*\
Nombre d’éléments dans le tableau.

*arr*\
Tableau dans lequel opérer la sélection.

### <a name="example"></a>Exemple

```cpp
#include <array>
#include <iostream>

using namespace std;

typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& e : c0)
    {
        cout << " " << e;
    }
    cout << endl;

    // display odd elements " 1 3"
    cout << " " << get<1>(c0);
    cout << " " << get<3>(c0) << endl;
}
```

```Output
0 1 2 3
1 3
```

## <a name="swap"></a><a name="swap"></a> échange

Une spécialisation de modèle non membre de `std::swap` qui échange deux objets de **tableau** .

```cpp
template <class Ty, std::size_t N>
void swap(array<Ty, N>& left, array<Ty, N>& right);
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type d’un élément.

*N*\
Taille du tableau.

*gauche*\
Premier tableau à échanger.

*Oui*\
Deuxième tableau à échanger.

### <a name="remarks"></a>Notes

La fonction de modèle exécute `left.swap(right)`.

### <a name="example"></a>Exemple

```cpp
// std__array__swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="see-also"></a>Voir aussi

[\<array>](../standard-library/array.md)
