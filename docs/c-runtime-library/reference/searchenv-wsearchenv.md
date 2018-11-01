---
title: _searchenv, _wsearchenv
ms.date: 11/04/2016
apiname:
- _searchenv
- _wsearchenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: c1d2361fceec448c98fd9e5a368653aac38c83e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628252"
---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv

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

*nom de variable*<br/>
Environnement dans lequel effectuer la recherche.

*chemin d’accès*<br/>
Mémoire tampon destinée à stocker le chemin d’accès complet.

## <a name="remarks"></a>Notes

Le **_searchenv** routine recherche le fichier cible dans le domaine spécifié. Le *varname* variable peut être n’importe quel environnement ou une variable définie par l’utilisateur, par exemple, **chemin d’accès**, **LIB**, ou **INCLUDE**, qui spécifie un liste de chemins d’accès de répertoire. Étant donné que **_searchenv** respecte la casse, *varname* doit correspondre à la casse de la variable d’environnement.

La routine recherche d'abord le fichier dans le répertoire de travail actuel. Si elle ne le trouve pas, elle parcourt les répertoires spécifiés par la variable d'environnement. Si le fichier cible est dans un de ces répertoires, le chemin d’accès qui vient d’être créé est copié dans *pathname*. Si le *filename* fichier est introuvable, *pathname* contient une chaîne vide se terminant par null.

Le *pathname* mémoire tampon doit être au moins **_MAX_PATH** caractères pour prendre en compte la longueur totale du nom de chemin d’accès construit. Sinon, **_searchenv** risque de saturer le *pathname* mettre en mémoire tampon et entraîner un comportement inattendu.

**_wsearchenv** est une version à caractères larges de **_searchenv**et les arguments de **_wsearchenv** sont des chaînes à caractères larges. **_wsearchenv** et **_searchenv** se comportent de façon identique dans le cas contraire.

Si *filename* est une chaîne vide, ces fonctions retournent **ENOENT**.

Si *filename* ou *pathname* est un **NULL** pointeur, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent -1 et la valeur **errno** à **EINVAL**.

Pour plus d’informations sur **errno** et les codes d’erreur, consultez [constantes errno](../../c-runtime-library/errno-constants.md).

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
