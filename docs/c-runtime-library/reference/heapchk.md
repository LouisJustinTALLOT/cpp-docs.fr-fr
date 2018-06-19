---
title: _heapchk | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _heapchk
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
- _heapchk
- heapchk
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3fc500ee86bde40def0e1e2d3dd3edad3127daf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399632"
---
# <a name="heapchk"></a>_heapchk

Exécute des vérifications de cohérence sur le tas.

## <a name="syntax"></a>Syntaxe

```C
int _heapchk( void );
```

## <a name="return-value"></a>Valeur de retour

**_heapchk** renvoie un des constantes manifestes entières suivantes définies dans Malloc.h.

|Valeur de retour|Condition|
|-|-|
**_HEAPBADBEGIN**|Les informations d’en-tête initiales sont incorrectes ou introuvables.
**_HEAPBADNODE**|Un nœud incorrect a été trouvé ou le tas est endommagé.
**_HEAPBADPTR**|Le pointeur vers le tas n’est pas valide.
**_HEAPEMPTY**|Le tas n’a pas été initialisé.
**_HEAPOK**|Le tas est cohérent.

En outre, si une erreur se produit, **_heapchk** définit **errno** à **ENOSYS**.

## <a name="remarks"></a>Notes

Le **_heapchk** fonction permet de déboguer les problèmes liés au tas en vérifiant la cohérence minimale du segment de mémoire. Si le système d’exploitation ne prend pas en charge **_heapchk**(par exemple, Windows 98), la fonction retourne **_HEAPOK** et définit **errno** à **ENOSYS**.

## <a name="requirements"></a>Spécifications

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
