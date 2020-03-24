---
title: _open, _wopen
ms.date: 11/04/2016
api_name:
- _open
- _wopen
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 4ce6e9aebe5d058143ad737f9c9db5bb68b30b1f
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150722"
---
# <a name="_open-_wopen"></a>_open, _wopen

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

Chacune de ces fonctions retourne un descripteur de fichier pour le fichier ouvert. Une valeur de retour de-1 indique une erreur ; dans ce cas, **errno** est défini sur l’une des valeurs suivantes.

|Valeur de la variable errno|Condition|
|-|-|
| **EACCES** | A essayé d'ouvrir un fichier en lecture seule pour un accès en écriture, le mode de partage du fichier n'autorise pas les opérations spécifiées ou le chemin d'accès donné est un répertoire. |
| **EEXIST** | **_O_CREAT** et **_O_EXCL** indicateurs spécifiés, mais le *nom de fichier* existe déjà. |
| **EINVAL** | Argument *Oflag* ou *PMODE* non valide. |
| **EMFILE** | Plus aucun descripteur de fichier n'est disponible (trop de fichiers sont ouverts). |
| **ENOENT** | Fichier ou chemin d’accès introuvable. |

Pour plus d’informations sur ces codes de retour et d’autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_open** ouvre le fichier spécifié par *filename* et la prépare pour la lecture ou l’écriture, comme spécifié par *Oflag*. **_wopen** est une version à caractères larges de **_open**; l’argument de *nom de fichier* pour **_wopen** est une chaîne de caractères larges. dans le cas contraire, **_wopen** et **_open** se comportent de la même façon.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*Oflag* est une expression d’entier formée à partir d’une ou plusieurs des constantes manifestes ou combinaisons de constantes suivantes, qui sont définies dans \<fcntl. h >.

