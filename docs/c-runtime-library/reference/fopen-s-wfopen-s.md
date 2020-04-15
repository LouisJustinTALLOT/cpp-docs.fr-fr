---
title: fopen_s, _wfopen_s
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 80d04e75637cfab9795bf5dfb9da9786cf4ebd71
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346493"
---
# <a name="fopen_s-_wfopen_s"></a>fopen_s, _wfopen_s

Ouvre un fichier. Ces versions de [fopen, _wfopen](fopen-wfopen.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*pFile (en)*<br/>
Pointeur désignant le pointeur de fichier appelé à recevoir le pointeur vers le fichier ouvert.

*Fichier*<br/>
Nom de fichier.

*mode*<br/>
Type d'accès autorisé.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec. Pour plus d’informations sur ces codes d’erreur, consultez, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d'erreur

|*pFile (en)*|*Fichier*|*mode*|Valeur de retour|Contenu de *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**Null**|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|inchangé|
|n'importe laquelle|**Null**|n'importe laquelle|**EINVAL (EN)**|inchangé|
|n'importe laquelle|n'importe laquelle|**Null**|**EINVAL (EN)**|inchangé|

## <a name="remarks"></a>Notes

Les dossiers ouverts par **fopen_s** et **_wfopen_s** ne sont pas sharables. Si vous exigez qu’un fichier soit sharable, utilisez [_fsopen, _wfsopen](fsopen-wfsopen.md) avec le mode de partage approprié constante, par exemple, **_SH_DENYNO** pour lire/écrire le partage.

La fonction **fopen_s** ouvre le fichier spécifié par *nom de fichier*. **_wfopen_s** est une version à caractère large de **fopen_s**; les arguments pour **_wfopen_s** sont des chaînes de caractère large. **_wfopen_s** et **fopen_s** se comportent de façon identique autrement.

**fopen_s** accepte les voies qui sont valables sur le système de fichiers au moment de l’exécution; Les chemins et les chemins de l’UNC qui impliquent des lecteurs réseau cartographiés sont acceptés par **fopen_s** tant que le système qui exécute le code a accès à la part ou à la commande réseau cartographiée au moment de l’exécution. Lorsque vous construisez des voies pour **fopen_s,** ne faites pas d’hypothèses sur la disponibilité des lecteurs, des chemins ou des parts de réseau dans l’environnement d’exécution. Vous pouvez utiliser des barres obliques (/) ou des barres obliques inverses (\\) comme séparateurs de répertoire dans un chemin.

Ces fonctions valident leurs paramètres. Si *pFile*, *nom de fichier*, ou *mode* est un pointeur nul, ces fonctions génèrent une exception de paramètre invalide, comme décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md).

Vérifiez toujours la valeur de retour pour savoir si la fonction a abouti avant d'effectuer d'autres opérations sur le fichier. Si une erreur se produit, le code d’erreur est retourné et le **errno** variable global est défini. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="unicode-support"></a>Prise en charge d’Unicode

**fopen_s** prend en charge les flux de fichiers Unicode. Pour ouvrir un fichier Unicode nouveau ou existant, passez un indicateur *ccs* qui spécifie l’encodage souhaité pour **fopen_s**:

