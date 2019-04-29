---
title: strerror, _strerror, _wcserror, __wcserror
ms.date: 11/04/2016
apiname:
- strerror
- _strerror
- _wcserror
- __wcserror
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
ms.openlocfilehash: 4038fcc29c18e5d73024cbe5688c674e00d1409e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353857"
---
# <a name="strerror-strerror-wcserror-wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Obtient une chaîne de message d’erreur système (**strerror**, **_wcserror**) ou met en forme une chaîne de message d’erreur fourni par l’utilisateur (**_strerror**, **__wcserror**). Il existe des versions plus sécurisées de ces fonctions. Consultez [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *strerror(
   int errnum
);
char *_strerror(
   const char *strErrMsg
);
wchar_t * _wcserror(
   int errnum
);
wchar_t * __wcserror(
   const wchar_t *strErrMsg
);
```

### <a name="parameters"></a>Paramètres

*errnum*<br/>
Numéro d'erreur.

*strErrMsg*<br/>
Message fourni par l'utilisateur.

## <a name="return-value"></a>Valeur de retour

Toutes ces fonctions retournent un pointeur vers la chaîne de message d'erreur. Les appels suivants peuvent remplacer la chaîne.

## <a name="remarks"></a>Notes

Le **strerror** fonction maps *errnum* sur une chaîne de message d’erreur et retourne un pointeur désignant la chaîne. Ni **strerror** ni **_strerror** n’imprime réellement le message : Pour cela, vous devez appeler une fonction de sortie telle que [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Si *strErrMsg* est passé en tant que **NULL**, **_strerror** retourne un pointeur vers une chaîne qui contient le message d’erreur système pour le dernier appel de bibliothèque qui a généré l’erreur. La chaîne de message d'erreur se termine par le caractère de saut de ligne ('\n'). Si *strErrMsg* n’est pas égal à **NULL**, puis **_strerror** retourne un pointeur vers une chaîne qui contient (dans l’ordre) votre message de type chaîne, un signe deux-points, un espace, l’erreur système message pour le dernier appel de bibliothèque qui produit une erreur et un caractère de saut de ligne. La longueur maximale de votre message de type chaîne est de 94 caractères.

Le numéro d’erreur pour **_strerror** est stocké dans la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Pour produire des résultats précis, appelez **_strerror** immédiatement après le retour de la routine de bibliothèque avec une erreur. Sinon, les appels suivants à **strerror** ou **_strerror** peut remplacer le **errno** valeur.

**_wcserror** et **__wcserror** sont des versions à caractères larges de **strerror** et **_strerror**, respectivement.

**_strerror**, **_wcserror**, et **__wcserror** ne font pas partie de la définition ANSI ; ils sont des extensions Microsoft et nous vous recommandons de ne pas utiliser les où vous voulez un code portable. Pour la compatibilité ANSI, utilisez **strerror** à la place.

Pour obtenir des chaînes d’erreur, nous vous recommandons de **strerror** ou **_wcserror** plutôt que les macros déconseillées [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) et [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) et les fonctions internes déconseillées **__sys_errlist** et **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [perror](perror-wperror.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
