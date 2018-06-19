---
title: fopen_s, _wfopen_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfopen_s
- fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef5587188cebe4ed7e91cbd95eb46cca7f05044
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405625"
---
# <a name="fopens-wfopens"></a>fopen_s, _wfopen_s

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

*pFile*<br/>
Pointeur désignant le pointeur de fichier appelé à recevoir le pointeur vers le fichier ouvert.

*filename*<br/>
Nom de fichier.

*mode*<br/>
Type d'accès autorisé.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec. Pour plus d’informations sur ces codes d’erreur, consultez, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d’erreur

|*pFile*|*filename*|*mode*|Valeur de retour|Contenu de *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|any|any|**EINVAL**|inchangé|
|any|**NULL**|any|**EINVAL**|inchangé|
|any|any|**NULL**|**EINVAL**|inchangé|

## <a name="remarks"></a>Notes

Les fichiers ouverts par **fopen_s** et **_wfopen_s** ne sont pas partageable. Si vous avez besoin qu’un fichier être partageable, utilisez [_fsopen, _wfsopen](fsopen-wfsopen.md) avec la constante de mode de partage appropriée, par exemple, **_SH_DENYNO** pour le partage de lecture/écriture.

Le **fopen_s** fonction ouvre le fichier spécifié par *nom de fichier*. **_wfopen_s** est une version à caractères larges de **fopen_s**; les arguments de **_wfopen_s** sont des chaînes à caractères larges. **_wfopen_s** et **fopen_s** comportent de façon identique.

**fopen_s** accepte les chemins d’accès valides sur le système de fichiers au point d’exécution ; Chemins d’accès UNC et les chemins d’accès qui impliquent des lecteurs réseau mappés sont acceptés par **fopen_s** tant que le système qui exécute le code a accès au partage ou au lecteur réseau mappé au moment de l’exécution. Lorsque vous construisez des chemins d’accès pour **fopen_s**, ne faites pas hypothèses quant à la disponibilité des lecteurs, chemins d’accès, ou partages réseau dans l’environnement d’exécution. Vous pouvez utiliser des barres obliques (/) ou des barres obliques inverses (\\) comme séparateurs de répertoire dans un chemin.

Ces fonctions valident leurs paramètres. Si *pFile*, *nom de fichier*, ou *mode* est un pointeur null, ces fonctions génèrent une exception de paramètre non valide, comme décrit dans [Validation de paramètre ](../../c-runtime-library/parameter-validation.md).

Vérifiez toujours la valeur de retour pour savoir si la fonction a abouti avant d'effectuer d'autres opérations sur le fichier. Si une erreur se produit, le code d’erreur est retourné et la variable globale **errno** est définie. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Prise en charge Unicode

**fopen_s** prend en charge les flux de fichiers Unicode. Pour ouvrir un fichier Unicode nouveau ou existant, passez un *ccs* indicateur qui spécifie l’encodage souhaité à **fopen_s**:

**fopen_s (& fp, « newfile.txt », « rw, ccs =**_codage_**») ;**

Valeurs autorisées de *codage* sont **UNICODE**, **UTF-8**, et **UTF-16LE**. Si aucune valeur n’est spécifiée il *codage*, **fopen_s** utilise le codage ANSI.

Si le fichier existe déjà et qu'il est ouvert pour lecture ou ajout, la marque d'ordre d'octet (BOM, Byte Order Mark), si elle est présente dans le fichier, détermine le codage. L’encodage BOM est prioritaire sur l’encodage spécifié par le *ccs* indicateur. Le *ccs* codage est utilisé uniquement lorsque aucune marque BOM n’est présent ou si le fichier est un nouveau fichier.

> [!NOTE]
> Détection BOM s’applique uniquement aux fichiers qui sont ouverts en mode Unicode ; Autrement dit, en passant le *ccs* indicateur.

Le tableau suivant résume les modes de diverses *ccs* indicateurs qui sont attribuées aux **fopen_s** et pour les marques d’ordre d’octet dans le fichier.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Encodages utilisés selon l'indicateur ccs et la marque BOM

