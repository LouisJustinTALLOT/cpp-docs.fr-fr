---
title: _expand | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f709df131ded856881dc171c2e1549d3d5d378e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402349"
---
# <a name="expand"></a>_expand

Modifie la taille d’un bloc de mémoire.

## <a name="syntax"></a>Syntaxe

```C
void *_expand(
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

**_étendre site** retourne un pointeur void vers le bloc de mémoire réalloué. **_étendre site**, contrairement à **realloc**, ne peut pas déplacer un bloc pour modifier sa taille. Par conséquent, s’il existe suffisamment de mémoire disponible pour étendre le bloc sans le déplacer, le *memblock* paramètre **_étendre site** est identique à la valeur de retour.

**_étendre site** retourne **NULL** si une erreur est détectée au cours de son fonctionnement. Par exemple, si **_étendre site** est utilisé pour réduire un bloc de mémoire, il peut détecter une altération dans le tas de petits blocs ou un pointeur de bloc non valide et retourner **NULL**.

Si mémoire disponible insuffisante pour étendre le bloc à la taille donnée sans le déplacer, la fonction retourne **NULL**. **_étendre site** ne retourne jamais un bloc de développé à une taille inférieure à demandée. En cas de défaillance, **errno** indiquant la nature de l’échec. Pour plus d’informations sur **errno**, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour vérifier la nouvelle taille de l’élément, utilisez **_msize**. Pour obtenir un pointeur vers un type autre que **void**, utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

Le **_étendre site** fonction modifie la taille d’un bloc de mémoire précédemment alloué par la tentative de développer ou réduire le bloc sans déplacer son emplacement dans le tas. Le *memblock* paramètre pointe vers le début du bloc. Le *taille* paramètre indique la nouvelle taille du bloc, en octets. Le contenu du bloc est inchangé jusqu’à la plus courte des tailles nouvelle et ancienne. *memblock* ne doit pas être un bloc qui a été libéré.

> [!NOTE]
> Sur les plateformes 64 bits, **_étendre site** peut vous engagez pas le bloc si la nouvelle taille est inférieure à la taille actuelle, en particulier si le bloc a été de taille inférieure à 16 Ko et par conséquent allouée dans le tas de Fragmentation faible, **_étendre site**  quitte le bloc inchangé et retourne *memblock*.

Lorsque l’application est liée à une version debug des bibliothèques Runtime C, **_étendre site** se résout en [_expand_dbg](expand-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

Cette fonction valide ses paramètres. Si *memblock* est un pointeur null, cette fonction appelle un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **NULL**. Si *taille* est supérieur à **_HEAP_MAXREQ**, **errno** a la valeur **ENOMEM** et la fonction retourne **NULL**.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
