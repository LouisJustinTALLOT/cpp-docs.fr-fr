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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5c1d63eea6561af6ab7f51c147c92e184d3d11f8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912062"
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

*numChars*<br/>
Nombre maximal de caractères à lire.

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne *Str*. La **valeur null** est retournée pour indiquer une erreur ou une condition de fin de fichier. Utilisez **feof** ou **le** pour déterminer si une erreur s’est produite. Si *Str* ou *Stream* est un pointeur null, si *numChars* est inférieur ou égal à zéro, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

## <a name="remarks"></a>Notes 

La fonction **fgets** lit une chaîne à partir de l’argument de *flux* d’entrée et la stocke dans *Str*. **fgets** lit les caractères à partir de la position actuelle du flux vers et y compris le premier caractère de saut de ligne, jusqu’à la fin du flux, ou jusqu’à ce que le nombre de caractères lus soit égal à *numChars* -1, selon ce qui se produit en premier. Le résultat stocké dans *Str* est ajouté avec un caractère null. Le caractère de saut de ligne, s’il est lu, est inclus dans la chaîne.

**fgetws** est une version à caractères larges de **fgets**.

**fgetws** lit l’argument à caractères larges *Str* comme une chaîne de caractères multioctets ou une chaîne à caractères larges selon que le *flux* est ouvert en mode texte ou binaire, respectivement. Pour plus d’informations sur l’utilisation des modes texte et binaire dans les E/S de flux Unicode et multioctets, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [E/S de flux Unicode en modes texte et binaire](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a> Exemple

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
[Obtient, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