|*Oflag* constante)|Comportement|
|-|-|
| **_O_APPEND** | Déplace le pointeur de fichier à la fin du fichier avant chaque opération d'écriture. |
| **_O_BINARY** | Ouvre le fichier en mode binaire (non traduit). (Pour obtenir une description du mode binaire, consultez [fopen](fopen-wfopen.md).) |
| **_O_CREAT** | Crée un fichier et l'ouvre pour l'accès en écriture. N’a aucun effet si le fichier spécifié par *filename* existe. L’argument *PMODE* est obligatoire lorsque **_O_CREAT** est spécifié. |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Crée un fichier temporaire et, dans la mesure du possible, n'effectue pas de vidage sur disque. L’argument *PMODE* est obligatoire lorsque **_O_CREAT** est spécifié. |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Crée un fichier temporaire ; le fichier est supprimé quand le dernier descripteur de fichier est fermé. L’argument *PMODE* est obligatoire lorsque **_O_CREAT** est spécifié. |
| **_O_CREAT** &#124; `_O_EXCL` | Retourne une valeur d’erreur s’il existe un fichier spécifié par *filename* . S’applique uniquement lorsqu’il est utilisé avec **_O_CREAT**. |
| **_O_NOINHERIT** | Empêche la création d'un descripteur de fichier partagé. |
| **_O_RANDOM** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque. |
| **_O_RDONLY** | Ouvre un fichier pour l'accès en lecture uniquement. Ne peut pas être spécifié avec **_O_RDWR** ou **_O_WRONLY**. |
| **_O_RDWR** | Ouvre un fichier pour l'accès en lecture et en écriture. Ne peut pas être spécifié avec **_O_RDONLY** ou **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque. |
| **_O_TEXT** | Ouvre un fichier en mode texte (traduit). (Pour plus d’informations, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Ouvre un fichier et le tronque à une longueur nulle. Le fichier doit disposer d'une autorisation en écriture. Ne peut pas être spécifié avec **_O_RDONLY**. **_O_TRUNC** utilisé avec **_O_CREAT** ouvre un fichier existant ou crée un fichier. **Remarque :** L’indicateur **_O_TRUNC** détruit le contenu du fichier spécifié. |
| **_O_WRONLY** | Ouvre un fichier pour l'accès en écriture uniquement. Ne peut pas être spécifié avec **_O_RDONLY** ou **_O_RDWR**. |
| **_O_U16TEXT** | Ouvre un fichier en mode Unicode UTF-16. |
| **_O_U8TEXT** | Ouvre un fichier en mode Unicode UTF-8. |
| **_O_WTEXT** | Ouvre un fichier en mode Unicode. |

Pour spécifier le mode d’accès au fichier, vous devez spécifier **_O_RDONLY**, **_O_RDWR**ou **_O_WRONLY**. Il n'y a aucune valeur par défaut pour le mode d'accès.

Si **_O_WTEXT** est utilisé pour ouvrir un fichier en lecture, **_open** lit le début du fichier et recherche une marque d’ordre d’octet (BOM). S'il en existe une, le fichier est considéré comme étant au format UTF-8 ou UTF-16LE, selon la marque d'ordre d'octet. Dans le cas contraire, le fichier est considéré comme étant au format ANSI. Lorsqu’un fichier est ouvert en écriture à l’aide de **_O_WTEXT**, UTF-16 est utilisé. Quel que soit le paramètre précédent ou la marque d’ordre d’octet, si **_O_U8TEXT** est utilisé, le fichier est toujours ouvert en UTF-8 ; Si **_O_U16TEXT** est utilisé, le fichier est toujours ouvert en UTF-16.

Lorsqu’un fichier est ouvert en mode Unicode à l’aide de **_O_WTEXT**, **_O_U8TEXT**ou **_O_U16TEXT**, les fonctions d’entrée traduisent les données lues à partir du fichier en données UTF-16 stockées en tant que type **wchar_t**. Les fonctions qui écrivent dans un fichier ouvert en mode Unicode attendent des mémoires tampons qui contiennent des données UTF-16 stockées en tant que type **wchar_t**. Si le fichier est encodé au format UTF-8, les données UTF-16 sont traduites en UTF-8 lors de leur écriture et le contenu du fichier encodé au format UTF-8 est traduit en UTF-16 lorsqu'il est lu. Toute tentative de lecture ou d'écriture d'un nombre impair d'octets en mode Unicode provoque une erreur de validation de paramètre. Pour lire ou écrire des données stockées dans votre programme au format UTF-8, utilisez un mode de fichier binaire ou texte au lieu d'un mode Unicode. Vous êtes responsable de toute traduction d'encodage nécessaire.

Si **_open** est appelé avec **_O_WRONLY** |  **_O_APPEND** (mode Append) et **_O_WTEXT**, **_O_U16TEXT**ou **_O_U8TEXT**, il tente d’abord d’ouvrir le fichier pour la lecture et l’écriture, de lire la nomenclature, puis de la rouvrir en écriture. Si l'ouverture du fichier pour l'accès en lecture et en écriture échoue, elle ouvre le fichier pour l'accès en écriture uniquement et utilise la valeur par défaut pour le paramètre de mode Unicode.

Lorsqu’au moins deux constantes manifestes sont utilisées pour former l’argument *Oflag* , les constantes sont combinées avec l’opérateur or au **&#124;** niveau du bit (). Pour en savoir plus sur les modes binaire et texte, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

L’argument *PMODE* est requis uniquement lorsque **_O_CREAT** est spécifié. Si le fichier existe déjà, *PMODE* est ignoré. Sinon, *PMODE* spécifie les paramètres d’autorisation de fichier, qui sont définis quand le nouveau fichier est fermé la première fois. **_open** applique le masque d’autorisation de fichier actuel à *PMODE* avant que les autorisations ne soient définies. (Pour plus d’informations, consultez [_umask](umask.md).) *PMODE* est une expression entière qui contient l’une des constantes manifestes suivantes, ou les deux, qui sont définies dans \<> sys\stat.h.

|*pmode*|Signification|
|-|-|
| **_S_IREAD** | Lecture autorisée uniquement. |
| **_S_IWRITE** | Écriture autorisée. (En fait, autorise la lecture et l'écriture.) |
| **_S_IREAD** &#124; **_S_IWRITE** | Lecture et écriture autorisées. |

Quand les deux constantes sont données, elles sont jointes avec l’opérateur or au **&#124;** niveau du bit (). Dans Windows, tous les fichiers sont lisibles ; l'autorisation d'écriture seule n'est pas disponible. Par conséquent, les modes **_S_IWRITE** et **_S_IREAD** |  **_S_IWRITE** sont équivalents.

Si une valeur autre qu’une combinaison de **_S_IREAD** et **_S_IWRITE** est spécifiée pour *PMODE*, même si elle spécifie un *PMODE* valide dans un autre système d’exploitation, ou si une valeur autre que les valeurs *Oflag* autorisées est spécifiée, la fonction génère une assertion en mode débogage et appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne-1 et définit **errno** sur **EINVAL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen**|\<io.h> ou \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_open** et **_wopen** sont des extensions Microsoft. Pour plus d’informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

### <a name="output"></a>Output

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
