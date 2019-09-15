---
title: _rmtmp
ms.date: 11/04/2016
api_name:
- _rmtmp
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rmtmp
- _rmtmp
helpviewer_keywords:
- removing temporary files
- _rmtmp function
- files [C++], temporary
- rmtmp function
- files [C++], removing
- temporary files [C++], removing
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
ms.openlocfilehash: 314399cf174974132a3635631162a7ffa89342c4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949160"
---
# <a name="_rmtmp"></a>_rmtmp

Supprime les fichiers temporaires.

## <a name="syntax"></a>Syntaxe

```C

int _rmtmp( void );
```

## <a name="return-value"></a>Valeur de retour

**_rmtmp** retourne le nombre de fichiers temporaires fermés et supprimés.

## <a name="remarks"></a>Notes

La fonction **_rmtmp** nettoie tous les fichiers temporaires dans le répertoire actif. La fonction supprime uniquement les fichiers créés par **tmpfile**; Utilisez-le uniquement dans le même répertoire que celui dans lequel les fichiers temporaires ont été créés.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_rmtmp**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [tmpfile](tmpfile.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_flushall](flushall.md)<br/>
[tmpfile](tmpfile.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
