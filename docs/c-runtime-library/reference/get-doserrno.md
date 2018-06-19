---
title: _get_doserrno | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_doserrno
- get_doserrno
dev_langs:
- C++
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7cef2c068fad2f18cb1d11d33e551588800cb64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399567"
---
# <a name="getdoserrno"></a>_get_doserrno

Obtient la valeur d’erreur retournée par le système d’exploitation avant qu’il est traduit en un **errno** valeur.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_doserrno( 
   int * pValue 
);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Un pointeur vers un entier doit être remplie avec la valeur actuelle de la **_doserrno** macro globale.

## <a name="return-value"></a>Valeur de retour

Si **_get_doserrno** réussit, elle retourne zéro ; en cas d’échec, elle retourne un code d’erreur. Si *pValue* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **EINVAL**.

## <a name="remarks"></a>Notes

Le **_doserrno** macro globale est définie à zéro pendant l’initialisation CRT, avant l’exécution commence. Elle prend la valeur d'erreur du système d'exploitation retournée par tout appel de fonction au niveau système qui retourne une erreur de système d'exploitation, et elle n'est jamais réinitialisée à zéro pendant l'exécution. Lorsque vous écrivez du code pour vérifier la valeur d’erreur retourné par une fonction, toujours claire **_doserrno** à l’aide de [_set_doserrno](set-doserrno.md) avant l’appel de fonction. Car un autre appel de fonction peut remplacer **_doserrno**, vérifiez la valeur à l’aide de **_get_doserrno** immédiatement après l’appel de fonction.

Nous vous recommandons de [_get_errno](get-errno.md) au lieu de **_get_doserrno** pour les codes d’erreur portable.

Les valeurs possibles de **_doserrno** sont définis dans \<errno.h >.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** est une extension Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
