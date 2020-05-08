---
title: realloc
ms.date: 4/2/2020
api_name:
- realloc
- _o_realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: 15c818ee6f70d02fb9b63f12deef6b1bf3698322
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917942"
---
# <a name="realloc"></a>realloc

Réallouent les blocs de mémoire.

## <a name="syntax"></a>Syntaxe

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Pointeur désignant le bloc de mémoire précédemment alloué.

*size*<br/>
Nouvelle taille en octets.

## <a name="return-value"></a>Valeur de retour

**realloc** retourne un pointeur **void** vers le bloc de mémoire réalloué (et éventuellement déplacé).

Si la mémoire disponible est insuffisante pour étendre le bloc à la taille donnée, le bloc d’origine reste inchangé et la **valeur null** est retournée.

Si la *taille* est égale à zéro, le bloc pointé par *memblock* est libéré ; la valeur de retour est **null**et *memblock* pointe vers un bloc libéré.

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que **void**, utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes 

La fonction **realloc** modifie la taille d’un bloc de mémoire alloué. L’argument *memblock* pointe vers le début du bloc de mémoire. Si *memblock* a la **valeur null**, **realloc** se comporte de la même façon que **malloc** et alloue un nouveau bloc de *taille* octets. Si *memblock* n’a pas la **valeur null**, il doit s’agir d’un pointeur retourné par un appel précédent à **calloc**, **malloc**ou **realloc**.

L’argument *Size* donne la nouvelle taille du bloc, en octets. Le contenu du bloc est inchangé tant que la plus courte des tailles nouvelle et ancienne n’est pas atteinte, même si le nouveau bloc peut se trouver à un autre emplacement. Étant donné que le nouveau bloc peut se trouver dans un nouvel emplacement de mémoire, il n’est pas garanti que le pointeur retourné par **realloc** soit le pointeur transmis via l’argument *memblock* . **realloc** n’a aucune mémoire allouée récemment dans le cas de la croissance de la mémoire tampon.

**realloc** affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** appelle **malloc** afin d’utiliser la fonction de [_set_new_mode](set-new-mode.md) C++ pour définir le nouveau mode de gestionnaire. Le nouveau mode de gestionnaire indique si, en cas d’échec, **malloc** est appelé à appeler la routine de nouveau gestionnaire telle qu’elle est définie par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec d’allocation de mémoire. Vous pouvez remplacer ce comportement par défaut de sorte que, lorsque **realloc** ne parvient pas à allouer de la mémoire, **malloc** appelle la routine de nouveau gestionnaire de la même façon que le **nouvel** opérateur quand il échoue pour la même raison. Pour ce faire, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec NEWMODE.OBJ (consultez [Options de lien](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version Debug des bibliothèques Runtime C, **réallocation** prend la valeur [_realloc_dbg](realloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** est marqué `__declspec(noalias)` et `__declspec(restrict)`, ce qui signifie que la fonction est garantie de ne pas modifier les variables globales et que le pointeur retourné n’a pas d’alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**realloc**|\<stdlib.h> et \<malloc.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Gratuit](free.md)<br/>
[malloc](malloc.md)<br/>
