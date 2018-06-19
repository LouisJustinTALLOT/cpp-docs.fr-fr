---
title: _flushall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _flushall
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _flushall
dev_langs:
- C++
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb094e2f99e0554320df69946470f42f461819d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398020"
---
# <a name="flushall"></a>_flushall

Vide tous les flux ; efface toutes les mémoires tampons.

## <a name="syntax"></a>Syntaxe

```C
int _flushall( void );
```

## <a name="return-value"></a>Valeur de retour

**_flushall** renvoie le nombre de flux ouverts (entrées et sorties). Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Par défaut, le **_flushall** fonction écrit dans le contenu de toutes les mémoires tampons associés au flux de sortie les fichiers appropriés. Le contenu de toutes les mémoires tampons associées aux flux d’entrée ouverts est effacé. (Ces mémoires tampons sont normalement gérées par le système d’exploitation, qui détermine à quel moment les données doivent être automatiquement écrites sur le disque : quand une mémoire tampon est saturée, quand un flux est fermé ou quand un programme se termine normalement sans fermer les flux.)

Si une lecture suit un appel à **_flushall**, nouvelles données sont en lecture à partir des fichiers d’entrée dans les tampons. Tous les flux restent ouverts après l’appel à **_flushall**.

La fonctionnalité de validation sur disque de la bibliothèque runtime garantit que les données critiques sont écrites directement sur le disque plutôt que dans les mémoires tampons du système d’exploitation. Sans réécrire un programme existant, vous pouvez activer cette fonctionnalité en liant les fichiers objets du programme avec Commode.obj. Dans le fichier exécutable résultant, les appels à **_flushall** écrire le contenu de toutes les mémoires tampons sur le disque. Uniquement **_flushall** et [fflush](fflush.md) sont affectées par Commode.obj.

Pour plus d’informations sur le contrôle de la fonctionnalité de validation sur disque, consultez [E/S de flux](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) et [_fdopen](fdopen-wfdopen.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
