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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ec21e4967d123c988886fa2e6ab996aad83ef206
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919665"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

Obtient la valeur actuelle de la variable globale **_wpgmptr** .

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Pointeur vers une chaîne à remplir avec la valeur actuelle de la variable **_wpgmptr** .

## <a name="return-value"></a>Valeur de retour

Retourne zéro si l'opération a réussi et un code d'erreur en cas d'échec. Si *pValue* a la **valeur null**, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **EINVAL**.

## <a name="remarks"></a>Notes 

Appelez uniquement **_get_wpgmptr** si votre programme a un point d’entrée étendu, tel que **wmain ()** ou **wWinMain ()**. La variable globale **_wpgmptr** contient le chemin d’accès complet au fichier exécutable associé au processus sous la forme d’une chaîne de caractères larges. Pour plus d’informations, consultez [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_get_pgmptr](get-pgmptr.md)<br/>
