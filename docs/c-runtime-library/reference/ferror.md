---
title: ferror
ms.date: 4/2/2020
api_name:
- ferror
- _o_ferror
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
- ferror
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
ms.openlocfilehash: 8a5e0bfac2069ed016253de4276e772ea7912605
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920150"
---
# <a name="ferror"></a>ferror

Vérifie si une erreur affecte un flux.

## <a name="syntax"></a>Syntaxe

```C
int ferror(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Si aucune erreur ne s’est produite sur le *flux* **, le** cotablit retourne 0. Sinon, elle retourne une valeur différente de zéro. Si Stream a la **valeur null**, il appelle le gestionnaire de paramètre non **valide, comme** décrit dans validation de [paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne 0.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

## <a name="remarks"></a>Notes 

La routine de la **réferrouse** (implémentée en tant que fonction et en tant que macro) teste une erreur de lecture ou d’écriture sur le fichier associé au *flux*. Si une erreur s’est produite, l’indicateur d’erreur pour le flux reste défini jusqu’à ce que le flux soit fermé ou rembobiné, ou jusqu’à ce que **clearerr** soit appelé.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**ferror**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a> Exemple

Consultez l’exemple relatif à [feof](feof.md).

## <a name="see-also"></a>Voir aussi

[Gestion des erreurs](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
