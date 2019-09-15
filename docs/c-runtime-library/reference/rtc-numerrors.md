---
title: _RTC_NumErrors
ms.date: 11/04/2016
api_name:
- _RTC_NumErrors
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _RTC_NumErrors
- RTC_NumErrors
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
ms.openlocfilehash: 72056208ca6d714f788ae325b90786f5be4ab443
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949033"
---
# <a name="_rtc_numerrors"></a>_RTC_NumErrors

Retourne le nombre total d’erreurs détectées par les vérifications d’erreurs au moment de l’exécution. Vous pouvez utiliser ce nombre comme contrôle dans une boucle **for**, où chaque valeur de la boucle est transmise à [_RTC_GetErrDesc](rtc-geterrdesc.md).

## <a name="syntax"></a>Syntaxe

```C

int _RTC_NumErrors( void );
```

## <a name="return-value"></a>Valeur de retour

Un entier dont la valeur représente le nombre total d’erreurs qui peuvent être détectées par les vérifications d’erreurs au moment de l’exécution de Visual C++.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_RTC_NumErrors**|\<rtcapi.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Vérifications des erreurs au moment de l’exécution](../../c-runtime-library/run-time-error-checking.md)<br/>
