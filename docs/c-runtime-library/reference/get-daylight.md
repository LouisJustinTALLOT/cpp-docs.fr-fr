---
title: _get_daylight
ms.date: 11/04/2016
api_name:
- __daylight
- _get_daylight
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: 9f63d3baa1e9411039d1482b4cbfbf4bce4e9872
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956045"
---
# <a name="_get_daylight"></a>_get_daylight

Récupère le décalage de l'heure d'été en heures.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Paramètres

*travaillé*<br/>
Décalage en heures de l'heure d'été.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite ou une valeur **errno** si une erreur se produit.

## <a name="remarks"></a>Notes

La fonction **_get_daylight** récupère le nombre d’heures de l’heure d’été sous la forme d’un entier. Si l'heure d'été est en vigueur, le décalage par défaut est d'une heure (même si quelques régions observent un décalage de deux heures).

Si *hours* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **EINVAL**.

Nous vous recommandons d’utiliser cette fonction au lieu de la macro **_daylight** ou de la fonction déconseillée **__daylight**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

Pour plus d'informations, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
