---
description: 'En savoir plus sur : _dupenv_s, _wdupenv_s'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3163645b83ec701478cca76d98fe5e17acdc86d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332880"
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

*mémoire tampon*<br/>
Mémoire tampon pour stocker la valeur de la variable.

*numberOfElements*<br/>
Taille de la *mémoire tampon*.

*argument*<br/>
Nom de la variable d'environnement.

## <a name="return-value"></a>Valeur renvoyée

Zéro en cas de réussite, code d'erreur en cas d'échec.

Ces fonctions valident leurs paramètres ; Si *buffer* ou *varname* a la **valeur null**, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions définissent **errno** sur **EINVAL** et retournent **EINVAL**.

Si ces fonctions ne peuvent pas allouer suffisamment de mémoire, elles définissent la valeur de *buffer* à **null** et *NumberOfElements* sur 0, et retournent **ENOMEM**.

## <a name="remarks"></a>Notes

La fonction **_dupenv_s** recherche la liste de variables d’environnement pour *varname*. Si la variable est trouvée, **_dupenv_s** alloue une mémoire tampon et copie la valeur de la variable dans la mémoire tampon. L’adresse et la longueur de la mémoire tampon sont retournées dans *buffer* et *NumberOfElements*. En allouant la mémoire tampon elle-même, **_dupenv_s** offre une alternative plus pratique à [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Il revient au programme appelant de libérer la mémoire en appelant [free](free.md).

Si la variable est introuvable, la *mémoire tampon* est définie sur **null**, *NumberOfElements* a la valeur 0 et la valeur de retour est 0, car cette situation n’est pas considérée comme une condition d’erreur.

Si vous n’êtes pas intéressé par la taille de la mémoire tampon, vous pouvez passer la **valeur null** pour *NumberOfElements*.

**_dupenv_s** ne respecte pas la casse dans le système d’exploitation Windows. **_dupenv_s** utilise la copie de l’environnement vers laquelle pointe la variable globale **_environ** pour accéder à l’environnement. Pour plus d’informations sur **_environ**, consultez les notes dans [getenv_s _wgetenv_s](getenv-s-wgetenv-s.md) .

La valeur de *buffer* est une copie de la valeur de la variable d’environnement ; sa modification n’a aucun effet sur l’environnement. Utilisez la fonction [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md) pour modifier la valeur d’une variable d’environnement.

**_wdupenv_s** est une version à caractères larges de **_dupenv_s**; les arguments de **_wdupenv_s** sont des chaînes à caractères larges. La variable globale **_wenviron** est une version à caractères larges de **_environ**. Pour plus d’informations sur **_wenviron**, consultez les notes dans [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[Constantes environnementales](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