|indicateur de CCS|Aucune marque BOM (ou nouveau fichier)|Marque BOM : UTF-8|Marque BOM : UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Une marque BOM est écrite automatiquement dans les fichiers ouverts pour écriture en mode Unicode.

Si *mode* est **», ccs =**_codage_**»**, **fopen_s** tente d’abord d’ouvrir le fichier avec accès en lecture accès et un accès en écriture. En cas de réussite, la fonction lit la marque BOM pour déterminer le codage du fichier ; en cas d'échec, elle utilise le codage par défaut pour le fichier. Dans les deux cas, **fopen_s** ouvrir à nouveau le fichier avec un accès en écriture seule. (Cela s’applique aux **un** n’est pas en mode uniquement, **a +**.)

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

La chaîne de caractères *mode* Spécifie le type d’accès demandé pour le fichier, comme suit.

|*mode*|Accès|
|-|-|
**"r"**|Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, la **fopen_s** appel échoue.
**"w"**|Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit.
**"a"**|S'ouvre pour écriture à la fin du fichier (ajout) sans supprimer le marqueur de fin de fichier (EOF) avant que de nouvelles données soient écrites dans le fichier. Crée le fichier s'il n'existe pas.
**"r+"**|Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister.
**"w+"**|Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit.
**"a+"**|S'ouvre pour lecture et ajout. L'opération d'ajout inclut la suppression du marqueur EOF avant que de nouvelles données soient écrites dans le fichier. Le marqueur EOF n'est pas restauré une fois l'écriture terminée. Crée le fichier s'il n'existe pas.

Quand un fichier est ouvert à l’aide de la **« a »** ou **« a + »** accéder au type, toutes les opérations se produisent à la fin du fichier d’écriture. Le pointeur de fichier peut être repositionné à l’aide de [fseek](fseek-fseeki64.md) ou [rembobiner](rewind.md), mais il est toujours redéplacé à la fin du fichier avant toute opération est effectuée afin que les données existantes ne peuvent pas être remplacées d’écriture.

Le **« a »** mode ne supprime pas le marqueur EOF avant d’ajouter au fichier. Après l'ajout, la commande MS-DOS TYPE affiche uniquement les données jusqu'au marqueur EOF d'origine, et non les données qui sont ajoutées au fichier. Le **« a + »** mode supprime le marqueur EOF avant l’ajout au fichier. Après l'ajout, la commande MS-DOS TYPE affiche toutes les données du fichier. Le **« a + »** mode est obligatoire pour ajouter des données dans un fichier de flux de données qui se termine par le marqueur EOF CTRL + Z.

Lorsque le **« r + »**, **« w + »**, ou **« a + »** type d’accès est spécifié, la lecture et l’écriture sont autorisées. (On dit que le fichier est ouvert pour « mise à jour ».) Toutefois, lorsque vous basculez de la lecture à l'écriture, l'opération d'entrée doit rencontrer un marqueur EOF. S'il n'existe aucun marqueur EOF, vous devez faire un appel intermédiaire à une fonction de positionnement de fichier. Les fonctions de positionnement de fichier sont **fsetpos**, [fseek](fseek-fseeki64.md), et [rembobiner](rewind.md). Lorsque vous basculez de l’écriture à lecture, vous devez utiliser un appel à **fflush** ou à une fonction de positionnement de fichier.

Outre les valeurs ci-dessus, les caractères suivants peuvent être inclus dans *mode* pour spécifier le mode de traduction des caractères de saut de ligne :

|*mode* modificateur|Mode de traduction|
|-|-|
**t**|Ouvrir en mode texte (traduit).
**b**|Ouvrir en mode binaire (non traduit) ; les traductions implique la suppression des caractères de retour chariot et de saut de ligne.

En mode texte (traduit), CTRL + Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture/écriture avec **« a + »**, **fopen_s** recherche un CTRL + z à la fin du fichier et le supprime, si possible. Pour cela, car il est à l’aide de [fseek](fseek-fseeki64.md) et **ftell** pour se déplacer dans un fichier qui se termine par un CTRL + Z peut provoquer [fseek](fseek-fseeki64.md) comportement incorrect vers la fin du fichier.

