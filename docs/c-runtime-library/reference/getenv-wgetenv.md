---
title: getenv, _wgetenv
ms.date: 11/04/2016
apiname:
- getenv
- _wgetenv
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
ms.openlocfilehash: 79c685fef8d6a4b966c53bb7d94b423d16971976
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568157"
---
# <a name="getenv-wgetenv"></a>getenv, _wgetenv

Obtient une valeur à partir de l'environnement actuel. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*nom de variable*<br/>
Nom de la variable d'environnement.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers l’environnement de la table entrée contenant *varname*. Il est déconseillé de modifier la valeur de la variable d’environnement à l’aide du pointeur retourné. Utilisez le [_putenv](putenv-wputenv.md) (fonction) pour modifier la valeur d’une variable d’environnement. La valeur de retour est **NULL** si *varname* est introuvable dans la table d’environnement.

## <a name="remarks"></a>Notes

Le **getenv** fonction recherche dans la liste des variables d’environnement pour *varname*. **getenv** n’est pas sensible à la casse dans le système d’exploitation Windows. **getenv** et **_putenv** utilisent la copie de l’environnement vers lequel pointé la variable globale **_environ** pour accéder à l’environnement. **getenv** fonctionne uniquement sur les structures de données accessibles à la bibliothèque d’exécution et non sur l’environnement « segment » créé pour le processus par le système d’exploitation. Par conséquent, les programmes qui utilisent le *envp* l’argument de [principal](../../cpp/main-program-startup.md) ou [wmain](../../cpp/main-program-startup.md) peut récupérer des informations non valides.

Si *varname* est **NULL**, cette fonction appelle un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **NULL**.

**_wgetenv** est une version à caractères larges de **getenv**; l’argument et valeur de retour de **_wgetenv** sont des chaînes à caractères larges. Le **_wenviron** (variable globale) est une version à caractères larges de **_environ**.

Dans un programme MBCS (par exemple, dans un programme ASCII SBSC), **_wenviron** est initialement **NULL** , car l’environnement se compose de chaînes de caractères multioctets. Ensuite, dans le premier appel à [_wputenv](putenv-wputenv.md), ou sur le premier appel à **_wgetenv** si un environnement (MBCS) existe déjà, un environnement de chaîne à caractères larges correspondant est créé et est ensuite vers lequel pointe **_wenviron**.

De même dans Unicode (**_wmain**) programme, **_environ** est initialement **NULL** , car l’environnement se compose de chaînes à caractères larges. Ensuite, dans le premier appel à **_putenv**, ou sur le premier appel à **getenv** si un environnement (Unicode) existe déjà, un environnement MBCS correspondant est créé et est ensuite vers lequel pointe **_ environ**.

Quand deux copies de l'environnement (MBCS et Unicode) existent simultanément dans un programme, le système Runtime doit gérer les deux copies, ce qui entraîne des temps d'exécution plus lents. Par exemple, lorsque vous appelez **_putenv**, un appel à **_wputenv** est aussi exécuté automatiquement, afin que les deux chaînes d’environnement correspondent.

> [!CAUTION]
> Dans de rares cas, quand le système Runtime gère une version Unicode et une version multioctet de l’environnement, il se peut que ces deux versions d’environnement ne correspondent pas exactement. En effet, même si une chaîne de caractères multioctets unique est mappée à une chaîne Unicode unique, le mappage d'une chaîne Unicode unique à une chaîne de caractères multioctets n'est pas nécessairement unique. Pour plus d’informations, consultez [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Le **_putenv** et **_getenv** familles de fonctions ne sont pas thread-safe. **_getenv** peut retourner un pointeur de chaîne lors de la **_putenv** modifie la chaîne, à l’origine des défaillances aléatoires. Assurez-vous que les appels à ces fonctions sont synchronisés.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

Pour vérifier ou modifier la valeur de la **TZ** utilisation de la variable, environnement **getenv**, **_putenv** et **_tzset** en fonction des besoins. Pour plus d’informations sur **TZ**, consultez [_tzset](tzset.md) et [_daylight, timezone et _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Configuration requise

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
