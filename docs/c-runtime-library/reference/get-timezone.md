---
title: _get_timezone | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_timezone
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
- _get_timezone
- get_timezone
dev_langs:
- C++
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 111cbff00d1f6119fbd806cc5fc3d14c28a7d7c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398274"
---
# <a name="gettimezone"></a>_get_timezone

Récupère la différence en secondes entre le temps universel coordonné (UTC) et l’heure locale.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_timezone(
    long* seconds
);
```

### <a name="parameters"></a>Paramètres

*Secondes*<br/>
Différence en secondes entre l’heure UTC et l’heure locale.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite ou une **errno** valeur si une erreur se produit.

## <a name="remarks"></a>Notes

Le **_get_timezone** fonction récupère la différence en secondes entre l’heure UTC et l’heure locale en tant qu’entier. La valeur par défaut est de 28 800 secondes, pour l’heure du Pacifique (huit heures après l’heure UTC).

Si *secondes* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **EINVAL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_timezone**|\<time.h>|

Pour plus d'informations, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_tzname](get-tzname.md)<br/>
