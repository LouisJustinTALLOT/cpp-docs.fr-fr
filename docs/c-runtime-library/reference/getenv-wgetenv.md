---
title: getenv, _wgetenv
description: Décrit la bibliothèque getenv et les fonctions du _wgetenv Runtime C de Microsoft.
ms.date: 4/2/2020
api_name:
- getenv
- _wgetenv
- _o__wgetenv
- _o_getenv
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
- _wgetenv
- getenv
- _tgetenv
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
no-loc:
- getenv
- _wgetenv
- getenv_s
- _wgetenv_s
- _putenv_s
- main
- wmain
- errno
- EINVAL
- ERANGE
- _environ
- _wenviron
- _putenv
- _wputenv
- _tgetenv_s
- _tzset
- _dupenv_s
- _wdupenv_s
ms.openlocfilehash: ea7fba1dd47123919dc0a01fd84bad65481b9db9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913668"
---
# <a name="getenv-_wgetenv"></a>getenv, _wgetenv

Obtient une valeur à partir de l'environnement actuel. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *getenv(
   const char *varname
);
wchar_t *_wgetenv(
   const wchar_t *varname
);
```

### <a name="parameters"></a>Paramètres

*argument*<br/>
Nom de la variable d'environnement.

## <a name="return-value"></a>Valeur retournée

Retourne un pointeur vers l’entrée de la table d’environnement contenant *varname*. Il est déconseillé de modifier la valeur de la variable d’environnement à l’aide du pointeur retourné. Utilisez la fonction [_putenv](putenv-wputenv.md) pour modifier la valeur d’une variable d’environnement. La valeur de retour est **null** si *varname* est introuvable dans la table d’environnement.

## <a name="remarks"></a>Notes 

La fonction **getenv** recherche la liste de variables d’environnement pour *varname*. **getenv** ne respecte pas la casse dans le système d’exploitation Windows. **getenv** et **_putenv** utilisent la copie de l’environnement vers laquelle pointe la variable globale **_environ** pour accéder à l’environnement. **getenv** fonctionne uniquement sur les structures de données accessibles à la bibliothèque Runtime et non sur l’environnement « segment » créé pour le processus par le système d’exploitation. Par conséquent, les programmes qui utilisent l’argument *envp* pour [main](../../cpp/main-function-command-line-args.md) ou [wmain](../../cpp/main-function-command-line-args.md) peuvent récupérer des informations non valides.

Si *varname* a la **valeur null**, cette fonction appelle un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la **valeur** **EINVAL** et retourne null.

**_wgetenv** est une version à caractères larges de **getenv**; l’argument et la valeur de retour de **_wgetenv** sont des chaînes à caractères larges. La variable globale **_wenviron** est une version à caractères larges de **_environ**.

Dans un programme MBCS (par exemple, dans un programme ASCII SBCS), **_wenviron** est initialement **null** , car l’environnement est composé de chaînes de caractères multioctets. Ensuite, lors du premier appel à [_wputenv](putenv-wputenv.md), ou lors du premier appel à **_wgetenv** si un environnement (MBCS) existe déjà, un environnement de chaîne de caractères larges correspondant est créé et est ensuite désigné par **_wenviron**.

De même, dans un programme Unicode (**_wmain**), **_environ** a initialement la **valeur null** , car l’environnement est composé de chaînes à caractères larges. Ensuite, lors du premier appel à **_putenv**, ou lors du premier appel à **getenv** si un environnement (Unicode) existe déjà, un environnement MBCS correspondant est créé et est ensuite désigné par **_environ**.

Quand deux copies de l'environnement (MBCS et Unicode) existent simultanément dans un programme, le système Runtime doit gérer les deux copies, ce qui entraîne des temps d'exécution plus lents. Par exemple, chaque fois que vous appelez **_putenv**, un appel à **_wputenv** est également exécuté automatiquement, de sorte que les deux chaînes d’environnement correspondent.

> [!CAUTION]
> Dans de rares cas, quand le système Runtime gère une version Unicode et une version multioctet de l’environnement, il se peut que ces deux versions d’environnement ne correspondent pas exactement. En effet, même si une chaîne de caractères multioctets unique est mappée à une chaîne Unicode unique, le mappage d'une chaîne Unicode unique à une chaîne de caractères multioctets n'est pas nécessairement unique. Pour plus d’informations, consultez [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Les familles de fonctions **_putenv** et **_getenv** ne sont pas thread-safe. **_getenv** peut retourner un pointeur de chaîne pendant que **_putenv** modifie la chaîne, ce qui provoque des échecs aléatoires. Assurez-vous que les appels à ces fonctions sont synchronisés.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

Pour vérifier ou modifier la valeur de la variable d’environnement **TZ** , utilisez **getenv**, **_putenv** et **_tzset** si nécessaire. Pour plus d’informations sur **TZ**, consultez [_tzset](tzset.md) et [_daylight, TimeZone et _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getenv.c
// compile with: /W3
// This program uses getenv to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *libvar;

   // Get the value of the LIB environment variable.
   libvar = getenv( "LIB" ); // C4996
   // Note: getenv is deprecated; consider using getenv_s instead

   if( libvar != NULL )
      printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects the environment
   // variable of the current process. The command processor's
   // environment is not changed.
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996
   // Note: _putenv is deprecated; consider using putenv_s instead

   // Get new value.
   libvar = getenv( "LIB" ); // C4996

   if( libvar != NULL )
      printf( "New LIB variable is: %s\n", libvar );
}
```

```Output
Original LIB variable is: C:\progra~1\devstu~1\vc\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[Constantes d’environnement](../../c-runtime-library/environmental-constants.md)<br/>
