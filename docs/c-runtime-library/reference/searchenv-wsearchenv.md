---
title: _searchenv, _wsearchenv
ms.date: 11/04/2016
api_name:
- _searchenv
- _wsearchenv
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
ms.openlocfilehash: a3139ab87335ba581ef65707602c5da1819ce4a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948771"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv, _wsearchenv

Utilise des chemins d’accès d’environnement pour rechercher un fichier. Il existe des versions plus sécurisées de ces fonctions. Consultez [_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
void _searchenv(
   const char *filename,
   const char *varname,
   char *pathname
);
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname
);
template <size_t size>
void _searchenv(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier à rechercher.

*argument*<br/>
Environnement dans lequel effectuer la recherche.

*pathname*<br/>
Mémoire tampon destinée à stocker le chemin d’accès complet.

## <a name="remarks"></a>Notes

La routine **_searchenv** recherche le fichier cible dans le domaine spécifié. La variable *varname* peut être n’importe quel environnement ou variable définie par l’utilisateur, par exemple **path**, **lib**ou **include**, qui spécifie une liste de chemins d’accès aux répertoires. Comme **_searchenv** respecte la casse, *varname* doit correspondre à la casse de la variable d’environnement.

La routine recherche d'abord le fichier dans le répertoire de travail actuel. Si elle ne le trouve pas, elle parcourt les répertoires spécifiés par la variable d'environnement. Si le fichier cible se trouve dans l’un de ces répertoires, le chemin d’accès qui vient d’être créé est copié dans le *nom de chemin*d’accès. Si le fichier de *nom* de fichier est introuvable, *pathname* contient une chaîne vide se terminant par null.

La mémoire tampon du *chemin d’accès* doit comporter au moins _ **MAX_PATH** caractères pour contenir la longueur totale du nom de chemin d’accès construit. Sinon, **_searchenv** peut saturer la mémoire tampon de *chemin d’accès* et provoquer un comportement inattendu.

**_wsearchenv** est une version à caractères larges de **_searchenv**, et les arguments de **_wsearchenv** sont des chaînes à caractères larges. dans le cas contraire, **_wsearchenv** et **_searchenv** se comportent de la même façon.

Si *filename* est une chaîne vide, ces fonctions retournent **ENOENT**.

Si *filename* ou *pathname* est un pointeur **null** , le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

Pour plus d’informations **sur les codes d’erreur et d'** erreur, consultez [errno, constantes](../../c-runtime-library/errno-constants.md).

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et plus sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_searchenv.c
// compile with: /W3
// This program searches for a file in
// a directory that's specified by an environment variable.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";

   // Search for file in PATH environment variable:
   _searchenv( searchfile, envvar, pathbuffer ); // C4996
   // Note: _searchenv is deprecated; consider using _searchenv_s
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
