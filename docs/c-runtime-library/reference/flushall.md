---
title: _flushall
ms.date: 4/2/2020
api_name:
- _flushall
- _o__flushall
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: 93181c0fe941a1c5e259e706771495666329bcb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346618"
---
# <a name="_flushall"></a>_flushall

Vide tous les flux ; efface toutes les mémoires tampons.

## <a name="syntax"></a>Syntaxe

```C
int _flushall( void );
```

## <a name="return-value"></a>Valeur de retour

**_flushall** renvoie le nombre de flux ouverts (entrée et sortie). Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Par défaut, la fonction **_flushall** écrit aux fichiers appropriés le contenu de tous les tampons associés aux flux de sortie ouverts. Le contenu de toutes les mémoires tampons associées aux flux d’entrée ouverts est effacé. (Ces mémoires tampons sont normalement gérées par le système d’exploitation, qui détermine à quel moment les données doivent être automatiquement écrites sur le disque : quand une mémoire tampon est saturée, quand un flux est fermé ou quand un programme se termine normalement sans fermer les flux.)

Si une lecture suit un appel à **_flushall,** de nouvelles données sont lues à partir des fichiers d’entrée dans les tampons. Tous les flux restent ouverts après l’appel à **_flushall**.

La fonctionnalité de validation sur disque de la bibliothèque runtime garantit que les données critiques sont écrites directement sur le disque plutôt que dans les mémoires tampons du système d’exploitation. Sans réécrire un programme existant, vous pouvez activer cette fonctionnalité en reliant les fichiers d’objets du programme à Commode.obj. Dans le fichier exécutable qui en résulte, les appels pour **_flushall** écrire le contenu de tous les tampons sur disque. Seuls **_flushall** et [fflush](fflush.md) sont affectés par Commode.obj.

Pour plus d’informations sur le contrôle de la fonctionnalité de validation sur disque, consultez [E/S de flux](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) et [_fdopen](fdopen-wfdopen.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
