---
title: _putenv, _wputenv
ms.date: 4/2/2020
api_name:
- _putenv
- _wputenv
- _o__putenv
- _o__wputenv
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
ms.openlocfilehash: 3e74959e6c6cdb2e27ce0d68ba40d02d64949904
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333043"
---
# <a name="_putenv-_wputenv"></a>_putenv, _wputenv

Crée, modifie ou supprime des variables d'environnement. Il existe des versions plus sécurisées de ces fonctions. Consultez [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Retour 0 en cas de succès ou -1 en cas d’erreur.

## <a name="remarks"></a>Notes

La fonction **_putenv** ajoute de nouvelles variables d’environnement ou modifie les valeurs des variables de l’environnement existantes. Les variables d'environnement définissent l'environnement d'exécution d'un processus (par exemple, le chemin de recherche par défaut pour les bibliothèques à lier à un programme). **_wputenv** est une version à caractère large de **_putenv**; *l’argument envstring* à **_wputenv** est une chaîne de caractère large.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*L’argument envstring* doit être un pointeur à une chaîne de la forme *varname*=*value_string*, où *le varname* est le nom de la variable de l’environnement à ajouter ou à modifier et *value_string* est la valeur de la variable. Si *le varname* fait déjà partie de l’environnement, sa valeur est remplacée par *value_string*; sinon, la nouvelle variable *varname* et sa *valeur value_string* sont ajoutées à l’environnement. Vous pouvez supprimer une variable de l’environnement en spécifiant un *value_string*vide, ou en d’autres termes, en spécifiant uniquement *le varname.*

**_putenv** et **_wputenv** n’affectent que l’environnement local du processus actuel; vous ne pouvez pas les utiliser pour modifier l’environnement au niveau de commande. Autrement dit, ces fonctions agissent uniquement sur les structures de données accessibles à la bibliothèque Runtime et non sur le segment d’environnement que le système d’exploitation a créé pour un processus. Quand le processus actif se termine, l’environnement repasse au niveau du processus appelant (dans la plupart des cas, celui du système d’exploitation). Cependant, l’environnement modifié peut être transmis à tous les nouveaux processus créés par **_spawn**, **_exec**, ou **le système**, et ces nouveaux processus obtiennent tous les nouveaux éléments ajoutés par **_putenv** et **_wputenv**.

Ne modifiez pas directement une entrée d’environnement : utilisez **plutôt _putenv** ou **_wputenv** pour la modifier. En particulier, la libération directe d’éléments de **l'_environ[]** de l’ensemble mondial pourrait conduire à la mise en œuvre d’une mémoire invalide.

**getenv** et **_putenv** utilisent la **variable** mondiale _environ pour accéder à la table de l’environnement; **_wgetenv** et **_wputenv** utilisent **_wenviron**. **_putenv** et **_wputenv** pourraient changer la valeur de **_environ** et **de _wenviron,** invalidant ainsi **l’argument _envp** à **l’argument principal** et _wenvp à **wmain**. **_wenvp** Par conséquent, il est plus sûr d’utiliser **_environ** ou **_wenviron** pour accéder à l’information sur l’environnement. Pour plus d’informations sur la relation entre **_putenv** et **_wputenv** aux variables globales, voir [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Les **_putenv** et **_getenv** familles de fonctions ne sont pas sans fil. **_getenv** pourrait retourner un pointeur de chaîne pendant **que _putenv** modifie la chaîne, provoquant des défaillances aléatoires. Assurez-vous que les appels à ces fonctions sont synchronisés.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Pour un échantillon de la façon d’utiliser **_putenv**, voir [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
