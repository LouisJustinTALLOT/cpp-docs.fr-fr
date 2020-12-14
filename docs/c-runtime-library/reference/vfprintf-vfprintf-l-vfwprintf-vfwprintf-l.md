---
description: 'En savoir plus sur : vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l'
title: vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l
ms.date: 11/04/2016
api_name:
- _vfprintf_l
- vfprintf
- vfwprintf
- _vfwprintf_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vfwprintf
- _vftprintf
- vfprintf
helpviewer_keywords:
- _vfwprintf_l function
- _vftprintf function
- vfprintf function
- _vftprintf_l function
- vfprintf_l function
- vftprintf_l function
- vfwprintf_l function
- vftprintf function
- vfwprintf function
- _vfprintf_l function
- formatted text [C++]
ms.assetid: 4443be50-cedf-40b2-b3e2-ff2b3af3b666
ms.openlocfilehash: 3c22b5bff6250c6869d1cc86573064b3e4c81348
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97279635"
---
# <a name="vfprintf-_vfprintf_l-vfwprintf-_vfwprintf_l"></a>vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l

Écrivez la sortie mise en forme en utilisant un pointeur désignant une liste d’arguments. Il existe des versions plus sécurisées de ces fonctions. Consultez [vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int vfprintf(
   FILE *stream,
   const char *format,
   va_list argptr
);
int _vfprintf_l(
   FILE *stream,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vfwprintf(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
int _vfwprintf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Paramètres

*train*<br/>
Pointeur désignant la structure **FILE**.

*format*<br/>
Spécification de format.

*argptr*<br/>
Pointeur vers la liste d'arguments.

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d’informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur renvoyée

**vfprintf** et **vfwprintf** retournent le nombre de caractères écrits, à l’exclusion du caractère null de fin, ou une valeur négative si une erreur de sortie se produit. Si *Stream* ou *format* est un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions prend un pointeur vers une liste d’arguments, puis met en forme et écrit les données spécifiées dans le *flux*.

**vfwprintf** est la version à caractères larges de **vfprintf**; les deux fonctions se comportent de la même manière si le flux est ouvert en mode ANSI. **vfprintf** ne prend pas actuellement en charge la sortie dans un flux Unicode.

Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf**|**vfprintf**|**vfprintf**|**vfwprintf**|
|**_vftprintf_l**|**_vfprintf_l**|**_vfprintf_l**|**_vfwprintf_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**vfprintf**, **_vfprintf_l**|\<stdio.h> et \<stdarg.h>|\<varargs.h>*|
|**vfwprintf**, **_vfwprintf_l**|\<stdio.h> ou \<wchar.h> , et \<stdarg.h>|\<varargs.h>*|

\* Requis pour la compatibilité UNIX V.

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
