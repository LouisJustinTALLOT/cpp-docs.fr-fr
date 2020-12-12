---
description: 'En savoir plus sur : _fwrite_nolock'
title: _fwrite_nolock
ms.date: 4/2/2020
api_name:
- _fwrite_nolock
- _o__fwrite_nolock
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
- _fwrite_nolock
- fwrite_nolock
helpviewer_keywords:
- fwrite_nolock function
- streams, writing data to
- _fwrite_nolock function
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
ms.openlocfilehash: 6b80933756c930403cbba464fb4921266b0d618f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273733"
---
# <a name="_fwrite_nolock"></a>_fwrite_nolock

Écrit des données dans un flux, sans verrouiller le thread.

## <a name="syntax"></a>Syntaxe

```C
size_t _fwrite_nolock(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Pointeur désignant les données à écrire.

*size*<br/>
Taille de l’élément en octets.

*count*<br/>
Nombre maximal d'éléments à écrire.

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur renvoyée

Identique à [fwrite](fwrite.md).

## <a name="remarks"></a>Notes

Cette fonction est une version sans verrouillage de **fwrite**. Elle est identique à **fwrite** , à ceci près qu’elle n’est pas protégée contre les interférences par d’autres threads. Elle peut être plus rapide, car elle n’entraîne pas la charge liée au verrouillage des autres threads. Utilisez cette fonction uniquement dans les contextes thread-safe, par exemple avec les applications monothread ou lorsque la portée appelante gère déjà l’isolation des threads.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fwrite_nolock**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [fread](fread.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fread](fread.md)<br/>
[_write](write.md)<br/>
