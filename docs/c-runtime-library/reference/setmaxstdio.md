---
title: _setmaxstdio
ms.date: 11/04/2016
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 58cffedf673e23a69c2d8040071b2e3353ff4502
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445082"
---
# <a name="setmaxstdio"></a>_setmaxstdio

Définit une valeur maximale pour le nombre de fichiers ouverts simultanément le **stdio** niveau.

## <a name="syntax"></a>Syntaxe

```C
int _setmaxstdio(
   int newmax
);
```

### <a name="parameters"></a>Paramètres

*newmax*<br/>
Nouvelle valeur maximale pour le nombre de fichiers ouverts simultanément le **stdio** niveau.

## <a name="return-value"></a>Valeur de retour

Retourne *newmax* en cas de réussite ; sinon -1.

Si *newmax* est inférieure à **_IOB_ENTRIES** ou une version ultérieure, le nombre maximal de handles disponibles dans le système d’exploitation, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [ Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne -1 et affecte **errno** à **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_setmaxstdio** fonction modifie la valeur maximale pour le nombre de fichiers qui peuvent être ouverts simultanément le **stdio** niveau.

Les E/S du Runtime C prennent désormais en charge beaucoup plus de fichiers ouverts sur les plateformes Win32 que dans les versions précédentes. Jusqu'à 2 048 fichiers peuvent être ouvert simultanément au [au niveau lowio](../../c-runtime-library/low-level-i-o.md) (autrement dit, ouvert et accessible au moyen de la **_open**, **_read**, **_write**, et ainsi de suite famille de fonctions d’e/s). Jusqu'à 512 fichiers peuvent être ouvert simultanément au [niveau stdio](../../c-runtime-library/stream-i-o.md) (autrement dit, ouvert et accessible au moyen de la **fopen**, **fgetc**, **fputc** et ainsi de suite de famille de fonctions). La limite de 512 fichiers ouverts à le **stdio** niveau peut être augmenté jusqu'à un maximum de 2 048 par le biais de la **_setmaxstdio** (fonction).

Étant donné que **stdio**-niveau de fonctions, telles que **fopen**, s’appuient sur le **lowio** functions, le nombre maximal de 2 048 est une limite supérieure pour le nombre de simultanément Ouvrez les fichiers accédés via la bibliothèque Runtime C.

> [!NOTE]
> Il est possible que cette limite supérieure soit au-delà de ce qu’une plateforme et une configuration Win32 particulières peuvent prendre en charge.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez [_getmaxstdio](getmaxstdio.md) pour obtenir un exemple d’utilisation de **_setmaxstdio**.

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
