---
title: break, instruction (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 3dda0b19fffaaf725ab363a0c4fe70d2ca54e3f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662499"
---
# <a name="break-statement-c"></a>break, instruction (C++)

Le **saut** instruction arrête l’exécution de l’englobante la plus proche boucle ou instruction conditionnelle dans laquelle elle apparaît. Le contrôle est passé à l'instruction qui suit l'instruction terminée, le cas échéant.

## <a name="syntax"></a>Syntaxe

```
break;
```

## <a name="remarks"></a>Notes

Le **saut** instruction est utilisée avec l’instruction conditionnelle [basculer](../cpp/switch-statement-cpp.md) instruction et avec le [faire](../cpp/do-while-statement-cpp.md), [pour](../cpp/for-statement-cpp.md), et [lors de la](../cpp/while-statement-cpp.md) instructions de boucle.

Dans un **basculer** instruction, le **saut** instruction provoque le programme à exécuter l’instruction suivante en dehors de la **basculer** instruction. Sans un **saut** chaque instruction, à partir de la mise en correspondance **cas** étiquette à la fin de la **basculer** instruction, y compris le **par défaut**clause, est exécutée.

Dans les boucles, le **saut** instruction arrête l’exécution de l’englobante la plus proche **faire**, **pour**, ou **tandis que** instruction. Le contrôle est passé à l'instruction qui suit l'instruction terminée, le cas échéant.

Dans les instructions imbriquées, le **saut** instruction se termine uniquement le **faire**, **pour**, **basculer**, ou **lors de la**instruction qui l’englobe immédiatement. Vous pouvez utiliser un **retourner** ou **goto** instruction pour transférer le contrôle de la plus profondément imbriquée des structures.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser le **saut** instruction dans un **pour** boucle.

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

Le code suivant montre comment utiliser **saut** dans un **tandis que** boucle et une **faire** boucle.

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

Le code suivant montre comment utiliser **saut** dans une instruction switch. Vous devez utiliser **saut** dans tous les cas si vous souhaitez traiter chaque cas séparément ; si vous n’utilisez pas **saut**, l’exécution du code passera au cas suivant.

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
[Instruction continue](../cpp/continue-statement-cpp.md)