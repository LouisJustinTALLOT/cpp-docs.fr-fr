---
title: calloc
description: La fonction de la bibliothèque Runtime C calloc alloue de la mémoire initialisée à zéro.
ms.date: 4/2/2020
api_name:
- calloc
- _o_calloc
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
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: 067ce6f347f4b24ad8c85990e70fe4d79305535c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213630"
---
# <a name="calloc"></a>calloc

Alloue un tableau dans la mémoire avec des éléments initialisés à 0.

## <a name="syntax"></a>Syntaxe

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>Paramètres

*number*<br/>
Nombre d'éléments.

*size*<br/>
Longueur en octets de chaque élément.

## <a name="return-value"></a>Valeur de retour

**calloc** retourne un pointeur vers l’espace alloué. L’espace de stockage désigné par la valeur de retour est obligatoirement aligné correctement pour le stockage de tout type d’objet. Pour obtenir un pointeur vers un type autre que **`void`** , utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

La fonction **calloc** alloue de l’espace de stockage pour un tableau d’éléments *Number* , chacun d’octets de *taille* longueur. Chaque élément est initialisé à 0.

**calloc** affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Dans l’implémentation Microsoft, si le *nombre* ou la *taille* est égal à zéro, **calloc** retourne un pointeur vers un bloc alloué d’une taille différente de zéro. Une tentative de lecture ou d’écriture dans le pointeur retourné provoque un comportement non défini.

**calloc** utilise la fonction C++ [_set_new_mode](set-new-mode.md) pour définir le *nouveau mode de gestionnaire*. Le nouveau mode de gestionnaire indique si, en cas d’échec, **calloc** doit appeler la routine de nouveau gestionnaire telle qu’elle est définie par [_set_new_handler](set-new-handler.md). Par défaut, **calloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec d’allocation de mémoire. Vous pouvez remplacer ce comportement par défaut de sorte que, lorsque **calloc** ne parvient pas à allouer de la mémoire, il appelle la routine de nouveau gestionnaire de la même façon que l' **`new`** opérateur quand il échoue pour la même raison. Pour ce faire, appelez

```C
_set_new_mode(1);
```

tôt dans votre programme, ou lien avec *NEWMODE. OBJ* (consultez [options de liaison](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version Debug des bibliothèques Runtime C, **calloc** est résolu en [_calloc_dbg](calloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** est marqué `__declspec(noalias)` et `__declspec(restrict)` , ce qui signifie que la fonction est garantie de ne pas modifier les variables globales et que le pointeur retourné n’est pas un alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**calloc**|\<stdlib.h> et \<malloc.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[Gratuit](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
