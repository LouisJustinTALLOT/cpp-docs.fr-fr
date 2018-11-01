---
title: _RTC_NumErrors
ms.date: 11/04/2016
apiname:
- _RTC_NumErrors
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
apitype: DLLExport
f1_keywords:
- _RTC_NumErrors
- RTC_NumErrors
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
ms.openlocfilehash: e13f85f2140473d6e971d27abb6012effd36c37c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477192"
---
# <a name="rtcnumerrors"></a>_RTC_NumErrors

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
