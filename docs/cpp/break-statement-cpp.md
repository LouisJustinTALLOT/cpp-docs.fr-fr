---
title: break, instruction (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 30ca602ecc65099adff7300f730c500a31fe0ed5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227606"
---
# <a name="break-statement-c"></a>break, instruction (C++)

L' **`break`** instruction termine l’exécution de la boucle englobante ou de l’instruction conditionnelle la plus proche dans laquelle elle apparaît. Le contrôle est passé à l'instruction qui suit l'instruction terminée, le cas échéant.

## <a name="syntax"></a>Syntaxe

```
break;
```

## <a name="remarks"></a>Notes

L' **`break`** instruction est utilisée avec l’instruction de [commutateur](../cpp/switch-statement-cpp.md) conditionnel et avec les instructions [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)et [while](../cpp/while-statement-cpp.md) .

Dans une **`switch`** instruction, l' **`break`** instruction fait en sorte que le programme exécute l’instruction suivante à l’extérieur de l' **`switch`** instruction. Sans **`break`** instruction, chaque instruction de l' **`case`** étiquette mise en correspondance à la fin de l' **`switch`** instruction, y compris la **`default`** clause, est exécutée.

Dans les boucles, l' **`break`** instruction termine l’exécution de l' **`do`** instruction, ou englobante la plus proche **`for`** **`while`** . Le contrôle est passé à l'instruction qui suit l'instruction terminée, le cas échéant.

Dans les instructions imbriquées, l' **`break`** instruction met fin **`do`** uniquement **`for`** à l’instruction,, **`switch`** ou **`while`** qui l’englobe immédiatement. Vous pouvez utiliser une **`return`** **`goto`** instruction ou pour transférer le contrôle à partir de structures plus profondément imbriquées.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser l' **`break`** instruction dans une **`for`** boucle.

```cpp
#include <iostream>
using namespace std;

int main()
{
    // An example of a standard for loop
    for (int i = 1; i < 10; i++)
    {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }

    // An example of a range-based for loop
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

    for (int i : nums) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }
}
```

```Output
In each case:
1
2
3
```

Le code suivant illustre l’utilisation **`break`** de dans une boucle **`while`** et une **`do`** boucle.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    }

    i = 0;
    do {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    } while (i < 10);
}
```

```Output
In each case:
0123
```

Le code suivant montre comment utiliser **`break`** dans une instruction switch. Vous devez utiliser **`break`** dans tous les cas si vous souhaitez gérer chaque cas séparément. Si vous n’utilisez pas **`break`** , l’exécution du code passe au cas suivant.

```cpp
#include <iostream>
using namespace std;

enum Suit{ Diamonds, Hearts, Clubs, Spades };

int main() {

    Suit hand;
    . . .
    // Assume that some enum value is set for hand
    // In this example, each case is handled separately
    switch (hand)
    {
    case Diamonds:
        cout << "got Diamonds \n";
        break;
    case Hearts:
        cout << "got Hearts \n";
        break;
    case Clubs:
        cout << "got Clubs \n";
        break;
    case Spades:
        cout << "got Spades \n";
        break;
    default:
          cout << "didn't get card \n";
    }
    // In this example, Diamonds and Hearts are handled one way, and
    // Clubs, Spades, and the default value are handled another way
    switch (hand)
    {
    case Diamonds:
    case Hearts:
        cout << "got a red card \n";
        break;
    case Clubs:
    case Spades:
    default:
        cout << "didn't get a red card \n";
    }
}
```

## <a name="see-also"></a>Voir aussi

[Instructions de saut](../cpp/jump-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[continue (instruction)](../cpp/continue-statement-cpp.md)
