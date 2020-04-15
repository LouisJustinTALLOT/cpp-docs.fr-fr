---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ef712ecb6236513d169b4a8836b1365b0aca0633
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337366"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Obtenez un message d’erreur système (**strerror_s**, **_wcserror_s**) ou imprimez un message d’erreur fourni par l’utilisateur **(_strerror_s**, **__wcserror_s**). Ces versions de [strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t strerror_s(
   char *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t numberOfElements,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *strErrMsg
);
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

*buffer*<br/>
Mémoire tampon devant contenir la chaîne d’erreur.

*nombreOfElements*<br/>
Taille de la mémoire tampon.

*errnum*<br/>
Numéro d’erreur.

*strErrMsg*<br/>
Message fourni par l'utilisateur.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

### <a name="error-condtions"></a>Conditions d’erreur

|*buffer*|*nombreOfElements*|*strErrMsg*|Contenu du *tampon*|
|--------------|------------------------|-----------------|--------------------------|
|**Null**|n'importe laquelle|n'importe laquelle|n/a|
|n'importe laquelle|0|n'importe laquelle|non modifié|

## <a name="remarks"></a>Notes

La **fonction strerror_s** cartes *errnum* à une chaîne de message d’erreur, le retour de la chaîne dans *le tampon*. **_strerror_s** ne prend pas le numéro d’erreur; il utilise la valeur actuelle de **errno** pour déterminer le message approprié. Ni **strerror_s** ni **_strerror_s** imprime réellement le message: Pour cela, vous devez appeler une fonction de sortie telle que [fprintf:](fprintf-fprintf-l-fwprintf-fwprintf-l.md)

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Si *strErrMsg* est **NULL**, **_strerror_s** renvoie une chaîne dans *le tampon* contenant le message d’erreur du système pour le dernier appel de bibliothèque qui a produit une erreur. La chaîne de message d'erreur se termine par le caractère de saut de ligne ('\n'). Si *strErrMsg* n’est pas égal à **NULL**, alors **_strerror_s** retourne une chaîne dans *le tampon* contenant (dans l’ordre) votre message de chaîne, un côlon, un espace, le message d’erreur du système pour le dernier appel de bibliothèque produisant une erreur, et un caractère newline. La longueur maximale de votre message de type chaîne est de 94 caractères.

Ces fonctions tronquent le message d’erreur si sa longueur dépasse *le nombreOfElements* -1. La chaîne résultante dans *le tampon* est toujours non terminée.

Le numéro d’erreur réel pour **_strerror_s** est stocké dans le [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)variable . Les messages d’erreur système sont accessibles via la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), qui est un tableau de messages classés par numéro d’erreur. **_strerror_s** accède au message d’erreur approprié en utilisant la valeur **errno** comme un index à la **_sys_errlist**variable . La valeur de la [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) variable est définie comme le nombre maximal d’éléments dans le **tableau _sys_errlist.** Pour produire des résultats précis, appelez **_strerror_s** immédiatement après le retour d’une routine de bibliothèque avec une erreur. Dans le cas contraire, les appels ultérieurs à **strerror_s** ou **_strerror_s** peuvent dépasser la valeur **errno.**

**_wcserror_s** et **__wcserror_s** sont des versions à caractère large de **strerror_s** et **_strerror_s**, respectivement.

Ces fonctions valident leurs paramètres. Si le tampon est **NULL** ou si le paramètre de taille est de 0, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, les fonctions retournent **EINVAL** et **placent errno** à **EINVAL**.

**_strerror_s**, **_wcserror_s**, et **__wcserror_s** ne font pas partie de la définition ANSI, mais sont plutôt des extensions Microsoft à elle. Ne les utilisez pas là où la portabilité est souhaitée; pour la compatibilité ANSI, utilisez **strerror_s** à la place.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de bibliothèque de débogé de ces fonctions remplissent d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
