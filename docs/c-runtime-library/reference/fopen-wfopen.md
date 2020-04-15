---
title: fopen, _wfopen
ms.date: 4/2/2020
api_name:
- _wfopen
- fopen
- _o__wfopen
- _o_fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: 4b9fa6542996b2c16128a841e2611b85e995be2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346409"
---
# <a name="fopen-_wfopen"></a>fopen, _wfopen

Ouvre un fichier. Des versions plus sécurisées de ces fonctions qui effectuent des validations supplémentaires des paramètres et retournent des codes d’erreur sont disponibles. Consultez [fopen_s, _wfopen_s](fopen-s-wfopen-s.md).

## <a name="syntax"></a>Syntaxe

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Paramètres

*Fichier*<br/>
Nom du fichier.

*mode*<br/>
Genre d'accès qui est activé.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le fichier ouvert. Une valeur de pointeur null indique une erreur. Si *le nom de fichier* ou le *mode* est **NULL** ou une chaîne vide, ces fonctions déclenchent le gestionnaire de paramètres invalide, qui est décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions renvoient **NULL** et **placent errno** à **EINVAL**.

Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **fopen** ouvre le fichier qui est spécifié par *nom de fichier*. Par défaut, une chaîne de *nom de fichier* étroite est interprétée à l’aide de la page de code ANSI (CP_ACP). Dans les applications de bureau Windows, la page de codes OEM (CP_OEMCP) peut être utilisée à la place avec la fonction [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) . Vous pouvez utiliser la fonction [AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) pour déterminer si le *nom de fichier* est interprété à l’aide de la page de code OEM par défaut du système. **_wfopen** est une version à caractère large de **fopen;** les arguments pour **_wfopen** sont des chaînes de caractère large. Sinon, **_wfopen** et **fopen** se comportent de façon identique. L’utilisation **de _wfopen** n’affecte pas l’ensemble de caractères codé qui est utilisé dans le flux de fichiers.

**fopen** accepte les voies qui sont valables sur le système de fichiers au point d’exécution; **fopen** accepte les chemins et les chemins de l’UNC qui impliquent des lecteurs réseau cartographiés tant que le système qui exécute le code a accès à la part ou à la commande cartographiée au moment de l’exécution. Lorsque vous construisez des chemins pour **fopen,** assurez-vous que les lecteurs, les chemins ou les actions réseau seront disponibles dans l’environnement d’exécution. Vous pouvez utiliser des barres obliques (/) ou des barres obliques inverses (\\) comme séparateurs de répertoire dans un chemin.

Vérifiez toujours la valeur de retour pour voir si le pointeur est null avant d'exécuter toute une autre opération sur le fichier. En cas d’erreur, le **errno** variable global est réglé et peut être utilisé pour obtenir des informations d’erreur spécifiques. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="unicode-support"></a>Prise en charge d'Unicode

**fopen** prend en charge les flux de fichiers Unicode. Pour ouvrir un fichier Unicode, passez un indicateur **ccs** qui spécifie l’encodage souhaité à **fopen**, comme suit.

> **FILE \*fp - fopen ("newfile.txt", "rt, ccs'**_encodage_**");**

Les valeurs autorisées *d’encodage* sont **UNICODE**, **UTF-8**, et **UTF-16LE**.

Lorsqu’un fichier est ouvert en mode Unicode, les fonctions d’entrée traduisent les données lues à partir du fichier en données UTF-16 stockées sous **forme de**type wchar_t . Les fonctions qui écrivent à un fichier ouvert en mode Unicode s’attendent à des tampons qui contiennent des données UTF-16 stockées sous forme de type **wchar_t**. Si le fichier est encodé au format UTF-8, les données UTF-16 sont traduites en UTF-8 lors de leur écriture et le contenu du fichier encodé au format UTF-8 est traduit en UTF-16 lorsqu'il est lu. Une tentative de lire ou d’écrire un nombre impair d’octets en mode Unicode provoque une erreur [de validation de paramètres.](../../c-runtime-library/parameter-validation.md) Pour lire ou écrire des données stockées dans votre programme au format UTF-8, utilisez un mode de fichier binaire ou texte au lieu d'un mode Unicode. Vous êtes responsable de toute traduction d'encodage nécessaire.

Si le fichier existe déjà et qu'il est ouvert pour lecture ou ajout, la marque d'ordre d'octet (BOM, Byte Order Mark), si elle est présente dans le fichier, détermine l'encodage. L’encodage BOM prime sur l’encodage spécifié par le drapeau **ccs.** L’encodage **ccs** n’est utilisé que lorsqu’aucun BOM n’est présent ou que le fichier est un nouveau fichier.

