---
title: fopen, _wfopen
ms.date: 11/04/2016
apiname:
- _wfopen
- fopen
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
ms.openlocfilehash: a8b204c2bf48802b8efcfe5ca487d62876942c29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540334"
---
# <a name="fopen-wfopen"></a>fopen, _wfopen

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

*filename*<br/>
Nom du fichier.

*mode*<br/>
Genre d'accès qui est activé.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le fichier ouvert. Une valeur de pointeur null indique une erreur. Si *filename* ou *mode* est **NULL** ou une chaîne vide, ces fonctions déclenchent le Gestionnaire de paramètre non valide, ce qui est décrit dans [paramètre Validation](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **NULL** et définissez **errno** à **EINVAL**.

Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **fopen** fonction ouvre le fichier spécifié par *filename*. Par défaut, une étroite *filename* chaîne est interprétée à l’aide de la page de codes ANSI (CP_ACP). Dans les applications de bureau Windows, la page de codes OEM (CP_OEMCP) peut être utilisée à la place avec la fonction [SetFileApisToOEM](/windows/desktop/api/fileapi/nf-fileapi-setfileapistooem) . Vous pouvez utiliser la [AreFileApisANSI](/windows/desktop/api/fileapi/nf-fileapi-arefileapisansi) fonction permettant de déterminer si *filename* est interprétée à l’aide de l’ANSI ou la page de codes OEM de valeur par défaut système. **_wfopen** est une version à caractères larges de **fopen**; les arguments de **_wfopen** sont des chaînes à caractères larges. Sinon, **_wfopen** et **fopen** ont un comportement identique. En utilisant simplement **_wfopen** n’affecte pas le jeu de caractères codé utilisé dans le flux de fichier.

**fopen** accepte les chemins d’accès valides sur le système de fichiers au moment de l’exécution ; **fopen** accepte les chemins d’accès UNC et des chemins d’accès qui impliquent des lecteurs réseau mappés tant que le système qui exécute le code a accès au partage ou au lecteur mappé au moment de l’exécution. Lorsque vous construisez des chemins d’accès pour **fopen**, assurez-vous que les lecteurs, les chemins d’accès ou les partages réseau sera disponibles dans l’environnement d’exécution. Vous pouvez utiliser des barres obliques (/) ou des barres obliques inverses (\\) comme séparateurs de répertoire dans un chemin.

Vérifiez toujours la valeur de retour pour voir si le pointeur est null avant d'exécuter toute une autre opération sur le fichier. Si une erreur se produit, la variable globale **errno** est défini et peut être utilisé pour obtenir des informations d’erreur spécifiques. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Prise en charge Unicode

**fopen** prend en charge les flux de fichiers Unicode. Pour ouvrir un fichier Unicode, passez un **ccs** indicateur qui spécifie l’encodage souhaité à **fopen**, comme suit.

> **FICHIER *fp = fopen (« newfile.txt », « rt + ccs =**_encodage_**») ;**

Valeurs autorisées de *encodage* sont **UNICODE**, **UTF-8**, et **UTF-16LE**.

