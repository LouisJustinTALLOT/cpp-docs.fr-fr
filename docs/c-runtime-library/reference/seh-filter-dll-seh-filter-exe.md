---
title: _seh_filter_dll, _seh_filter_exe
ms.date: 11/04/2016
api_name:
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- XcptFilter
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- corecrt_startup/_seh_filter_exe
- corecrt_startup/_seh_filter_dll
helpviewer_keywords:
- XcptFilter function
- _XcptFilter function
- _seh_filter_dll function
- _seh_filter_exe function
ms.assetid: 747e5963-3a12-4bf5-b5c4-d4c1b6068e15
ms.openlocfilehash: c8c76a4a1d1a39e26f5e78869d3b107578d2085a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948695"
---
# <a name="_seh_filter_dll-_seh_filter_exe"></a>_seh_filter_dll, _seh_filter_exe

Identifie l’exception et l’action associée à entreprendre.

## <a name="syntax"></a>Syntaxe

```C
int __cdecl _seh_filter_dll(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
int __cdecl _seh_filter_exe(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
```

### <a name="parameters"></a>Paramètres

*_ExceptionNum*<br/>
L’identificateur de l’exception.

*_ExceptionPtr*<br/>
Pointeur vers les informations sur l’exception.

## <a name="return-value"></a>Valeur de retour

Entier qui indique l’action à entreprendre, en fonction du résultat du traitement de l’exception.

## <a name="remarks"></a>Notes

Ces méthodes sont appelées par l’expression de filtre d’exception de l’[instruction try-except](../../cpp/try-except-statement.md). La méthode consulte une table interne de constantes pour identifier l’exception, et déterminer l’action appropriée, comme indiqué ici. Les numéros relatifs aux exceptions sont définis dans winnt.h, alors que les numéros relatifs aux signaux sont définis dans signal.h.

|Numéro d’exception (unsigned long)|Numéro de signal|
|----------------------------------------|-------------------|
|STATUS_ACCESS_VIOLATION|SIGSEGV|
|STATUS_ILLEGAL_INSTRUCTION|SIGILL|
|STATUS_PRIVILEGED_INSTRUCTION|SIGILL|
|STATUS_FLOAT_DENORMAL_OPERAND|SIGFPE|
|STATUS_FLOAT_DIVIDE_BY_ZERO|SIGFPE|
|STATUS_FLOAT_INEXACT_RESULT|SIGFPE|
|STATUS_FLOAT_INVALID_OPERATION|SIGFPE|
|STATUS_FLOAT_OVERFLOW|SIGFPE|
|STATUS_FLOAT_STACK_CHECK|SIGFPE|
|STATUS_FLOAT_UNDERFLOW|SIGFPE|

## <a name="requirements"></a>Configuration requise

**En-tête :** corecrt_startup.h

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
