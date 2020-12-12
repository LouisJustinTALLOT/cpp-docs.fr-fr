---
description: 'En savoir plus sur : paramètres positionnels printf_p'
title: Paramètres positionnels printf_p
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
helpviewer_keywords:
- _printf_p function, positional parameters
- printf_p function, positional parameters
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
ms.openlocfilehash: 2db76bc937e52b5945bf39cab1f47161fd3b162c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213427"
---
# <a name="printf_p-positional-parameters"></a>Paramètres positionnels printf_p

Les paramètres positionnels permettent de spécifier à l’aide d’un nombre l’argument à remplacer dans un champ de chaîne de format. Voici les fonctions `printf` avec paramètres positionnels disponibles :

| Fonctions printf non-positionnelles | Équivalents de paramètres positionnels |
|---|---|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|
|[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|
|[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|
|[vprintf, _vprintf_l, vwprintf, _vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|
|[vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, \_ _vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|

## <a name="how-to-specify-positional-parameters"></a>Comment spécifier des paramètres positionnels

### <a name="parameter-indexing"></a>Indexation des paramètres

Par défaut, en l’absence de mise en forme positionnelle, les fonctions positionnelles se comportent comme les fonctions non positionnelles. Vous spécifiez le paramètre positionnel à mettre en forme à l’aide de `%n$` au début du spécificateur de format, où `n` correspond à la position du paramètre à mettre en forme dans la liste de paramètres. La position de paramètre commence à 1 pour le premier argument suivant la chaîne de format. Le reste du spécificateur de format suit les mêmes règles que le spécificateur de format `printf`. Pour plus d’informations sur les spécificateurs de format, consultez [Syntaxe de spécification de format : fonctions printf et wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

Voici un exemple de mise en forme positionnelle :

```C
_printf_p("%1$s %2$s", "November", "10");
```

Cela imprime :

```
November 10
```

L’ordre des nombres utilisés ne doit pas nécessairement corresponde à l’ordre des arguments. Par exemple, voici une chaîne de format valide :

```C
_printf_p("%2$s %1$s", "November", "10");
```

Cela imprime :

```
10 November
```

Contrairement aux chaînes de format classiques, vous pouvez utiliser des paramètres positionnels plusieurs fois dans une chaîne de format. Par exemple :

```C
_printf_p("%1$d times %1$d is %2$d", 10, 100);
```

Cela imprime :

```
10 times 10 is 100
```

Tous les arguments doivent être utilisés au moins une fois dans la chaîne de format. Le nombre maximal de paramètres positionnels autorisés dans une chaîne de format est fourni par `_ARGMAX`.

### <a name="width-and-precision"></a>Largeur et précision

Vous pouvez utiliser `*n$` pour spécifier un paramètre positionnel comme spécificateur de largeur ou de précision, où `n` est la position du paramètre de largeur ou de précision dans la liste de paramètres. La position de la valeur de largeur ou de précision doit apparaître immédiatement après le symbole \*. Par exemple :

```C
_printf_p("%1$*2$s","Hello", 10);
```

ou

```C
_printf_p("%2$*1$s", 10, "Hello");
```

### <a name="mixing-positional-and-non-positional-arguments"></a>Mélange d’arguments positionnels et non-positionnels

Les paramètres positionnels ne doivent pas être mélangés avec des paramètres non positionnels dans la même chaîne de format. Si aucune mise en forme positionnelle n’est utilisée, tous les spécificateurs de format doivent utiliser la mise en forme positionnelle. Toutefois, `printf_p` et les fonctions connexes prennent toujours en charge les paramètres non positionnels dans les chaînes de format qui contiennent des paramètres positionnels.

## <a name="example"></a>Exemple

```C
// positional_args.c
// Build by using: cl /W4 positional_args.c
// Positional arguments allow the specification of the order
// in which arguments are consumed in a formatting string.

#include <stdio.h>

int main()
{
    int     i = 1,
            j = 2,
            k = 3;
    double  x = 0.1,
            y = 2.22,
            z = 333.3333;
    char    *s1 = "abc",
            *s2 = "def",
            *s3 = "ghi";

    // If positional arguments are unspecified,
    // normal input order is used.
    _printf_p("%d %d %d\n", i, j, k);

    // Positional arguments are numbers followed by a $ character.
    _printf_p("%3$d %1$d %2$d\n", i, j, k);

    // The same positional argument may be reused.
    _printf_p("%1$d %2$d %1$d\n", i, j);

    // The positional arguments may appear in any order.
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);

    // Precision and width specifiers must be int types.
    _printf_p("%3$*5$f %2$.*4$f %1$*4$.*5$f\n", x, y, z, j, k);
}
```

```Output
1 2 3
3 1 2
1 2 1
abc def ghi
ghi abc def
333.333300 2.22 0.100
```

## <a name="see-also"></a>Voir aussi

[Syntaxe de spécification de format : fonctions printf et wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)
