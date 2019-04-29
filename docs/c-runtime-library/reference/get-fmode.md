---
title: _get_fmode
ms.date: 11/04/2016
apiname:
- _get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: dc4740b20ab7283dd8b9f73f458eaba34e582832
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287560"
---
# <a name="getfmode"></a>_get_fmode

Obtient le mode de traduction de fichier par défaut pour les opérations d’E/S de fichier.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Paramètres

*pmode*<br/>
Un pointeur vers un entier à remplir avec le mode par défaut actuel : **_O_TEXT** ou **_O_BINARY**.

## <a name="return-value"></a>Valeur de retour

Retourne zéro si l'opération a réussi et un code d'erreur en cas d'échec. Si *pmode* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **EINVAL**.

## <a name="remarks"></a>Notes

La fonction obtient la valeur de la variable globale [_fmode](../../c-runtime-library/fmode.md). Cette variable Spécifie le mode de traduction de fichier par défaut pour les deux de bas niveau et diffuser les opérations d’e/s de fichier, tel que **_open**, **_pipe**, **fopen**, et [ freopen](freopen-wfreopen.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Voir aussi

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
