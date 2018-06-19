---
title: _mktemp, _wmktemp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wmktemp
- _mktemp
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
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
dev_langs:
- C++
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 087348b3cc59fb1b47699fc0e64f533c22d992b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404345"
---
# <a name="mktemp-wmktemp"></a>_mktemp, _wmktemp

Crée un nom de fichier unique. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [_mktemp_s, _wmktemp_s](mktemp-s-wmktemp-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*nameTemplate*<br/>
Modèle de nom de fichier.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le nameTemplate modifié. La fonction retourne **NULL** si *nameTemplate* est incorrect ou n’y a plus de noms uniques peuvent être créées à partir de la nameTemplate donné.

## <a name="remarks"></a>Notes

Le **_mktemp** fonction crée un nom de fichier unique en modifiant le *nameTemplate* argument. **_mktemp** gère automatiquement les arguments de chaîne de caractères multioctets selon le cas, reconnaissant les séquences de caractères multioctets selon la page de codes multioctets en cours d’utilisation par le système d’exécution. **_wmktemp** est une version à caractères larges de **_mktemp**; la valeur des arguments et de retour de **_wmktemp** sont des chaînes à caractères larges. **_wmktemp** et **_mktemp** comportent de façon identique, à ceci près que **_wmktemp** ne gère pas les chaînes de caractères multioctets.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

Le *nameTemplate* argument présente sous la forme *base ** XXXXXX*, où *base* est la partie du nouveau nom de fichier que vous fournissez et chaque X est un espace réservé pour un caractère fourni par **_mktemp**. Chaque caractère d’espace réservé dans *nameTemplate* doit être un x majuscule **_mktemp** conserve *base* et remplace le premier X de fin par un caractère alphabétique. **_mktemp** remplace la fin suivant x avec une valeur à cinq chiffres ; cette valeur est un numéro unique identifiant le processus appelant, ou dans les programmes multithread, le thread appelant.

Chaque appel réussi à **_mktemp** modifie *nameTemplate*. Dans chaque appel suivant le même processus ou thread avec le même *nameTemplate* argument, **_mktemp** vérifications pour les noms de fichiers qui correspondent aux noms retournés par **_mktemp** dans appels précédents. Si aucun fichier n’existe pour un nom donné, **_mktemp** retourne ce nom. Si les fichiers existent pour tous les noms précédemment retournaient, **_mktemp** crée un nouveau nom en remplaçant le caractère alphabétique utilisé dans le nom précédemment retourné par la lettre minuscule suivante disponible, dans l’ordre, à partir de « a » à « z ». Par exemple, si *base* est :

> **fn**

et la valeur à cinq chiffres fournie par **_mktemp** est 12345, le premier nom retourné est :

> **fichier fna12345**

Si ce nom est utilisé pour créer le fichier FNA12345 et si ce fichier existe toujours, le nom suivant retourné sur un appel du même processus ou thread avec le même *base* pour *nameTemplate* est :

> **fnb12345**

Si le fichier FNA12345 n'existe pas, le nom suivant retourné est de nouveau :

> **fichier fna12345**

**_mktemp** peut créer un maximum de 26 noms de fichiers uniques pour chaque combinaison de *base* et *nameTemplate* valeurs. Par conséquent, FNZ12345 est le nom de fichier unique **_mktemp** peut créer pour le *base* et *nameTemplate* valeurs utilisées dans cet exemple.

En cas d’échec, **errno** est définie. Si *nameTemplate* a un format non valide (par exemple, moins de 6 x), **errno** a la valeur **EINVAL**. Si **_mktemp** ne peut pas créer un nom unique, car tous les 26 noms de fichiers possibles existent déjà, **_mktemp** nameTemplate affecte une chaîne vide et retourne **EEXIST**.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
