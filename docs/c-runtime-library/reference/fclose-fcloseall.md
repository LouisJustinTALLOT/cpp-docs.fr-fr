---
title: fclose, _fcloseall
ms.date: 11/04/2016
api_name:
- fclose
- _fcloseall
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 215925fb16f5d51e481ae92cbb45b0270bd5ebd4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941503"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Ferme un flux (**fclose**) ou ferme tous les flux ouverts ( **_fcloseall**).

## <a name="syntax"></a>Syntaxe

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fclose** retourne 0 si le flux est fermé avec succès. **_fcloseall** retourne le nombre total de flux fermés. Les deux fonctions retournent **EOF** pour indiquer une erreur.

## <a name="remarks"></a>Notes

La fonction **fclose** ferme le *flux*. Si *Stream* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **fclose** définit **errno** sur **EINVAL** et retourne **EOF**. Il est recommandé de toujours vérifier le pointeur de *flux* avant d’appeler cette fonction.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

La fonction **_fcloseall** ferme tous les flux ouverts, à l’exception de **stdin**, **stdout**, **stderr** (et, dans MS-DOS, **_stdaux** et **_stdprn**). Il ferme et supprime également tous les fichiers temporaires créés par **tmpfile**. Dans les deux fonctions, toutes les mémoires tampons associées au flux sont vidées avant la fermeture. Les mémoires tampons allouées par le système sont libérées quand le flux est fermé. Les mémoires tampons affectées par l’utilisateur avec **setbuf** et **setvbuf** ne sont pas automatiquement libérées.

**Remarque :** Lorsque ces fonctions sont utilisées pour fermer un flux, le descripteur de fichier sous-jacent et le handle de fichier du système d’exploitation (ou socket) sont fermés, ainsi que le flux. Ainsi, si le fichier a été ouvert à l’origine comme handle de fichier ou descripteur de fichier et s’il est fermé avec **fclose**, n’appelez pas **Fermer** pour fermer le descripteur de fichier ; n’appelez pas la fonction **CloseHandle** Win32 pour fermer le descripteur de fichier.

**fclose** et **_fcloseall** incluent du code pour vous protéger contre les interférences d’autres threads. Pour une version sans verrouillage d’un **fclose**, consultez **_fclose_nolock**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Consultez l’exemple relatif à [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
