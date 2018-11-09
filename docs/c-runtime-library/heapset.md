---
title: _heapset
ms.date: 11/04/2016
apiname:
- _heapset
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _heapset
- heapset
helpviewer_keywords:
- checking heap
- heapset function
- heaps, checking
- debugging [CRT], heap-related problems
- _heapset function
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
ms.openlocfilehash: c93624b8b56fb53eb15263dbd0d203cd9130eacf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528191"
---
# <a name="heapset"></a>_heapset

Vérifie la cohérence minimale des tas et définit les entrées libres sur une valeur spécifiée.

> [!IMPORTANT]
>  Cette fonction est obsolète. Depuis Visual Studio 2015, elle n’est pas disponible dans la bibliothèque CRT.

## <a name="syntax"></a>Syntaxe

```
int _heapset(
   unsigned int fill
);
```

#### <a name="parameters"></a>Paramètres

*fill*<br/>
Caractère de remplissage.

## <a name="return-value"></a>Valeur de retour

`_heapset` retourne une des constantes manifestes entières suivantes définies dans Malloc.h.

|||
|-|-|
| `_HEAPBADBEGIN`  | Informations d’en-tête initiales non valides ou introuvables.  |
| `_HEAPBADNODE`  | Tas endommagé ou nœud incorrect trouvé.  |
| `_HEAPEMPTY`  | Tas non initialisé.  |
| `_HEAPOK`  | Le tas est cohérent.  |

En outre, si une erreur se produit, `_heapset` définit `errno` sur `ENOSYS`.

## <a name="remarks"></a>Notes

La fonction `_heapset` affiche les emplacements de mémoire disponible ou les nœuds qui ont été remplacés accidentellement.

`_heapset` vérifie la cohérence minimale sur le tas, puis définit chaque octet des entrées libres du tas sur la valeur `fill` . Cette valeur connue indique les emplacements de mémoire du tas qui contiennent des nœuds libres et ceux qui contiennent des données qui ont été écrites accidentellement dans de la mémoire libérée. Si le système d’exploitation ne prend pas en charge `_heapset`(par exemple Windows 98), la fonction resururne `_HEAPOK` et définit `errno` sur `ENOSYS`.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|`_heapset`|\<malloc.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../c-runtime-library/compatibility.md) dans l'introduction.

## <a name="example"></a>Exemple

```
// crt_heapset.c
// This program checks the heap and
// fills in free entries with the character 'Z'.

#include <malloc.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int heapstatus;
   char *buffer;

   if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is
      exit( 0 );                        //    initialized
   heapstatus = _heapset( 'Z' );        // Fill in free entries
   switch( heapstatus )
   {
   case _HEAPOK:
      printf( "OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf( "OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
   free( buffer );
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../c-runtime-library/heapadd.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)