---
title: _alloca
ms.date: 11/04/2016
api_name:
- _alloca
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
- _alloca
- alloca
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
ms.openlocfilehash: 77ce6e0cdb5e1ad3f5317989c7804abc5aed4e69
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821432"
---
# <a name="_alloca"></a>_alloca

Alloue de la mémoire sur la pile. Cette fonction est déconseillée, car une version plus sécurisée est disponible ; consultez [_malloca](malloca.md).

## <a name="syntax"></a>Syntaxe

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>Parameters

*size*<br/>
Octets à allouer à partir de la pile.

## <a name="return-value"></a>Valeur de retour

La routine **_alloca** retourne un pointeur **void** vers l’espace alloué, qui est garanti correctement aligné pour le stockage de tout type d’objet. Si la *taille* est égale à 0, **_alloca** alloue un élément de longueur zéro et retourne un pointeur valide vers cet élément.

Une exception de dépassement de capacité de pile est générée si l’espace ne peut pas être alloué. L’exception de dépassement de capacité de pile n’est pas une exception C++ ; il s’agit d’une exception structurée. Au lieu d’utiliser la gestion des exceptions C++, vous devez utiliser la [gestion des exceptions structurée](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Notes

**_alloca** alloue des octets de *taille* à partir de la pile du programme. L’espace alloué est automatiquement libéré lorsque la fonction appelante se termine (et non lorsque l’allocation passe simplement hors de portée). Par conséquent, ne transmettez pas la valeur de pointeur retournée par **_alloca** en tant qu’argument pour [libérer](free.md).

Il existe des restrictions relatives à l’appel explicite de **_alloca** dans un gestionnaire d’exceptions (Eh). Les routines EH qui s’exécutent sur des processeurs de classe x86 opèrent dans le cadre de leur propre mémoire : elles effectuent leurs tâches dans un espace mémoire qui n’est pas basé sur l’emplacement actuel du pointeur de pile de la fonction englobante. Les implémentations les plus courantes incluent les expressions de gestion des exceptions structurées Windows NT (SEH) et les expressions de clause catch C++. Par conséquent, l’appel explicite de **_alloca** dans l’un des scénarios suivants entraîne l’échec d’un programme pendant le retour à la routine Eh appelante :

- Expression de filtre d’exception SEH Windows NT : `__except ( _alloca() )`

- Gestionnaire d’exception finale SEH Windows NT : `__finally { _alloca() }`

- Expression de clause catch EH C++

Toutefois, **_alloca** peut être appelée directement à partir d’une routine Eh ou à partir d’un rappel fourni par l’application qui est appelé par l’un des scénarios Eh précédemment listés.

> [!IMPORTANT]
> Dans Windows XP, si **_alloca** est appelée à l’intérieur d’un bloc try/catch, vous devez appeler [_resetstkoflw](resetstkoflw.md) dans le bloc catch.

Outre les restrictions ci-dessus, lorsque vous utilisez l’option[/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , **_alloca** ne peut pas être utilisé dans les blocs **__except** . Pour plus d’informations, consultez [Restrictions de /clr](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Configuration requise pour

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

    // If an exception occurred with the _alloca function
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
