---
description: 'En savoir plus sur : _RTC_NumErrors'
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
ms.openlocfilehash: df103f5aada8c896669b82abc1b65621597acf1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168707"
---
# <a name="_rtc_numerrors"></a>_RTC_NumErrors

Retourne le nombre total d’erreurs détectées par les vérifications d’erreurs au moment de l’exécution. Vous pouvez utiliser ce nombre comme contrôle dans une **`for`** boucle, où chaque valeur de la boucle est passée à [_RTC_GetErrDesc](rtc-geterrdesc.md).

## <a name="syntax"></a>Syntaxe

```C

int _RTC_NumErrors( void );
```

## <a name="return-value"></a>Valeur de retour

Un entier dont la valeur représente le nombre total d’erreurs qui peuvent être détectées par les vérifications d’erreurs au moment de l’exécution de Visual C++.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_RTC_NumErrors**|\<rtcapi.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Vérification des erreurs au moment de l’exécution](../../c-runtime-library/run-time-error-checking.md)<br/>
