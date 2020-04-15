---
title: _mktemp, _wmktemp
ms.date: 4/2/2020
api_name:
- _wmktemp
- _mktemp
- _o__mktemp
- _o__wmktemp
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
ms.openlocfilehash: 8affd20ca7826f0d383f749567c9625d61dacd48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338717"
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

Chacune de ces fonctions renvoie un pointeur au nom modifiéTemplate. La fonction **renvoie NULL** si *le nomTemplate* est mal formé ou pas de noms plus uniques peuvent être créés à partir du nom donnéTemplate.

## <a name="remarks"></a>Notes

La fonction **_mktemp** crée un nom de fichier unique en modifiant l’argument *du nomTemplate.* **_mktemp** gère automatiquement les arguments de chaîne multioctets, le cas échéant, en reconnaissant les séquences multioctets-caractères selon la page de code multioctet actuellement utilisée par le système de temps d’exécution. **_wmktemp** est une version à caractère large de **_mktemp**; l’argument et la valeur de retour de **_wmktemp** sont des chaînes de caractère large. **_wmktemp** et **_mktemp** se comportent de la même façon autrement, sauf que **_wmktemp** ne gère pas les cordes multioctets.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

*L’argument de nomTemplate* a la *base*de formulaire XXXXXX, où la *base* est la partie du nouveau nom de fichier que vous fournissez et chaque X est un espace réservé pour un personnage fourni par **_mktemp**. Chaque personnage de placeholder dans *le nomTemplate* doit être une majuscule X. **_mktemp** conserve la *base* et remplace le premier X de fuite par un caractère alphabétique. **_mktemp** remplace les X suivants avec une valeur à cinq chiffres; cette valeur est un nombre unique identifiant le processus d’appel, ou dans les programmes multithreaded, le fil d’appel.

Chaque appel réussi à **_mktemp** modifie *le nomTemplate*. Dans chaque appel ultérieur du même processus ou du même thread avec le même *argument de nomTemplate,* **_mktemp** vérifie les noms de fichiers qui correspondent aux noms retournés par **_mktemp** dans les appels précédents. S’il n’existe pas de fichier pour un nom donné, **_mktemp** renvoie ce nom. Si des fichiers existent pour tous les noms précédemment retournés, **_mktemp** crée un nouveau nom en remplaçant le caractère alphabétique qu’il a utilisé dans le nom précédemment retourné avec la prochaine lettre de lowercase disponible, dans l’ordre, de «a» à «z». Par exemple, si la *base* est :

> **Fn**

et la valeur à cinq chiffres fournie par **_mktemp** est de 12345, le prénom retourné est :

> **fna12345**

Si ce nom est utilisé pour créer le fichier FNA12345 et que ce fichier existe toujours, le nom suivant retourné sur un appel du même processus ou thread avec la même *base* pour *le nomTemplate* est:

> **fnb12345**

Si le fichier FNA12345 n'existe pas, le nom suivant retourné est de nouveau :

> **fna12345**

**_mktemp** peut créer un maximum de 26 noms de fichiers uniques pour toute combinaison donnée de valeurs *de base* et *de nameTemplate.* Par conséquent, FNZ12345 est le dernier nom de fichier unique **_mktemp** pouvez créer pour les valeurs *de base* et *de nameTemplate* utilisées dans cet exemple.

Sur l’échec, **errno** est fixé. Si *le nomTemplate* a un format invalide (par exemple, moins de 6 X), **errno** est réglé sur **EINVAL**. Si **_mktemp** n’est pas en mesure de créer un nom unique parce que les 26 noms de fichiers possibles existent déjà, **_mktemp** définit le nomTemplate à une chaîne vide et renvoie **EEXIST**.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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
