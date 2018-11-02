---
title: _fflush_nolock
ms.date: 11/04/2016
apiname:
- _fflush_nolock
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
- fflush_nolock
- _fflush_nolock
helpviewer_keywords:
- fflush_nolock function
- _fflush_nolock function
- streams, flushing
- flushing
ms.assetid: 5e33c4a1-b10c-4001-ad01-210757919291
ms.openlocfilehash: 721098899525df02dc3b3d121cf894f8056fcb98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464101"
---
# <a name="fflushnolock"></a>_fflush_nolock

Vide un flux sans verrouiller le thread.

## <a name="syntax"></a>Syntaxe

```C
int _fflush_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Consultez [fflush](fflush.md).

## <a name="remarks"></a>Notes

Cette fonction est une version sans verrouillage de **fflush**. Il est identique à **fflush** , à ceci près qu’il n’est pas protégé contre les interférences par d’autres threads. Elle peut être plus rapide, car elle n’entraîne pas la charge liée au verrouillage des autres threads. Utilisez cette fonction uniquement dans les contextes thread-safe, par exemple avec les applications monothread ou lorsque la portée appelante gère déjà l’isolation des threads.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fflush_nolock**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
