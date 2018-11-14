---
title: Checked Iterators
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL_THROWS
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
ms.openlocfilehash: 163729b401fa917d7df0002c621998f5021757f6
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521490"
---
# <a name="checked-iterators"></a>Checked Iterators

Les itérateurs vérifiés garantissent que les limites de votre conteneur ne sont pas remplacées. Les itérateurs vérifiés s’appliquent aux versions Release et aux versions Debug. Pour plus d’informations sur l’utilisation des itérateurs de débogage quand vous compilez en mode débogage, consultez [Prise en charge des itérateurs de débogage](../standard-library/debug-iterator-support.md).

## <a name="remarks"></a>Notes

Pour plus d’informations sur désactivation des avertissements générés par les itérateurs vérifiés, consultez [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

Vous pouvez utiliser la macro de préprocesseur [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) pour activer ou désactiver la fonctionnalité des itérateurs vérifiés. Si _ITERATOR_DEBUG_LEVEL est définie comme 1 ou 2, une utilisation non sécurisée d’itérateurs provoque une erreur d’exécution et le programme se termine. S'il est défini sur 0, les itérateurs vérifiés sont désactivés. Par défaut, la valeur de _ITERATOR_DEBUG_LEVEL est 0 pour les versions release et 2 pour les versions debug.

> [!IMPORTANT]
> Une documentation et un code source plus anciens peuvent faire référence à la macro [_SECURE_SCL](../standard-library/secure-scl.md). Utilisez _ITERATOR_DEBUG_LEVEL pour contrôler les _SECURE_SCL. Pour plus d’informations, consultez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

Lorsque _ITERATOR_DEBUG_LEVEL est défini comme 1 ou 2, ces vérifications d’itérateur sont effectuées :

- Tous les itérateurs standard (par exemple, [vector::iterator](../standard-library/vector-class.md#iterator)) sont vérifiés.

- Si un itérateur de sortie est un itérateur vérifié, les appels aux fonctions de bibliothèque standard comme [std::copy](../standard-library/algorithm-functions.md#copy) obtiennent un comportement vérifié.

- Si un itérateur de sortie est un itérateur non vérifié, les appels aux fonctions de bibliothèque standard entraînent des avertissements du compilateur.

- Les fonctions suivantes génèrent une erreur d’exécution si un accès est hors des limites du conteneur :

|||||
|-|-|-|-|
|[basic_string::operator\[\]](../standard-library/basic-string-class.md#op_at)|[bitset::operator\[\]](../standard-library/bitset-class.md#op_at)|[back](../standard-library/deque-class.md#back)|[front](../standard-library/deque-class.md#front)|
|[deque::operator\[\]](../standard-library/deque-class.md#op_at)|[back](../standard-library/list-class.md#back)|[front](../standard-library/list-class.md#front)|[back](../standard-library/queue-class.md#back)|
|[front](../standard-library/queue-class.md#front)|[vector::operator\[\]](../standard-library/vector-class.md#op_at)|[back](../standard-library/vector-class.md#back)|[front](../standard-library/vector-class.md#front)|

Lorsque _ITERATOR_DEBUG_LEVEL est définie comme 0 :

- Tous les itérateurs standard sont non vérifiés. Les itérateurs peuvent être déplacés au delà des limites du conteneur, ce qui entraîne un comportement indéfini.

- Si un itérateur de sortie est un itérateur vérifié, les appels aux fonctions de bibliothèque standard comme `std::copy` obtiennent un comportement vérifié.

- Si un itérateur de sortie est un itérateur non vérifié, les appels aux fonctions de bibliothèque standard obtiennent un comportement non vérifié.

Un itérateur vérifié fait référence à un itérateur qui appelle `invalid_parameter_handler` si vous tentez de dépasser les limites du conteneur. Pour plus d’informations sur `invalid_parameter_handler`, consultez [Validation de paramètre](../c-runtime-library/parameter-validation.md).

Les adaptateurs d’itérateur qui prennent en charge des itérateurs vérifiés sont la [classe checked_array_iterator](../standard-library/checked-array-iterator-class.md) et la [classe unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

## <a name="example"></a>Exemple

Lorsque vous compilez à l’aide de _ITERATOR_DEBUG_LEVEL défini sur 1 ou 2, une erreur d’exécution se produira si vous tentez d’accéder à un élément qui est en dehors des limites du conteneur à l’aide de l’opérateur d’indexation de certaines classes.

```cpp
// checked_iterators_1.cpp
// cl.exe /Zi /MDd /EHsc /W4

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;
   v.push_back(67);

   int i = v[0];
   cout << i << endl;

   i = v[1]; //triggers invalid parameter handler
}
```

Ce programme affiche « 67 », puis une boîte de dialogue d’échec d’assertion avec des informations supplémentaires sur l’erreur.

## <a name="example"></a>Exemple

De même, lorsque vous compilez à l’aide de _ITERATOR_DEBUG_LEVEL défini sur 1 ou 2, une erreur d’exécution se produira si vous essayez d’accéder à un élément à l’aide de `front` ou `back` dans les classes de conteneur lorsque le conteneur est vide.

```cpp
// checked_iterators_2.cpp
// cl.exe /Zi /MDd /EHsc /W4
#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;

   int& i = v.front(); // triggers invalid parameter handler
}
```

Ce programme affiche une boîte de dialogue d’échec d’assertion avec des informations supplémentaires sur l’erreur.

## <a name="example"></a>Exemple

Le code suivant illustre différents scénarios de cas d'usage d'itérateur avec des commentaires sur chacun d'eux. Par défaut, _ITERATOR_DEBUG_LEVEL est définie à 2 dans les versions Debug et la valeur 0 dans les versions commerciales.

```cpp
// checked_iterators_3.cpp
// cl.exe /MTd /EHsc /W4

#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (an overrun causes a debug assertion)
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (an overrun causes undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (an overrun causes a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun causes undefined behavior)
    int a8[16];
    int * p8 = a8;
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

Quand vous compilez ce code à l’aide de `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp`, le compilateur émet un avertissement, mais compile sans erreur dans un fichier exécutable :

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

Lors de l’exécution à partir de la ligne de commande, le fichier exécutable génère cette sortie :

```Output
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120
```

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
