---
title: _get_daylight | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __daylight
- _get_daylight
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_daylight
- _get_daylight
dev_langs:
- C++
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fbe7e36db2e5ca5365f43dc23281d9b5e79077d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398121"
---
# <a name="getdaylight"></a>_get_daylight

Récupère le décalage de l'heure d'été en heures.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Paramètres

*Heures*<br/>
Décalage en heures de l'heure d'été.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite ou une **errno** valeur si une erreur se produit.

## <a name="remarks"></a>Notes

Le **_get_daylight** fonction récupère le nombre d’heures à l’heure sous forme d’entier. Si l'heure d'été est en vigueur, le décalage par défaut est d'une heure (même si quelques régions observent un décalage de deux heures).

Si *heures* est **NULL**, le Gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **EINVAL**.

Nous vous recommandons d’utiliser cette fonction au lieu de la macro **_daylight** ou la fonction déconseillée **__daylight**.

## <a name="requirements"></a>Spécifications

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
