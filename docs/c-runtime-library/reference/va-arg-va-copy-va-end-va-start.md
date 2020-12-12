---
description: 'En savoir plus sur les éléments suivants : va_arg, va_copy, va_end, va_start'
title: va_arg, va_copy, va_end, va_start
ms.date: 11/04/2016
api_name:
- va_arg
- va_end
- va_copy
- va_start
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
helpviewer_keywords:
- variable argument lists, accessing
- va_start macro
- va_arg macro
- va_end macro
- arguments [C++], argument lists
- va_list macro
- va_dcl macro
- va_alist macro
- va_copy macro
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
ms.openlocfilehash: 368a08e3ceb78d09d11a9f661772c6b0abef471f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299278"
---
# <a name="va_arg-va_copy-va_end-va_start"></a>va_arg, va_copy, va_end, va_start

Accède à des listes d’arguments variables.

## <a name="syntax"></a>Syntaxe

```C
type va_arg(
   va_list arg_ptr,
   type
);
void va_copy(
   va_list dest,
   va_list src
); // (ISO C99 and later)
void va_end(
   va_list arg_ptr
);
void va_start(
   va_list arg_ptr,
   prev_param
); // (ANSI C89 and later)
void va_start(
   arg_ptr
);  // (deprecated Pre-ANSI C89 standardization version)
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Type d’argument à récupérer.

*arg_ptr*<br/>
Pointeur désignant la liste d’arguments.

*dest*<br/>
Pointeur vers la liste d’arguments à initialiser à partir de *src*

*src*<br/>
Pointeur vers la liste d’arguments initialisée à copier vers *dest*.

*prev_param*<br/>
Paramètre qui précède le premier argument facultatif.

## <a name="return-value"></a>Valeur renvoyée

**va_arg** retourne l’argument actuel. **va_copy**, **va_start** et **va_end** ne retournent pas de valeurs.

## <a name="remarks"></a>Notes

Les macros **va_arg**, **va_copy**, **va_end** et **va_start** offrent un moyen portable d’accéder aux arguments d’une fonction lorsque la fonction accepte un nombre variable d’arguments. Il existe deux versions de ces macros : les macros définies dans STDARG.H, qui sont conformes à la norme ISO C99, et les macros définies dans VARARGS.H qui, bien que dépréciées, sont conservées pour des besoins de compatibilité descendante avec le code qui a été écrit avant la norme ANSI C89.

Ces macros considèrent que la fonction accepte un nombre fixe d’arguments obligatoires, suivi d’un nombre variable d’arguments facultatifs. Les arguments obligatoires sont déclarés à la fonction en tant que paramètres ordinaires et sont accessibles via les noms des paramètres. Les arguments facultatifs sont accessibles via les macros contenues dans STDARG.H (ou dans VARARGS.H pour le code qui a été écrit avant la norme ANSI C89). Ils définissent le pointeur désignant le premier argument facultatif de la liste d’arguments, récupère les arguments de la liste et réinitialise le pointeur dès que le traitement de l’argument est terminé.

Les macros standard C, définies dans STDARG.H, sont utilisées comme suit :

- **va_start** définit *arg_ptr* sur le premier argument facultatif de la liste d’arguments passée à la fonction. L’argument *arg_ptr* doit avoir le type **va_list** . L’argument *prev_param* est le nom du paramètre requis qui précède immédiatement le premier argument facultatif dans la liste d’arguments. Si *prev_param* est déclarée avec la classe de stockage Register, le comportement de la macro n’est pas défini. **va_start** doit être utilisé avant que **va_arg** soit utilisé pour la première fois.

- **va_arg** récupère une valeur de *type* à partir de l’emplacement donné par *arg_ptr*, et incrémente *arg_ptr* pour pointer vers l’argument suivant dans la liste en utilisant la taille du *type* pour déterminer où commence l’argument suivant. **va_arg** pouvez utiliser un nombre quelconque de fois dans la fonction pour récupérer des arguments de la liste.

- **va_copy** effectue une copie d’une liste d’arguments dans son état actuel. Le paramètre *src* doit déjà être initialisé avec **va_start**; elle a peut-être été mise à jour avec des appels de **va_arg** , mais elle ne doit pas avoir été réinitialisée avec **va_end**. L’argument suivant extrait par **va_arg** de *dest* est le même que l’argument suivant extrait de *src*.

- Une fois tous les arguments récupérés, **va_end** réinitialise le pointeur à la **valeur null**. **va_end** doit être appelé sur chaque liste d’arguments initialisée avec **va_start** ou **va_copy** avant le retour de la fonction.

> [!NOTE]
> Les macros contenues dans VARARGS.H sont obsolètes et sont conservées uniquement pour assurer une compatibilité descendante avec le code qui a été écrit avant la norme ANSI C89. Dans tous les autres cas, utilisez les macros contenues dans STDARGS.H.

Quand ils sont compilés à l’aide de [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), les programmes qui utilisent ces macros peuvent générer des résultats inattendus en raison des différences entre les systèmes de type natif et les systèmes de type CLR (Common Language Runtime). Prenons l’exemple de ce programme :

```C
#include <stdio.h>
#include <stdarg.h>

