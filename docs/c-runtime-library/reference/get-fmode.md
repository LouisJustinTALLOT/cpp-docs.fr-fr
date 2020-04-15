---
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: fbaa30d0842400037f37508df94726f3e7fd7090
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345167"
---
# <a name="_get_fmode"></a>_get_fmode

Obtient le mode de traduction de fichier par défaut pour les opérations d’E/S de fichier.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Paramètres

*pmode*<br/>
Un pointeur à un intégriste à remplir avec le mode par défaut actuel: **_O_TEXT** ou **_O_BINARY**.

## <a name="return-value"></a>Valeur de retour

Retourne zéro si l'opération a réussi et un code d'erreur en cas d'échec. Si *le pmode* est **NULL**, le gestionnaire de paramètre invalide est invoqué tel que décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction renvoie **EINVAL**.

## <a name="remarks"></a>Notes

La fonction obtient la valeur de la variable globale [_fmode](../../c-runtime-library/fmode.md). Cette variable spécifie le mode de traduction de fichiers par défaut pour les opérations I/O de fichier de bas niveau et de flux, telles que **_open**, **_pipe**, **fopen**, et [freopen](freopen-wfreopen.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Voir aussi

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[Fichier de texte et de mode binaire I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
