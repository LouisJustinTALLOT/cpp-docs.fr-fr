---
title: fgets, fgetws
ms.date: 4/2/2020
api_name:
- fgets
- fgetws
- _o_fgets
- _o_fgetws
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
- _fgetts
- fgetws
- fgets
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
ms.openlocfilehash: a1120529157801aac5cf1c4fd61f844fde443bed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346868"
---
# <a name="fgets-fgetws"></a>fgets, fgetws

Obtiennent une chaîne à partir d’un flux.

## <a name="syntax"></a>Syntaxe

```C
char *fgets(
   char *str,
   int numChars,
   FILE *stream
);
wchar_t *fgetws(
   wchar_t *str,
   int numChars,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Emplacement de stockage des données.

*numChars (numChars)*<br/>
Nombre maximal de caractères à lire.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne *str*. **NULL** est retourné pour indiquer une erreur ou une condition de fin de fichier. Utilisez **le feof** ou **le ferror** pour déterminer si une erreur s’est produite. Si *str* ou *flux* est un pointeur nul, ou *numChars* est inférieur ou égal à zéro, cette fonction invoque le gestionnaire de paramètres invalide, tel que décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction renvoie **NULL**.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

## <a name="remarks"></a>Notes

La fonction **fgets** lit une chaîne de l’argument du *flux* d’entrée et le stocke en *str*. **fgets** lit des caractères de la position actuelle du flux à et y compris le premier personnage newline, à la fin du flux, ou jusqu’à ce que le nombre de caractères lus est égal à *numChars* - 1, selon le premier. Le résultat stocké dans *str* est joint avec un caractère nul. Le caractère de saut de ligne, s’il est lu, est inclus dans la chaîne.

**fgetws** est une version à caractère large de **fgets**.

**fgetws** lit le *str* argument de grand caractère comme une chaîne multioctet-caractère ou une chaîne de caractère large selon si *le flux* est ouvert en mode texte ou en mode binaire, respectivement. Pour plus d’informations sur l’utilisation des modes texte et binaire dans les E/S de flux Unicode et multioctets, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [E/S de flux Unicode en modes texte et binaire](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fgets.c
// This program uses fgets to display
// the first line from a file.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[100];

   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )
   {
      if( fgets( line, 100, stream ) == NULL)
         printf( "fgets error\numChars" );
      else
         printf( "%s", line);
      fclose( stream );
   }
}
```

### <a name="input-crt_fgetstxt"></a>Entrée : crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[obtient, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
