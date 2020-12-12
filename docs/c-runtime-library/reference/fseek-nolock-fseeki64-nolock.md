---
description: 'En savoir plus sur : _fseek_nolock, _fseeki64_nolock'
title: _fseek_nolock, _fseeki64_nolock
ms.date: 4/2/2020
api_name:
- _fseek_nolock
- _fseeki64_nolock
- _o__fseek_nolock
- _o__fseeki64_nolock
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
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
ms.openlocfilehash: 3a8701dcb7380bee31d1d04aa92209169682e54d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114259"
---
# <a name="_fseek_nolock-_fseeki64_nolock"></a>_fseek_nolock, _fseeki64_nolock

Déplace le pointeur de fichier vers un emplacement spécifié.

## <a name="syntax"></a>Syntaxe

```C
int _fseek_nolock(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64_nolock(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Paramètres

*train*<br/>
Pointeur désignant la structure **FILE**.

*offset*<br/>
Nombre d’octets à partir d’*origin*.

*lancé*<br/>
Position initiale.

## <a name="return-value"></a>Valeur renvoyée

Identique à [fseek](fseek-fseeki64.md) et [_fseeki64](fseek-fseeki64.md), respectivement.

## <a name="remarks"></a>Notes

Ces fonctions sont les versions sans verrouillage de [fseek](fseek-fseeki64.md) et [_fseeki64](fseek-fseeki64.md), respectivement. Celles-ci sont identiques à [fseek](fseek-fseeki64.md) et [_fseeki64](fseek-fseeki64.md) , à ceci près qu’elles ne sont pas protégées contre les interférences par d’autres threads. Ces fonctions peuvent être plus rapides, car elles n’entraînent pas la charge du verrouillage des autres threads. Utilisez ces fonctions uniquement dans les contextes thread-safe, tels que les applications à un seul thread ou lorsque la portée appelante gère déjà l'isolation des threads.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fseek_nolock**, **_fseeki64_nolock**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[Rewind](rewind.md)<br/>
