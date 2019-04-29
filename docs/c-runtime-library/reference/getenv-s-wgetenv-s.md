---
title: getenv_s, _wgetenv_s
ms.date: 11/04/2016
apiname:
- getenv_s
- _wgetenv_s
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
- getenv_s
- _tgetenv_s
- _wgetenv_s
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
ms.openlocfilehash: eac3c036e2f4f271c7bc2d77c8ae82bec28d3617
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331738"
---
# <a name="getenvs-wgetenvs"></a>getenv_s, _wgetenv_s

Obtient une valeur à partir de l'environnement actuel. Ces versions de [getenv, _wgetenv](getenv-wgetenv.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t getenv_s(
   size_t *pReturnValue,
   char* buffer,
   size_t numberOfElements,
   const char *varname
);
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *varname
);
template <size_t size>
errno_t getenv_s(
   size_t *pReturnValue,
   char (&buffer)[size],
   const char *varname
); // C++ only
template <size_t size>
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t (&buffer)[size],
   const wchar_t *varname
); // C++ only
```

### <a name="parameters"></a>Paramètres

*pReturnValue*<br/>
Taille de mémoire tampon nécessaire ou 0 si la variable est introuvable.

*buffer*<br/>
Mémoire tampon chargée de stocker la valeur de la variable d'environnement.

*numberOfElements*<br/>
Taille de *tampon*.

*varname*<br/>
Nom de la variable d'environnement.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite ; code d'erreur en cas d'échec.

### <a name="error-conditions"></a>Conditions d’erreur

|*pReturnValue*|*buffer*|*numberOfElements*|*varname*|Valeur de retour|
|--------------------|--------------|------------------------|---------------|------------------|
|**NULL**|any|any|any|**EINVAL**|
|any|**NULL**|>0|any|**EINVAL**|
|any|any|any|**NULL**|**EINVAL**|

Ces conditions d’erreur appellent un gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions définissent **errno** à **EINVAL** et retourner **EINVAL**.

En outre, si la mémoire tampon est trop petite, ces fonctions retournent **ERANGE**. Elles n'appellent pas de gestionnaire de paramètres non valides. Elles écrivent simplement la taille de mémoire tampon requise en *pReturnValue*et permettent ainsi aux programmes d’appeler la fonction avec une plus grande mémoire tampon.

## <a name="remarks"></a>Notes

Le **getenv_s** fonction recherche dans la liste des variables d’environnement pour *varname*. **getenv_s** n’est pas sensible à la casse dans le système d’exploitation Windows. **getenv_s** et [_putenv_s](putenv-s-wputenv-s.md) utilisent la copie de l’environnement qui est indiqué par la variable globale **_environ** pour accéder à l’environnement. **getenv_s** fonctionne uniquement sur les structures de données qui sont accessibles à la bibliothèque d’exécution et non sur l’environnement « segment » qui est créé pour le processus par le système d’exploitation. Par conséquent, les programmes qui utilisent le *envp* l’argument de [principal](../../cpp/main-program-startup.md) ou [wmain](../../cpp/main-program-startup.md) risquent de récupérer des informations non valides.

**_wgetenv_s** est une version à caractères larges de **getenv_s**; l’argument et valeur de retour de **_wgetenv_s** sont des chaînes à caractères larges. Le **_wenviron** (variable globale) est une version à caractères larges de **_environ**.

Dans un programme MBCS (par exemple, dans un programme ASCII SBSC), **_wenviron** est initialement **NULL** , car l’environnement se compose de chaînes de caractères multioctets. Ensuite, dans le premier appel à [_wputenv](putenv-wputenv.md), ou sur le premier appel à **_wgetenv_s**, si un environnement (MBCS) existe déjà, un environnement de chaîne à caractères larges correspondant est créé et est ensuite vers lequel pointe **_wenviron**.

De même dans Unicode (**_wmain**) programme, **_environ** est initialement **NULL** , car l’environnement se compose de chaînes à caractères larges. Ensuite, dans le premier appel à [_putenv](putenv-wputenv.md), ou sur le premier appel à **getenv_s** si un environnement (Unicode) existe déjà, un environnement MBCS correspondant est créé et est ensuite vers lequel pointe **_ environ**.

Quand il existe simultanément deux copies de l'environnement (MBCS et Unicode) dans un programme, le système Runtime doit gérer les deux copies, ce qui ralentit les temps d'exécution. Par exemple, lorsque vous appelez **_putenv**, un appel à **_wputenv** est aussi exécuté automatiquement afin que les deux chaînes d’environnement correspondent.

> [!CAUTION]
> Dans de rares cas, quand le système Runtime gère une version Unicode et une version multioctet de l'environnement, il se peut que les deux versions d'environnement ne correspondent pas exactement. En effet, même si une chaîne de caractères multioctets unique est mappée à une chaîne Unicode unique, le mappage d'une chaîne Unicode unique à une chaîne de caractères multioctets n'est pas nécessairement unique. Pour plus d’informations, consultez [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Le **_putenv_s** et **_getenv_s** familles de fonctions ne sont pas thread-safe. **_getenv_s** peut retourner un pointeur de chaîne lors de la **_putenv_s** modifie la chaîne et entraînent des échecs aléatoires. Assurez-vous que les appels à ces fonctions sont synchronisés.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite ainsi d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Pour vérifier ou modifier la valeur de la **TZ** utilisation de la variable, environnement **getenv_s**, **_putenv**, et **_tzset**, selon les besoins. Pour plus d’informations sur **TZ**, consultez [_tzset](tzset.md) et [_daylight, _dstbias, _timezone et _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getenv_s.c
// This program uses getenv_s to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* libvar;
   size_t requiredSize;

   getenv_s( &requiredSize, NULL, 0, "LIB");
   if (requiredSize == 0)
   {
      printf("LIB doesn't exist!\n");
      exit(1);
   }

   libvar = (char*) malloc(requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects
   // the environment variable of the current process. The command
   // processor's environment is not changed.
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );

   getenv_s( &requiredSize, NULL, 0, "LIB");

   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the new value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "New LIB variable is: %s\n", libvar );

   free(libvar);
}
```

```Output
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[Constantes d’environnement](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
