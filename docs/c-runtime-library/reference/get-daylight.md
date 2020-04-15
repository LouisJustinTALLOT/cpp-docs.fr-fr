---
title: _get_daylight
ms.date: 4/2/2020
api_name:
- __daylight
- _get_daylight
- _o___daylight
- _o__get_daylight
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
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: 0abab77b1429b263c7e5d84a6d395f0411ebf8a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345303"
---
# <a name="_get_daylight"></a>_get_daylight

Récupère le décalage de l'heure d'été en heures.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Paramètres

*Heures*<br/>
Décalage en heures de l'heure d'été.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de succès ou d’une valeur **d’errno** en cas d’erreur.

## <a name="remarks"></a>Notes

La fonction **_get_daylight** récupère le nombre d’heures d’heure d’été en tant qu’intégrant. Si l'heure d'été est en vigueur, le décalage par défaut est d'une heure (même si quelques régions observent un décalage de deux heures).

Si *les heures* sont **NULL**, le gestionnaire de paramètre invalide est invoqué comme décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et retourne **EINVAL**.

Nous vous recommandons d’utiliser cette fonction au lieu de la macro **_daylight** ou la fonction dépréciée **__daylight**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