> [!NOTE]
> La détection BOM ne s’applique qu’aux fichiers ouverts en mode Unicode (c’est-à-dire en passant le drapeau **ccs).**

Le tableau suivant résume les modes utilisés pour divers signaux **d’alarme administrés** aux marques **de fopen** et d’ordre byte dans le fichier.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codages utilisés selon l'indicateur ccs et la marque BOM

|indicateur ccs|Aucune marque BOM (ou nouveau fichier)|Marque BOM : UTF-8|Marque BOM : UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Une marque BOM est écrite automatiquement dans les fichiers ouverts pour écriture en mode Unicode.

Si *le mode* est " **a, ccs '**_codage_**",** **fopen** tente d’abord d’ouvrir le fichier en utilisant à la fois lire et écrire l’accès. Si l'opération réussit, la fonction lit la marque BOM pour déterminer l'encodage du fichier ; si elle échoue, la fonction utilise l'encodage par défaut pour le fichier. Dans les deux cas, **fopen** rouvrira ensuite le fichier en utilisant l’accès à la écriture seulement. (Cela s’applique uniquement au mode **« a »** et non au mode « a **»** .)

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

Le *mode* de chaîne de caractères spécifie le type d’accès demandé pour le fichier, comme suit.

|*mode*|Accès|
|-|-|
| **"r"** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou ne peut pas être trouvé, **l’appel fopen** échoue. |
| **"w"** | Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit. |
| **"a"** | S'ouvre pour écriture à la fin du fichier (ajout) sans supprimer le marqueur de fin de fichier (EOF) avant que de nouvelles données soient écrites dans le fichier. Crée le fichier s'il n'existe pas. |
| **"r"** | Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister. |
| **"W"** | Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit. |
| **"A"** | S'ouvre pour lecture et ajout. L'opération d'ajout inclut la suppression du marqueur EOF avant que de nouvelles données soient écrites dans le fichier. Le marqueur EOF n'est pas restauré une fois l'écriture terminée. Crée le fichier s'il n'existe pas. |

Lorsqu’un fichier est ouvert en utilisant le type **d’accès « a »** ou le type **d’accès « a »,** toutes les opérations d’écriture se produisent à la fin du fichier. Le pointeur de fichier peut être repositionné en utilisant [fseek](fseek-fseeki64.md) ou [rembobinage](rewind.md), mais est toujours déplacé vers la fin du fichier avant toute opération d’écriture est effectuée. Par conséquent, les données existantes ne peuvent pas être remplacées.

Le mode **"a"** ne supprime pas le marqueur EOF avant qu’il ne s’abat sur le fichier. Après l'ajout, la commande MS-DOS TYPE affiche uniquement les données jusqu'au marqueur EOF d'origine, et non les données ajoutées au fichier. Avant qu’il n’appende le fichier, le mode **« a »** supprime le marqueur EOF. Après l'ajout, la commande MS-DOS TYPE affiche toutes les données du fichier. Le mode **« a »** est nécessaire pour passer à un fichier de flux qui est terminé avec le marqueur EOF CTRL-Z.

Lorsque le type **d’accès « r »**, **« w »** ou « **a »** est spécifié, la lecture et l’écriture sont activées (le fichier est dit ouvert pour la « mise à jour »). Toutefois, lorsque vous basculez de la lecture à l'écriture, l'opération d'entrée doit rencontrer un marqueur EOF. S'il n'existe aucun marqueur EOF, vous devez utiliser un appel à une fonctionnalité de positionnement de fichier. Les fonctions de positionnement de fichier sont **fsetpos**, [fseek](fseek-fseeki64.md), et [rembobiner](rewind.md). Lorsque vous passez de l’écriture à la lecture, vous devez utiliser un appel intermédiaire à **fflush** ou à une fonction de positionnement de fichier.

En plus des valeurs antérieures, les caractères suivants peuvent être annexés en *mode* pour spécifier le mode de traduction pour les caractères newline.

|*modificateur de mode*|Mode de traduction|
|-|-|
| **T** | Ouvrir en mode texte (traduit). |
| **B** | Ouvrez en mode binaire (non traduit); les traductions impliquant des caractères de transport-retour et d’alimentation en ligne sont supprimées. |

