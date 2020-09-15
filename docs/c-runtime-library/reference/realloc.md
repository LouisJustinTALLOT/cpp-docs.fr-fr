---
title: realloc
description: Informations de référence sur l’API pour realloc (); qui réalloue des blocs de mémoire.
ms.date: 9/11/2020
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
ms.openlocfilehash: c68909b2f5d73959465d63af522ceeb00c8ce23e
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075814"
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

*`memblock`*\
Pointeur désignant le bloc de mémoire précédemment alloué.

*`size`*\
Nouvelle taille en octets.

## <a name="return-value"></a>Valeur de retour

**`realloc`** retourne un **`void`** pointeur vers le bloc de mémoire réalloué (et éventuellement déplacé).

Si la mémoire disponible est insuffisante pour étendre le bloc à la taille donnée, le bloc d’origine reste inchangé et **`NULL`** est retourné.

Si *`size`* est égal à zéro, le bloc désigné par *`memblock`* est libéré ; la valeur de retour est **`NULL`** et *`memblock`* pointe vers un bloc libéré.

La valeur de retour pointe vers un espace de stockage qui est correctement aligné pour le stockage de tout type d’objet. Pour obtenir un pointeur vers un type autre que **`void`** , utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

> [!NOTE]
> **`realloc`** n’a pas été mis à jour pour implémenter le comportement C17, car le nouveau comportement n’est pas compatible avec le système d’exploitation Windows.

La **`realloc`** fonction modifie la taille d’un bloc de mémoire alloué. L' *`memblock`* argument pointe vers le début du bloc de mémoire. Si *`memblock`* a **`NULL`** **`realloc`** la forme, se comporte de la même façon que **`malloc`** et alloue un nouveau bloc d' *`size`* octets. Si *`memblock`* n’a pas **`NULL`** la valeur, il doit s’agir d’un pointeur retourné par un appel précédent à **`calloc`** , **`malloc`** ou **`realloc`** .

L' *`size`* argument donne la nouvelle taille du bloc, en octets. Le contenu du bloc est inchangé tant que la plus courte des tailles nouvelle et ancienne n’est pas atteinte, même si le nouveau bloc peut se trouver à un autre emplacement. Étant donné que le nouveau bloc peut se trouver dans un nouvel emplacement de mémoire, il n’est pas garanti que le pointeur retournée par **`realloc`** soit le pointeur transmis via l' *`memblock`* argument. **`realloc`** n’a pas une mémoire qui vient d’être allouée dans le cas de la croissance de la mémoire tampon.

**`realloc`** affecte **`errno`** à **`ENOMEM`** la valeur si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **`_HEAP_MAXREQ`** . Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**`realloc`** appelle afin **`malloc`** d’utiliser la fonction de [_set_new_mode](set-new-mode.md) C++ pour définir le nouveau mode de gestionnaire. Le nouveau mode de gestionnaire indique si, en cas **`malloc`** d’échec, doit appeler la routine de nouveau gestionnaire telle qu’elle est définie par [_set_new_handler](set-new-handler.md). Par défaut, **`malloc`** n’appelle pas la routine de nouveau gestionnaire en cas d’échec d’allocation de mémoire. Vous pouvez remplacer ce comportement par défaut de sorte que, lorsque ne **`realloc`** parvient pas à allouer de la mémoire, **`malloc`** appelle la routine de nouveau gestionnaire de la même façon que l' **`new`** opérateur quand il échoue pour la même raison. Pour ce faire, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec NEWMODE.OBJ (consultez [Options de lien](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version de débogage des bibliothèques Runtime C, **`realloc`** se résout en [_realloc_dbg](realloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**`realloc`** est marqué `__declspec(noalias)` et `__declspec(restrict)` , ce qui signifie que la fonction est garantie de ne pas modifier les variables globales et que le pointeur retourné n’a pas d’alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`realloc`**|\<stdlib.h> et \<malloc.h>|

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

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)\
[calloc](calloc.md)\
[Gratuit](free.md)\
[malloc](malloc.md)
