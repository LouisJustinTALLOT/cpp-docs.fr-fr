---
description: 'En savoir plus sur : _get_fmode'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 56716b7e8c12c5a3de79098a8227be31148ae386
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303646"
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
Pointeur vers un entier à remplir avec le mode par défaut actuel : **_O_TEXT** ou **_O_BINARY**.

## <a name="return-value"></a>Valeur renvoyée

Retourne zéro si l'opération a réussi et un code d'erreur en cas d'échec. Si *PMODE* a la **valeur null**, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **EINVAL**.

## <a name="remarks"></a>Notes

La fonction obtient la valeur de la variable globale [_fmode](../../c-runtime-library/fmode.md). Cette variable spécifie le mode de traduction de fichier par défaut pour les opérations d’e/s de fichier de flux et de bas niveau, telles que **_open**, **_pipe**, **fopen** et [freopen](freopen-wfreopen.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
[E/s de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
