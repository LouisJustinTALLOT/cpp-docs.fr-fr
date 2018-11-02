---
title: _get_doserrno
ms.date: 11/04/2016
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
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: d28b9ec47108f7051a908f874584bbfddf5d6a3d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605164"
---
# <a name="getdoserrno"></a>_get_doserrno

Obtient la valeur d’erreur retournée par le système d’exploitation avant qu’il est traduit en une **errno** valeur.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_doserrno( 
   int * pValue 
);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Un pointeur vers un entier à remplir avec la valeur actuelle de la **_doserrno** macro globale.

## <a name="return-value"></a>Valeur de retour

Si **_get_doserrno** réussit, elle retourne zéro ; si elle échoue, elle retourne un code d’erreur. Si *pValue* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **EINVAL**.

## <a name="remarks"></a>Notes

Le **_doserrno** macro globale est définie sur zéro pendant l’initialisation CRT, avant l’exécution commence. Elle prend la valeur d'erreur du système d'exploitation retournée par tout appel de fonction au niveau système qui retourne une erreur de système d'exploitation, et elle n'est jamais réinitialisée à zéro pendant l'exécution. Lorsque vous écrivez du code pour vérifier la valeur d’erreur retourné par une fonction, effacez toujours **_doserrno** à l’aide de [_set_doserrno](set-doserrno.md) avant l’appel de fonction. Car un autre appel de fonction peut remplacer **_doserrno**, vérifiez la valeur à l’aide de **_get_doserrno** immédiatement après l’appel de fonction.

Nous vous recommandons de [_get_errno](get-errno.md) au lieu de **_get_doserrno** pour les codes d’erreurs portables.

Les valeurs possibles de **_doserrno** sont définis dans \<errno.h >.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** est une extension Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
