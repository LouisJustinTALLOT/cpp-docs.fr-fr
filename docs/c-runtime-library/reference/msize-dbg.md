---
description: 'En savoir plus sur : _msize_dbg'
title: _msize_dbg
ms.date: 11/04/2016
api_name:
- _msize_dbg
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
- _msize_dbg
- msize_dbg
helpviewer_keywords:
- memory blocks
- _msize_dbg function
- msize_dbg function
ms.assetid: a333f4b6-f8a2-4e61-bb69-cb34063b8cef
ms.openlocfilehash: 8ead0257e990322e88e20ce6111ff590dbc71686
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256391"
---
# <a name="_msize_dbg"></a>_msize_dbg

Calcule la taille d’un bloc de mémoire dans le tas (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
size_t _msize_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Paramètres

*Permanence*<br/>
Pointeur désignant le bloc de mémoire duquel déterminer la taille.

*blockType*<br/>
Type du bloc de mémoire spécifié : **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, **_msize_dbg** retourne la taille (en octets) du bloc de mémoire spécifié. Sinon, elle retourne la **valeur null**.

## <a name="remarks"></a>Notes

**_msize_dbg** est une version de débogage de la fonction _ [MSize](msize.md) . Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_msize_dbg** est réduit à un appel à **_msize**. **_Msize** et **_msize_dbg** calculent la taille d’un bloc de mémoire dans le tas de base, mais **_msize_dbg** ajoute deux fonctionnalités de débogage : elle inclut les mémoires tampons de chaque côté de la partie utilisateur du bloc de mémoire dans la taille retournée et elle autorise les calculs de taille pour des types de bloc spécifiques.

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de blocs d’allocation et sur leur utilisation, consultez [types de blocs sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Cette fonction valide son paramètre. Si *memblock* est un pointeur null, **_msize** appelle un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’erreur est gérée, la fonction affecte à **errno** la valeur **EINVAL** et retourne-1.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_msize_dbg**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_msize_dbg.c
// compile with: /MTd
/*
* This program allocates a block of memory using _malloc_dbg
* and then calls _msize_dbg to display the size of that block.
* Next, it uses _realloc_dbg to expand the amount of
* memory used by the buffer and then calls _msize_dbg again to
* display the new amount of memory allocated to the buffer.
*/

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
        long *buffer, *newbuffer;
        size_t size;

        /*
         * Call _malloc_dbg to include the filename and line number
         * of our allocation request in the header
         */
        buffer = (long *)_malloc_dbg( 40 * sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
        if( buffer == NULL )
               exit( 1 );

        /*
         * Get the size of the buffer by calling _msize_dbg
         */
        size = _msize_dbg( buffer, _NORMAL_BLOCK );
        printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

        /*
         * Reallocate the buffer using _realloc_dbg and show the new size
         */
        newbuffer = _realloc_dbg( buffer, size + (40 * sizeof(long)), _NORMAL_BLOCK, __FILE__, __LINE__ );
        if( newbuffer == NULL )
               exit( 1 );
        buffer = newbuffer;
        size = _msize_dbg( buffer, _NORMAL_BLOCK );
        printf( "Size of block after _realloc_dbg of 40 more longs: %u\n", size );

        free( buffer );
        exit( 0 );
}
```

### <a name="output"></a>Output

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _realloc_dbg of 40 more longs: 320
```

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
