---
title: null, instruction
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
ms.openlocfilehash: 2797937b184bebe0e29f8e5eae428f601c824811
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245178"
---
# <a name="null-statement"></a>null, instruction

Le « instruction null » est une instruction d’expression avec le *expression* manquant. Elle s'avère utile lorsque la syntaxe du langage demande une instruction, mais pas d'évaluation d'expression. Elle se compose d'un point-virgule.

Les instructions null sont couramment utilisées comme espaces réservés dans les instructions d'itération ou comme instructions sur lesquelles placer des étiquettes à la fin d'instructions composées ou de fonctions.

Le fragment de code suivant montre comment copier une chaîne vers une autre et comporte l'instruction null :

```cpp
// null_statement.cpp
char *myStrCpy( char *Dest, const char *Source )
{
    char *DestStart = Dest;

    // Assign value pointed to by Source to
    // Dest until the end-of-string 0 is
    // encountered.
    while( *Dest++ = *Source++ )
        ;   // Null statement.

    return DestStart;
}

int main()
{
}
```

## <a name="see-also"></a>Voir aussi

[Instruction d’expression](../cpp/expression-statement.md)