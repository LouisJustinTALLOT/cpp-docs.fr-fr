---
title: fopen_s, _wfopen_s
description: Décrit l’API pour `fopen_s` et. `_wfopen_s`
ms.date: 11/20/2020
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
ms.openlocfilehash: 1d6d0b739db1177b903c0e8aa8e6f55e49c1df16
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483163"
---
# <a name="fopen_s-_wfopen_s"></a>`fopen_s`, `_wfopen_s`

Ouvre un fichier. Ces versions de [`fopen, _wfopen`](fopen-wfopen.md) ont des améliorations en matière de sécurité, comme décrit dans [fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t fopen_s(
   FILE** pFile,
   const char *filename,
   const char *mode
);
errno_t _wfopen_s(
   FILE** pFile,
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Paramètres

*`pFile`*\
Pointeur désignant le pointeur de fichier appelé à recevoir le pointeur vers le fichier ouvert.

*`filename`*\
Nom de fichier.

*`mode`*\
Type d'accès autorisé.

## <a name="return-value"></a>Valeur renvoyée

Zéro si l'opération a réussi ; code d'erreur en cas de échec. Pour plus d’informations sur ces codes d’erreur, consultez [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

### <a name="error-conditions"></a>Conditions d'erreur

|*`pFile`*|*`filename`*|*`mode`*|Valeur renvoyée|Contenu de *`pFile`*|
|-------------|----------------|------------|------------------|------------------------|
|**`NULL`**|n'importe laquelle|n'importe laquelle|**`EINVAL`**|inchangé|
|n'importe laquelle|**`NULL`**|n'importe laquelle|**`EINVAL`**|inchangé|
|n'importe laquelle|n'importe laquelle|**`NULL`**|**`EINVAL`**|inchangé|

## <a name="remarks"></a>Notes

Les fichiers ouverts par **`fopen_s`** et **`_wfopen_s`** ne peuvent pas être partagés. Si vous avez besoin qu’un fichier soit partageable, utilisez [`_fsopen, _wfsopen`](fsopen-wfsopen.md) avec la constante de mode de partage appropriée, par exemple **`_SH_DENYNO`** pour le partage en lecture/écriture.

La **`fopen_s`** fonction ouvre le fichier spécifié par *filename*. **`_wfopen_s`** est une version à caractères larges de **`fopen_s`** ; les arguments de **`_wfopen_s`** sont des chaînes à caractères larges. **`_wfopen_s`** et **`fopen_s`** se comportent sinon de la même façon.

**`fopen_s`** accepte les chemins d’accès qui sont valides sur le système de fichiers au point d’exécution ; Les chemins d’accès UNC et les chemins d’accès qui impliquent des lecteurs réseau mappés sont acceptés par **`fopen_s`** tant que le système qui exécute le code a accès au partage ou au lecteur réseau mappé au moment de l’exécution. Lorsque vous construisez des chemins pour **`fopen_s`** , ne faites pas de suppositions quant à la disponibilité des lecteurs, chemins d’accès ou partages réseau dans l’environnement d’exécution. Vous pouvez utiliser des barres obliques (/) ou des barres obliques inverses (\\) comme séparateurs de répertoire dans un chemin.

Ces fonctions valident leurs paramètres. Si *`pFile`* , *`filename`* ou *`mode`* est un pointeur null, ces fonctions génèrent une exception de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md).

Vérifiez toujours la valeur de retour pour voir si la fonction a réussi avant d’effectuer d’autres opérations sur le fichier. Si une erreur se produit, le code d’erreur est retourné et la variable globale **`errno`** est définie. Pour plus d’informations, consultez [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="unicode-support"></a>Prise en charge d’Unicode

**`fopen_s`** prend en charge les flux de fichiers Unicode. Pour ouvrir un fichier Unicode nouveau ou existant, transmettez un indicateur *CCS* qui spécifie l’encodage souhaité à **`fopen_s`** :

**`fopen_s(&fp, "newfile.txt", "rw, ccs=**_encoding_**");`**

Les valeurs autorisées d' *encodage* sont **`UNICODE`** , **`UTF-8`** et **`UTF-16LE`** . Si aucune valeur n’est spécifiée pour *`encoding`* , **`fopen_s`** utilise l’encodage ANSI.

Si le fichier existe déjà et qu'il est ouvert pour lecture ou ajout, la marque d'ordre d'octet (BOM, Byte Order Mark), si elle est présente dans le fichier, détermine le codage. L’encodage BOM est prioritaire sur l’encodage spécifié par l' *`ccs`* indicateur. L' *`ccs`* encodage est utilisé uniquement quand aucune marque Bom n’est présente ou si le fichier est un nouveau fichier.

> [!NOTE]
> La détection BOM s’applique uniquement aux fichiers ouverts en mode Unicode. autrement dit, en passant l' *`ccs`* indicateur.

Le tableau suivant récapitule les modes pour les différents *`ccs`* indicateurs donnés à **`fopen_s`** et pour les marques d’ordre d’octet dans le fichier.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codages utilisés selon l'indicateur ccs et la marque BOM

|indicateur CCS|Aucune marque BOM (ou nouveau fichier)|Marque BOM : UTF-8|Marque BOM : UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**`UNICODE`**|**`UTF-16LE`**|**`UTF-8`**|**`UTF-16LE`**|
|**`UTF-8`**|**`UTF-8`**|**`UTF-8`**|**`UTF-16LE`**|
|**`UTF-16LE`**|**`UTF-16LE`**|**`UTF-8`**|**`UTF-16LE`**|

Une marque BOM est écrite automatiquement dans les fichiers ouverts pour écriture en mode Unicode.

Si *`mode`* est **`"a, ccs=` _encodage_ `"`**, **`fopen_s`** tente d’abord d’ouvrir le fichier avec un accès en lecture et un accès en écriture. En cas de réussite, la fonction lit la marque BOM pour déterminer le codage du fichier ; en cas d'échec, elle utilise le codage par défaut pour le fichier. Dans les deux cas, **`fopen_s`** ouvre à nouveau le fichier avec un accès en écriture seule. (Cela s’applique **`a`** uniquement au mode, et non à **`a+`** .)

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tfopen_s`**|**`fopen_s`**|**`fopen_s`**|**`_wfopen_s`**|

La chaîne *`mode`* de caractères spécifie le type d’accès demandé pour le fichier, comme suit.

|*`mode`*|Accès|
|-|-|
| **`"r"`** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, l' **`fopen_s`** appel échoue. |
| **`"w"`** | Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit. |
| **`"a"`** | S'ouvre pour écriture à la fin du fichier (ajout) sans supprimer le marqueur de fin de fichier (EOF) avant que de nouvelles données soient écrites dans le fichier. Crée le fichier s'il n'existe pas. |
| **`"r+"`** | Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister. |
| **"w +"** | Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit. |
| **`"a+"`** | S'ouvre pour lecture et ajout. L'opération d'ajout inclut la suppression du marqueur EOF avant que de nouvelles données soient écrites dans le fichier. Le marqueur EOF n’est pas restauré une fois l’écriture terminée. Crée le fichier s'il n'existe pas. |

Lorsqu’un fichier est ouvert à l’aide **`"a"`** du **`"a+"`** type d’accès ou, toutes les opérations d’écriture se produisent à la fin du fichier. Le pointeur de fichier peut être repositionné à l’aide de [`fseek`](fseek-fseeki64.md) ou de [`rewind`](rewind.md) , mais il est toujours redéplacé à la fin du fichier avant toute opération d’écriture, de sorte que les données existantes ne peuvent pas être remplacées.

Le **`"a"`** mode ne supprime pas le marqueur EOF avant l’ajout au fichier. Une fois l’ajout effectué, la `TYPE` commande MS-DOS affiche uniquement les données jusqu’au marqueur EOF d’origine, et non les données ajoutées au fichier. Le **`"a+"`** mode supprime le marqueur EOF avant d’ajouter au fichier. Après l’ajout, la `TYPE` commande MS-DOS affiche toutes les données dans le fichier. Le **`"a+"`** mode est requis pour l’ajout à un fichier de flux qui se termine par le `CTRL+Z` marqueur EOF.

Lorsque le **`"r+"`** **`"w+"`** type d’accès, ou **`"a+"`** est spécifié, la lecture et l’écriture sont autorisées. (On dit que le fichier est ouvert pour « mise à jour ».) Toutefois, lorsque vous passez de la lecture à l’écriture, l’opération d’entrée doit être effectuée sur un marqueur EOF. S’il n’existe aucun marqueur EOF, vous devez utiliser un appel intermédiaire à une fonction de positionnement de fichier. Les fonctions de positionnement de fichier sont **`fsetpos`** , [`fseek`](fseek-fseeki64.md) et [`rewind`](rewind.md) . Quand vous passez de l’écriture à la lecture, vous devez utiliser un appel intermédiaire à **`fflush`** ou à une fonction de positionnement de fichier.

Outre les valeurs ci-dessus, les caractères suivants peuvent être inclus dans *`mode`* pour spécifier le mode de traduction pour les caractères de saut de ligne :

|*`mode`* modificateur|Mode de traduction|
|-|-|
| **`t`** | Ouvrir en mode texte (traduit). |
| **`b`** | Ouvrir en mode binaire (non traduit); les traductions qui impliquent des caractères de retour chariot et de saut de ligne sont supprimées. |

En mode texte (traduit), `CTRL+Z` est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture/écriture avec **`"a+"`** , **`fopen_s`** recherche un `CTRL+Z` à la fin du fichier et le supprime, si possible. Cela est dû au fait que l’utilisation de [`fseek`](fseek-fseeki64.md) et **`ftell`** de pour se déplacer dans un fichier qui se termine par un `CTRL+Z` peut entraîner un [`fseek`](fseek-fseeki64.md) comportement incorrect de près de la fin du fichier.

En outre, en mode texte, les combinaisons retour chariot/saut de ligne sont traduites en flux à ligne unique en entrée, et les caractères de saut de ligne sont traduits en combinaisons retour chariot-saut de ligne en sortie. Lorsqu'une fonction d'E/S de flux Unicode s'exécute en mode texte (comportement par défaut), on suppose que le flux source ou de destination est une séquence de caractères multioctets. Les fonctions d’entrée de flux Unicode convertissent les caractères multioctets en caractères larges (comme dans le cas d’un appel à la **`mbtowc`** fonction). Pour la même raison, les fonctions de sortie de flux Unicode convertissent les caractères larges en caractères multioctets (comme dans le cas d’un appel à la **`wctomb`** fonction).

Si **`t`** ou **`b`** n’est pas spécifié dans *`mode`* , le mode de traduction par défaut est défini par la variable globale [_fmode](../../c-runtime-library/fmode.md). Si **`t`** ou **`b`** a pour préfixe l’argument, la fonction échoue et retourne **`NULL`** .

Pour plus d’informations sur l’utilisation des modes texte et binaire dans les E/S de flux Unicode et multioctets, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [E/S de flux Unicode en modes texte et binaire](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*`mode`* modificateur|Comportement|
|-|-|
| **`c`** | Activez l’indicateur de validation pour le *nom* de fichier associé afin que le contenu de la mémoire tampon de fichier soit écrit directement sur le disque si **`fflush`** ou **`_flushall`** est appelé. |
| **`n`** | Réinitialiser l’indicateur de validation pour le *nom de fichier* associé sur « no-commit ». Il s’agit de la valeur par défaut. Substitue également l'indicateur de validation global si vous liez votre programme avec COMMODE.OBJ. La valeur par défaut de l’indicateur de validation globale est « no-commit », sauf si vous liez explicitement votre programme avec COMMODE.OBJ (consultez [Link Options](../../c-runtime-library/link-options.md)). |
| **`n`** | Spécifie que le fichier n’est pas hérité par les processus enfants. |
| **`S`** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque. |
| **`R`** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque. |
| **`t`** | Spécifie un fichier comme temporaire. Si possible, il n’est pas vidé sur le disque. |
| **`D`** | Spécifie un fichier comme temporaire. Elle est supprimée lorsque le dernier pointeur de fichier est fermé. |
| **`ccs=**`_coda_ | Spécifie le jeu de caractères encodé à utiliser (l’un des **`UTF-8`** , **`UTF-16LE`** ou **`UNICODE`** ) pour ce fichier. Laissez ce paramètre non spécifié si vous souhaitez bénéficier de l'encodage ANSI. |

Les caractères valides pour la *`mode`* chaîne utilisée dans **`fopen_s`** et [`_fdopen`](fdopen-wfdopen.md) correspondent aux *`oflag`* arguments utilisés dans [`_open`](open-wopen.md) et [`_sopen`](sopen-wsopen.md) , comme suit.

|Caractères dans la *`mode`* chaîne|Valeur équivalente *`oflag`* pour `_open`/`_sopen`|
|-------------------------------|----------------------------------------------------|
|**`a`**|**`_O_WRONLY`** &#124; **`_O_APPEND`** (généralement **`_O_WRONLY`** &#124; **`_O_CREAT`** &#124; **`_O_APPEND`** )|
|**`a+`**|**`_O_RDWR`** &#124; **`_O_APPEND`** (généralement **`_O_RDWR`** &#124; **`_O_APPEND`** &#124; **`_O_CREAT`** )|
|**`R`**|**`_O_RDONLY`**|
|**`r+`**|**`_O_RDWR`**|
|**`w`**|**`_O_WRONLY`** (généralement **`_O_WRONLY`** &#124; **`_O_CREAT`** &#124; **_O_TRUNC**)|
|**`w+`**|**`_O_RDWR`** (généralement **`_O_RDWR`** &#124; **`_O_CREAT`** &#124; **_O_TRUNC**)|
|**`b`**|**`_O_BINARY`**|
|**`t`**|**`_O_TEXT`**|
|**`c`**|None|
|**`n`**|None|
|**`S`**|**`_O_SEQUENTIAL`**|
|**`R`**|**`_O_RANDOM`**|
|**`t`**|**`_O_SHORTLIVED`**|
|**`D`**|**`_O_TEMPORARY`**|
|**`ccs=UNICODE`**|**`_O_WTEXT`**|
|**`ccs=UTF-8`**|**`_O_UTF8`**|
|**`ccs=UTF-16LE`**|**`_O_UTF16`**|

Si vous utilisez **`rb`** le mode, les fichiers Win32 mappés en mémoire peuvent également être une option si vous n’avez pas besoin de déplacer votre code, vous vous attendez à lire la majeure partie du fichier ou vous ne vous souciez pas des performances du réseau.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**`fopen_s`**|`<stdio.h>`|
|**`_wfopen_s`**|`<stdio.h>` ou `<wchar.h>`|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

Les **`c`** **`n`** options, et **`t`** *`mode`* sont des extensions Microsoft pour **`fopen_s`** et [`_fdopen`](fdopen-wfdopen.md) et ne doivent pas être utilisées là où la portabilité ANSI est souhaitée.

## <a name="example"></a>Exemple

```C
// crt_fopen_s.c
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   errno_t err;

   // Open for read (will fail if file "crt_fopen_s.c" doesn't exist)
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );
   if( err == 0 )
   {
      printf( "The file 'crt_fopen_s.c' was opened\n" );
   }
   else
   {
      printf( "The file 'crt_fopen_s.c' was not opened\n" );
   }

   // Open for write
   err = fopen_s( &stream2, "data2", "w+" );
   if( err == 0 )
   {
      printf( "The file 'data2' was opened\n" );
   }
   else
   {
      printf( "The file 'data2' was not opened\n" );
   }

   // Close stream if it isn't NULL
   if( stream )
   {
      err = fclose( stream );
      if ( err == 0 )
      {
         printf( "The file 'crt_fopen_s.c' was closed\n" );
      }
      else
      {
         printf( "The file 'crt_fopen_s.c' was not closed\n" );
      }
   }

   // All other files are closed:
   int numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>Voir aussi

[E/s de flux](../../c-runtime-library/stream-i-o.md)\
[`fclose, _fcloseall`](fclose-fcloseall.md)\
[`_fdopen, _wfdopen`](fdopen-wfdopen.md)\
[`ferror`](ferror.md)\
[`_fileno`](fileno.md)\
[`freopen, _wfreopen`](freopen-wfreopen.md)\
[`_open, _wopen`](open-wopen.md)\
[`_setmode`](setmode.md)
