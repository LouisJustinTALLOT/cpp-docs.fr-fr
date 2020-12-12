---
description: 'En savoir plus sur : _fsopen, _wfsopen'
title: _fsopen, _wfsopen
ms.date: 4/2/2020
api_name:
- _wfsopen
- _fsopen
- _o__fsopen
- _o__wfsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
ms.openlocfilehash: c7b54a6735939e26c8ff0153abc640e3dc2c8b41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318336"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen, _wfsopen

Ouvre un flux avec le partage de fichiers.

## <a name="syntax"></a>Syntaxe

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier à ouvrir.

*mode*<br/>
Type d'accès autorisé.

*shflag*<br/>
Type de partage autorisé.

## <a name="return-value"></a>Valeur renvoyée

Chacune de ces fonctions retourne un pointeur vers le flux. Une valeur de pointeur null indique une erreur. Si *filename* ou *mode* a la **valeur null** ou est une chaîne vide, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent la **valeur null** et attribuent à **errno** la valeur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_fsopen** ouvre le fichier spécifié par *nom* de fichier en tant que flux et prépare le fichier pour la lecture ou l’écriture partagée ultérieure, tel que défini par les arguments mode et *shflag* . **_wfsopen** est une version à caractères larges de **_fsopen**; les arguments de *nom de fichier* et de *mode* de **_wfsopen** sont des chaînes à caractères larges. dans le cas contraire, **_wfsopen** et **_fsopen** se comportent de la même façon.

Le *mode* chaîne de caractères spécifie le type d’accès demandé pour le fichier, comme indiqué dans le tableau suivant.

|Terme|Définition|
|----------|----------------|
|**r**|Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, l’appel de **_fsopen** échoue.|
|**s**|Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit.|
|**un**|Ouvre pour l'écriture à la fin du fichier (ajout) ; crée d'abord le fichier s'il n'existe pas.|
|**"r +"**|Ouvre pour l'accès en lecture et en écriture. (Le fichier doit exister.)|
|**"w +"**|Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier spécifié existe, son contenu est détruit.|
|**"a +"**|Ouvre pour l'écriture et l'ajout ; crée d'abord le fichier s'il n'existe pas.|

Utilisez les types **« w »** et **« w + »** avec précaution, car ils peuvent détruire les fichiers existants.

Lorsqu’un fichier est ouvert avec le type d’accès **« a »** ou **« a + »** , toutes les opérations d’écriture se produisent à la fin du fichier. Le pointeur de fichier peut être repositionné à l’aide de [fseek](fseek-fseeki64.md) ou [rembobiner](rewind.md), mais il est toujours redéplacé à la fin du fichier avant toute opération d’écriture. Par conséquent, les données existantes ne peuvent pas être remplacées. Quand le type d’accès **"r +"**, **"w +"** ou **"a +"** est spécifié, la lecture et l’écriture sont autorisées (le fichier est dit ouvert pour mise à jour). Cependant, quand vous basculez entre lecture et écriture, une opération intermédiaire [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) ou [rewind](rewind.md) doit exister. La position actuelle peut être spécifiée pour l’opération [fsetpos](fsetpos.md) ou [fseek](fseek-fseeki64.md) , si vous le souhaitez. Outre les valeurs ci-dessus, l’un des caractères suivants peut être inclus dans le *mode* pour spécifier le mode de traduction pour les nouvelles lignes et pour la gestion des fichiers.

|Terme|Définition|
|----------|----------------|
|**t**|Ouvre un fichier en mode texte (traduit). Dans ce mode, les combinaisons retour chariot-saut de ligne sont traduites en flux à ligne unique (LF) en entrée et les caractères de saut de ligne sont traduits en combinaisons retour chariot/saut de ligne en sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture ou en lecture/écriture, **_fsopen** recherche un Ctrl + Z à la fin du fichier et le supprime, si possible. Cela est dû au fait que l’utilisation de [fseek](fseek-fseeki64.md) et de [ftell](ftell-ftelli64.md) pour se déplacer dans un fichier qui se termine par un Ctrl + Z peut provoquer un comportement incorrect de [fseek](fseek-fseeki64.md) à proximité de la fin du fichier.|
|**b**|Ouvre un fichier en mode binaire (non traduit) ; les traductions ci-dessus sont supprimées.|
|**S**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque.|
|**R**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque.|
|**T**|Spécifie un fichier comme temporaire. Si possible, il n'est pas vidé sur disque.|
|**D**|Spécifie un fichier comme temporaire. Il est supprimé lorsque le dernier pointeur de fichier est fermé.|

Si **t** ou **b** n'est pas spécifié dans *mode*, le mode de traduction est défini par la variable de mode par défaut **_fmode**. Si **t** ou **b** est préfixé à l’argument, la fonction échoue et retourne la **valeur null**. Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

L’argument *shflag* est une expression constante constituée de l’une des constantes manifestes suivantes, définies dans share. h.

|Terme|Définition|
|----------|----------------|
|**_SH_COMPAT**|Définit le mode de compatibilité pour les applications 16 bits.|
|**_SH_DENYNO**|Autorise l'accès en lecture et en écriture.|
|**_SH_DENYRD**|Refuse l'accès en lecture au fichier.|
|**_SH_DENYRW**|Refuse l'accès en lecture et en écriture au fichier.|
|**_SH_DENYWR**|Refuse l'accès en écriture au fichier.|

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|En-têtes facultatifs|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Pour la constante de manifeste pour le paramètre *shflag* .|
|**_wfsopen**|\<stdio.h> ou \<wchar.h>|\<share.h><br /><br /> Pour la constante de manifeste pour le paramètre *shflag* .|

## <a name="example"></a>Exemple

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
