---
title: Mot clé _Noreturn et macro noreturn (C11)
description: Décrit le `_Noreturn` mot clé et la `noreturn` macro.
ms.date: 10/19/2020
f1_keywords:
- _Noreturn_c
- noreturn
helpviewer_keywords:
- keywords [C]
ms.openlocfilehash: 68448d8b8c999c92fb240100c25048fa94a559b9
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274689"
---
# <a name="_noreturn-keyword-and-noreturn-macro-c11"></a>`_Noreturn` mot clé et `noreturn` macro (C11)

Le `_Noreturn` mot clé a été introduit dans C11. Elle indique au compilateur que la fonction à laquelle elle est appliquée ne retourne pas à l’appelant. Le compilateur sait que le code qui suit un appel à une `_Noreturn` fonction est inaccessible. Un exemple d’une fonction qui ne retourne pas est [Abort](../c-runtime-library/reference/abort.md). S’il est possible que le workflow de contrôle retourne à l’appelant, la fonction ne doit pas avoir l' `_Noreturn` attribut.

Le mot clé est généralement utilisé par le biais de la macro pratique, `noreturn` , fournie dans <stdnoreturn. h>, qui mappe au `_Noreturn` mot clé.

Les principaux avantages de l’utilisation de `_Noreturn` (ou de l’équivalent `noreturn` ) ont pour but de clarifier la fonction dans le code pour les futurs lecteurs et de détecter le code inaccessible de manière involontaire.

Une fonction marquée `noreturn` ne doit pas inclure de type de retour, car elle ne retourne pas de valeur à l’appelant. Elle doit avoir la valeur `void`.

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

## <a name="requirements"></a>Configuration requise

|Macro|En-tête requis|
|-------------|---------------------|
|**`noreturn`**|\<stdnoreturn.h>|

## <a name="see-also"></a>Voir aussi

[/STD (spécifier la version du langage standard)](../build/reference/std-specify-language-standard-version.md)\
[/W4 (spécifier le niveau d’avertissement)](../build/reference/compiler-option-warning-level.md)\
[AVERTISSEMENT C4702](../error-messages\compiler-warnings\compiler-warning-level-4-c4702.md)\
[__declspec (noreturn)](../cpp/noreturn.md)
