---
title: _get_doserrno
ms.date: 11/04/2016
api_name:
- _get_doserrno
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
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 2810ead8bdd7d6c77cb2b55f4f97371bfc9751e6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956036"
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

## <a name="return-value"></a>Valeur de retour

Si **_get_doserrno** a la valeur, elle retourne zéro ; en cas d’échec, elle retourne un code d’erreur. Si *pValue* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **EINVAL**.

## <a name="remarks"></a>Notes

La macro globale **_doserrno** a la valeur zéro pendant l’initialisation du CRT, avant le début de l’exécution du processus. Elle prend la valeur d'erreur du système d'exploitation retournée par tout appel de fonction au niveau système qui retourne une erreur de système d'exploitation, et elle n'est jamais réinitialisée à zéro pendant l'exécution. Quand vous écrivez du code pour vérifier la valeur d’erreur retournée par une fonction, effacez toujours **_doserrno** à l’aide de [_set_doserrno](set-doserrno.md) avant l’appel de fonction. Étant donné qu’un autre appel de fonction peut remplacer **_doserrno**, vérifiez la valeur à l’aide de **_get_doserrno** immédiatement après l’appel de la fonction.

Nous vous recommandons d’utiliser [_get_errno](get-errno.md) au lieu de **_get_doserrno** pour les codes d’erreur portables.

Les valeurs possibles de **_doserrno** sont définies \<dans errno. h >.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** est une extension Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
