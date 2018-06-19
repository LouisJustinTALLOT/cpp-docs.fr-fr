---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 362716963911a29a9b3558c387e69c4cd91b369e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415580"
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Obtenez un message d’erreur système (**strerror_s**, **_wcserror_s**) ou imprimer un message d’erreur fourni par l’utilisateur (**_strerror_s**, **__wcserror_s** ). Ces versions de [strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*numberOfElements*<br/>
Taille de la mémoire tampon.

*errnum*<br/>
Numéro d'erreur.

*strErrMsg*<br/>
Message fourni par l'utilisateur.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

### <a name="error-condtions"></a>Conditions d’erreur

|*buffer*|*numberOfElements*|*strErrMsg*|Contenu de *tampon*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|any|any|N/A|
|any|0|any|non modifié|

## <a name="remarks"></a>Notes

Le **strerror_s** mappages de fonction *errnum* vers une chaîne de message d’erreur, retournant la chaîne dans *tampon*. **_strerror_s** n’accepte pas le numéro d’erreur ; Il utilise la valeur actuelle de **errno** pour déterminer le message approprié. Ni **strerror_s** ni **_strerror_s** réellement imprime le message : pour ce faire, vous devez appeler une fonction de sortie tel que [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Si *strErrMsg* est **NULL**, **_strerror_s** retourne une chaîne dans *tampon* contenant le message d’erreur système pour le dernier appel de bibliothèque qui a généré une erreur. La chaîne de message d'erreur se termine par le caractère de saut de ligne ('\n'). Si *strErrMsg* n’est pas égal à **NULL**, puis **_strerror_s** retourne une chaîne dans *tampon* contenant (dans l’ordre) votre message de type chaîne, un signe deux-points, un espace, le message d’erreur système pour le dernier appel de bibliothèque produisant une erreur et un caractère de saut de ligne. La longueur maximale de votre message de type chaîne est de 94 caractères.

Ces fonctions tronquent le message d’erreur si sa longueur dépasse *numberOfElements* -1. La chaîne obtenue dans *tampon* est toujours terminée par null.

Le numéro d’erreur réel pour **_strerror_s** est stocké dans la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Les messages d’erreur système sont accessibles via la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), qui est un tableau de messages classés par numéro d’erreur. **_strerror_s** accède au message d’erreur approprié à l’aide de la **errno** valeur comme un index de la variable **_sys_errlist**. La valeur de la variable [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) est défini comme le nombre maximal d’éléments dans le **_sys_errlist** tableau. Pour générer des résultats précis, appelez **_strerror_s** immédiatement après le retour de la routine de bibliothèque avec une erreur. Sinon, les appels suivants à **strerror_s** ou **_strerror_s** peut remplacer le **errno** valeur.

**_wcserror_s** et **__wcserror_s** sont des versions à caractères larges de **strerror_s** et **_strerror_s**, respectivement.

Ces fonctions valident leurs paramètres. Si la mémoire tampon est **NULL** ou si le paramètre de taille est égale à 0, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, les fonctions retournent **EINVAL** et **errno** à **EINVAL**.

**_strerror_s**, **_wcserror_s**, et **__wcserror_s** ne font pas partie de la définition ANSI mais sont plutôt des extensions de Microsoft. Ne les utilisez pas lorsque la portabilité est souhaitée ; pour la compatibilité ANSI, utilisez **strerror_s** à la place.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Les versions debug de ces fonctions remplissent d'abord la mémoire tampon avec 0xFD. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

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

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
