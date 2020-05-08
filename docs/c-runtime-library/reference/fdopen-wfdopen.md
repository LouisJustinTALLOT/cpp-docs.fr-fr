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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 227f9e31c689b0259c429e2ffd9fce074903bd71
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920175"
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

*FD*<br/>
Descripteur du fichier ouvert.

*mode*<br/>
Type d'accès fichier.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur désignant le flux ouvert. Une valeur de pointeur null indique une erreur. Quand une erreur se produit, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EBADF**, ce qui indique un descripteur de fichier incorrect ou **EINVAL**, qui indique que le *mode* était un pointeur null.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes 

La fonction **_fdopen** associe un flux d’e/s au fichier identifié par *FD*et permet ainsi à un fichier ouvert pour les e/s de bas niveau d’être mis en mémoire tampon et mis en forme. **_wfdopen** est une version à caractères larges de **_fdopen**; l’argument *mode* de **_wfdopen** est une chaîne de caractères larges. **_wfdopen** et **_fdopen** sinon se comportent de la même façon.

Les descripteurs de fichiers passés dans **_fdopen** sont détenus par le **fichier retourné &#42;** flux. Si **_fdopen** réussit, n’appelez [ \_pas Close](close.md) sur le descripteur de fichier. L’appel de [fclose](fclose-fcloseall.md) sur le **fichier retourné &#42;** également fermer le descripteur de fichier.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|\_UNICODE et \_MBCS non définis|\_MBCS défini|\_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

La chaîne de caractères de *mode* spécifie le type d’accès au fichier demandé pour le fichier :

| *mode* | Accès |
|--------|--------|
| **r** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, l’appel **fopen** échoue. |
| **s** | Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit. |
| **un** | Ouvre pour l’écriture à la fin du fichier (ajout). Crée le fichier s'il n'existe pas. |
| **"r +"** | Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister. |
| **"w +"** | Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit. |
| **"a +"** | S'ouvre pour lecture et ajout. Crée le fichier s'il n'existe pas. |

Lorsqu’un fichier est ouvert avec le type d’accès **« a »** ou **« a + »** , toutes les opérations d’écriture se produisent à la fin du fichier. Le pointeur de fichier peut être repositionné à l’aide de [fseek](fseek-fseeki64.md) ou [rembobiner](rewind.md), mais il est toujours redéplacé à la fin du fichier avant toute opération d’écriture. Par conséquent, les données existantes ne peuvent pas être remplacées. Quand le type d’accès **"r +"**, **"w +"** ou **"a +"** est spécifié, la lecture et l’écriture sont autorisées (le fichier est dit ouvert pour "mettre à jour"). Toutefois, lorsque vous basculez entre la lecture et l’écriture, il doit y avoir une opération [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)ou [rembobiner](rewind.md) intermédiaire. Si vous le souhaitez, vous pouvez spécifier la position actuelle pour l’opération [fsetpos](fsetpos.md) ou [fseek](fseek-fseeki64.md) .

Outre les valeurs ci-dessus, les caractères suivants peuvent également être inclus dans le *mode* pour spécifier le mode de traduction pour les caractères de saut de ligne :

| modificateur de *mode* | Comportement |
|-----------------|----------|
| **t** | Ouvrir en mode texte (traduit). Dans ce mode, les combinaisons retour chariot-saut de ligne sont traduites en flux d'une ligne (saut de ligne) en entrée, et les caractères de saut de ligne sont traduits en combinaisons retour chariot/saut de ligne en sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. |
| **p** | Ouvrir en mode binaire (non traduit). Toutes les traductions du mode **t** sont supprimées. |
| **secteur** | Activez l’indicateur de validation pour le *nom* de fichier associé afin que le contenu de la mémoire tampon de fichier soit écrit directement sur le disque si **fflush** ou **_flushall** est appelé. |
| **n** | Réinitialiser l’indicateur de validation pour le *nom de fichier* associé sur « no-commit ». Il s’agit de la valeur par défaut. Il remplace également l’indicateur de validation global si vous liez votre programme avec le mode. obj. La valeur par défaut de l’indicateur de validation global est « no-Commit », sauf si vous liez explicitement votre programme avec le paramètre commode. obj. |

Les options de *mode* **t**, **c**et **n** sont des extensions Microsoft pour **fopen** et **_fdopen**. Ne les utilisez pas si vous voulez préserver la portabilité ANSI.

Si **t** ou **b** n’est pas spécifié en *mode*, le mode de traduction par défaut est défini par [ \_](../../c-runtime-library/fmode.md)la variable globale fmode. Si **t** ou **b** est préfixé à l’argument, la fonction échoue et retourne la valeur null. Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Les caractères valides pour la chaîne de *mode* utilisée dans **fopen** et **_fdopen** correspondent aux arguments *Oflag* utilisés dans [ \_Open](open-wopen.md) et [ \_sopen](sopen-wsopen.md), comme indiqué dans le tableau suivant :

|Caractères dans la chaîne de *mode*|Valeur *Oflag* équivalente pour **_open** et **_sopen**|
|---------------------------------|---------------------------------------------------|
|**un**|**\_O\_WRONLY &#124; \_o\_Append** (généralement ** \_o\_WRONLY &#124; \_o\_Create \_&#124;\_o Append**)|
|**r +**|**\_O\_RDWR &#124; \_o\_Append** (généralement ** \_o\_RDWR &#124; \_o\_Append &#124; \_o\_Create** )|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (généralement ** \_o\_WRONLY &#124; \_o\_Creating \_&#124;\_o trunc**)|
|**w +**|**\_O\_RDWR** (généralement ** \_o\_RDWR &#124; \_o\_Creating \_&#124;\_o trunc**)|
|**p**|**\_binaire\_O**|
|**t**|**\_O\_Text**|
|**secteur**|None|
|**n**|None|

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a> Exemple

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
[\_DUP, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_ouvrir, \_wopen](open-wopen.md)<br/>
