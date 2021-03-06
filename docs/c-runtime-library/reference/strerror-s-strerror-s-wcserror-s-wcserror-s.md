---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
description: Fonctionne avec des améliorations de sécurité pour obtenir un message d’erreur système ou imprimer un message d’erreur fourni par l’utilisateur.
ms.date: 09/25/2020
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
- _o__strerror_s
- _o__wcserror_s
- _o_strerror_s
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
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
ms.openlocfilehash: 4e594a37425714ef521c083785120e2262225b19
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414618"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Obtenir un message d’erreur système (**strerror_s**, **_wcserror_s**) ou imprimer un message d’erreur fourni par l’utilisateur (**_strerror_s**, **__wcserror_s**). Ces versions de [strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t strerror_s(
   char *buffer,
   size_t sizeInBytes,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t sizeInBytes,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t sizeInWords,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t sizeInWords,
   const wchar_t *strErrMsg
);
```

```cpp
template <size_t size>
errno_t strerror_s(
   char (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t _strerror_s(
   char (&buffer)[size],
   const char *strErrMsg
); // C++ only
template <size_t size>
errno_t _wcserror_s(
   wchar_t (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t __wcserror_s(
   wchar_t (&buffer)[size],
   const wchar_t *strErrMsg
); // C++ only
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*\
Mémoire tampon devant contenir la chaîne d’erreur.

*sizeInBytes*\
Nombre d'octets dans la mémoire tampon.

*sizeInWords*\
Nombre de mots dans la mémoire tampon.

*ErrNum*\
Numéro d’erreur.

*strErrMsg*\
Message fourni par l'utilisateur.

## <a name="return-value"></a>Valeur renvoyée

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

### <a name="error-conditions"></a>Conditions d’erreur

|*mémoire tampon*|*sizeInBytes/sizeInWords*|*strErrMsg*|Contenu de la *mémoire tampon*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|n'importe laquelle|n'importe laquelle|n/a|
|n'importe laquelle|0|n'importe laquelle|non modifié|

## <a name="remarks"></a>Notes

La fonction **strerror_s** est thread-safe.

La fonction **strerror_s** mappe *ErrNum* à une chaîne de message d’erreur, en retournant la chaîne dans la *mémoire tampon*. **_strerror_s** ne prend pas le numéro d’erreur ; elle utilise la valeur actuelle de **errno** pour déterminer le message approprié. Ni **strerror_s** ni **_strerror_s** n’imprime réellement le message : pour cela, vous devez appeler une fonction de sortie telle que [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Si *strErrMsg* a la **valeur null**, **_strerror_s** retourne une chaîne dans *buffer* qui contient le message d’erreur système pour le dernier appel de bibliothèque qui a généré une erreur. La chaîne de message d'erreur se termine par le caractère de saut de ligne ('\n'). Si *strErrMsg* n’est pas égal à **null**, **_strerror_s** retourne une chaîne dans *buffer* qui contient (dans l’ordre) votre message de chaîne, un signe deux-points, un espace, le message d’erreur système pour le dernier appel de bibliothèque qui a généré une erreur et un caractère de saut de ligne. La longueur maximale de votre message de type chaîne est de 94 caractères.

Ces fonctions tronquent le message d’erreur si sa longueur dépasse la taille de la mémoire tampon-1. La chaîne résultante dans la *mémoire tampon* sera toujours terminée par un caractère null.

Le numéro d’erreur réel pour **_strerror_s** est stocké dans la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Les messages d’erreur système sont accessibles via la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), qui est un tableau de messages classés par numéro d’erreur. **_strerror_s** accède au message d’erreur approprié en utilisant la valeur **errno** comme index de la variable **_sys_errlist**. La valeur de la variable [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) est définie comme le nombre maximal d’éléments dans le tableau **_sys_errlist** . Pour obtenir des résultats précis, appelez **_strerror_s** immédiatement après le retour d’une routine de bibliothèque avec une erreur. Sinon, les appels suivants à **strerror_s** ou **_strerror_s** peuvent remplacer la valeur **errno** .

**_wcserror_s** et **__wcserror_s** sont respectivement des versions à caractères larges de **strerror_s** et de **_strerror_s**.

Ces fonctions valident leurs paramètres. Si buffer a la **valeur null** ou si le paramètre size a la valeur 0, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, les fonctions retournent **EINVAL** et attribuent à **errno** la valeur **EINVAL**.

**_strerror_s**, **_wcserror_s**et **__wcserror_s** ne font pas partie de la définition ANSI, mais plutôt des extensions Microsoft. Ne les utilisez pas là où la portabilité est souhaitée ; pour la compatibilité ANSI, utilisez **strerror_s** à la place.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strerror_s**, **_strerror_s**|\<string.h>|
|**_wcserror_s**, **__wcserror_s**|\<string.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [perror](perror-wperror.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)\
[clearerr](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
