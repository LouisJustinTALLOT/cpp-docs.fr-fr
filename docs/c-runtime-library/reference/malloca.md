---
description: 'En savoir plus sur : _malloca'
title: _malloca
ms.date: 11/04/2016
api_name:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: 8357bc15ba432a0adb390494882ee4b63adf70f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299798"
---
# <a name="_malloca"></a>_malloca

Alloue de la mémoire sur la pile. Il s’agit d’une version de [_alloca](alloca.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Octets à allouer à partir de la pile.

## <a name="return-value"></a>Valeur renvoyée

La routine **_malloca** retourne un **`void`** pointeur vers l’espace alloué, qui est garanti être correctement aligné pour le stockage de tout type d’objet. Si la *taille* est égale à 0, **_malloca** alloue un élément de longueur zéro et retourne un pointeur valide vers cet élément.

Si la *taille* est supérieure à **_ALLOCA_S_THRESHOLD**, **_malloca** tente d’allouer sur le tas et retourne un pointeur null si l’espace ne peut pas être alloué. Si la *taille* est inférieure ou égale à **_ALLOCA_S_THRESHOLD**, **_malloca** tente d’allouer sur la pile, et une exception de dépassement de capacité de la pile est générée si l’espace ne peut pas être alloué. L’exception de dépassement de capacité de la pile n’est pas une exception C++. Il s’agit d’une exception structurée. Au lieu d’utiliser la gestion des exceptions C++, vous devez utiliser la [gestion structurée des exceptions](../../cpp/structured-exception-handling-c-cpp.md) (SEH) pour intercepter cette exception.

## <a name="remarks"></a>Notes

**_malloca** alloue des octets de *taille* à partir de la pile du programme ou du segment de mémoire si la requête dépasse une certaine taille en octets donnée par **_ALLOCA_S_THRESHOLD**. La différence entre **_malloca** et **_alloca** est que **_alloca** est toujours alloué sur la pile, quelle que soit la taille. Contrairement à **_alloca**, qui ne requiert pas ou n’autorise pas un **appel à libérer** pour libérer la mémoire ainsi allouée, **_malloca** requiert l’utilisation de [_freea](freea.md) pour libérer de la mémoire. En mode débogage, **_malloca** alloue toujours de la mémoire à partir du tas.

Il existe des restrictions relatives à l’appel explicite de **_malloca** dans un gestionnaire d’exceptions (Eh). Les routines EH qui s’exécutent sur des processeurs de classe x86 opèrent dans le cadre de leur propre mémoire : elles effectuent leurs tâches dans un espace mémoire qui n’est pas basé sur l’emplacement actuel du pointeur de pile de la fonction englobante. Les implémentations les plus courantes incluent les expressions de gestion des exceptions structurées Windows NT (SEH) et les expressions de clause catch C++. Par conséquent, l’appel explicite de **_malloca** dans l’un des scénarios suivants entraîne l’échec d’un programme pendant le retour à la routine Eh appelante :

- Expression de filtre d’exception SEH Windows NT : **`__except`** ( `_malloca ()` )

- Gestionnaire d’exceptions finales SEH Windows NT : **`__finally`** { `_malloca ()` }

- Expression de clause catch EH C++

Toutefois, **_malloca** peut être appelée directement à partir d’une routine Eh ou à partir d’un rappel fourni par l’application qui est appelé par l’un des scénarios Eh précédemment listés.

> [!IMPORTANT]
> Dans Windows XP, si **_malloca** est appelée à l’intérieur d’un bloc try/catch, vous devez appeler [_resetstkoflw](resetstkoflw.md) dans le bloc catch.

Outre les restrictions ci-dessus, lors de l’utilisation de l’option [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , **_malloca** ne peut pas être utilisé dans des **`__except`** blocs. Pour plus d’informations, consultez [Restrictions de /clr](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_malloca**|\<malloc.h>|

## <a name="example-malloca"></a>Exemple : malloca

```C
// crt_malloca_simple.c
#include <stdio.h>
#include <malloc.h>

void Fn()
{
   char * buf = (char *)_malloca( 100 );
   // do something with buf
   _freea( buf );
}

int main()
{
   Fn();
}
```

## <a name="example-malloca-exception"></a>Exemple : exception malloca

```C
// crt_malloca_exception.c
// This program demonstrates the use of
// _malloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size;
    int     numberRead = 0;
    int     errcode = 0;
    void    *p = NULL;
    void    *pMarker = NULL;

    while (numberRead == 0)
    {
        printf_s("Enter the number of bytes to allocate "
                 "using _malloca: ");
        numberRead = scanf_s("%d", &size);
    }

    // Do not use try/catch for _malloca,
    // use __try/__except, since _malloca throws
    // Structured Exceptions, not C++ exceptions.

    __try
    {
        if (size > 0)
        {
            p =  _malloca( size );
        }
        else
        {
            printf_s("Size must be a positive number.");
        }
        _freea( p );
    }

    // Catch any exceptions that may occur.
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_malloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf("Could not reset the stack!");
            _exit(1);
        }
    };
}
```

### <a name="input"></a>Entrée

```Input
1000
```

### <a name="sample-output"></a>Exemple de sortie

```Output
Enter the number of bytes to allocate using _malloca: 1000
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
