---
title: _putenv, _wputenv
ms.date: 11/04/2016
api_name:
- _putenv
- _wputenv
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
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
ms.openlocfilehash: 8fe699a476ea1dd09a6ce9922294bce398df16b2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949891"
---
# <a name="_putenv-_wputenv"></a>_putenv, _wputenv

Crée, modifie ou supprime des variables d'environnement. Il existe des versions plus sécurisées de ces fonctions. Consultez [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>Paramètres

*envstring*<br/>
Définition de chaîne d’environnement.

## <a name="return-value"></a>Valeur de retour

Retourne 0 en cas de réussite ou-1 en cas d’erreur.

## <a name="remarks"></a>Notes

La fonction **_putenv** ajoute de nouvelles variables d’environnement ou modifie les valeurs des variables d’environnement existantes. Les variables d'environnement définissent l'environnement d'exécution d'un processus (par exemple, le chemin de recherche par défaut pour les bibliothèques à lier à un programme). **_wputenv** est une version à caractères larges de **_putenv**; l’argument *envstring* de **_wputenv** est une chaîne de caractères larges.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

L’argument *envstring* doit être un pointeur vers une chaîne au format *varname*=*value_string*, où *varname* est le nom de la variable d’environnement à ajouter ou modifier et *value_string* est la variable ajoutée. Si *varname* fait déjà partie de l’environnement, sa valeur est remplacée par *value_string*; dans le cas contraire, la nouvelle variable *varname* et sa valeur *value_string* sont ajoutées à l’environnement. Vous pouvez supprimer une variable de l’environnement en spécifiant un *value_string*vide, ou en d’autres termes, en spécifiant uniquement *varname*=.

**_putenv** et **_wputenv** affectent uniquement l’environnement local au processus actuel. vous ne pouvez pas les utiliser pour modifier l’environnement au niveau de la commande. Autrement dit, ces fonctions agissent uniquement sur les structures de données accessibles à la bibliothèque Runtime et non sur le segment d’environnement que le système d’exploitation a créé pour un processus. Quand le processus actif se termine, l’environnement repasse au niveau du processus appelant (dans la plupart des cas, celui du système d’exploitation). Toutefois, l’environnement modifié peut être passé à tous les nouveaux processus créés par **_spawn**, **_exec**ou **System**, et ces nouveaux processus obtiennent les nouveaux éléments ajoutés par **_putenv** et **_wputenv**.

Ne modifiez pas directement une entrée d’environnement : utilisez à la place **_putenv** ou **_wputenv** pour la modifier. En particulier, la libération directe des éléments du tableau global **_environ []** peut entraîner une mémoire non valide.

**getenv** et **_putenv** utilisent la variable globale **_environ** pour accéder à la table d’environnement. **_wgetenv** et **_wputenv** utilisent **_wenviron**. **_putenv** et **_wputenv** peuvent modifier la valeur de **_environ** et **_wenviron**, invalidant ainsi l’argument **_envp** en **main** et l’argument **_wenvp** en **wmain**. Par conséquent, il est plus sûr d’utiliser **_environ** ou **_wenviron** pour accéder aux informations de l’environnement. Pour plus d’informations sur la relation entre **_putenv** et **_wputenv** et les variables globales, consultez [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Les familles de fonctions **_putenv** et **_getenv** ne sont pas thread-safe. **_getenv** peut retourner un pointeur de chaîne pendant que **_putenv** modifie la chaîne, ce qui provoque des échecs aléatoires. Assurez-vous que les appels à ces fonctions sont synchronisés.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **_putenv**, consultez [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
