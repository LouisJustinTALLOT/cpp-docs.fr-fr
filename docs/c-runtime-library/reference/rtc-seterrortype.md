---
title: _RTC_SetErrorType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83395727b37ea3901e2e3c28d7adb6663f043d12
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32406613"
---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType

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
Valeur à affecter à ce *errnum*. Par exemple, vous pouvez utiliser une virgule **_CRT_ERROR**. Si vous utilisez **_CrtDbgReport** en tant que gestionnaire d’erreurs, *ErrType* ne peut être l’un des symboles définis dans [_CrtSetReportMode](crtsetreportmode.md). Si vous disposez de votre propre gestionnaire d’erreurs ([_RTC_SetErrorFunc](rtc-seterrorfunc.md)), vous pouvez avoir autant d’*ErrType* que d’*errnum*.

Un *ErrType* _rtc_errtype_ignore a une signification particulière pour **_CrtSetReportMode**; l’erreur est ignorée.

## <a name="return-value"></a>Valeur de retour

La valeur précédente pour le type d’erreur *type*.

## <a name="remarks"></a>Notes

Par défaut, toutes les erreurs sont définies sur *ErrType* = 1, qui correspond à **_CRT_ERROR**. Pour plus d’informations sur les types d’erreur par défaut tels que **_CRT_ERROR**, consultez [_CrtDbgReport](crtdbgreport-crtdbgreportw.md).

Avant d’appeler cette fonction, vous devez d’abord appeler une des fonctions d’initialisation de vérification d’erreurs au moment de l’exécution. Consultez [Utilisation de contrôles d’exécution sans la bibliothèque Runtime C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Vérifications des erreurs au moment de l’exécution](../../c-runtime-library/run-time-error-checking.md)<br/>
