---
title: _calloc_dbg
ms.date: 11/04/2016
api_name:
- _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
ms.openlocfilehash: eab17348e473a4f642e784defe4569e0e799299e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939317"
---
# <a name="_calloc_dbg"></a>_calloc_dbg

Alloue une série de blocs de mémoire dans le tas avec de l’espace supplémentaire pour un en-tête de débogage et des mémoires tampons de remplacement (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*certain*<br/>
Nombre de blocs de mémoire demandé.

*size*<br/>
Taille de chaque bloc de mémoire demandée (octets).

*blockType*<br/>
Type de bloc de mémoire demandé : _ **client_block** ou **_NORMAL_BLOCK**.

Pour plus d’informations sur les types de blocs d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **null**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **null**.

Les paramètres *filename* et *LineNumber* sont disponibles uniquement lorsque **_calloc_dbg** a été appelé explicitement ou que la constante de préprocesseur _ [CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) a été définie.

## <a name="return-value"></a>Valeur de retour

Une fois l’opération réussie, cette fonction retourne un pointeur vers la partie utilisateur du dernier bloc de mémoire alloué, appelle la nouvelle fonction de gestionnaire ou retourne la **valeur null**. Pour obtenir une description complète du comportement de retour, voir la section Notes. Pour plus d’informations sur l’utilisation de la fonction du nouveau gestionnaire, consultez la fonction [calloc](calloc.md).

## <a name="remarks"></a>Notes

**_calloc_dbg** est une version de débogage de la fonction [calloc](calloc.md) . Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_calloc_dbg** est réduit à un appel à **calloc**. **Calloc** et **_calloc_dbg** allouez des blocs de mémoire de *nombres* dans le tas de base, mais **_calloc_dbg** propose plusieurs fonctionnalités de débogage :

- Mémoires tampons de chaque côté de la partie utilisateur du bloc pour vérifier la présence de fuites

- Paramètre de type de bloc pour effectuer le suivi des types d’allocation spécifiques

- /informations d'*LineNumber* du nom de fichier pour déterminer l’origine des demandes d’allocation.

**_calloc_dbg** alloue chaque bloc de mémoire avec un peu plus d’espace que la *taille*demandée. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. Quand le bloc est alloué, la partie utilisateur du bloc est renseignée avec la valeur 0xCD et chaque mémoire tampon de remplacement est renseignée avec la valeur 0xFD.

**_calloc_dbg** définit **errno** sur **ENOMEM** si une allocation de mémoire échoue ; **EINVAL** est retourné si la quantité de mémoire nécessaire (y compris la surcharge mentionnée précédemment) dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans une build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
