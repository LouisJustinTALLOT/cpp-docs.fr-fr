---
title: _fdopen, _wfdopen
ms.date: 12/12/2017
apiname:
- _fdopen
- _wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: c68bc835adf19df7f1538d30b2be162fe6dc6021
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584455"
---
# <a name="fdopen-wfdopen"></a>_fdopen, _wfdopen

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

*fd*<br/>
Descripteur du fichier ouvert.

*mode*<br/>
Type d'accès fichier.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur désignant le flux ouvert. Une valeur de pointeur null indique une erreur. Quand une erreur se produit, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** prend la valeur **EBADF**, ce qui indique un descripteur de fichier incorrect, ou **EINVAL**, ce qui indique que *mode*  était un pointeur null.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_fdopen** fonction associe le fichier qui est identifié par un flux d’e/s *fd*, permettant ainsi un fichier est ouvert pour les e/s de bas niveau être mis en mémoire tampon et mise en forme. **_wfdopen** est une version à caractères larges de **_fdopen**; le *mode* l’argument de **_wfdopen** est une chaîne de caractères larges. **_wfdopen** et **_fdopen** sinon se comportent de façon identique.

Transmis à des descripteurs de fichiers **_fdopen** sont détenus par retourné **fichier &#42;**  flux. Si **_fdopen** est réussie, n’appelez pas [ \_fermer](close.md) sur le descripteur de fichier. Appel [fclose](fclose-fcloseall.md) sur retourné **fichier &#42;**  ferme également le descripteur de fichier.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|\_UNICODE et \_MBCS non définis|\_MBCS défini|\_UNICODE définie|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

Le *mode* chaîne de caractères Spécifie le type d’accès au fichier demandé pour le fichier :

|*mode*|Accès|
|-|-|
**"r"**|Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, la **fopen** appeler échoue.
**"w"**|Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit.
**"a"**|S’ouvre pour écriture à la fin du fichier (ajout). Crée le fichier s'il n'existe pas.
**"r+"**|Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister.
**"w+"**|Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit.
**"a+"**|S'ouvre pour lecture et ajout. Crée le fichier s'il n'existe pas.

Quand un fichier est ouvert avec le **« a »** ou **« a + »** accéder au type, toutes les opérations se produisent à la fin du fichier d’écriture. Le pointeur de fichier peut être repositionné à l’aide de [fseek](fseek-fseeki64.md) ou [rewind](rewind.md), mais il est toujours redéplacé à la fin du fichier avant toute opération d’écriture. Par conséquent, les données existantes ne peuvent pas être remplacées. Lorsque le **« r + »**, **« w + »**, ou **« a + »** type d’accès est spécifié, la lecture et l’écriture sont autorisées (le fichier est réputé être ouvert pour « update »). Toutefois, lorsque vous basculez entre lecture et écriture, il doit y avoir un intermédiaire [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), ou [rewind](rewind.md) opération. Vous pouvez spécifier la position actuelle pour le [fsetpos](fsetpos.md) ou [fseek](fseek-fseeki64.md) opération, si vous le souhaitez.

Outre les valeurs ci-dessus, les caractères suivants peuvent également être inclus dans *mode* pour spécifier le mode de traduction pour les caractères de saut de ligne :

|*mode* modificateur|Comportement|
|-|-|
**t**|Ouvrir en mode texte (traduit). Dans ce mode, les combinaisons retour chariot-saut de ligne sont traduites en flux d'une ligne (saut de ligne) en entrée, et les caractères de saut de ligne sont traduits en combinaisons retour chariot/saut de ligne en sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée.
**b**|Ouvrir en mode binaire (non traduit). Les traductions du **t** mode sont supprimés.
**c**|Activer l’indicateur de validation associé au *filename* afin que le contenu de la mémoire tampon de fichier est écrites directement sur le disque si **fflush** ou **_flushall** est appelée.
**n**|Réinitialiser l’indicateur de validation associé au *filename* pour « no-commit ». Il s'agit de la valeur par défaut. Substitue aussi l'indicateur de validation globale si vous liez votre programme avec Commode.obj. La valeur par défaut de l’indicateur de validation globale est « no-commit », sauf si vous liez explicitement votre programme avec Commode.obj.

Le **t**, **c**, et **n** *mode* options sont des extensions Microsoft pour **fopen** et **_fdopen**. Ne les utilisez pas si vous voulez préserver la portabilité ANSI.

Si **t** ou **b** n’est pas spécifié dans *mode*, le mode de traduction par défaut est défini par la variable globale [ \_fmode](../../c-runtime-library/fmode.md). Si **t** ou **b** est préfixé à l’argument, la fonction échoue et retourne la valeur NULL. Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Caractères valides pour le *mode* chaîne utilisée dans **fopen** et **_fdopen** correspondent aux *oflag* arguments utilisés dans [ \_ouvrir](open-wopen.md) et [ \_sopen](sopen-wsopen.md), comme illustré dans ce tableau :

|Les caractères de *mode* chaîne|Équivalent *oflag* valeur **_open** et **_sopen**|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_WRONLY &#124; \_O\_APPEND** (généralement  **\_O\_WRONLY &#124; \_O\_créer &#124; \_O \_APPEND**)|
|**a +**|**\_O\_RDWR &#124; \_O\_APPEND** (généralement  **\_O\_RDWR &#124; \_O\_APPEND &#124; \_O\_ Créer un** )|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (généralement  **\_O\_WRONLY &#124; \_O\_créer &#124; \_O\_TRUNC**)|
|**w +**|**\_O\_RDWR** (généralement  **\_O\_RDWR &#124; \_O\_créer &#124; \_O\_TRUNC**)|
|**b**|**\_O\_BINAIRE**|
|**t**|**\_O\_TEXTE**|
|**c**|None|
|**n**|None|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

### <a name="input-crtfdopentxt"></a>Entrée : crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Sortie

```Output
Lines in file: 2
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_Ouvrir, \_wopen](open-wopen.md)<br/>
