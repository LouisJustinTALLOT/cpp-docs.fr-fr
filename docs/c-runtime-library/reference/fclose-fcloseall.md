---
title: fclose, _fcloseall
ms.date: 11/04/2016
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
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 4713ffb7ecdf8da73e5f949bbef7be124dfaf28a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334877"
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall

Ferme un flux (**fclose**) ou ferme tous les flux ouverts (**_fcloseall**).

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

**fclose** retourne 0 si le flux est fermé correctement. **_fcloseall** retourne le nombre total de flux fermés. Les deux fonctions retournent **EOF** pour indiquer une erreur.

## <a name="remarks"></a>Notes

Le **fclose** fonction se ferme *flux*. Si *flux* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **fclose** définit **errno** à **EINVAL** et retourne **EOF**. Il est recommandé que le *flux* pointeur toujours être activée avant d’appeler cette fonction.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Le **_fcloseall** fonction ferme tous les flux ouverts sauf **stdin**, **stdout**, **stderr** (et, dans MS-DOS, **_stdaux**  et **_stdprn**). Ferme et supprime tous les fichiers temporaires créés par également **tmpfile**. Dans les deux fonctions, toutes les mémoires tampons associées au flux sont vidées avant la fermeture. Les mémoires tampons allouées par le système sont libérées quand le flux est fermé. Mémoires tampons assignées par l’utilisateur avec **setbuf** et **setvbuf** ne sont pas automatiquement libérées.

**Remarque :** Lorsque ces fonctions sont utilisées pour fermer un flux de données, le sous-jacent descripteur de fichier et du système d’exploitation handle de fichier (ou socket) est fermé, ainsi que le flux. Par conséquent, si le fichier a été ouvert à l’origine en tant que fichier gérer ou descripteur de fichier et est fermé avec **fclose**, n’appelez pas également **_close** à fermer le descripteur de fichier ; n’appelez pas la fonction Win32  **CloseHandle** pour fermer le handle de fichier.

**fclose** et **_fcloseall** inclure du code pour vous protéger contre les interférences avec d’autres threads. Pour la version sans verrouillage d’un **fclose**, consultez **_fclose_nolock**.

## <a name="requirements"></a>Configuration requise

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
