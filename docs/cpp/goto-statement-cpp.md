---
title: goto, instruction (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: aac308905a01a52a4ce5ee0fa3be03f2f33ac1cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153695"
---
# <a name="goto-statement-c"></a>goto, instruction (C++)

Le **goto** instruction transfère sans condition le contrôle à l’instruction étiquetée par l’identificateur spécifié.

## <a name="syntax"></a>Syntaxe

```
goto identifier;
```

## <a name="remarks"></a>Notes

L'instruction étiquetée indiquée par `identifier` doit se trouver dans la fonction actuelle. Tous les noms `identifier` sont membres d'un espace de noms interne et, par conséquent, n'interfèrent pas avec d'autres identificateurs.

Une étiquette d’instruction est uniquement explicite pour un **goto** instruction ; sinon, les étiquettes d’instruction sont ignorés. Les étiquettes ne peuvent pas être redéclarées.

Un **goto** instruction n’est pas autorisée à transférer le contrôle vers un emplacement qui ignore l’initialisation de n’importe quelle variable qui est dans la portée de cet emplacement. L’exemple suivant déclenche C2362 :

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

Il est conseillé d’utiliser le **saut**, **continuer**, et **retourner** instructions au lieu du **goto** instruction chaque fois que possibles. Toutefois, étant donné que le **saut** instruction se termine à partir d’un seul niveau d’une boucle, vous devrez peut-être utiliser un **goto** instruction pour quitter une boucle profondément imbriquée.

Pour plus d’informations sur les étiquettes et la **goto** instruction, consultez [instructions étiquetées](../cpp/labeled-statements.md).

## <a name="example"></a>Exemple

Dans cet exemple, un **goto** instruction transfère le contrôle au point étiqueté `stop` lorsque `i` est égal à 3.

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
