---
description: 'En savoir plus sur : _get_doserrno'
title: _get_doserrno
ms.date: 4/2/2020
api_name:
- _get_doserrno
- _o__get_doserrno
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: ecd2dd79fa50cc8b723556399c7a637ce59e8461
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341462"
---
# <a name="_get_doserrno"></a>_get_doserrno

Obtient la valeur d’erreur retournée par le système d’exploitation avant qu’elle ne soit traduite en valeur **errno** .

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Pointeur vers un entier à remplir avec la valeur actuelle de la macro globale **_doserrno** .

## <a name="return-value"></a>Valeur renvoyée

Si **_get_doserrno** fonctionne, elle retourne zéro ; en cas d’échec, elle retourne un code d’erreur. Si *pValue* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **EINVAL**.

## <a name="remarks"></a>Notes

La macro globale **_doserrno** est définie sur zéro pendant l’initialisation du CRT, avant le début de l’exécution du processus. Elle prend la valeur d'erreur du système d'exploitation retournée par tout appel de fonction au niveau système qui retourne une erreur de système d'exploitation, et elle n'est jamais réinitialisée à zéro pendant l'exécution. Quand vous écrivez du code pour vérifier la valeur d’erreur retournée par une fonction, effacez toujours **_doserrno** à l’aide de [_set_doserrno](set-doserrno.md) avant l’appel de fonction. Comme un autre appel de fonction peut remplacer **_doserrno**, vérifiez la valeur à l’aide de **_get_doserrno** immédiatement après l’appel de fonction.

Nous vous recommandons [_get_errno](get-errno.md) au lieu de **_get_doserrno** pour les codes d’erreur portables.

Les valeurs possibles de **_doserrno** sont définies dans \<errno.h> .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** est une extension Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
