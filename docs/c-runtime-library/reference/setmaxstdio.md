---
title: _setmaxstdio
ms.date: 05/21/2019
api_name:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 620213b4df9ea555189a1403b3c9e83b55cad6c6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948221"
---
# <a name="_setmaxstdio"></a>_setmaxstdio

Définit un nombre maximal de fichiers ouverts simultanément au niveau des E/S de flux.

## <a name="syntax"></a>Syntaxe

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>Paramètres

*new_max*<br/>
Nouveau nombre maximal de fichiers ouverts simultanément au niveau des E/S de flux.

## <a name="return-value"></a>Valeur de retour

Retourne *new_max* en cas de réussite ; sinon -1.

Si *new_max* est inférieur à **_IOB_ENTRIES**, ou supérieur au nombre maximal de descripteurs disponibles dans le système d’exploitation, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne -1 et définit **errno** sur **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_setmaxstdio** modifie la valeur maximale pour le nombre de fichiers pouvant être ouverts simultanément au niveau des E/S de flux.

Les E/S du Runtime C prennent désormais en charge jusqu’à 8 192 fichiers ouverts simultanément au [niveau d’E/S bas](../../c-runtime-library/low-level-i-o.md). Ce niveau inclut les fichiers ouverts et pour lesquels l’accès est effectué via la famille **_open**, **_read** et **_write** de fonctions d’E/S. Par défaut, jusqu’à 512 fichiers peuvent être ouverts simultanément au [niveau des E/S de flux](../../c-runtime-library/stream-i-o.md). Ce niveau inclut les fichiers ouverts et pour lesquels l’accès est effectué via la famille **fopen**, **fgetc** et **fputc** de fonctions. La limite de 512 fichiers ouverts au niveau des E/S de flux peut être portée à un maximum de 8 192 en utilisant la fonction **_setmaxstdio**.

Sachant que les fonctions du niveau E/S de flux, comme **fopen** s’appuient sur les fonctions de niveau E/S bas, le maximum de 8 192 est une limite supérieure stricte pour le nombre de fichiers ouverts simultanément accessibles via la bibliothèque Runtime C.

> [!NOTE]
> Il est possible que cette limite supérieure soit au-delà de ce qu’une plateforme et une configuration Win32 particulières peuvent prendre en charge.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **_setmaxstdio**, consultez [_getmaxstdio](getmaxstdio.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
