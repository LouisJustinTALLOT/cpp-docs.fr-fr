---
title: strerror, _strerror, _wcserror, __wcserror
description: Décrit les fonctions de la bibliothèque Runtime C (CRT) de Microsoft strerror, _strerror, _wcserror et __wcserror.
ms.date: 4/2/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
- _o___wcserror
- _o__strerror
- _o__wcserror
- _o_strerror
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 30885974b9c9fbf0fdca0e52808fb8bd1dfbaffe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920036"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Obtient une chaîne de message d’erreur système (**strerror**, **_wcserror**) ou met en forme une chaîne de message d’erreur fournie par l’utilisateur (**_strerror**, **__wcserror**). Il existe des versions plus sécurisées de ces fonctions. Consultez [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Syntaxe

```C
char * strerror(
   int errnum );

char * _strerror(
   const char *strErrMsg );

wchar_t * _wcserror(
   int errnum );

wchar_t * __wcserror(
   const wchar_t *strErrMsg );
```

### <a name="parameters"></a>Paramètres

*ErrNum*\
Numéro d’erreur.

*strErrMsg*\
Message fourni par l'utilisateur.

## <a name="return-value"></a>Valeur retournée

Toutes ces fonctions retournent un pointeur vers une chaîne de message d’erreur, dans une mémoire tampon de stockage de thread local détenue par le Runtime. Les appels ultérieurs sur le même thread peuvent remplacer cette chaîne.

## <a name="remarks"></a>Notes 

La fonction **strerror** mappe *ErrNum* à une chaîne de message d’erreur et retourne un pointeur vers la chaîne. Les fonctions **strerror** et **_strerror** n’impriment en fait pas le message. Pour imprimer, appelez une fonction de sortie telle que [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Si *strErrMsg* est passé comme **null**, **_strerror** retourne un pointeur vers une chaîne. Il contient le message d’erreur système pour le dernier appel de bibliothèque qui a généré une erreur. La chaîne de message d'erreur se termine par le caractère de saut de ligne ('\n'). Quand *strErrMsg* n’est pas **null**, la chaîne contient, dans l’ordre : votre chaîne *strErrMsg* , un signe deux-points, un espace, le message d’erreur système et un caractère de saut de ligne. Votre message de type chaîne peut avoir une longueur maximale de 94 caractères, en caractères étroits (**_strerror**) ou larges (**__wcserror**).

Le numéro d’erreur réel pour **_strerror** est stocké dans la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Pour obtenir des résultats précis, appelez **_strerror** immédiatement après qu’une routine de bibliothèque a retourné une erreur. Dans le cas contraire, les appels ultérieurs aux routines de bibliothèque peuvent remplacer la valeur **errno** .

**_wcserror** et **__wcserror** sont respectivement des versions à caractères larges de **strerror** et **_strerror**.

**_strerror**, **_wcserror**et **__wcserror** sont spécifiques à Microsoft et ne font pas partie de la bibliothèque C standard. Nous vous déconseillons de les utiliser là où vous voulez un code portable. Pour la compatibilité C standard, utilisez **strerror** à la place.

Pour recevoir des chaînes d’erreur, nous vous recommandons d’utiliser **strerror** ou **_wcserror** au lieu des macros déconseillées [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) et [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) et les fonctions internes dépréciées **__sys_errlist** et **__sys_nerr**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a> Exemple

Consultez l’exemple relatif à [perror](perror-wperror.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)\
[clearerr](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
