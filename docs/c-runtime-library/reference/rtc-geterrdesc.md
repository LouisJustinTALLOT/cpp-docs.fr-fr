---
title: _RTC_GetErrDesc
ms.date: 11/04/2016
apiname:
- _RTC_GetErrDesc
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
- RTC_GetErrDesc
- _RTC_GetErrDesc
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
ms.openlocfilehash: d164626ea89bbe10f5b2ffe4224bf6381e40bab0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590305"
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc

Retourne une brève description d’un type de vérification d’erreurs au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>Paramètres

*errnum*<br/>
Un nombre entre zéro et un de moins que la valeur retournée par **_RTC_NumErrors**.

## <a name="return-value"></a>Valeur de retour

Une chaîne de caractères qui contient une brève description d’un des types d’erreurs détectées par le système de vérification d’erreurs au moment de l’exécution. Si l’erreur est inférieure à zéro ou supérieur ou égal à la valeur retournée par [_RTC_NumErrors](rtc-numerrors.md), **_RTC_GetErrDesc** retourne **NULL**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[Vérifications des erreurs au moment de l’exécution](../../c-runtime-library/run-time-error-checking.md)<br/>