En outre, en mode texte, combinaisons de sauts de ligne de chariot sont traduites en sauts de ligne uniques en entrée, et les caractères de saut de ligne sont traduits en combinaisons de sauts de ligne de chariot en sortie. Lorsqu'une fonction d'E/S de flux Unicode s'exécute en mode texte (comportement par défaut), on suppose que le flux source ou de destination est une séquence de caractères multioctets. Par conséquent, les fonctions d’entrée de flux Unicode convertissent les caractères multioctets en caractères larges (comme après un appel à la fonction **mbtowc**). Pour la même raison, les fonctions de flux de sortie Unicode convertissent les caractères larges en caractères multioctets (comme après un appel à la fonction **wctomb**).

Si **t** ou **b** n’est pas donné dans *mode*, le mode de traduction par défaut est défini par la variable globale [_fmode](../../c-runtime-library/fmode.md). Si **t** ou **b** est préfixé à l’argument, la fonction échoue et le retourne **NULL**.

Pour plus d’informations sur l’utilisation des modes texte et binaire dans les E/S de flux Unicode et multioctets, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [E/S de flux Unicode en modes texte et binaire](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*mode* modificateur|Comportement|
|-|-|
**c**|Activer l’indicateur de validation associé au *nom de fichier* afin que le contenu de la mémoire tampon de fichier est écrites directement sur le disque si le paramètre **fflush** ou **_flushall** est appelée.
**n**|Réinitialiser l’indicateur de validation associé au *nom de fichier* pour « no-commit ». Il s'agit de la valeur par défaut. Substitue également l'indicateur de validation global si vous liez votre programme avec COMMODE.OBJ. La valeur par défaut de l’indicateur de validation globale est « no-commit », sauf si vous liez explicitement votre programme avec COMMODE.OBJ (consultez [Link Options](../../c-runtime-library/link-options.md)).
**N**|Indique que le fichier n'est pas hérité par les processus enfants.
**S**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque.
**R**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque.
**T**|Spécifie un fichier comme temporaire. Si possible, il n'est pas vidé sur disque.
**D**|Spécifie un fichier comme temporaire. Il est supprimé lorsque le dernier pointeur de fichier est fermé.
**CCS =**_codage_|Spécifie le jeu à utiliser de caractères codés (un des **UTF-8**, **UTF-16LE**, ou **UNICODE**) pour ce fichier. Laissez ce paramètre non spécifié si vous souhaitez bénéficier de l'encodage ANSI.

Les caractères valides pour le *mode* chaîne utilisée dans **fopen_s** et [_fdopen](fdopen-wfdopen.md) correspondent aux *oflag* arguments utilisés dans [_ Ouvrez](open-wopen.md) et [_sopen](sopen-wsopen.md), comme suit.

|Les caractères de *mode* chaîne|Équivalent *oflag* valeur _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** &#124; **_O_APPEND** (généralement **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_APPEND **)|
|**un +**|**_O_RDWR** &#124; **_O_APPEND** (généralement **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**w**|**_O_WRONLY** (généralement **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_TRUNC **)|
|**w +**|**_O_RDWR** (généralement **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|Aucun|
|**n**|Aucun|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**CCS = UNICODE**|**_O_WTEXT**|
|**CCS = UTF-8**|**_O_UTF8**|
|**CCS = UTF-16LE**|**_O_UTF16**|

Si vous utilisez **rb** mode, ne doivent porter votre code et s’attendent à lire un lot du fichier et/ou ne vous souciez des performances réseau, les fichiers Win32 mappés en mémoire peuvent être également une option.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

Le **c**, **n**, et **t** *mode* options sont des extensions Microsoft **fopen_s** et [_fdopen](fdopen-wfdopen.md) et ne doit pas être utilisée là où la portabilité ANSI est souhaitée.

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
