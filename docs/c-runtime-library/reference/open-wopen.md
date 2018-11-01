---
title: _open, _wopen
ms.date: 11/04/2016
apiname:
- _open
- _wopen
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
- _wopen
- _topen
- _open
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
ms.openlocfilehash: 2395b1aa48b7802a508ab0cb8be1ef35a1a81564
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612986"
---
# <a name="open-wopen"></a>_open, _wopen

Ouvre un fichier. Ces fonctions sont dépréciées, car des versions plus sécurisées sont disponibles. Consultez [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _open(
   const char *filename,
   int oflag [,
   int pmode]
);
int _wopen(
   const wchar_t *filename,
   int oflag [,
   int pmode]
);
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier.

*oflag*<br/>
Type d'opérations autorisées.

*pmode*<br/>
Mode d'autorisation.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un descripteur de fichier pour le fichier ouvert. Une valeur de retour de -1 indique une erreur ; Dans ce cas **errno** est défini sur l’une des valeurs suivantes.

|Valeur de la variable errno|Condition|
|-|-|
**EACCES**|A essayé d'ouvrir un fichier en lecture seule pour un accès en écriture, le mode de partage du fichier n'autorise pas les opérations spécifiées ou le chemin d'accès donné est un répertoire.
**EEXIST**|**_O_CREAT** et **_O_EXCL** indicateurs spécifiés, mais *filename* existe déjà.
**EINVAL**|Non valide *oflag* ou *pmode* argument.
**EMFILE**|Plus aucun descripteur de fichier n'est disponible (trop de fichiers sont ouverts).
**ENOENT**|Fichier ou chemin d’accès introuvable.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_open** fonction ouvre le fichier spécifié par *filename* et le prépare pour la lecture ou écriture, comme spécifié par *oflag*. **_wopen** est une version à caractères larges de **_open**; le *filename* l’argument de **_wopen** est une chaîne de caractères larges. **_wopen** et **_open** se comportent de façon identique dans le cas contraire.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*oflag* est une expression d’entier formée à partir d’un ou plusieurs des constantes manifestes suivantes ou des combinaisons de constantes qui sont définies dans \<fcntl.h >.

|*oflag* constante|Comportement|
|-|-|
**_O_APPEND**|Déplace le pointeur de fichier à la fin du fichier avant chaque opération d'écriture.
**_O_BINARY**|Ouvre le fichier en mode binaire (non traduit). (Pour obtenir une description du mode binaire, consultez [fopen](fopen-wfopen.md).)
**_O_CREAT**|Crée un fichier et l'ouvre pour l'accès en écriture. N’a aucun effet si le fichier spécifié par *filename* existe. Le *pmode* argument est requis quand **_O_CREAT** est spécifié.
**_O_CREAT** &AMP;#124; **_O_SHORT_LIVED**|Crée un fichier temporaire et, dans la mesure du possible, n'effectue pas de vidage sur disque. Le *pmode* argument est requis quand **_O_CREAT** est spécifié.
**_O_CREAT** &AMP;#124; **_O_TEMPORARY**|Crée un fichier temporaire ; le fichier est supprimé quand le dernier descripteur de fichier est fermé. Le *pmode* argument est requis quand **_O_CREAT** est spécifié.
**_O_CREAT**&AMP;#124; ` _O_EXCL`|Retourne une valeur d’erreur si un fichier spécifié par *filename* existe. S’applique uniquement lorsque utilisé avec **_O_CREAT**.
**_O_NOINHERIT**|Empêche la création d'un descripteur de fichier partagé.
**_O_RANDOM**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque.
**_O_RDONLY**|Ouvre un fichier pour l'accès en lecture uniquement. Ne peut pas être spécifié avec **_O_RDWR** ou **_O_WRONLY**.
**_O_RDWR**|Ouvre un fichier pour l'accès en lecture et en écriture. Ne peut pas être spécifié avec **_O_RDONLY** ou **_O_WRONLY**.
**_O_SEQUENTIAL**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque.
**_O_TEXT**|Ouvre un fichier en mode texte (traduit). (Pour plus d’informations, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [fopen](fopen-wfopen.md).)
**_O_TRUNC**|Ouvre un fichier et le tronque à une longueur nulle. Le fichier doit disposer d'une autorisation en écriture. Ne peut pas être spécifié avec **_O_RDONLY**. **_O_TRUNC** utilisé avec **_O_CREAT** ouvre un fichier existant ou crée un fichier. **Remarque :** le **_O_TRUNC** indicateur détruit le contenu du fichier spécifié.
**_O_WRONLY**|Ouvre un fichier pour l'accès en écriture uniquement. Ne peut pas être spécifié avec **_O_RDONLY** ou **_O_RDWR**.
**_O_U16TEXT**|Ouvre un fichier en mode Unicode UTF-16.
**_O_U8TEXT**|Ouvre un fichier en mode Unicode UTF-8.
**_O_WTEXT**|Ouvre un fichier en mode Unicode.

Pour spécifier le mode d’accès de fichier, vous devez spécifier soit **_O_RDONLY**, **_O_RDWR**, ou **_O_WRONLY**. Il n'y a aucune valeur par défaut pour le mode d'accès.

Si **_O_WTEXT** est utilisé pour ouvrir un fichier en lecture, **_open** lit le début du fichier et recherche une marque d’ordre d’octet (BOM). S'il en existe une, le fichier est considéré comme étant au format UTF-8 ou UTF-16LE, selon la marque d'ordre d'octet. Dans le cas contraire, le fichier est considéré comme étant au format ANSI. Quand un fichier est ouvert en écriture à l’aide de **_O_WTEXT**, UTF-16 est utilisé. Quel que soit de n’importe quel paramètre précédent ou octet marque d’ordre, si **_O_U8TEXT** est utilisé, le fichier est toujours ouvert en UTF-8 ; si **_O_U16TEXT** est utilisé, le fichier est toujours ouvert en UTF-16.

Quand un fichier est ouvert en mode Unicode à l’aide de **_O_WTEXT**, **_O_U8TEXT**, ou **_O_U16TEXT**, d’entrée fonctions traduisent les données lues à partir du fichier en données UTF-16 stockées en tant que type **wchar_t**. Fonctions qui écrivent dans un fichier ouvert en mode Unicode attendent des mémoires tampons qui contiennent des données UTF-16 stockées comme type **wchar_t**. Si le fichier est encodé au format UTF-8, les données UTF-16 sont traduites en UTF-8 lors de leur écriture et le contenu du fichier encodé au format UTF-8 est traduit en UTF-16 lorsqu'il est lu. Toute tentative de lecture ou d'écriture d'une quantité impaire d'octets en mode Unicode provoque une erreur de validation de paramètre. Pour lire ou écrire des données stockées dans votre programme au format UTF-8, utilisez un mode de fichier binaire ou texte au lieu d'un mode Unicode. Vous êtes responsable de toute traduction d'encodage nécessaire.

Si **_open** est appelée avec **_O_WRONLY** | **_O_APPEND** (mode append) et **_O_WTEXT**, **_O_ U16TEXT**, ou **_O_U8TEXT**, il tente d’abord d’ouvrir le fichier pour lecture et écriture, lire la marque BOM, puis rouvrez-la pour un accès en écriture uniquement. Si l'ouverture du fichier pour l'accès en lecture et en écriture échoue, elle ouvre le fichier pour l'accès en écriture uniquement et utilise la valeur par défaut pour le paramètre de mode Unicode.

Quand deux ou plusieurs constantes manifestes sont utilisées pour former le *oflag* argument, les constantes sont combinées avec l’opérateur OR au niveau du bit ( **&#124;** ). Pour en savoir plus sur les modes binaire et texte, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Le *pmode* argument est requis uniquement lorsque **_O_CREAT** est spécifié. Si le fichier existe déjà, *pmode* est ignoré. Sinon, *pmode* spécifie les paramètres d’autorisation de fichier, qui sont définis quand le nouveau fichier est fermé pour la première fois. **_Ouvrir** applique le masque d’autorisation de fichier actuelle à *pmode* avant que les autorisations sont définies. (Pour plus d’informations, consultez [_umask](umask.md).) *pmode* est une expression d’entier qui contient moins le des constantes manifestes suivantes, qui sont définies dans \<sys\stat.h >.

|*pmode*|Signification|
|-|-|
**_S_IREAD**|Lecture autorisée uniquement.
**_S_IWRITE**|Écriture autorisée. (En fait, autorise la lecture et l'écriture.)
**_S_IREAD** &AMP;#124; **_S_IWRITE**|Lecture et écriture autorisées.

Quand les deux constantes sont données, elles sont jointes avec l’opérateur OR au niveau du bit ( **&#124;** ). Dans Windows, tous les fichiers sont lisibles ; l'autorisation d'écriture seule n'est pas disponible. Par conséquent, les modes **_S_IWRITE** et **_S_IREAD** | **_S_IWRITE** sont équivalentes.

Si une valeur différente d’une combinaison de **_S_IREAD** et **_S_IWRITE** est spécifiée pour *pmode*, même si elle spécifierait valide *pmode*dans un autre système d’exploitation, ou si une valeur quelconque autorisées *oflag* valeurs est spécifié, la fonction génère une assertion en mode débogage et appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne -1 et affecte **errno** à **EINVAL**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen**|\<io.h> ou \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_Ouvrir** et **_wopen** sont des extensions Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_open.c
// compile with: /W3
/* This program uses _open to open a file
* named CRT_OPEN.C for input and a file named CRT_OPEN.OUT
* for output. The files are then closed.
*/
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int fh1, fh2;

   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996
   // Note: _open is deprecated; consider using _sopen_s instead
   if( fh1 == -1 )
      perror( "Open failed on input file" );
   else
   {
      printf( "Open succeeded on input file\n" );
      _close( fh1 );
   }

   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |
                            _S_IWRITE ); // C4996
   if( fh2 == -1 )
      perror( "Open failed on output file" );
   else
   {
      printf( "Open succeeded on output file\n" );
      _close( fh2 );
   }
}
```

### <a name="output"></a>Sortie

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>Voir aussi

[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
