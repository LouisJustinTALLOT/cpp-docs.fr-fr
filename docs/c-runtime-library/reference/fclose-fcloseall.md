---
title: fclose, _fcloseall
ms.date: 4/2/2020
api_name:
- fclose
- _fcloseall
- _o__fcloseall
- _o_fclose
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: b2ee14c5fc8bb47cc2652443c0263bd14147c90d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347490"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Ferme un flux (**fclose**) ou ferme tous les flux ouverts **(_fcloseall**).

## <a name="syntax"></a>Syntaxe

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Paramètres

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fclose** revient 0 si le flux est fermé avec succès. **_fcloseall** renvoie le nombre total de cours d’eau fermés. Les deux fonctions **renvoient EOF** pour indiquer une erreur.

## <a name="remarks"></a>Notes

La fonction **fclose** ferme *le flux*. Si *le flux* est **NULL**, le gestionnaire de paramètres invalides est invoqué, tel que décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **fclose** met **errno** à **EINVAL** et retourne **EOF**. Il est recommandé que le pointeur de *flux* soit toujours vérifié avant d’appeler cette fonction.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

La fonction **_fcloseall** ferme tous les flux ouverts à **l’exception de stdin**, **stdout**, **stderr** (et, en MS-DOS, **_stdaux** et **_stdprn**). Il ferme et supprime également tous les fichiers temporaires créés par **tmpfile**. Dans les deux fonctions, toutes les mémoires tampons associées au flux sont vidées avant la fermeture. Les mémoires tampons allouées par le système sont libérées quand le flux est fermé. Les tampons assignés par l’utilisateur avec **setbuf** et **setvbuf** ne sont pas automatiquement libérés.

**Remarque :** Quand ces fonctions sont utilisées pour fermer un flux, le descripteur de fichier sous-jacent et le handle de fichier de système d’exploitation (ou socket) sont fermés, ainsi que le flux. Ainsi, si le fichier a été ouvert à l’origine comme un descripteur de poignée de fichier ou de fichier et est fermé avec **fclose**, n’appelez pas également **_close** de fermer le descripteur de fichier; n’appelez pas la fonction Win32 **CloseHandle** pour fermer la poignée de fichier.

**fclose** et **_fcloseall** inclure du code pour se protéger contre les interférences contre d’autres threads. Pour la version non-locking d’un **fclose**, voir **_fclose_nolock**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