void testit (int i, ...)
{
    va_list argptr;
    va_start(argptr, i);

    if (i == 0)
    {
        int n = va_arg(argptr, int);
        printf("%d\n", n);
    }
    else
    {
        char *s = va_arg(argptr, char*);
        printf("%s\n", s);
    }

    va_end(argptr);
}

int main()
{
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int
    testit(1, NULL);       // 2nd problem: NULL is not a char*
}
```

Notez que **testit** s’attend à ce que le deuxième paramètre soit un **`int`** ou un **`char*`** . Les arguments passés sont 0xFFFFFFFF (un **`unsigned int`** , et non un **`int`** ) et **null** (en fait un **`int`** , et non un **`char*`** ). Quand le programme est compilé pour du code natif, il génère cette sortie :

```Output
-1

(null)
```

## <a name="requirements"></a>Spécifications

**En-tête :** \<stdio.h> les \<stdarg.h>

**En-tête déconseillé :**\<varargs.h>

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_va.c
// Compile with: cl /W3 /Tc crt_va.c
// The program below illustrates passing a variable
// number of arguments using the following macros:
//      va_start            va_arg              va_copy
//      va_end              va_list

#include <stdio.h>
#include <stdarg.h>
#include <math.h>

double deviation(int first, ...);

int main( void )
{
    /* Call with 3 integers (-1 is used as terminator). */
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));

    /* Call with 4 integers. */
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));

    /* Call with just -1 terminator. */
    printf("Deviation is: %f\n", deviation(-1));
}

/* Returns the standard deviation of a variable list of integers. */
double deviation(int first, ...)
{
    int count = 0, i = first;
    double mean = 0.0, sum = 0.0;
    va_list marker;
    va_list copy;

    va_start(marker, first);     /* Initialize variable arguments. */
    va_copy(copy, marker);       /* Copy list for the second pass */
    while (i != -1)
    {
        sum += i;
        count++;
        i = va_arg(marker, int);
    }
    va_end(marker);              /* Reset variable argument list. */
    mean = sum ? (sum / count) : 0.0;

    i = first;                  /* reset to calculate deviation */
    sum = 0.0;
    while (i != -1)
    {
        sum += (i - mean)*(i - mean);
        i = va_arg(copy, int);
    }
    va_end(copy);               /* Reset copy of argument list. */
    return count ? sqrt(sum / count) : 0.0;
}
```

```Output
Deviation is: 0.816497
Deviation is: 2.236068
Deviation is: 0.000000
```

## <a name="see-also"></a>Voir aussi

[Accès aux arguments](../../c-runtime-library/argument-access.md)<br/>
[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
