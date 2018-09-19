---
title: Instruction de null | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27180a8252344f7b3185ec83b48ebef42f832907
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077358"
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