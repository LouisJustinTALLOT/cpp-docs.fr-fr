---
description: 'En savoir plus sur : _RTC_GetErrDesc'
title: _RTC_GetErrDesc
ms.date: 11/04/2016
api_name:
- _RTC_GetErrDesc
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
- RTC_GetErrDesc
- _RTC_GetErrDesc
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
ms.openlocfilehash: 5e9beccec5e13d6c2c00e3edaefec695a8e16737
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168720"
---
# <a name="_rtc_geterrdesc"></a>_RTC_GetErrDesc

Retourne une brève description d’un type de vérification d’erreurs au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>Paramètres

*ErrNum*<br/>
Un nombre entre zéro et un de moins que la valeur retournée par **_RTC_NumErrors**.

## <a name="return-value"></a>Valeur renvoyée

Une chaîne de caractères qui contient une brève description d’un des types d’erreurs détectées par le système de vérification d’erreurs au moment de l’exécution. Si l’erreur est inférieure à zéro ou supérieure ou égale à la valeur retournée par [_RTC_NumErrors](rtc-numerrors.md), **_RTC_GetErrDesc** retourne la valeur **null**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[Vérification des erreurs au moment de l’exécution](../../c-runtime-library/run-time-error-checking.md)<br/>
