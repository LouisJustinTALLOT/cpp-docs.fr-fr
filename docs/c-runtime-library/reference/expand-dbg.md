---
title: _expand_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _expand_dbg
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
apitype: DLLExport
f1_keywords:
- expand_dbg
- _expand_dbg
dev_langs: C++
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6062cec95c2471408db4e67f97dac4fddb5233e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="expanddbg"></a>_expand_dbg
Redimensionne un bloc de mémoire spécifié dans le tas en étendant ou en réduisant le bloc (version de débogage uniquement).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_expand_dbg(   
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `userData`  
 Pointeur vers le bloc de mémoire précédemment alloué.  
  
 `newSize`  
 Nouvelle taille demandée pour le bloc (en octets).  
  
 `blockType`  
 Type demandé pour le bloc redimensionné : `_CLIENT_BLOCK` ou `_NORMAL_BLOCK`.  
  
 `filename`  
 Pointeur désignant le nom du fichier source qui a demandé l’opération d’extension ou `NULL`.  
  
 `linenumber`  
 Numéro de ligne dans le fichier source où l’opération d’extension a été demandée ou `NULL`.  
  
 Les paramètres `filename` et `linenumber` sont disponibles uniquement quand `_expand_dbg` a été appelée explicitement ou quand la constante du préprocesseur [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) a été définie.  
  
## <a name="return-value"></a>Valeur de retour  
 Si l’opération réussit, `_expand_dbg` retourne un pointeur désignant le bloc de mémoire redimensionné. Étant donné que la mémoire n’est pas déplacée, l’adresse est identique à userData. Si une erreur s’est produite ou que le bloc n’a pas pu être étendu à la taille demandée, la fonction retourne `NULL`. En cas d’échec, `errno` comporte des informations issues du système d’exploitation sur la nature de l’échec. Pour plus d’informations sur `errno`, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Notes  
 La fonction `_expand_dbg` est une version de débogage de la fonction _[expand](../../c-runtime-library/reference/expand.md). Quand [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à `_expand_dbg` est réduit à un appel à `_expand`. `_expand` et `_expand_dbg` redimensionnent toutes deux un bloc de mémoire dans le tas de base, mais `_expand_dbg` gère plusieurs fonctionnalités de débogage : des mémoires tampons de chaque côté de la partie utilisateur du bloc pour vérifier la présence de fuites, un paramètre de type de bloc pour effectuer le suivi de types d’allocation spécifiques et des informations `filename`/`linenumber` pour déterminer l’origine des demandes d’allocation.  
  
 `_expand_dbg` redimensionne le bloc de mémoire spécifié avec un peu plus d’espace que la valeur `newSize` demandée. `newSize` peut être inférieure ou supérieure à la taille du bloc de mémoire alloué initialement. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. Le redimensionnement s’effectue en étendant ou en réduisant le bloc de mémoire d’origine. `_expand_dbg` ne déplace pas le bloc de mémoire, comme le fait la fonction [_realloc_dbg](../../c-runtime-library/reference/realloc-dbg.md).  
  
 Quand `newSize` est supérieur à la taille du bloc d’origine, le bloc de mémoire est étendu. Pendant une extension, si le bloc de mémoire ne peut pas être étendu à la taille demandée, `NULL` est retourné. Quand `newSize` est inférieur à la taille du bloc d’origine, le bloc de mémoire est réduit jusqu’à ce que la nouvelle taille soit obtenue.  
  
 Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, consultez [Détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans une build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
 Cette fonction valide ses paramètres. Si `memblock` est un pointeur null ou que la taille est supérieure à `_HEAP_MAXREQ`, cette fonction appelle un gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l'exécution est autorisée à se poursuivre, `errno` a la valeur `EINVAL` et la fonction retourne une valeur `NULL`.  
  
## <a name="requirements"></a>Spécifications  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_expand_dbg`|\<crtdbg.h>|  
  
 Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliothèques  
 Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Exemple  
  
```  
// crt_expand_dbg.c  
//  
// This program allocates a block of memory using _malloc_dbg  
// and then calls _msize_dbg to display the size of that block.  
// Next, it uses _expand_dbg to expand the amount of  
// memory used by the buffer and then calls _msize_dbg again to  
// display the new amount of memory allocated to the buffer.  
//  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   long *buffer;  
   size_t size;  
  
   // Call _malloc_dbg to include the filename and line number  
   // of our allocation request in the header  
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if( buffer == NULL )  
      exit( 1 );  
  
   // Get the size of the buffer by calling _msize_dbg  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
   // Expand the buffer using _expand_dbg and show the new size  
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
   if( buffer == NULL )  
      exit( 1 );  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",  
           size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after _malloc_dbg of 40 longs: 160  
Size of block after _expand_dbg of 1 more long: 164  
```  
  
## <a name="comment"></a>Commentaire  
 La sortie de ce programme dépend de la capacité de votre ordinateur à étendre toutes les sections. Si toutes les sections sont étendues, la sortie est reflétée dans la section de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Routines de débogage](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)