En mode texte, CTRL-Z est interprété comme un personnage EOF sur l’entrée. Dans les fichiers ouverts pour la lecture/écriture en utilisant **"a"**, les contrôles **fopen** pour un CTRL-Z à la fin du fichier et le supprime, si c’est possible. Ceci est fait parce que l’utilisation [de fseek](fseek-fseeki64.md) et **ftell** pour se déplacer dans un fichier qui se termine avec CTRL-Z peut provoquer [fseek](fseek-fseeki64.md) de se comporter incorrectement vers la fin du fichier.

En mode texte, les combinaisons d’alimentation en ligne de retour de transport sont traduites en flux de ligne unique sur l’entrée, et les caractères d’alimentation en ligne sont traduits en combinaisons d’alimentation de retour de transport sur la sortie. Lorsqu'une fonction d'E/S de flux Unicode s'exécute en mode texte (comportement par défaut), on suppose que le flux source ou de destination est une séquence de caractères multioctets. Par conséquent, les fonctions d’entrée de flux Unicode convertissent les caractères multioctets en caractères larges (comme après un appel à la fonction **mbtowc**). Pour la même raison, les fonctions de flux de sortie Unicode convertissent les caractères larges en caractères multioctets (comme après un appel à la fonction **wctomb**).

Si **t** ou **b** n’est pas donné en *mode,* le mode de traduction par défaut est défini par la variable globale [_fmode](../../c-runtime-library/fmode.md). Si **t** ou **b** est préfixé à l’argument, la fonction échoue et renvoie **NULL**.

Pour plus d’informations sur la façon d’utiliser les modes texte et binaire dans les E/S de flux multioctets et Unicode, consultez [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Les options suivantes peuvent être annexées en *mode* pour spécifier des comportements supplémentaires.

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

Les caractères valides pour la chaîne *de mode* qui est utilisé dans **le fopen** et **_fdopen** correspondent à des arguments *delag* qui sont utilisés dans [_open](open-wopen.md) et [_sopen](sopen-wsopen.md), comme suit.

|Personnages dans la chaîne *de mode*|Équivalent de valeur \_ *delag* pour l’ouverture /\_sopen|
|-------------------------------|----------------------------------------------------|
|**Un**|**\_O\_WRONLY** &#124; ** \_O\_APPEND** (généralement ** \_O\_WRONLY** &#124; ** \_O\_CREAT** &#124; ** \_\_O APPEND**)|
|**a**|**\_O\_RDWR** &#124; ** \_O\_APPEND** (généralement ** \_O\_RDWR** &#124; ** \_O\_APPEND** &#124; ** \_O\_CREAT** )|
|**R**|**\_O\_RDONLY**|
|**r**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (généralement ** \_\_O WRONLY** &#124; ** \_O\_CREAT** &#124; ** \_O\_TRUNC**)|
|**w**|**\_O\_RDWR** (généralement ** \_\_O RDWR** &#124; ** \_\_O CREAT** &#124; ** \_O\_TRUNC**)|
|**B**|**\_O\_BINAIRE**|
|**T**|**\_O\_TEXTE**|
|**C**|None|
|**n**|None|
|**S**|**\_O\_SÉQUENTIEL**|
|**R**|**\_O\_ALÉATOIRE**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_TEMPORAIRE**|
|**ccs-UNICODE**|**\_O\_WTEXT**|
|**ccs-UTF-8**|**\_O\_UTF8**|
|**ccs-UTF-16LE**|**\_O\_UTF16**|

Si vous utilisez le mode **rb,** vous n’avez pas à porter votre code, et si vous vous attendez à lire la plupart d’un grand fichier ou ne sont pas préoccupés par les performances du réseau, vous pouvez également envisager d’utiliser la mémoire cartographié fichiers Win32 comme une option.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> ou \<wchar.h>|

**_wfopen** est une extension Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

Les options de *mode* **c**, **n**, **t**, **S**, **R**, **T**et **D** sont des extensions Microsoft pour **le fopen** et **_fdopen** et ne doivent pas être utilisées là où la portabilité ansI est souhaitée.

## <a name="example-1"></a>Exemple 1

Le programme suivant ouvre deux fichiers.  Il utilise **fclose** pour fermer le premier fichier et **_fcloseall** pour fermer tous les fichiers restants.

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>Exemple 2

Le programme suivant crée un fichier (ou le remplace s'il existe), en mode texte avec encodage Unicode.  Il écrit ensuite deux chaînes dans le fichier et ferme le fichier. La sortie est un fichier nommé _wfopen_test.xml, qui contient les données de la section de sortie.

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
