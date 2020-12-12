---
description: 'En savoir plus sur : _RTC_SetErrorFunc'
title: _RTC_SetErrorFunc
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorFunc
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
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
ms.openlocfilehash: 454fd54e0960e8ce52c94b4e4a1e0a93ea99d3eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268936"
---
# <a name="_rtc_seterrorfunc"></a>_RTC_SetErrorFunc

Désigne une fonction comme gestionnaire pour signaler les vérifications d’erreurs au moment de l’exécution (RTC). Cette fonction est déconseillée ; Utilisez à la place **_RTC_SetErrorFuncW** .

## <a name="syntax"></a>Syntaxe

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>Paramètres

*function*<br/>
L’adresse de la fonction qui va gérer les vérifications d’erreurs au moment de l’exécution.

## <a name="return-value"></a>Valeur renvoyée

La fonction d’erreur définie précédemment. S’il n’existe aucune fonction définie précédemment, retourne la **valeur null**.

## <a name="remarks"></a>Notes

N’utilisez pas cette fonction. Utilisez plutôt **_RTC_SetErrorFuncW**. Elle est conservée uniquement pour assurer la compatibilité descendante.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Vérification des erreurs au moment de l’exécution](../../c-runtime-library/run-time-error-checking.md)<br/>
