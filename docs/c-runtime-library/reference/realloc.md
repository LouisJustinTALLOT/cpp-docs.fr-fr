---
title: realloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6452d14e0a8630c68d5e179fd94d531db1b667ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408092"
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

**realloc** retourne un **void** pointeur vers le bloc de mémoire réalloué (et éventuellement déplacé).

S’il n’est pas suffisamment de mémoire pour étendre le bloc à la taille donnée, le bloc d’origine reste inchangé, et **NULL** est retourné.

Si *taille* est zéro, le bloc désigné par *memblock* est libérée ; la valeur de retour est **NULL**, et *memblock* pointe sur un blocs libérés.

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que **void**, utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

Le **realloc** fonction modifie la taille d’un bloc de mémoire alloué. Le *memblock* argument pointe vers le début du bloc de mémoire. Si *memblock* est **NULL**, **realloc** se comporte de la même façon que **malloc** et alloue un nouveau bloc de *taille*octets. Si *memblock* n’est pas **NULL**, il doit être un pointeur retourné par un appel précédent à **calloc**, **malloc**, ou **realloc** .

Le *taille* argument donne la nouvelle taille du bloc, en octets. Le contenu du bloc est inchangé tant que la plus courte des tailles nouvelle et ancienne n’est pas atteinte, même si le nouveau bloc peut se trouver à un autre emplacement. Étant donné que le nouveau bloc peut être dans un nouvel emplacement de mémoire, le pointeur retourné par **realloc** n’est pas garanti comme étant le pointeur passé le *memblock* argument. **realloc** ne pas zéro qui vient d’être la mémoire allouée dans le cas de croissance de la mémoire tampon.

**realloc** définit **errno** à **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** appelle **malloc** afin d’utiliser C++ [_set_new_mode](set-new-mode.md) fonction pour définir le nouveau mode de gestionnaire. Le nouveau mode de gestionnaire indique si, en cas d’échec, **malloc** consiste à appeler la routine du gestionnaire en tant que jeu par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine du gestionnaire sur les échecs d’allocation de mémoire. Vous pouvez substituer ce comportement par défaut afin que, lorsque **realloc** ne parvient pas à allouer de la mémoire, **malloc** appelle la routine du Gestionnaire de la même façon que les **nouveau** opérateur est Lorsqu’il échoue pour la même raison. Pour remplacer la valeur par défaut, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec NEWMODE.OBJ (consultez [Options de lien](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version debug des bibliothèques Runtime C, **realloc** se résout en [_realloc_dbg](realloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** est marquée `__declspec(noalias)` et `__declspec(restrict)`, ce qui signifie que la fonction ne peut ne pas modifier les variables globales, et que le pointeur retourné n’est pas un alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

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
[free](free.md)<br/>
[malloc](malloc.md)<br/>
