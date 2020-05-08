---
title: _searchenv_s, _wsearchenv_s
ms.date: 4/2/2020
api_name:
- _wsearchenv_s
- _searchenv_s
- _o__searchenv_s
- _o__wsearchenv_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
ms.openlocfilehash: 5dd21013c8910ba07e2d23606af49bc80458dbc6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918996"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s, _wsearchenv_s

Recherche un fichier en utilisant des chemins d’environnement. Ces versions de [getenv, _wgetenv](searchenv-wsearchenv.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char *pathname,
   size_t numberOfElements
);
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname,
   size_t numberOfElements
);
template <size_t size>
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*extension*<br/>
Nom du fichier à rechercher.

*argument*<br/>
Environnement dans lequel effectuer la recherche.

*chemin*<br/>
Mémoire tampon destinée à stocker le chemin d’accès complet.

*numberOfElements*<br/>
Taille de la mémoire tampon du *chemin d’accès* .

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

Si *filename* est une chaîne vide, la valeur de retour est **ENOENT**.

### <a name="error-conditions"></a>Conditions d'erreur

|*extension*|*argument*|*chemin*|*numberOfElements*|Valeur retournée|Contenu du *chemin d’accès*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|n'importe laquelle|n'importe laquelle|**NUL**|n'importe laquelle|**EINVAL**|n/a|
|**NUL**|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL**|inchangé|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|<= 0|**EINVAL**|inchangé|

Si l’une de ces conditions d’erreur se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent **EINVAL**.

## <a name="remarks"></a>Notes 

La routine **_searchenv_s** recherche le fichier cible dans le domaine spécifié. La variable *varname* peut être n’importe quel environnement ou variable définie par l’utilisateur qui spécifie une liste de chemins d’accès aux répertoires, tels que **path**, **lib**et **include**. Étant donné que **_searchenv_s** est sensible à la casse, *varname* doit correspondre à la casse de la variable d’environnement. Si *varname* ne correspond pas au nom d’une variable d’environnement définie dans l’environnement du processus, la fonction retourne zéro et la variable de *chemin d’accès* est inchangée.

La routine recherche d’abord le fichier dans le répertoire de travail actif. Si elle ne le trouve pas, elle parcourt ensuite les répertoires spécifiés par la variable d’environnement. Si le fichier cible se trouve dans l’un de ces répertoires, le chemin d’accès qui vient d’être créé est copié dans le *nom de chemin*d’accès. Si le fichier de *nom* de fichier est introuvable, *pathname* contient une chaîne vide se terminant par null.

La mémoire tampon du *chemin d’accès* doit être d’au moins **_MAX_PATH** caractères pour tenir compte de la longueur totale du nom de chemin d’accès construit. Sinon, **_searchenv_s** risque de saturer la mémoire tampon de *chemin d’accès* , ce qui se traduit par un comportement inattendu.

**_wsearchenv_s** est une version à caractères larges de **_searchenv_s**; les arguments de **_wsearchenv_s** sont des chaînes à caractères larges. dans le cas contraire, **_wsearchenv_s** et **_searchenv_s** se comportent de la même façon.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_searchenv_s.c
/* This program searches for a file in
* a directory specified by an environment variable.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";
   errno_t err;

   /* Search for file in PATH environment variable: */
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );
   if (err != 0)
   {
      printf("Error searching the path. Error code: %d\n", err);
   }
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
