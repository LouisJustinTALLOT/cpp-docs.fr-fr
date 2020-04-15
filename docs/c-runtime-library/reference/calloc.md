---
title: calloc
description: Le calloc de la fonction de bibliothèque d’exécution C alloue la mémoire zéro-initialisée.
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: fb4f7d6dc059023d34cb0b811edf5dfb48cb7a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333649"
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

*nombre*<br/>
Nombre d'éléments.

*Taille*<br/>
Longueur en octets de chaque élément.

## <a name="return-value"></a>Valeur de retour

**calloc** renvoie un pointeur à l’espace alloué. L’espace de stockage désigné par la valeur de retour est obligatoirement aligné correctement pour le stockage de tout type d’objet. Pour obtenir un pointeur à un type autre que **vide,** utilisez un type de fonte sur la valeur de retour.

## <a name="remarks"></a>Notes

La fonction **calloc** alloue de l’espace de stockage pour un éventail d’éléments de *nombre,* chacun des octets de *taille* de longueur. Chaque élément est initialisé à 0.

**calloc** définit **errno** à **ENOMEM** si une allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Dans la implémentation de Microsoft, si le *nombre* ou la *taille* est nul, **calloc** renvoie un pointeur à un bloc alloué de taille non nulle. Une tentative de lire ou d’écrire à travers le pointeur retourné conduit à un comportement indéfini.

**calloc** utilise la fonction [de _set_new_mode](set-new-mode.md) de Cmd pour définir le nouveau mode *de manutention*. Le nouveau mode de manutention indique si, en cas de défaillance, **calloc** est d’appeler la nouvelle routine de gestionnaire tel que défini par [_set_new_handler](set-new-handler.md). Par défaut, **calloc** n’appelle pas la nouvelle routine de gestionnaire sur l’omission d’allouer la mémoire. Vous pouvez passer outre à ce comportement par défaut de sorte que, lorsque **calloc** ne parvient pas à allouer la mémoire, il appelle la nouvelle routine de gestionnaire de la même manière que le **nouvel** opérateur fait quand il échoue pour la même raison. Pour ce faire, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou un lien avec *NEWMODE. OBJ* (voir [Options de lien](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version débogéque des bibliothèques C run-time, **calloc** se résout à [_calloc_dbg](calloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** est `__declspec(noalias)` `__declspec(restrict)`marqué et , ce qui signifie que la fonction est garantie de ne pas modifier les variables globales, et que le pointeur retourné n’est pas alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
