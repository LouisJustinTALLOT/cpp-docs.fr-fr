---
title: _putenv_s, _wputenv_s
ms.date: 11/04/2016
apiname:
- _wputenv_s
- _putenv_s
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
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: f675c2c0a2b12db3cce841dd0db9fa722393f1b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357861"
---
# <a name="putenvs-wputenvs"></a>_putenv_s, _wputenv_s

Crée, modifie ou supprime des variables d'environnement. Il s’agit de versions de [_putenv, _wputenv](putenv-wputenv.md), mais qui intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>Paramètres

*varname*<br/>
Nom de la variable d'environnement.

*value_string*<br/>
Valeur à attribuer à la variable d'environnement.

## <a name="return-value"></a>Valeur de retour

Retourne 0 en cas de réussite et un code d'erreur dans le cas contraire.

### <a name="error-conditions"></a>Conditions d’erreur

|*varname*|*value_string*|Valeur de retour|
|------------|-------------|------------------|
|**NULL**|any|**EINVAL**|
|any|**NULL**|**EINVAL**|

Si l’une des conditions d’erreur se produit, ces fonctions appellent un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EINVAL** et définissez **errno** à **EINVAL**.

## <a name="remarks"></a>Notes

Le **_putenv_s** fonction ajoute de nouvelles variables d’environnement ou modifie les valeurs des variables d’environnement existantes. Les variables d'environnement définissent l'environnement d'exécution d'un processus (par exemple, le chemin de recherche par défaut pour les bibliothèques à lier à un programme). **_wputenv_s** est une version à caractères larges de **_putenv_s**; le *envstring* l’argument de **_wputenv_s** est une chaîne de caractères larges.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname* est le nom de la variable d’environnement à être ajouté ou modifié et *chaîne_de_valeur* est la valeur de la variable. Si *varname* fait déjà partie de l’environnement, sa valeur est remplacée par *chaîne_de_valeur*; sinon, la nouvelle *varname* variable et son *chaîne_de_valeur*  sont ajoutés à l’environnement. Vous pouvez supprimer une variable à partir de l’environnement en spécifiant une chaîne vide (autrement dit, « ») pour *chaîne_de_valeur*.

**_putenv_s** et **_wputenv_s** affectent uniquement l’environnement local pour le processus en cours ; vous ne pouvez pas les utiliser pour modifier l’environnement au niveau de la commande. Ces fonctions agissent uniquement sur les structures de données accessibles à la bibliothèque Runtime et non sur l'environnement « segment » que le système d'exploitation crée pour un processus. Quand le processus actif se termine, l'environnement repasse au niveau du processus appelant qui, dans la plupart des cas, est le niveau du système d'exploitation. Toutefois, l’environnement modifié peut être passé aux nouveaux processus créés par **_spawn**, **_exec**, ou **système**, et ces nouveaux processus obtiennent les nouveaux éléments sont ajouté par **_putenv_s** et **_wputenv_s**.

Ne modifiez pas une entrée d’environnement directement ; au lieu de cela, utilisez **_putenv_s** ou **_wputenv_s** pour le modifier. En particulier, libérer directement des éléments de la **[] _environ** tableau global peut entraîner une mémoire non valide à traiter.

**getenv** et **_putenv_s** utiliser la variable globale **_environ** pour accéder à la table d’environnement ; **_wgetenv** et **_wputenv_s** utiliser **_wenviron**. **_putenv_s** et **_wputenv_s** peut changer la valeur de **_environ** et **_wenviron**et ainsi invalider le *envp*argument **principal** et le **_wenvp** l’argument de **wmain**. Par conséquent, il est préférable d’utiliser **_environ** ou **_wenviron** pour accéder aux informations de l’environnement. Pour plus d’informations sur la relation de **_putenv_s** et **_wputenv_s** vis-à-vis des variables globales, consultez [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Le **_putenv_s** et **_getenv_s** familles de fonctions ne sont pas thread-safe. **_getenv_s** peut retourner un pointeur de chaîne lors de la **_putenv_s** est, modifie la chaîne et entraînent des échecs aléatoires. Assurez-vous que les appels à ces fonctions sont synchronisés.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple qui montre comment utiliser **_putenv_s**, consultez [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
