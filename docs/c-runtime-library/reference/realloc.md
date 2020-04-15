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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 964c465a95d44de9d8a4d399f23ec43f8a3a6692
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332934"
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

*Taille*<br/>
Nouvelle taille en octets.

## <a name="return-value"></a>Valeur de retour

**réaffecter** retourne un pointeur **vide** au bloc de mémoire réaffecté (et peut-être déplacé).

S’il n’y a pas assez de mémoire disponible pour étendre le bloc à la taille donnée, le bloc d’origine est laissé inchangé, et **NULL** est retourné.

Si *la taille* est nulle, alors le bloc pointé vers le *memblock* est libéré; la valeur de retour est **NULL**, et *memblock* est laissé pointant vers un bloc libéré.

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur à un type autre que **vide,** utilisez un type de fonte sur la valeur de retour.

## <a name="remarks"></a>Notes

La fonction **de réaffectation** modifie la taille d’un bloc mémoire alloué. *L’argument memblock* indique le début du bloc de mémoire. Si *memblock* est **NULL**, **réaffecter** se comporte de la même manière que **malloc** et alloue un nouveau bloc d’octets de *taille.* Si *memblock* n’est pas **NULL**, il devrait être un pointeur retourné par un appel précédent à **calloc**, **malloc**, ou **réaffecter**.

*L’argument de taille* donne la nouvelle taille du bloc, dans les octets. Le contenu du bloc est inchangé tant que la plus courte des tailles nouvelle et ancienne n’est pas atteinte, même si le nouveau bloc peut se trouver à un autre emplacement. Parce que le nouveau bloc peut être dans un nouvel emplacement de mémoire, le pointeur retourné par **réaffectation n’est** pas garanti d’être le pointeur passé par l’argument *memblock.* **réaffecter** ne zéro mémoire nouvellement allouée dans le cas de la croissance tampon.

**réaffectation** définit **errno** à **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**réaffecter** les appels **malloc** afin d’utiliser la fonction [de _set_new_mode](set-new-mode.md) de C pour définir le nouveau mode de manutention. Le nouveau mode de manutention indique si, en cas de défaillance, **malloc** est d’appeler la nouvelle routine de gestionnaire tel que défini par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la nouvelle routine de gestionnaire sur l’omission d’allouer la mémoire. Vous pouvez passer outre à ce comportement par défaut de sorte que, lorsque **la réaffectation** ne parvient pas à allouer la mémoire, **malloc** appelle la nouvelle routine de gestionnaire de la même manière que le **nouvel** opérateur fait quand il échoue pour la même raison. Pour ce faire, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec NEWMODE.OBJ (consultez [Options de lien](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version débogéque des bibliothèques C run-time, **réaffecter résout** à [_realloc_dbg](realloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**réaffectation** est marquée `__declspec(noalias)` et `__declspec(restrict)`, ce qui signifie que la fonction est garantie de ne pas modifier les variables globales, et que le pointeur retourné n’est pas alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
