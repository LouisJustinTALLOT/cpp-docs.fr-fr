---
description: 'En savoir plus sur : _dupenv_s_dbg, _wdupenv_s_dbg'
title: _dupenv_s_dbg, _wdupenv_s_dbg
ms.date: 11/04/2016
api_name:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
ms.openlocfilehash: a12e5adc55cd69b8336b3f9f50d982f80ec1b070
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332900"
---
# <a name="_dupenv_s_dbg-_wdupenv_s_dbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg

Obtenir une valeur à partir de l'environnement actuel  Versions de [_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md) qui allouent de la mémoire avec [_malloc_dbg](malloc-dbg.md) pour fournir des informations de débogage supplémentaires.

## <a name="syntax"></a>Syntaxe

```C
errno_t _dupenv_s_dbg(
   char **buffer,
   size_t *numberOfElements,
   const char *varname,
   int blockType,
   const char *filename,
   int linenumber
);
errno_t _wdupenv_s_dbg(
   wchar_t **buffer,
   size_t * numberOfElements,
   const wchar_t *varname,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Mémoire tampon pour stocker la valeur de la variable.

*numberOfElements*<br/>
Taille de la *mémoire tampon*.

*argument*<br/>
Nom de la variable d'environnement.

*blockType*<br/>
Type demandé du bloc de mémoire : **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

*filename*<br/>
Pointeur vers le nom du fichier source ou **null**.

*LineNumber*<br/>
Numéro de ligne dans le fichier source ou **null**.

## <a name="return-value"></a>Valeur renvoyée

Zéro en cas de réussite, code d'erreur en cas d'échec.

Ces fonctions valident leurs paramètres ; Si *buffer* ou *varname* a la **valeur null**, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions définissent **errno** sur **EINVAL** et retournent **EINVAL**.

Si ces fonctions ne peuvent pas allouer suffisamment de mémoire, elles définissent la valeur de *buffer* à **null** et *NumberOfElements* sur 0, et retournent **ENOMEM**.

## <a name="remarks"></a>Notes

Les fonctions **_dupenv_s_dbg** et **_wdupenv_s_dbg** sont identiques à **_dupenv_s** et **_wdupenv_s** , à ceci près que, lorsque **_DEBUG** est défini, ces fonctions utilisent la version Debug de [malloc](malloc.md), [_malloc_dbg](malloc-dbg.md), pour allouer de la mémoire pour la valeur de la variable d’environnement. Pour plus d’informations sur les fonctionnalités de débogage de **_malloc_dbg**, consultez [_malloc_dbg](malloc-dbg.md).

Dans la plupart des cas, vous n'avez pas besoin d'appeler ces fonctions de manière explicite. Au lieu de cela, vous pouvez définir l’indicateur **_CRTDBG_MAP_ALLOC**. Lorsque **_CRTDBG_MAP_ALLOC** est définie, les appels à **_dupenv_s** et **_wdupenv_s** sont remappés **à _dupenv_s_dbg** et **_wdupenv_s_dbg**, respectivement, avec la valeur de *Blocktype* définie sur **_NORMAL_BLOCK**. Vous n’avez donc pas besoin d’appeler ces fonctions de manière explicite, sauf si vous souhaitez marquer les blocs du tas comme **_CLIENT_BLOCK**. Pour plus d’informations sur les types de bloc, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_dupenv_s_dbg.c
#include  <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
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
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
