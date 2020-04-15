---
title: _fread_nolock
ms.date: 4/2/2020
api_name:
- _fread_nolock
- _o__fread_nolock
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
- _fread_nolock
- fread_nolock
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- fread_nolock function
- _fread_nolock function
- streams [C++], reading data from
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
ms.openlocfilehash: 97b37b4fee85a827faa4b309741afe56d8d0cbb9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346099"
---
# <a name="_fread_nolock"></a>_fread_nolock

Lit des données à partir d’un flux de données, sans verrouiller d’autres threads.

## <a name="syntax"></a>Syntaxe

```C
size_t _fread_nolock(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Emplacement de stockage des données.

*Taille*<br/>
Taille de l’élément en octets.

*count*<br/>
Nombre maximal d’éléments à lire.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Consultez [fread](fread.md).

## <a name="remarks"></a>Notes

Cette fonction est une version non-locking de **fread**. Il est identique à **fread** sauf qu’il n’est pas protégé contre les interférences par d’autres threads. Elle peut être plus rapide, car elle n’entraîne pas la charge liée au verrouillage des autres threads. Utilisez cette fonction uniquement dans les contextes thread-safe, par exemple avec les applications monothread ou lorsque la portée appelante gère déjà l’isolation des threads.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fread_nolock**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
