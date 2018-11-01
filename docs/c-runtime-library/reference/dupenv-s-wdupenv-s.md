---
title: _dupenv_s, _wdupenv_s
ms.date: 11/04/2016
apiname:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: bc8af3282b57c9fa411aac97f5fa4d414bc3305b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646497"
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s, _wdupenv_s

Obtient une valeur à partir de l'environnement actuel.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*numberOfElements*<br/>
Taille de *tampon*.

*nom de variable*<br/>
Nom de la variable d'environnement.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, code d'erreur en cas d'échec.

Ces fonctions valident leurs paramètres ; Si *tampon* ou *varname* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions définissent **errno** à **EINVAL** et retourner **EINVAL**.

Si ces fonctions ne peut pas allouer suffisamment de mémoire, elles définies *tampon* à **NULL** et *numberOfElements* à 0 et retournent **ENOMEM**.

## <a name="remarks"></a>Notes

Le **_dupenv_s** fonction recherche dans la liste des variables d’environnement pour *varname*. Si la variable est trouvée, **_dupenv_s** alloue une mémoire tampon et copie la valeur de la variable dans la mémoire tampon. Adresse et la longueur de la mémoire tampon sont retournées dans *tampon* et *numberOfElements*. En allouant la mémoire tampon elle-même, **_dupenv_s** fournit une alternative plus pratique à [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Il revient au programme appelant de libérer la mémoire en appelant [free](free.md).

Si la variable est introuvable, puis *tampon* a la valeur **NULL**, *numberOfElements* est définie sur 0, et la valeur de retour est 0, car cette situation n’est pas considérée comme une erreur condition.

Si vous n’êtes pas intéressé par la taille de la mémoire tampon, vous pouvez passer **NULL** pour *numberOfElements*.

**_dupenv_s** n’est pas sensible à la casse dans le système d’exploitation Windows. **_dupenv_s** utilise la copie de l’environnement vers lequel pointé la variable globale **_environ** pour accéder à l’environnement. Consultez les notes dans [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) pour une présentation de **_environ**.

La valeur dans *tampon* est une copie de la valeur de la variable d’environnement ; modification n’a aucun effet sur l’environnement. Utilisez la fonction [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md) pour modifier la valeur d’une variable d’environnement.

**_wdupenv_s** est une version à caractères larges de **_dupenv_s**; les arguments de **_wdupenv_s** sont des chaînes à caractères larges. Le **_wenviron** (variable globale) est une version à caractères larges de **_environ**. Consultez les notes dans [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) pour en savoir plus sur **_wenviron**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Configuration requise

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

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[Constantes d’environnement](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
