---
description: 'En savoir plus sur : Goto, instruction (C++)'
title: goto, instruction (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: c8f94a5c2dfbd6ff3bd33223944180a4d1642b0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221382"
---
# <a name="goto-statement-c"></a>goto, instruction (C++)

L' **`goto`** instruction transfère sans condition le contrôle à l’instruction étiquetée par l’identificateur spécifié.

## <a name="syntax"></a>Syntaxe

```
goto identifier;
```

## <a name="remarks"></a>Notes

L'instruction étiquetée indiquée par `identifier` doit se trouver dans la fonction actuelle. Tous les noms `identifier` sont membres d'un espace de noms interne et, par conséquent, n'interfèrent pas avec d'autres identificateurs.

Une étiquette d’instruction est significative uniquement pour une **`goto`** instruction ; sinon, les étiquettes d’instruction sont ignorées. Les étiquettes ne peuvent pas être redéclarées.

Une **`goto`** instruction n’est pas autorisée à transférer le contrôle vers un emplacement qui ignore l’initialisation d’une variable qui est dans la portée de cet emplacement. L’exemple suivant déclenche C2362 :

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

Il s’agit d’un bon style de programmation pour utiliser les **`break`** **`continue`** instructions, et **`return`** au lieu de l’instruction dans la mesure du **`goto`** possible. Toutefois, étant donné que l' **`break`** instruction quitte un seul niveau d’une boucle, vous devrez peut-être utiliser une **`goto`** instruction pour quitter une boucle profondément imbriquée.

Pour plus d’informations sur les étiquettes et l' **`goto`** instruction, consultez [instructions étiquetées](../cpp/labeled-statements.md).

## <a name="example"></a>Exemple

Dans cet exemple, une **`goto`** instruction transfère le contrôle au point étiqueté `stop` lorsque `i` est égal à 3.

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>Voir aussi

[Instructions de saut](../cpp/jump-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
