---
title: _dupenv_s, _wdupenv_s
ms.date: 4/2/2020
api_name:
- _dupenv_s
- _wdupenv_s
- _o__dupenv_s
- _o__wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: f65f1da3e8cef077df04d0bdb7eb2aaf75afd9fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348059"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s, _wdupenv_s

Obtient une valeur à partir de l'environnement actuel.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _dupenv_s(
   char **buffer,
   size_t *numberOfElements,
   const char *varname
);
errno_t _wdupenv_s(
   wchar_t **buffer,
   size_t *numberOfElements,
   const wchar_t *varname
);
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Mémoire tampon pour stocker la valeur de la variable.

*nombreOfElements*<br/>
Taille du *tampon*.

*varname varname*<br/>
Nom de la variable d'environnement.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, code d'erreur en cas d'échec.

Ces fonctions valident leurs paramètres ; si *le tampon* ou le *varname* est **NULL**, le gestionnaire de paramètre invalide est invoqué comme décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions **définies errno** à **EINVAL** et retourner **EINVAL**.

Si ces fonctions ne peuvent pas allouer suffisamment de mémoire, elles fixent le *tampon* à **NULL** et *numberOfElements* à 0, et renvoient **ENOMEM**.

## <a name="remarks"></a>Notes

La fonction **_dupenv_s** recherche la liste des variables de l’environnement pour *le varname*. Si la variable est trouvée, **_dupenv_s** alloue un tampon et copie la valeur de la variable dans le tampon. L’adresse et la longueur du tampon sont retournées en *tampon* et *en nombreOfElements*. En allouant le tampon lui-même, **_dupenv_s** offre une alternative plus pratique à [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Il revient au programme appelant de libérer la mémoire en appelant [free](free.md).

Si la variable n’est pas trouvée, alors *le tampon* est réglé à **NULL**, *numberOfElements* est réglé à 0, et la valeur de retour est de 0 parce que cette situation n’est pas considérée comme une condition d’erreur.

Si vous n’êtes pas intéressé par la taille du tampon, vous pouvez passer **NULL** pour *numberOfElements*.

**_dupenv_s n’est** pas sensible au cas dans le système d’exploitation Windows. **_dupenv_s** utilise la copie de l’environnement pointée par la variable mondiale **_environ** pour accéder à l’environnement. Voir les remarques dans [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) pour une discussion sur **_environ**.

La valeur du *tampon* est une copie de la valeur de la variable de l’environnement; le modifier n’a aucun effet sur l’environnement. Utilisez la fonction [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md) pour modifier la valeur d’une variable d’environnement.

**_wdupenv_s** est une version à caractère large de **_dupenv_s**; les arguments de **_wdupenv_s** sont des chaînes de caractère large. La **variable mondiale _wenviron** est une version à caractère large de **_environ**. Voir les remarques dans [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) pour en savoir plus sur **_wenviron**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_dupenv_s.c
#include  <stdlib.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[Constants environnementaux](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
