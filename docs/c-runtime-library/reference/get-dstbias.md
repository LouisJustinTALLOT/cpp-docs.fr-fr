---
title: _get_dstbias
ms.date: 4/2/2020
api_name:
- _get_dstbias
- __dstbias
- _o___dstbias
- _o__get_dstbias
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: 969b6d2dfd83a1a136fdfb3d17f8f843337b792c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345230"
---
# <a name="_get_dstbias"></a>_get_dstbias

Récupère le décalage de l'heure d'été en secondes.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>Paramètres

*Secondes*<br/>
Décalage en secondes de l'heure d'été.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de succès ou d’une valeur **d’errno** en cas d’erreur.

## <a name="remarks"></a>Notes

La fonction **_get_dstbias** récupère le nombre de secondes en heure d’été en tant qu’intégrant. Si l'heure d'été est en vigueur, le décalage par défaut est de 3 600 secondes, ce qui correspond au nombre de secondes dans une heure (même si quelques régions observent un décalage de deux heures).

Si *les secondes* sont **NULL**, le gestionnaire de paramètre invalide est invoqué comme décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et retourne **EINVAL**.

Nous vous recommandons d’utiliser cette fonction au lieu de la macro **_dstbias** ou la fonction dépréciée **__dstbias**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
