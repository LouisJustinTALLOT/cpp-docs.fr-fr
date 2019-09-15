---
title: _RTC_SetErrorType
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
ms.openlocfilehash: 6c1eff5920931aa3b72bf3dbc6232c371828b16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948923"
---
# <a name="_rtc_seterrortype"></a>_RTC_SetErrorType

Associe une erreur qui est détectée par les vérifications d’erreurs au moment de l’exécution (RTC) avec un type. Votre gestionnaire d’erreurs traite la sortie des erreurs du type spécifié.

## <a name="syntax"></a>Syntaxe

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>Paramètres

*errnum*<br/>
Nombre compris entre zéro et un, inférieur à la valeur retournée par [_RTC_NumErrors](rtc-numerrors.md).

*ErrType*<br/>
Valeur à affecter à ce *errnum*. Par exemple, vous pouvez utiliser une virgule **_CRT_ERROR**. Si vous utilisez _ **CrtDbgReport** comme gestionnaire d’erreurs, *ErrType* peut uniquement être l’un des symboles définis dans _ [CrtSetReportMode](crtsetreportmode.md). Si vous disposez de votre propre gestionnaire d’erreurs ([_RTC_SetErrorFunc](rtc-seterrorfunc.md)), vous pouvez avoir autant d’ *ErrType*qu’il y a d’ *errnum*.

Un *ErrType* de _RTC_ERRTYPE_IGNORE a une signification particulière pour _ **CrtSetReportMode**; l’erreur est ignorée.

## <a name="return-value"></a>Valeur de retour

Valeur précédente pour le *type*d’erreur.

## <a name="remarks"></a>Notes

Par défaut, toutes les erreurs sont définies sur *ErrType* = 1, qui correspond à **_CRT_ERROR**. Pour plus d’informations sur les types d’erreur par défaut tels que **_CRT_ERROR**, consultez [_CrtDbgReport](crtdbgreport-crtdbgreportw.md).

Avant d’appeler cette fonction, vous devez d’abord appeler une des fonctions d’initialisation de vérification d’erreurs au moment de l’exécution. Consultez [Utilisation de contrôles d’exécution sans la bibliothèque Runtime C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Vérifications des erreurs au moment de l’exécution](../../c-runtime-library/run-time-error-checking.md)<br/>
