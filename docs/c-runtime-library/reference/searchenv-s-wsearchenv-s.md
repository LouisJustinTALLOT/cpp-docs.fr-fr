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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3d526c546e1496b3b13b14a12c9025cbd0347cd2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332403"
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

*Fichier*<br/>
Nom du fichier à rechercher.

*varname varname*<br/>
Environnement dans lequel effectuer la recherche.

*Chemin*<br/>
Mémoire tampon destinée à stocker le chemin d’accès complet.

*nombreOfElements*<br/>
Taille du tampon *du nom de chemin.*

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

Si *le nom de fichier* est une chaîne vide, la valeur de retour est **ENOENT**.

### <a name="error-conditions"></a>Conditions d'erreur

|*Fichier*|*varname varname*|*Chemin*|*nombreOfElements*|Valeur retournée|Contenu du nom de *chemin*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|n'importe laquelle|n'importe laquelle|**Null**|n'importe laquelle|**EINVAL (EN)**|n/a|
|**Null**|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|inchangé|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|<= 0|**EINVAL (EN)**|inchangé|

Si l’une de ces conditions d’erreur se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retourner **EINVAL**.

## <a name="remarks"></a>Notes

Le **_searchenv_s** les recherches de routine pour le fichier cible dans le domaine spécifié. La variable *varname* peut être n’importe quel environnement ou variable définie par l’utilisateur qui spécifie une liste de chemins d’annuaire, tels que **PATH**, **LIB**, et **INCLUDE**. Étant **donné que _searchenv_s** est sensible aux cas, le *varname* doit correspondre au cas de la variable de l’environnement. Si *le varname* ne correspond pas au nom d’une variable d’environnement définie dans l’environnement du processus, la fonction renvoie zéro et la variable de nom de chemin est *inchangée.*

La routine recherche d’abord le fichier dans le répertoire de travail actif. Si elle ne le trouve pas, elle parcourt ensuite les répertoires spécifiés par la variable d’environnement. Si le fichier cible est dans l’un de ces répertoires, le chemin nouvellement créé est copié en *nom de chemin*. Si le fichier *du nom de fichier* n’est pas trouvé, le nom de *voie* contient une corde vide non terminée.

Le tampon *de nom de chemin* doit être au moins **_MAX_PATH** caractères longs pour accueillir la longueur complète du nom du chemin construit. Sinon, **_searchenv_s** pourrait envahir le tampon *de nom de chemin* résultant en un comportement inattendu.

**_wsearchenv_s** est une version à caractère large de **_searchenv_s**; les arguments pour **_wsearchenv_s** sont des chaînes de caractère large. **_wsearchenv_s** et **_searchenv_s** se comportent de façon identique autrement.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
