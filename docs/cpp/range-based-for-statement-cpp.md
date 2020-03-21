---
title: Basé sur une plage, instruction (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: af9811fd707d4dbc28158dba3b6b3fbfcc43e4fe
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077181"
---
# <a name="range-based-for-statement-c"></a>Basé sur une plage, instruction (C++)

Exécute `statement` à plusieurs reprises et séquentiellement pour chaque élément de `expression`.

## <a name="syntax"></a>Syntaxe

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>Notes

Utilisez l’instruction **for** basée sur une plage pour construire des boucles qui doivent s’exécuter par le biais d’une « plage », qui est définie comme tout ce que vous pouvez itérer (par exemple C++ , `std::vector`, ou toute autre séquence de bibliothèque standard dont la plage est définie par une `begin()` et `end()`. Le nom qui est déclaré dans la partie `for-range-declaration` est local pour l’instruction **for** et ne peut pas être déclaré de nouveau dans `expression` ou `statement`. Notez que le mot clé [auto](../cpp/auto-cpp.md) est préféré dans la partie `for-range-declaration` de l’instruction.

**Nouveautés de Visual Studio 2017 :**  Les boucles for basées sur une plage ne requièrent plus que Begin () et end () retournent des objets du même type. Ainsi, end() peut retourner un objet sentinel, à l’image de ceux utilisés par les plages définies selon la proposition Ranges-V3. Pour plus d’informations, consultez [Generalizing the Range-Based For Loop](https://wg21.link/p0184r0) et la [bibliothèque range-v3 sur GitHub](https://github.com/ericniebler/range-v3).

Ce code montre comment utiliser **des boucles for** basées sur une plage pour itérer au sein d’un tableau et d’un vecteur :

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

Une boucle **for** basée sur une plage se termine quand l’une de ces `statement` est exécutée : [break](../cpp/break-statement-cpp.md), [Return](../cpp/return-statement-cpp.md)ou [goto](../cpp/goto-statement-cpp.md) à une instruction étiquetée en dehors de la boucle **for** basée sur une plage. Une instruction [continue](../cpp/continue-statement-cpp.md) dans une boucle **for** basée sur une plage ne termine que l’itération en cours.

Gardez à l’esprit ces faits sur la plage **pour**:

- Reconnaît automatiquement les tableaux.

- Reconnaît les conteneurs qui ont des `.begin()` et des `.end()`.

- Utilise la `begin()` de recherche dépendante d’un argument et `end()` pour toute autre chose.

## <a name="see-also"></a>Voir aussi

[auto](../cpp/auto-cpp.md)<br/>
[Instructions d’itération](../cpp/iteration-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[while, instruction (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while, instruction (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for, instruction (C++)](../cpp/for-statement-cpp.md)