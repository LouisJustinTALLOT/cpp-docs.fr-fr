---
title: Mot clé _Noreturn et macro noreturn (C11)
description: Décrit le `_Noreturn` mot clé et la `noreturn` macro.
ms.date: 10/16/2020
f1_keywords:
- _Noreturn_c
- noreturn
helpviewer_keywords:
- keywords [C]
ms.openlocfilehash: f876485b5be497688c5cf1dd8fca206d08560de0
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92182809"
---
# <a name="_noreturn-keyword-and-noreturn-macro-c11"></a>`_Noreturn` mot clé et `noreturn` macro (C11)

Le `_Noreturn` mot clé a été introduit dans C11. Elle indique au compilateur que la fonction à laquelle elle est appliquée ne retourne pas. Le compilateur sait que le code qui suit un appel à une `_Noreturn` fonction est inaccessible.

Une macro pratique, `noreturn` , fournie dans <stdnoreturn. h>, est mappée au `_Noreturn` mot clé.

Les principaux avantages de l’utilisation de `_Noreturn` (ou de l’équivalent `noreturn` ) ont pour but de clarifier la fonction dans le code pour les futurs lecteurs et de détecter le code inaccessible de manière involontaire.

## <a name="example-using-noreturn-macro-and-_noreturn-keyword"></a>Exemple utilisant une `noreturn` macro et un `_Noreturn ` mot clé

L’exemple suivant illustre le `_Noreturn` mot clé et la `noreturn` macro équivalente.

IntelliSense peut générer une erreur parasite, `E0065` , si vous utilisez la macro `noreturn` que vous pouvez ignorer. Elle ne vous empêche pas d’exécuter l’exemple.

```C
// Compile with Warning Level4 (/W4) and /std:c11
#include <stdio.h>
#include <stdlib.h>
#include <stdnoreturn.h>

noreturn void fatal_error(void)
{
    exit(3);
}

_Noreturn void not_coming_back(void)
{
    puts("There's no coming back");
    fatal_error();
    return; // warning C4645 - function declared with noreturn has a return statement
}

void done(void)
{
    puts("We'll never get here");
}

int main(void)
{
    not_coming_back();
    done(); // warning c4702 - unreachable code

    return 0;
}
```

## <a name="requirements"></a>Spécifications

|Macro|En-tête requis|
|-------------|---------------------|
|**`noreturn`**|\<stdnoreturn.h>|

## <a name="see-also"></a>Voir aussi

[/STD (spécifier la version du langage standard)](../build/reference/std-specify-language-standard-version.md)\
[/W4 (spécifier le niveau d’avertissement)](../build/reference/compiler-option-warning-level.md) 
 [Avertissement C4702](../error-messages\compiler-warnings\compiler-warning-level-4-c4702.md)