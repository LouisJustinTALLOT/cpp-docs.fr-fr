---
title: _get_wpgmptr
ms.date: 4/2/2020
api_name:
- _get_wpgmptr
- _o__get_wpgmptr
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
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 1e54d3dbdc837c491f5b39d33a9b8197094ac60b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344865"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

Obtient la valeur actuelle de la **variable mondiale _wpgmptr.**

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Un pointeur à une chaîne à remplir avec la valeur actuelle de la **variable _wpgmptr.**

## <a name="return-value"></a>Valeur de retour

Retourne zéro si l'opération a réussi et un code d'erreur en cas d'échec. Si *pValue* est **NULL**, le gestionnaire de paramètres invalides est invoqué comme décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et retourne **EINVAL**.

## <a name="remarks"></a>Notes

Appelez seulement **_get_wpgmptr** si votre programme a un point d’entrée large, comme **wmain()** ou **wWinMain()**. La **variable mondiale _wpgmptr** contient le chemin complet vers l’exécutable associé au processus comme une chaîne à caractère large. Pour plus d’informations, consultez [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_get_pgmptr](get-pgmptr.md)<br/>
