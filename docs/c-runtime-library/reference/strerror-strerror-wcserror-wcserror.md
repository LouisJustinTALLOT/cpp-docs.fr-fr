---
title: strerror, _strerror, _wcserror, __wcserror
description: Décrit les fonctions Microsoft C Runtime Library (CRT) strerror, _strerror, _wcserror et __wcserror.
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 9eecb7376cf476f0128dc20c8884746a3b4d47d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337327"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Obtient une chaîne de message d’erreur système (**strerror**, **_wcserror**) ou formate une chaîne de message d’erreur fournie par l’utilisateur (**_strerror**, **__wcserror**). Il existe des versions plus sécurisées de ces fonctions. Consultez [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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

*errnum*\
Numéro d’erreur.

*strErrMsg*\
Message fourni par l'utilisateur.

## <a name="return-value"></a>Valeur retournée

Toutes ces fonctions renvoient un pointeur à une chaîne de message d’erreur, dans un tampon de stockage thread-local appartenant à l’heure d’exécution. Des appels ultérieurs sur le même thread peuvent remplacer cette chaîne.

## <a name="remarks"></a>Notes

La fonction **strerror** cartographie *l’erreur* à une chaîne de message d’erreur et renvoie un pointeur à la chaîne. Les fonctions **strerror** et **_strerror** n’impriment pas réellement le message. Pour imprimer, appelez une fonction de sortie telle que [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Si *strErrMsg* est passé comme **NULL**, **_strerror** retourne un pointeur à une chaîne. Il contient le message d’erreur du système pour le dernier appel de bibliothèque qui a produit une erreur. La chaîne de message d'erreur se termine par le caractère de saut de ligne ('\n'). Lorsque *strErrMsg* n’est pas **NULL**, la chaîne contient, dans l’ordre: votre corde *strErrMsg,* un côlon, un espace, le message d’erreur du système, et un caractère newline. Votre message de chaîne peut être, tout au plus, 94 caractères de long, soit étroit (**_strerror**) ou large (**__wcserror**) caractères.

Le numéro d’erreur réel pour **_strerror** est stocké dans le [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)variable . Pour produire des résultats précis, appelez **_strerror** immédiatement après qu’une routine de bibliothèque renvoie une erreur. Sinon, les appels ultérieurs aux routines de bibliothèque peuvent dépasser la valeur **errno.**

**_wcserror** et **__wcserror** sont des versions à caractère large de **strerror** et **_strerror**, respectivement.

**_strerror**, **_wcserror**, et **__wcserror** sont spécifiques à Microsoft, ne font pas partie de la bibliothèque Standard C. Nous ne vous recommandons pas de les utiliser là où vous voulez du code portable. Pour la compatibilité Standard C, utilisez **plutôt strerror.**

Pour obtenir des chaînes d’erreur, nous recommandons **strerror** ou **_wcserror** au lieu des macros dépréciés [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) et [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) et les fonctions internes dépréciées **__sys_errlist** et **__sys_nerr**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Cartographies de routine de texte générique

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

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [perror](perror-wperror.md).

## <a name="see-also"></a>Voir aussi

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)\
[plus clair](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
