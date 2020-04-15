---
title: _fdopen, _wfdopen
ms.date: 4/2/2020
api_name:
- _fdopen
- _wfdopen
- _o__fdopen
- _o__wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 82a7e891e8bd6031ebbf761534b6df7cd8488d36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347389"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen, _wfdopen

Associe un flux à un fichier ouvert précédemment pour une E/S de bas niveau.

## <a name="syntax"></a>Syntaxe

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Paramètres

*Fd*<br/>
Descripteur du fichier ouvert.

*mode*<br/>
Type d'accès fichier.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur désignant le flux ouvert. Une valeur de pointeur null indique une erreur. Quand une erreur se produit, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé soit à **EBADF**, ce qui indique un mauvais descripteur de fichier, ou **EINVAL**, ce qui indique que *le mode* était un pointeur nul.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_fdopen** associe un flux I/O au fichier identifié par *fd,* et permet ainsi d’ouvrir un fichier ouvert pour que le niveau I/O de bas niveau soit tamponné et formaté. **_wfdopen** est une version à caractère large de **_fdopen**; l’argument *du mode* pour **_wfdopen** est une chaîne de caractère large. **_wfdopen** et **_fdopen** se comportent autrement de façon identique.

Les descripteurs de fichiers transmis **dans _fdopen** appartiennent au flux de **&#42;FILE** retourné. Si **_fdopen** est couronnée de succès, ne pas appeler [ \_près](close.md) du descripteur de fichier. Appeler [fclose](fclose-fcloseall.md) sur le FILE retourné **&#42;** ferme également le descripteur de fichier.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|\_UNICODE \_et MBCS non définis|\_MBCS défini|\_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

La chaîne de caractères *en mode* spécifie le type d’accès au fichier demandé pour le fichier :

| *mode* | Accès |
|--------|--------|
| **"r"** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou ne peut pas être trouvé, **l’appel fopen** échoue. |
| **"w"** | Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit. |
| **"a"** | Ouvre pour l’écriture à la fin du fichier (appending). Crée le fichier s'il n'existe pas. |
| **"r"** | Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister. |
| **"W"** | Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit. |
| **"A"** | S'ouvre pour lecture et ajout. Crée le fichier s'il n'existe pas. |

Lorsqu’un fichier est ouvert avec le type **d’accès** **« a »** ou « a », toutes les opérations d’écriture se produisent à la fin du fichier. Le pointeur de fichier peut être repositionné en utilisant [fseek](fseek-fseeki64.md) ou [rembobinage](rewind.md), mais il est toujours déplacé vers la fin du fichier avant toute opération de rédaction est effectuée. Par conséquent, les données existantes ne peuvent pas être écrasées. Lorsque le type **d’accès « r »**, **« w »** ou « **a »** est spécifié, la lecture et l’écriture sont autorisées (le fichier est dit ouvert pour la « mise à jour »). Cependant, lorsque vous passez de la lecture à l’écriture, il doit y avoir un [fflush](fflush.md)intervenant , [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), ou [l’opération de rembobinage.](rewind.md) Vous pouvez spécifier la position actuelle pour [l’opération fsetpos](fsetpos.md) ou [fseek,](fseek-fseeki64.md) si vous le souhaitez.

En plus des valeurs ci-dessus, les caractères suivants peuvent également être inclus en *mode* pour spécifier le mode de traduction pour les caractères newline :

| *modificateur de mode* | Comportement |
|-----------------|----------|
| **T** | Ouvrir en mode texte (traduit). Dans ce mode, les combinaisons retour chariot-saut de ligne sont traduites en flux d'une ligne (saut de ligne) en entrée, et les caractères de saut de ligne sont traduits en combinaisons retour chariot/saut de ligne en sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. |
| **B** | Ouvrir en mode binaire (non traduit). Toutes les traductions du mode **t** sont supprimées. |
| **C** | Activez le drapeau de validation du nom de *fichier* associé afin que le contenu du tampon de fichier soit écrit directement sur disque si **fflush** ou **_flushall** est appelé. |
| **n** | Réinitialisez le drapeau de validation du *nom de fichier* associé à « non-commit ». Il s’agit de la valeur par défaut. Il remplace également le drapeau de validation global si vous liez votre programme avec Commode.obj. Le défaut global de validation du drapeau est « sans engagement » à moins que vous ne liez explicitement votre programme à Commode.obj. |

Les options de **n** *mode* **t**, **c**, et n sont des extensions Microsoft pour **fopen** et **_fdopen**. Ne les utilisez pas si vous voulez préserver la portabilité ANSI.

Si **t** ou **b** n’est pas donné en *mode,* le mode de traduction par défaut est défini par le [ \_fmode](../../c-runtime-library/fmode.md)variable globale . Si **t** ou **b** est préfixé à l’argument, la fonction échoue et renvoie NULL. Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Les caractères valides pour la chaîne *de mode* utilisée dans **le fopen** et **_fdopen** correspondent à des arguments *delag* utilisés dans [ \_l’ouverture](open-wopen.md) et [ \_le sopen,](sopen-wsopen.md)comme le montre ce tableau :

|Personnages dans la chaîne *de mode*|Équivalent *de* valeur pour **_open** et **_sopen**|
|---------------------------------|---------------------------------------------------|
|**Un**|**\_O\_WRONLY &#124; \_O\_APPEND** (généralement ** \_O\_WRONLY \_\_&#124; O CREAT \_\_&#124; O APPEND**)|
|**a**|**\_O\_RDWR &#124; \_O\_APPEND** (généralement ** \_O\_RDWR \_\_&#124; O APPEND \_\_&#124; O CREAT** )|
|**R**|**\_O\_RDONLY**|
|**r**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (généralement ** \_O\_WRONLY \_\_&#124; O CREAT \_\_&#124; O TRUNC**)|
|**w**|**\_O\_RDWR** (généralement ** \_O\_RDWR \_\_&#124; O CREAT \_\_&#124; O TRUNC**)|
|**B**|**\_O\_BINAIRE**|
|**T**|**\_O\_TEXTE**|
|**C**|None|
|**n**|None|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crt_fdopentxt"></a>Entrée : crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Output

```Output
Lines in file: 2
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_ouvert, \_wopen](open-wopen.md)<br/>
