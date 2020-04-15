---
title: _expand
ms.date: 4/2/2020
api_name:
- _expand
- _o__expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: 7f2a789bc5f475411808bc00a4280b7573b67cf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347554"
---
# <a name="_expand"></a>_expand

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

*Taille*<br/>
Nouvelle taille en octets.

## <a name="return-value"></a>Valeur de retour

**_expand** renvoie un pointeur vide au bloc de mémoire réaffecté. **_expand**, contrairement à **la réaffectation**, ne peut pas déplacer un bloc pour changer sa taille. Ainsi, s’il y a suffisamment de mémoire disponible pour étendre le bloc sans le déplacer, le paramètre *memblock* à **_expand** est le même que la valeur de retour.

**_expand** renvoie **NULL** lorsqu’une erreur est détectée pendant son fonctionnement. Par exemple, si **_expand** est utilisé pour rétrécir un bloc de mémoire, il peut détecter la corruption dans le petit tas de bloc ou un pointeur de bloc invalide et retourner **NULL**.

S’il n’y a pas suffisamment de mémoire disponible pour étendre le bloc à la taille donnée sans le déplacer, la fonction retourne **NULL**. **_expand** ne renvoie jamais un bloc élargi à une taille inférieure à la demande. En cas d’échec, **errno** indique la nature de l’échec. Pour plus d’informations sur **errno**, voir [errno, _doserrno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour vérifier la nouvelle taille de l’article, utilisez **_msize**. Pour obtenir un pointeur à un type autre que **vide,** utilisez un type de fonte sur la valeur de retour.

## <a name="remarks"></a>Notes

La fonction **_expand** modifie la taille d’un bloc de mémoire précédemment attribué en essayant d’étendre ou de contracter le bloc sans déplacer son emplacement dans le tas. Le *paramètre memblock* indique le début du bloc. Le paramètre *de taille* donne la nouvelle taille du bloc, dans les octets. Le contenu du bloc est inchangé jusqu’à la plus courte des tailles nouvelle et ancienne. *memblock* ne devrait pas être un bloc qui a été libéré.

> [!NOTE]
> Sur les plates-formes 64 bits, **_expand** pourrait ne pas contracter le bloc si la nouvelle taille est inférieure à la taille actuelle; en particulier, si le bloc était de moins de 16K de taille et donc alloué dans le tas de faible fragmentation, **_expand** laisse le bloc inchangé et retourne *memblock*.

Lorsque l’application est liée à une version débogé de déboguer des bibliothèques C run-time, **_expand** se résout à [_expand_dbg](expand-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

Cette fonction valide ses paramètres. Si *memblock* est un pointeur nul, cette fonction invoque un gestionnaire de paramètres invalide, tel que décrit dans [La validation des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction renvoie **NULL**. Si *la taille* est supérieure à **_HEAP_MAXREQ,** **errno** est réglé sur **ENOMEM** et la fonction retourne **NULL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
[Gratuit](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
