---
title: _heapchk
ms.date: 11/04/2016
api_name:
- _heapchk
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: 857feb66d89d5dc406042478156483ecb86a2474
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954818"
---
# <a name="_heapchk"></a>_heapchk

Exécute des vérifications de cohérence sur le tas.

## <a name="syntax"></a>Syntaxe

```C
int _heapchk( void );
```

## <a name="return-value"></a>Valeur de retour

**_heapchk** retourne l’une des constantes de manifeste entières suivantes définies dans malloc. h.

|Valeur de retour|Condition|
|-|-|
| **_HEAPBADBEGIN** | Les informations d’en-tête initiales sont incorrectes ou introuvables. |
| **_HEAPBADNODE** | Un nœud incorrect a été trouvé ou le tas est endommagé. |
| **_HEAPBADPTR** | Le pointeur vers le tas n’est pas valide. |
| **_HEAPEMPTY** | Le tas n’a pas été initialisé. |
| **_HEAPOK** | Le tas est cohérent. |

En outre, si une erreur se produit, **_heapchk** affecte à **errno** la valeur **ENOSYS**.

## <a name="remarks"></a>Notes

La fonction **_heapchk** permet de déboguer les problèmes liés au tas en vérifiant une cohérence minimale du tas. Si le système d’exploitation ne prend pas en charge **_heapchk**(par exemple, Windows 98), la fonction retourne **_HEAPOK** et définit **errno** sur **ENOSYS**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
