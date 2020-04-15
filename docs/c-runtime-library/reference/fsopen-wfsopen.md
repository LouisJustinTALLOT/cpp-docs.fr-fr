---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 49907808729375e3bea18a5f4bbf204852e0072a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345697"
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

*Fichier*<br/>
Nom du fichier à ouvrir.

*mode*<br/>
Type d'accès autorisé.

*shflag*<br/>
Type de partage autorisé.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le flux. Une valeur de pointeur null indique une erreur. Si *le nom de fichier* ou le *mode* est **NULL** ou une chaîne vide, ces fonctions invoquent le gestionnaire de paramètres invalides, tel que décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions renvoient **NULL** et **placent errno** à **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_fsopen** ouvre le fichier spécifié par *nom de fichier* comme un flux et prépare le fichier pour la lecture ou l’écriture partagée ultérieure, tel que défini par le mode et les arguments *shflag.* **_wfsopen** est une version à caractère large de **_fsopen**; les arguments *de nom de fichier* et de *mode* pour **_wfsopen** sont des chaînes de caractère large. **_wfsopen** et **_fsopen** se comportent de façon identique autrement.

Le *mode* de chaîne de caractères spécifie le type d’accès demandé pour le fichier, comme indiqué dans le tableau suivant.

|Terme|Définition|
|----------|----------------|
|**"r"**|Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou ne peut pas être trouvé, **l'_fsopen’appel** échoue.|
|**"w"**|Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit.|
|**"a"**|Ouvre pour l'écriture à la fin du fichier (ajout) ; crée d'abord le fichier s'il n'existe pas.|
|**"r"**|Ouvre pour l'accès en lecture et en écriture. (Le fichier doit exister.)|
|**"W"**|Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier spécifié existe, son contenu est détruit.|
|**"A"**|Ouvre pour l'écriture et l'ajout ; crée d'abord le fichier s'il n'existe pas.|

Utilisez les types **"w"** et **"w"** avec soin, car ils peuvent détruire les fichiers existants.

Lorsqu’un fichier est ouvert avec le type **d’accès** **« a »** ou « a », toutes les opérations d’écriture se produisent à la fin du fichier. Le pointeur de fichier peut être repositionné à l’aide [de fseek](fseek-fseeki64.md) ou [rembobinage](rewind.md), mais il est toujours déplacé vers la fin du fichier avant toute opération de rédaction est effectuée. Par conséquent, les données existantes ne peuvent pas être écrasées. Lorsque le type **d’accès « r »**, **« w »** ou « **a »** est spécifié, la lecture et l’écriture sont autorisées (le fichier est dit ouvert pour la mise à jour). Cependant, quand vous basculez entre lecture et écriture, une opération intermédiaire [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) ou [rewind](rewind.md) doit exister. La position actuelle peut être spécifiée pour [l’opération fsetpos](fsetpos.md) ou [fseek,](fseek-fseeki64.md) si désiré. En plus des valeurs ci-dessus, l’un des personnages suivants peut être inclus dans le *mode* pour spécifier le mode de traduction pour les nouvelles lignes, et pour la gestion des fichiers.

|Terme|Définition|
|----------|----------------|
|**T**|Ouvre un fichier en mode texte (traduit). Dans ce mode, les combinaisons d’alimentation en ligne de retour de transport (CR-LF) sont traduites en flux à ligne unique (LF) sur l’entrée et les caractères LF sont traduits en combinaisons CR-LF sur la sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts pour la lecture ou la lecture/écriture, **_fsopen** vérifie un CTRL-Z à la fin du fichier et le supprime, si possible. Ceci est fait parce que l’utilisation [de fseek](fseek-fseeki64.md) et [ftell](ftell-ftelli64.md) pour se déplacer dans un fichier qui se termine par un CTRL-Z pourrait provoquer [fseek](fseek-fseeki64.md) de se comporter incorrectement près de la fin du fichier.|
|**B**|Ouvre un fichier en mode binaire (non traduit) ; les traductions ci-dessus sont supprimées.|
|**S**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque.|
|**R**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque.|
|**T**|Spécifie un fichier comme temporaire. Si possible, il n'est pas vidé sur disque.|
|**D**|Spécifie un fichier comme temporaire. Il est supprimé lorsque le dernier pointeur de fichier est fermé.|

Si **t** ou **b** n'est pas spécifié dans *mode*, le mode de traduction est défini par la variable de mode par défaut **_fmode**. Si **t** ou **b** est préfixé à l’argument, la fonction échoue et renvoie **NULL**. Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

*L’argument shflag* est une expression constante composée de l’une des constantes manifestes suivantes, définies dans Share.h.

|Terme|Définition|
|----------|----------------|
|**_SH_COMPAT**|Définit le mode de compatibilité pour les applications 16 bits.|
|**_SH_DENYNO**|Autorise l'accès en lecture et en écriture.|
|**_SH_DENYRD**|Refuse l'accès en lecture au fichier.|
|**_SH_DENYRW**|Refuse l'accès en lecture et en écriture au fichier.|
|**_SH_DENYWR**|Refuse l'accès en écriture au fichier.|

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|En-têtes facultatifs|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Pour la constante manifeste pour le paramètre *de shflag.*|
|**_wfsopen**|\<stdio.h> ou \<wchar.h>|\<share.h><br /><br /> Pour la constante manifeste pour le paramètre *de shflag.*|

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
