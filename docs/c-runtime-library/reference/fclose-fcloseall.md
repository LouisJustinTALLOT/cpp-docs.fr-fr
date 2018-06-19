---
title: fclose, _fcloseall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
dev_langs:
- C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71b98a239cd1a6504611bf436533e7b5fbe1302c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400237"
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall

Ferme un flux de données (**fclose**) ou ferme tous les flux ouverts (**_fcloseall**).

## <a name="syntax"></a>Syntaxe

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Paramètres

*Flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fclose** retourne 0 si le flux est fermé correctement. **_fcloseall** renvoie le nombre total de flux fermé. Les deux fonctions retournent **EOF** pour indiquer une erreur.

## <a name="remarks"></a>Notes

Le **fclose** fonction ferme *flux*. Si *flux* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **fclose** définit **errno** à **EINVAL** et retourne **EOF**. Il est recommandé que le *flux* pointeur toujours être vérifiées avant d’appeler cette fonction.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Le **_fcloseall** fonction ferme tous les flux ouverts sauf **stdin**, **stdout**, **stderr** (et MS-DOS, **_stdaux**  et **_stdprn**). Ferme également et supprime tous les fichiers temporaires créés par **tmpfile**. Dans les deux fonctions, toutes les mémoires tampons associées au flux sont vidées avant la fermeture. Les mémoires tampons allouées par le système sont libérées quand le flux est fermé. Mémoires tampons affectées par l’utilisateur avec **setbuf** et **setvbuf** ne sont pas libérés automatiquement.

**Remarque :** Quand ces fonctions sont utilisées pour fermer un flux, le descripteur de fichier sous-jacent et le handle de fichier de système d’exploitation (ou socket) sont fermés, ainsi que le flux. Par conséquent, si le fichier a été ouverte en tant que fichier gérer ou descripteur de fichier et est fermée avec **fclose**, effectuer un appel pas également **_close** à fermer le descripteur de fichier ; n’appelez pas la fonction Win32  **CloseHandle** pour fermer le handle de fichier.

**fclose** et **_fcloseall** inclure du code pour vous protéger contre toute interférence avec d’autres threads. Pour une version sans verrouillage d’un **fclose**, consultez **_fclose_nolock**.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
