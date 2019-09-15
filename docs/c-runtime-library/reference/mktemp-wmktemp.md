---
title: _mktemp, _wmktemp
ms.date: 11/04/2016
api_name:
- _wmktemp
- _mktemp
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
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
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
ms.openlocfilehash: 7cfca04d4f0df2673a2221f00a1263f73e8516ec
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951579"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp, _wmktemp

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

Chacune de ces fonctions retourne un pointeur vers le nameTemplate modifié. La fonction retourne la **valeur null** si *nameTemplate* est incorrect ou qu’il n’est pas possible de créer d’autres noms uniques à partir du nameTemplate donné.

## <a name="remarks"></a>Notes

La fonction **_mktemp** crée un nom de fichier unique en modifiant l’argument *nameTemplate* . **_mktemp** gère automatiquement les arguments de chaîne de caractères multioctets si nécessaire, en identifiant les séquences de caractères multioctets en fonction de la page de codes multioctets en cours d’utilisation par le système d’exécution. **_wmktemp** est une version à caractères larges de **_mktemp**; l’argument et la valeur de retour de **_wmktemp** sont des chaînes à caractères larges. les **_wmktemp** et **_mktemp** se comportent de la même manière, sauf que **_wmktemp** ne gère pas les chaînes de caractères multioctets.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

L’argument *nameTemplate* se présente sous la forme de *base*xxxxxx, où *base* est la partie du nouveau nom de fichier que vous fournissez et chaque X est un espace réservé pour un caractère fourni par **_mktemp**. Chaque caractère d’espace réservé dans *nameTemplate* doit être un x majuscule. **_mktemp** conserve la *base* et remplace le premier X de fin par un caractère alphabétique. **_mktemp** remplace le X de fin suivant par une valeur à cinq chiffres ; Cette valeur est un nombre unique qui identifie le processus appelant, ou dans les programmes multithread, le thread appelant.

Chaque appel réussi à **_mktemp** modifie *nameTemplate*. Dans chaque appel suivant du même processus ou thread avec le même argument *nameTemplate* , **_mktemp** recherche les noms de fichiers qui correspondent aux noms retournés par **_mktemp** dans les appels précédents. Si aucun fichier n’existe pour un nom donné, **_mktemp** retourne ce nom. Si des fichiers existent pour tous les noms précédemment retournés, **_mktemp** crée un nouveau nom en remplaçant le caractère alphabétique qu’il a utilisé dans le nom précédemment retourné par la lettre minuscule suivante disponible, dans l’ordre, de « a » à « z ». Par exemple, si *base* est :

> **fn**

et la valeur à cinq chiffres fournie par **_mktemp** est 12345, le premier nom retourné est :

> **fna12345**

Si ce nom est utilisé pour créer le fichier FNA12345 et que ce fichier existe toujours, le nom suivant retourné sur un appel du même processus ou thread avec la même *base* pour *nameTemplate* est :

> **fnb12345**

Si le fichier FNA12345 n'existe pas, le nom suivant retourné est de nouveau :

> **fna12345**

**_mktemp** peut créer un maximum de 26 noms de fichiers uniques pour une combinaison donnée de valeurs de *base* et *nameTemplate* . Par conséquent, FNZ12345 est le dernier nom de fichier unique que **_mktemp** peut créer pour les valeurs de *base* et *nameTemplate* utilisées dans cet exemple.

En cas d’échec, **errno** est défini. Si *nameTemplate* a un format non valide (par exemple, moins de 6 X), **errno** a la valeur **EINVAL**. Si **_mktemp** ne parvient pas à créer un nom unique car les 26 noms de fichiers possibles existent déjà, **_mktemp** définit nameTemplate sur une chaîne vide et retourne **EEXIST**.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

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
