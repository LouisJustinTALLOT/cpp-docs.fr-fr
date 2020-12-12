---
description: 'En savoir plus sur : _fflush_nolock'
title: _fflush_nolock
ms.date: 4/2/2020
api_name:
- _fflush_nolock
- _o__fflush_nolock
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fflush_nolock
- _fflush_nolock
helpviewer_keywords:
- fflush_nolock function
- _fflush_nolock function
- streams, flushing
- flushing
ms.assetid: 5e33c4a1-b10c-4001-ad01-210757919291
ms.openlocfilehash: 77b2db1c26a5121b74a8c3b92c50ac41af153802
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289281"
---
# <a name="_fflush_nolock"></a>_fflush_nolock

Vide un flux sans verrouiller le thread.

## <a name="syntax"></a>Syntaxe

```C
int _fflush_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur renvoyée

Consultez [fflush](fflush.md).

## <a name="remarks"></a>Notes

Cette fonction est une version sans verrouillage de **fflush**. Elle est identique à **fflush** , à ceci près qu’elle n’est pas protégée contre les interférences par d’autres threads. Elle peut être plus rapide, car elle n’entraîne pas la charge liée au verrouillage des autres threads. Utilisez cette fonction uniquement dans les contextes thread-safe, par exemple avec les applications monothread ou lorsque la portée appelante gère déjà l’isolation des threads.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fflush_nolock**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
