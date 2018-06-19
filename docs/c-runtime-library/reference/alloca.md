---
title: _alloca | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _alloca
apilocation:
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
apitype: DLLExport
f1_keywords:
- _alloca
- alloca
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fdc595d33bdc5ce464df1aed86cf885e5673ddc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394114"
---
# <a name="alloca"></a>_alloca

Alloue de la mémoire sur la pile. Cette fonction est déconseillée, car une version plus sécurisée est disponible ; consultez [_malloca](malloca.md).

## <a name="syntax"></a>Syntaxe

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Octets à allouer à partir de la pile.

## <a name="return-value"></a>Valeur de retour

Le **_alloca** routine retourne un **void** pointeur vers l’espace alloué, ce qui est obligatoirement aligné correctement pour le stockage de tout type d’objet. Si *taille* est 0, **_alloca** alloue un élément vide et retourne un pointeur valid vers cet élément.

Une exception de dépassement de capacité de pile est générée si l’espace ne peut pas être alloué. L’exception de dépassement de capacité de pile n’est pas une exception C++ ; il s’agit d’une exception structurée. Au lieu d’utiliser la gestion des exceptions C++, vous devez utiliser la [gestion des exceptions structurée](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Notes

**_alloca** alloue *taille* octets à partir de la pile du programme. L’espace alloué est automatiquement libérée lorsque la fonction d’appel s’arrête (pas lors de l’allocation n’est hors de portée). Par conséquent, ne passez pas de la valeur du pointeur retournée par **_alloca** en tant qu’argument à [libre](free.md).

Il existe des restrictions à appeler explicitement **_alloca** dans un gestionnaire d’exceptions (GE). Les routines EH qui s’exécutent sur des processeurs de classe x86 opèrent dans le cadre de leur propre mémoire : elles effectuent leurs tâches dans un espace mémoire qui n’est pas basé sur l’emplacement actuel du pointeur de pile de la fonction englobante. Les implémentations les plus courantes incluent les expressions de gestion des exceptions structurées Windows NT (SEH) et les expressions de clause catch C++. Par conséquent, appeler explicitement **_alloca** dans un des résultats défaillance d’un programme pendant le retour à l’appel de la routine EH scénarios suivants :

- Expression de filtre d’exception SEH de Windows NT : `__except ( _alloca() )`

- Gestionnaire d’exceptions finale de Windows NT SEH : `__finally { _alloca() }`

- Expression de clause catch EH C++

Toutefois, **_alloca** peut être appelée directement à partir de dans une routine de gestionnaire d’événements ou à partir d’un rappel fourni par l’application qui est appelé par un des scénarios de gestionnaire d’événements mentionnés précédemment.

> [!IMPORTANT]
> Dans Windows XP, si **_alloca** est appelée à l’intérieur d’un bloc try/catch, vous devez appeler [_resetstkoflw](resetstkoflw.md) dans le bloc catch.

Outre les restrictions ci-dessus, lorsque vous utilisez la[/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) option, **_alloca** ne peut pas être utilisé dans **__except** blocs. Pour plus d'informations, consultez [/clr Restrictions](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_alloca**|\<malloc.h>|

## <a name="example"></a>Exemple

```C
// crt_alloca.c
// This program demonstrates the use of
// _alloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size = 1000;
    int     errcode = 0;
    void    *pData = NULL;

    // Note: Do not use try/catch for _alloca,
    // use __try/__except, since _alloca throws
    // Structured Exceptions, not C++ exceptions.

    __try {
        // An unbounded _alloca can easily result in a
        // stack overflow.
        // Checking for a size < 1024 bytes is recommended.
        if (size > 0 && size < 1024)
        {
            pData = _alloca( size );
            printf_s( "Allocated %d bytes of stack at 0x%p",
                      size, pData);
        }
        else
        {
            printf_s("Tried to allocate too many bytes.\n");
        }
    }

    // If an exception occured with the _alloca function
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_alloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf_s("Could not reset the stack!\n");
            _exit(1);
        }
    };
}
```

```Output
Allocated 1000 bytes of stack at 0x0012FB50
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
[_malloca](malloca.md)<br/>
