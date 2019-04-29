---
title: _fsopen, _wfsopen
ms.date: 11/04/2016
apiname:
- _wfsopen
- _fsopen
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
ms.openlocfilehash: 197a4f690a6626edbfec27ea4abef1999b6cedaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287694"
---
# <a name="fsopen-wfsopen"></a>_fsopen, _wfsopen

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

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le flux. Une valeur de pointeur null indique une erreur. Si *filename* ou *mode* est **NULL** ou une chaîne vide, ces fonctions appellent le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre ](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **NULL** et définissez **errno** à **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_fsopen** fonction ouvre le fichier spécifié par *filename* sous forme de flux et prépare le fichier en lecture partagée ultérieure ou d’écriture, comme défini par le mode et *shflag*arguments. **_wfsopen** est une version à caractères larges de **_fsopen**; le *filename* et *mode* arguments à **_wfsopen** sont chaînes à caractères larges. **_wfsopen** et **_fsopen** se comportent de façon identique dans le cas contraire.

La chaîne de caractères *mode* Spécifie le type d’accès demandé pour le fichier, comme indiqué dans le tableau suivant.

|Terme|Définition|
|----------|----------------|
|**"r"**|Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, la **_fsopen** appeler échoue.|
|**"w"**|Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit.|
|**"a"**|Ouvre pour l'écriture à la fin du fichier (ajout) ; crée d'abord le fichier s'il n'existe pas.|
|**"r+"**|Ouvre pour l'accès en lecture et en écriture. (Le fichier doit exister.)|
|**"w+"**|Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier spécifié existe, son contenu est détruit.|
|**"a+"**|Ouvre pour l'écriture et l'ajout ; crée d'abord le fichier s'il n'existe pas.|

Utilisez le **« w »** et **« w + »** types avec précaution, car ils peuvent détruire les fichiers existants.

Quand un fichier est ouvert avec le **« a »** ou **« a + »** accéder au type, toutes les opérations se produisent à la fin du fichier d’écriture. Le pointeur de fichier peut être repositionné à l’aide de [fseek](fseek-fseeki64.md) ou [rewind](rewind.md), mais il est toujours redéplacé à la fin du fichier avant toute opération d’écriture. Par conséquent, les données existantes ne peuvent pas être remplacées. Lorsque le **« r + »**, **« w + »**, ou **« a + »** type d’accès est spécifié, la lecture et l’écriture sont autorisées (le fichier est réputé être ouvert pour mise à jour). Cependant, quand vous basculez entre lecture et écriture, une opération intermédiaire [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) ou [rewind](rewind.md) doit exister. La position actuelle peut être spécifiée pour le [fsetpos](fsetpos.md) ou [fseek](fseek-fseeki64.md) opération, si vous le souhaitez. Outre les valeurs ci-dessus, un des caractères suivants permettre être inclus dans *mode* pour spécifier le mode de traduction pour les nouvelles lignes et pour la gestion des fichiers.

|Terme|Définition|
|----------|----------------|
|**t**|Ouvre un fichier en mode texte (traduit). Dans ce mode, combinaisons (CR-LF) flux de transport retour de ligne sont traduites en flux d’une ligne (LF) en entrée et les caractères de saut de ligne sont traduits en combinaisons retour chariot / saut de ligne lors de la sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture ou lecture/écriture, **_fsopen** recherche un CTRL + Z à la fin du fichier et le supprime, si possible. En effet à l’aide de [fseek](fseek-fseeki64.md) et [ftell](ftell-ftelli64.md) pour se déplacer dans un fichier qui se termine par un CTRL + Z peut provoquer [fseek](fseek-fseeki64.md) au comportement incorrect vers la fin du fichier.|
|**b**|Ouvre un fichier en mode binaire (non traduit) ; les traductions ci-dessus sont supprimées.|
|**S**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque.|
|**R**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque.|
|**T**|Spécifie un fichier comme temporaire. Si possible, il n'est pas vidé sur disque.|
|**D**|Spécifie un fichier comme temporaire. Il est supprimé lorsque le dernier pointeur de fichier est fermé.|

Si **t** ou **b** n'est pas spécifié dans *mode*, le mode de traduction est défini par la variable de mode par défaut **_fmode**. Si **t** ou **b** est préfixé à l’argument, la fonction échoue et le retourne **NULL**. Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

L’argument *shflag* est une expression constante constituée de l’une des constantes manifestes suivantes, définies dans Share.h.

|Terme|Définition|
|----------|----------------|
|**_SH_COMPAT**|Définit le mode de compatibilité pour les applications 16 bits.|
|**_SH_DENYNO**|Autorise l'accès en lecture et en écriture.|
|**_SH_DENYRD**|Refuse l'accès en lecture au fichier.|
|**_SH_DENYRW**|Refuse l'accès en lecture et en écriture au fichier.|
|**_SH_DENYWR**|Refuse l'accès en écriture au fichier.|

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|En-têtes facultatifs|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Pour la constante de manifeste *shflag* paramètre.|
|**_wfsopen**|\<stdio.h> ou \<wchar.h>|\<share.h><br /><br /> Pour la constante de manifeste *shflag* paramètre.|

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