Lorsqu’un fichier est ouvert en mode Unicode, les fonctions d’entrée traduisent les données lues à partir du fichier en données UTF-16 stockées comme type **wchar_t**. Fonctions qui écrivent dans un fichier ouvert en mode Unicode attendent des mémoires tampons qui contiennent des données UTF-16 stockées comme type **wchar_t**. Si le fichier est encodé au format UTF-8, les données UTF-16 sont traduites en UTF-8 lors de leur écriture et le contenu du fichier encodé au format UTF-8 est traduit en UTF-16 lorsqu'il est lu. Toute tentative de lecture ou d'écriture d'un nombre impair d'octets en mode Unicode provoque une erreur de [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Pour lire ou écrire des données stockées dans votre programme au format UTF-8, utilisez un mode de fichier binaire ou texte au lieu d'un mode Unicode. Vous êtes responsable de toute traduction d'encodage nécessaire.

Si le fichier existe déjà et qu'il est ouvert pour lecture ou ajout, la marque d'ordre d'octet (BOM, Byte Order Mark), si elle est présente dans le fichier, détermine l'encodage. L’encodage BOM est prioritaire sur l’encodage spécifié par le **ccs** indicateur. Le **ccs** encodage est utilisé uniquement lorsque aucune marque BOM n’est présent ou le fichier est un nouveau fichier.

> [!NOTE]
> La détection BOM s’applique uniquement aux fichiers qui sont ouverts en mode Unicode (autrement dit, en passant le **ccs** indicateur).

Le tableau suivant récapitule les modes qui sont utilisés pour différents **ccs** indicateurs donnés **fopen** et marques d’ordre d’octet dans le fichier.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Encodages utilisés selon l'indicateur ccs et la marque BOM

|indicateur de CCS|Aucune marque BOM (ou nouveau fichier)|Marque BOM : UTF-8|Marque BOM : UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Une marque BOM est écrite automatiquement dans les fichiers ouverts pour écriture en mode Unicode.

Si *mode* est **» a, ccs =**_encodage_**»**, **fopen** tente d’abord d’ouvrir le fichier à l’aide en lecture accès et en écriture. Si l'opération réussit, la fonction lit la marque BOM pour déterminer l'encodage du fichier ; si elle échoue, la fonction utilise l'encodage par défaut pour le fichier. Dans les deux cas, **fopen** rouvrira le fichier en utilisant l’accès en écriture seule. (Cela s’applique aux **« a »** mode uniquement, pas pour **« a + »** mode.)

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

La chaîne de caractères *mode* Spécifie le type d’accès demandé pour le fichier, comme suit.

|*mode*|Accès|
|-|-|
**"r"**|Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, la **fopen** appeler échoue.
**"w"**|Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit.
**"a"**|S'ouvre pour écriture à la fin du fichier (ajout) sans supprimer le marqueur de fin de fichier (EOF) avant que de nouvelles données soient écrites dans le fichier. Crée le fichier s'il n'existe pas.
**"r+"**|Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister.
**"w+"**|Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit.
**"a+"**|S'ouvre pour lecture et ajout. L'opération d'ajout inclut la suppression du marqueur EOF avant que de nouvelles données soient écrites dans le fichier. Le marqueur EOF n'est pas restauré une fois l'écriture terminée. Crée le fichier s'il n'existe pas.

Quand un fichier est ouvert à l’aide de la **« a »** type d’accès ou le **« a + »** accéder au type, toutes les opérations se produisent à la fin du fichier d’écriture. Le pointeur de fichier peut être repositionné à l’aide de [fseek](fseek-fseeki64.md) ou [rewind](rewind.md), mais est toujours redéplacé à la fin du fichier avant toute opération d’écriture. Par conséquent, les données existantes ne peuvent pas être remplacées.

Le **« a »** mode ne supprime pas le marqueur EOF avant d’ajouter au fichier. Après l'ajout, la commande MS-DOS TYPE affiche uniquement les données jusqu'au marqueur EOF d'origine, et non les données ajoutées au fichier. Avant d’ajouter au fichier, le **« a + »** mode ne supprime pas le marqueur EOF. Après l'ajout, la commande MS-DOS TYPE affiche toutes les données du fichier. Le **« a + »** mode est obligatoire pour ajouter des données dans un fichier de flux de données qui se termine par le marqueur EOF CTRL + Z.

Lorsque le **« r + »**, **« w + »**, ou **« a + »** type d’accès est spécifié, la lecture et l’écriture sont activés (le fichier est réputé être ouvert pour « update »). Toutefois, lorsque vous basculez de la lecture à l'écriture, l'opération d'entrée doit rencontrer un marqueur EOF. S'il n'existe aucun marqueur EOF, vous devez utiliser un appel à une fonctionnalité de positionnement de fichier. Les fonctions de positionnement de fichier sont **fsetpos**, [fseek](fseek-fseeki64.md), et [rewind](rewind.md). Lorsque vous basculez d’écriture à la lecture, vous devez utiliser un appel à **fflush** ou à une fonction de positionnement de fichier.

Outre les valeurs précédentes, les caractères suivants peuvent être ajoutés aux *mode* pour spécifier le mode de traduction pour les caractères de saut de ligne.

|*mode* modificateur|Mode de traduction|
|-|-|
**t**|Ouvrir en mode texte (traduit).
**b**|Ouvrir en mode binaire (non traduit) ; les traductions implique la suppression des caractères de retour chariot et de saut de ligne.

En mode texte, CTRL + Z est interprété comme un caractère EOF en entrée. Dans les fichiers qui sont ouverts en lecture/écriture à l’aide de **« a + »**, **fopen** recherche un CTRL + Z à la fin du fichier et le supprime, si possible. En effet à l’aide de [fseek](fseek-fseeki64.md) et **ftell** pour se déplacer dans un fichier qui se termine par CTRL + Z peut provoquer [fseek](fseek-fseeki64.md) comportement incorrect vers la fin du fichier.

En mode texte, combinaisons de sauts de ligne de chariot sont traduites en sauts de ligne uniques en entrée, et les caractères de saut de ligne sont traduits en combinaisons de sauts de ligne de chariot en sortie. Lorsqu'une fonction d'E/S de flux Unicode s'exécute en mode texte (comportement par défaut), on suppose que le flux source ou de destination est une séquence de caractères multioctets. Par conséquent, les fonctions d’entrée de flux Unicode convertissent les caractères multioctets en caractères larges (comme après un appel à la fonction **mbtowc**). Pour la même raison, les fonctions de flux de sortie Unicode convertissent les caractères larges en caractères multioctets (comme après un appel à la fonction **wctomb**).

Si **t** ou **b** n’est pas spécifié dans *mode*, le mode de traduction par défaut est défini par la variable globale [_fmode](../../c-runtime-library/fmode.md). Si **t** ou **b** est préfixé à l’argument, la fonction échoue et le retourne **NULL**.

Pour plus d’informations sur la façon d’utiliser les modes texte et binaire dans les E/S de flux multioctets et Unicode, consultez [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Les options suivantes peuvent être ajoutées aux *mode* pour spécifier des comportements supplémentaires.

|*mode* modificateur|Comportement|
|-|-|
**c**|Activer l’indicateur de validation associé au *filename* afin que le contenu de la mémoire tampon de fichier est écrites directement sur le disque si **fflush** ou **_flushall** est appelée.
**n**|Réinitialiser l’indicateur de validation associé au *filename* pour « no-commit ». Il s'agit de la valeur par défaut. Substitue également l'indicateur de validation global si vous liez votre programme avec COMMODE.OBJ. La valeur par défaut de l’indicateur de validation globale est « no-commit », sauf si vous liez explicitement votre programme avec COMMODE.OBJ (consultez [Link Options](../../c-runtime-library/link-options.md)).
**N**|Indique que le fichier n'est pas hérité par les processus enfants.
**S**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque.
**R**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque.
**T**|Spécifie un fichier comme temporaire. Si possible, il n'est pas vidé sur disque.
**D**|Spécifie un fichier comme temporaire. Il est supprimé lorsque le dernier pointeur de fichier est fermé.
**CCS =**_encodage_|Spécifie le codé en jeu de caractères à utiliser (un des **UTF-8**, **UTF-16LE**, ou **UNICODE**) pour ce fichier. Laissez ce paramètre non spécifié si vous souhaitez bénéficier de l'encodage ANSI.

Caractères valides pour le *mode* chaîne qui est utilisée dans **fopen** et **_fdopen** correspondent aux *oflag* arguments qui sont utilisés dans [_open](open-wopen.md) et [_sopen](sopen-wsopen.md), comme suit.

|Les caractères de *mode* chaîne|Équivalent *oflag* valeur pour _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** &#124; **_O_APPEND** (généralement **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_APPEND **)|
|**a +**|**_O_RDWR** &#124; **_O_APPEND** (généralement **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**w**|**_O_WRONLY** (généralement **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_TRUNC **)|
|**w +**|**_O_RDWR** (généralement **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|Aucun.|
|**n**|Aucun.|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**CCS = UNICODE**|**_O_WTEXT**|
|**CCS = UTF-8**|**_O_UTF8**|
|**CCS = UTF-16LE**|**_O_UTF16**|

Si vous utilisez **rb** mode, vous n’avez pas porter votre code, et si vous attendez à lire la majeure partie d’un fichier volumineux ou ne souhaitez pas concernées sur les performances du réseau, vous pouvez également envisager si utiliser la mémoire des fichiers Win32 mappés en tant qu’option.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> ou \<wchar.h>|

**_wfopen** est une extension Microsoft. Pour plus d'informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

Le **c**, **n**, **t**, **S**, **R**, **T**, et **D**  *mode* options sont des extensions Microsoft pour **fopen** et **_fdopen** et ne doit pas être utilisé lorsque la portabilité ANSI est souhaitée.

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
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
