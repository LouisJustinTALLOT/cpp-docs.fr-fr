---
description: 'En savoir plus sur : _putenv_s, _wputenv_s'
title: _putenv_s, _wputenv_s
ms.date: 4/2/2020
api_name:
- _wputenv_s
- _putenv_s
- _o__putenv_s
- _o__wputenv_s
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
ms.openlocfilehash: bba9d595d716f3a8e5e9c41326a0258b10e8abf8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246290"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s, _wputenv_s

Crée, modifie ou supprime des variables d'environnement. Il s’agit de versions de [_putenv, _wputenv](putenv-wputenv.md), mais qui intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*argument*<br/>
Nom de la variable d'environnement.

*value_string*<br/>
Valeur à attribuer à la variable d'environnement.

## <a name="return-value"></a>Valeur renvoyée

Retourne 0 en cas de réussite et un code d'erreur dans le cas contraire.

### <a name="error-conditions"></a>Conditions d'erreur

|*argument*|*value_string*|Valeur retournée|
|------------|-------------|------------------|
|**NULL**|n'importe laquelle|**EINVAL**|
|n'importe laquelle|**NULL**|**EINVAL**|

Si l’une des conditions d’erreur se produit, ces fonctions appellent un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EINVAL** et attribuent à **errno** la valeur **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **_putenv_s** ajoute de nouvelles variables d’environnement ou modifie les valeurs des variables d’environnement existantes. Les variables d'environnement définissent l'environnement d'exécution d'un processus (par exemple, le chemin de recherche par défaut pour les bibliothèques à lier à un programme). **_wputenv_s** est une version à caractères larges de **_putenv_s**; l’argument *envstring* pour **_wputenv_s** est une chaîne de caractères larges.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname* est le nom de la variable d’environnement à ajouter ou à modifier, *value_string* la valeur de la variable. Si *varname* fait déjà partie de l’environnement, sa valeur est remplacée par *value_string*; dans le cas contraire, la nouvelle variable *varname* et ses *value_string* sont ajoutés à l’environnement. Vous pouvez supprimer une variable de l’environnement en spécifiant une chaîne vide (autrement dit, «») pour *value_string*.

**_putenv_s** et **_wputenv_s** affectent uniquement l’environnement local au processus en cours ; vous ne pouvez pas les utiliser pour modifier l’environnement au niveau de la commande. Ces fonctions agissent uniquement sur les structures de données accessibles à la bibliothèque Runtime et non sur l'environnement « segment » que le système d'exploitation crée pour un processus. Quand le processus actif se termine, l'environnement repasse au niveau du processus appelant qui, dans la plupart des cas, est le niveau du système d'exploitation. Toutefois, l’environnement modifié peut être passé aux nouveaux processus créés par **_spawn**, **_exec** ou **System**, et ces nouveaux processus obtiennent les nouveaux éléments ajoutés par **_putenv_s** et **_wputenv_s**.

Ne modifiez pas directement une entrée d’environnement ; au lieu de cela, utilisez **_putenv_s** ou **_wputenv_s** pour le modifier. En particulier, la libération directe des éléments du tableau global **_environ []** peut entraîner la prise en considération d’une mémoire non valide.

**getenv** et **_putenv_s** utilisent la variable globale **_environ** pour accéder à la table d’environnement. **_wgetenv** et **_wputenv_s** utilisent **_wenviron**. **_putenv_s** et **_wputenv_s** peuvent modifier la valeur de **_environ** et **_wenviron**, et ainsi invalider l’argument *envp* en **main** et l’argument **_wenvp** en **wmain**. Par conséquent, il est plus sûr d’utiliser **_environ** ou **_wenviron** pour accéder aux informations de l’environnement. Pour plus d’informations sur la relation entre les **_putenv_s** et les **_wputenv_s** et les variables globales, consultez [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Les familles de fonctions **_putenv_s** et **_getenv_s** ne sont pas thread-safe. **_getenv_s** peut retourner un pointeur de chaîne pendant que **_putenv_s** modifie la chaîne, ce qui provoque des échecs aléatoires. Assurez-vous que les appels à ces fonctions sont synchronisés.

## <a name="requirements"></a>Spécifications

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
