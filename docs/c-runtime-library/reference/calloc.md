---
title: calloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- calloc
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
- calloc
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6986e1caec25cd544919039f690544af429524af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394884"
---
# <a name="calloc"></a>calloc

Alloue un tableau dans la mémoire avec des éléments initialisés à 0.

## <a name="syntax"></a>Syntaxe

```C
void *calloc(
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Paramètres

*Nombre*<br/>
Nombre d'éléments.

*size*<br/>
Longueur en octets de chaque élément.

## <a name="return-value"></a>Valeur de retour

**calloc** retourne un pointeur vers l’espace alloué. L’espace de stockage désigné par la valeur de retour est obligatoirement aligné correctement pour le stockage de tout type d’objet. Pour obtenir un pointeur vers un type autre que **void**, utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

Le **calloc** fonction alloue de l’espace de stockage pour un tableau de *nombre* éléments, chacun de longueur *taille* octets. Chaque élément est initialisé à 0.

**calloc** définit **errno** à **ENOMEM** si une allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**calloc** appelle **malloc** à utiliser C++ [_set_new_mode](set-new-mode.md) fonction pour définir le nouveau mode de gestionnaire. Le nouveau mode de gestionnaire indique si, en cas d’échec, **malloc** consiste à appeler la routine du gestionnaire en tant que jeu par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine du gestionnaire sur les échecs d’allocation de mémoire. Vous pouvez substituer ce comportement par défaut afin que, lorsque **calloc** ne parvient pas à allouer de la mémoire, **malloc** appelle la routine du Gestionnaire de la même façon que les **nouveau** opérateur est Lorsqu’il échoue pour la même raison. Pour remplacer la valeur par défaut, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec NEWMODE.OBJ (consultez [Options de lien](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version debug des bibliothèques Runtime C, **calloc** se résout en [_calloc_dbg](calloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** est marquée `__declspec(noalias)` et `__declspec(restrict)`, ce qui signifie que la fonction ne peut ne pas modifier les variables globales, et que le pointeur retourné n’est pas un alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

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
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
