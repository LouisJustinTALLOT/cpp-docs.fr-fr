---
description: 'En savoir plus sur : instruction for basée sur une plage (C++)'
title: Basé sur une plage, instruction (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 0d32086009190fe69333a2f36ff03bb551396d98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319389"
---
# <a name="range-based-for-statement-c"></a>Basé sur une plage, instruction (C++)

S’exécute `statement` de manière répétée et séquentielle pour chaque élément dans `expression` .

## <a name="syntax"></a>Syntaxe

> **`for (`***for-Range-DECLARATION* **`:`** *expression***`)`**\
&emsp;*instruction*

## <a name="remarks"></a>Notes

Utilisez l’instruction basée sur une plage **`for`** pour construire des boucles qui doivent s’exécuter par le biais d’une *plage*, qui est définie comme tout ce que vous pouvez itérer, par exemple, `std::vector` ou toute autre séquence de bibliothèque standard C++ dont la plage est définie par un `begin()` et un `end()` . Le nom qui est déclaré dans la `for-range-declaration` partie est local à l' **`for`** instruction et ne peut pas être déclaré à nouveau dans `expression` ou `statement` . Notez que le [`auto`](../cpp/auto-cpp.md) mot clé est préféré dans la `for-range-declaration` partie de l’instruction.

**Nouveautés de Visual Studio 2017 :**  Les boucles basées sur une plage **`for`** ne requièrent plus cet `begin()` `end()` objet et retournent des objets du même type. Cela permet `end()` à de retourner un objet Sentinel, tel qu’utilisé par les plages définies dans les plages-v3. Pour plus d’informations, consultez [généralisation de la `For` boucle de Range-Based](https://wg21.link/p0184r0) et de la [bibliothèque Range-v3 sur GitHub](https://github.com/ericniebler/range-v3).

Ce code montre comment utiliser des boucles basées sur **`for`** une plage pour itérer au sein d’un tableau et d’un vecteur :

```cpp
// range-based-for.cpp
// compile by using: cl /EHsc /nologo /W4
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    // Basic 10-element integer array.
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // Range-based for loop to iterate through the array.
    for( int y : x ) { // Access by value using a copy declared as a specific type.
                       // Not preferred.
        cout << y << " ";
    }
    cout << endl;

    // The auto keyword causes type inference to be used. Preferred.

    for( auto y : x ) { // Copy of 'x', almost always undesirable
        cout << y << " ";
    }
    cout << endl;

    for( auto &y : x ) { // Type inference by reference.
        // Observes and/or modifies in-place. Preferred when modify is needed.
        cout << y << " ";
    }
    cout << endl;

    for( const auto &y : x ) { // Type inference by const reference.
        // Observes in-place. Preferred when no modify is needed.
        cout << y << " ";
    }
    cout << endl;
    cout << "end of integer array test" << endl;
    cout << endl;

    // Create a vector object that contains 10 elements.
    vector<double> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(i + 0.14159);
    }

    // Range-based for loop to iterate through the vector, observing in-place.
    for( const auto &j : v ) {
        cout << j << " ";
    }
    cout << endl;
    cout << "end of vector test" << endl;
}
```

Voici la sortie :

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

Une boucle basée sur une plage **`for`** se termine quand l’une d’entre elles `statement` est exécutée : [`break`](../cpp/break-statement-cpp.md) , [`return`](../cpp/return-statement-cpp.md) ou [`goto`](../cpp/goto-statement-cpp.md) à une instruction étiquetée en dehors de la boucle basée sur une plage **`for`** . Une [`continue`](../cpp/continue-statement-cpp.md) instruction dans une boucle basée sur une plage **`for`** ne termine que l’itération en cours.

Gardez à l’esprit ces faits sur la plage **`for`** :

- Reconnaît automatiquement les tableaux.

- Reconnaît les conteneurs qui ont `.begin()` et `.end()` .

- Utilise une recherche dépendante d’un argument `begin()` et `end()` pour toute autre chose.

## <a name="see-also"></a>Voir aussi

[`auto`](../cpp/auto-cpp.md)<br/>
[Instructions d'itération](../cpp/iteration-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[`while` Instruction (C++)](../cpp/while-statement-cpp.md)<br/>
[`do-while` Instruction (C++)](../cpp/do-while-statement-cpp.md)<br/>
[`for` Instruction (C++)](../cpp/for-statement-cpp.md)
