---
title: _get_pgmptr
ms.date: 4/2/2020
api_name:
- _get_pgmptr
- _o__get_pgmptr
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: efcac6a64c01bee38a3753bdec378dae625db35e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345023"
---
# <a name="_get_pgmptr"></a>_get_pgmptr

Obtient la valeur actuelle de la **variable mondiale _pgmptr.**

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Un pointeur à une chaîne à remplir avec la valeur actuelle de la **variable _pgmptr.**

## <a name="return-value"></a>Valeur de retour

Retourne zéro si l'opération a réussi et un code d'erreur en cas d'échec. Si *pValue* est **NULL**, le gestionnaire de paramètres invalides est invoqué comme décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et retourne **EINVAL**.

## <a name="remarks"></a>Notes

Appelez **uniquement _get_pgmptr** si votre programme a un point d’entrée étroit, comme **principal ()** ou **WinMain()**. La **variable mondiale _pgmptr** contient toute la voie vers l’exécutable associée au processus. Pour plus d’informations, consultez [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_get_wpgmptr](get-wpgmptr.md)<br/>