**fopen_s(&fp, "newfile.txt", "rw, ccs"**_codage_**");**

Les valeurs autorisées *d’encodage* sont **UNICODE**, **UTF-8**, et **UTF-16LE**. S’il n’y a pas de valeur spécifiée pour *l’encodage,* **fopen_s** utilise l’encodage ANSI.

Si le fichier existe déjà et qu'il est ouvert pour lecture ou ajout, la marque d'ordre d'octet (BOM, Byte Order Mark), si elle est présente dans le fichier, détermine le codage. L’encodage BOM prime sur l’encodage spécifié par le drapeau *ccs.* L’encodage *ccs* n’est utilisé que lorsqu’aucun BOM n’est présent ou si le fichier est un nouveau fichier.

> [!NOTE]
> La détection BOM ne s’applique qu’aux fichiers ouverts en mode Unicode ; c’est-à-dire, en passant le drapeau *ccs.*

Le tableau suivant résume les modes pour divers indicateurs ccs qui sont *donnés* à **fopen_s** et pour les marques d’ordre Byte dans le fichier.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codages utilisés selon l'indicateur ccs et la marque BOM

|indicateur ccs|Aucune marque BOM (ou nouveau fichier)|Marque BOM : UTF-8|Marque BOM : UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Une marque BOM est écrite automatiquement dans les fichiers ouverts pour écriture en mode Unicode.

Si *le mode* est « **a, ccsMD**_encodage_**»,** **fopen_s** tente d’abord d’ouvrir le fichier avec l’accès à la lecture et d’écrire l’accès. En cas de réussite, la fonction lit la marque BOM pour déterminer le codage du fichier ; en cas d'échec, elle utilise le codage par défaut pour le fichier. Dans les deux cas, **fopen_s** ré-ouvre ensuite le fichier avec un accès à la écriture seulement. (Cela s’applique à **un** mode seulement, pas **a .)**

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

Le *mode* de chaîne de caractères spécifie le type d’accès demandé pour le fichier, comme suit.

|*mode*|Accès|
|-|-|
| **"r"** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou ne peut pas être trouvé, **l’appel fopen_s** échoue. |
| **"w"** | Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit. |
| **"a"** | S'ouvre pour écriture à la fin du fichier (ajout) sans supprimer le marqueur de fin de fichier (EOF) avant que de nouvelles données soient écrites dans le fichier. Crée le fichier s'il n'existe pas. |
| **"r"** | Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister. |
| **"W"** | Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit. |
| **"A"** | S'ouvre pour lecture et ajout. L'opération d'ajout inclut la suppression du marqueur EOF avant que de nouvelles données soient écrites dans le fichier. Le marqueur EOF n'est pas restauré une fois l'écriture terminée. Crée le fichier s'il n'existe pas. |

Lorsqu’un fichier est ouvert en utilisant le type **d’accès «** **a »** ou « a », toutes les opérations d’écriture se produisent à la fin du fichier. Le pointeur de fichier peut être repositionné en utilisant [fseek](fseek-fseeki64.md) ou [rembobinage](rewind.md), mais il est toujours déplacé vers la fin du fichier avant toute opération de rédaction est effectuée de sorte que les données existantes ne peuvent pas être écrasées.

Le mode **"a"** ne supprime pas le marqueur EOF avant de passer au fichier. Après l'ajout, la commande MS-DOS TYPE affiche uniquement les données jusqu'au marqueur EOF d'origine, et non les données qui sont ajoutées au fichier. Le mode **« a »** supprime le marqueur EOF avant de passer au fichier. Après l'ajout, la commande MS-DOS TYPE affiche toutes les données du fichier. Le mode **« a »** est nécessaire pour passer à un fichier de flux qui est terminé à l’aide du marqueur EOF CTRL-Z.

Lorsque le type **d’accès « r »**, **« w »** ou « **a »** est spécifié, la lecture et l’écriture sont autorisées. (Le fichier est dit être ouvert pour "mise à jour".) Toutefois, lorsque vous passez de la lecture à l’écriture, l’opération d’entrée doit rencontrer un marqueur EOF. S'il n'existe aucun marqueur EOF, vous devez faire un appel intermédiaire à une fonction de positionnement de fichier. Les fonctions de positionnement de fichiers sont **fsetpos**, [fseek](fseek-fseeki64.md), et [rembobiner](rewind.md). Lorsque vous passez de l’écriture à la lecture, vous devez utiliser un appel intermédiaire à **fflush** ou à une fonction de positionnement de fichiers.

En plus des valeurs ci-dessus, les caractères suivants peuvent être inclus en *mode* pour spécifier le mode de traduction pour les caractères newline :

|*modificateur de mode*|Mode de traduction|
|-|-|
| **T** | Ouvrir en mode texte (traduit). |
| **B** | Ouvrez en mode binaire (non traduit); les traductions impliquant des caractères de transport-retour et d’alimentation en ligne sont supprimées. |

En mode texte (traduit), CTRL-Z est interprété comme un personnage en fin de dossier sur l’entrée. Dans les fichiers ouverts pour la lecture/écriture avec **"a"**, **fopen_s** vérifie pour un CTRL-Z à la fin du fichier et le supprime, si possible. Ceci est fait parce que l’utilisation [de fseek](fseek-fseeki64.md) et **ftell** pour se déplacer dans un fichier qui se termine par un CTRL-Z, peut provoquer [fseek](fseek-fseeki64.md) de se comporter incorrectement près de la fin du fichier.

En outre, en mode texte, les combinaisons d’alimentation en ligne de retour de transport sont traduites en flux de ligne unique sur l’entrée, et les caractères d’alimentation en ligne sont traduits en combinaisons d’alimentation de retour de transport sur la sortie. Lorsqu'une fonction d'E/S de flux Unicode s'exécute en mode texte (comportement par défaut), on suppose que le flux source ou de destination est une séquence de caractères multioctets. Par conséquent, les fonctions d’entrée de flux Unicode convertissent les caractères multioctets en caractères larges (comme après un appel à la fonction **mbtowc**). Pour la même raison, les fonctions de flux de sortie Unicode convertissent les caractères larges en caractères multioctets (comme après un appel à la fonction **wctomb**).

Si **t** ou **b** n’est pas donné en *mode,* le mode de traduction par défaut est défini par la variable globale [_fmode](../../c-runtime-library/fmode.md). Si **t** ou **b** est préfixé à l’argument, la fonction échoue et renvoie **NULL**.

Pour plus d’informations sur l’utilisation des modes texte et binaire dans les E/S de flux Unicode et multioctets, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [E/S de flux Unicode en modes texte et binaire](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*modificateur de mode*|Comportement|
|-|-|
| **C** | Activez le drapeau de validation du nom de *fichier* associé afin que le contenu du tampon de fichier soit écrit directement sur disque si **fflush** ou **_flushall** est appelé. |
| **n** | Réinitialisez le drapeau de validation du *nom de fichier* associé à « non-commit ». Il s’agit de la valeur par défaut. Substitue également l'indicateur de validation global si vous liez votre programme avec COMMODE.OBJ. La valeur par défaut de l’indicateur de validation globale est « no-commit », sauf si vous liez explicitement votre programme avec COMMODE.OBJ (consultez [Link Options](../../c-runtime-library/link-options.md)). |
| **Â¡n** | Indique que le fichier n'est pas hérité par les processus enfants. |
| **S** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque. |
| **R** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque. |
| **T** | Spécifie un fichier comme temporaire. Si possible, il n'est pas vidé sur disque. |
| **D** | Spécifie un fichier comme temporaire. Il est supprimé lorsque le dernier pointeur de fichier est fermé. |
| **codage ccsMD**_encoding_ | Spécifie le caractère codé mis à utiliser (un de **UTF-8**, **UTF-16LE**, ou **UNICODE**) pour ce fichier. Laissez ce paramètre non spécifié si vous souhaitez bénéficier de l'encodage ANSI. |

Les caractères valides pour la chaîne *de mode* utilisée dans **fopen_s** et [_fdopen](fdopen-wfdopen.md) correspondent à des arguments *delag* utilisés dans [_open](open-wopen.md) et [_sopen,](sopen-wsopen.md)comme suit.

|Personnages dans la chaîne *de mode*|Équivalent *de* valeur pour _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**Un**|**_O_WRONLY** **_O_APPEND &#124;** (généralement **_O_WRONLY** &#124; **_O_CREAT &#124;** _O_APPEND)|
|**a**|**_O_RDWR** **_O_APPEND** &#124; (généralement **_O_RDWR** &#124; _O_APPEND _O_CREAT **de** **&#124;)**|
|**R**|**_O_RDONLY**|
|**r**|**_O_RDWR**|
|**W**|**_O_WRONLY** (généralement **_O_WRONLY** &#124; **_O_CREAT** &#124;md _O_TRUNCMD)|
|**w**|**_O_RDWR** (généralement **_O_RDWR** &#124; _O_CREAT **&#124;** **_O_TRUNC)**|
|**B**|**_O_BINARY**|
|**T**|**_O_TEXT**|
|**C**|None|
|**n**|None|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs-UNICODE**|**_O_WTEXT**|
|**ccs-UTF-8**|**_O_UTF8**|
|**ccs-UTF-16LE**|**_O_UTF16**|

Si vous utilisez le mode **rb,** n’aurez pas besoin de porter votre code, et s’attendre à lire une grande partie du fichier et / ou ne se soucient pas des performances du réseau, mémoire cartographié fichiers Win32 peut également être une option.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

Les options de **t** *mode* **c**, **n**, et t sont des extensions Microsoft pour **fopen_s** et [_fdopen](fdopen-wfdopen.md) et ne doivent pas être utilisées là où la portabilité ANSI est souhaitée.

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

   // Open for read (will fail if file "crt_fopen_s.c" does not exist)
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

   // Close stream if it is not NULL
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

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
