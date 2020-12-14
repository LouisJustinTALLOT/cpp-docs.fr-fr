---
description: 'En savoir plus sur : _expand'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 31558bb67266430cc028e37a1e23dff2fa411356
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235959"
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

*size*<br/>
Nouvelle taille en octets.

## <a name="return-value"></a>Valeur renvoyée

**_expand** retourne un pointeur void vers le bloc de mémoire réalloué. **_expand**, contrairement à **realloc**, ne peut pas déplacer un bloc pour modifier sa taille. Ainsi, s’il y a suffisamment de mémoire disponible pour développer le bloc sans le déplacer, le paramètre *memblock* à **_expand** est identique à la valeur de retour.

**_expand** retourne la **valeur null** lorsqu’une erreur est détectée pendant son fonctionnement. Par exemple, si **_expand** est utilisé pour réduire un bloc de mémoire, il peut détecter une altération dans le tas de petits blocs ou un pointeur de bloc non valide et retourner la **valeur null**.

Si la mémoire disponible est insuffisante pour étendre le bloc à la taille donnée sans la déplacer, la fonction retourne la **valeur null**. **_expand** ne retourne jamais un bloc développé à une taille inférieure à celle demandée. Si une défaillance se produit, **errno** indique la nature de la défaillance. Pour plus d’informations sur **errno**, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour vérifier la nouvelle taille de l’élément, utilisez **_msize**. Pour obtenir un pointeur vers un type autre que **`void`** , utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

La fonction **_expand** modifie la taille d’un bloc de mémoire précédemment alloué en tentant de développer ou de contracter le bloc sans déplacer son emplacement dans le tas. Le paramètre *memblock* pointe vers le début du bloc. Le paramètre *Size* donne la nouvelle taille du bloc, en octets. Le contenu du bloc est inchangé jusqu’à la plus courte des tailles nouvelle et ancienne. *memblock* ne doit pas être un bloc qui a été libéré.

> [!NOTE]
> Sur les plateformes 64 bits, **_expand** peut ne pas contracter le bloc si la nouvelle taille est inférieure à la taille actuelle ; en particulier, si le bloc était d’une taille inférieure à 16 Ko et est donc alloué dans le segment de fragmentation faible, **_expand** laisse le bloc inchangé et retourne *memblock*.

Lorsque l’application est liée à une version Debug des bibliothèques Runtime C, **_expand** se résout en [_expand_dbg](expand-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

Cette fonction valide ses paramètres. Si *memblock* est un pointeur null, cette fonction appelle un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**. Si la *taille* est supérieure **à _HEAP_MAXREQ**, **errno** a la valeur **ENOMEM** et la fonction retourne la **valeur null**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
