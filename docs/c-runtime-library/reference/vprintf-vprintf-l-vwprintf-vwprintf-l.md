---
title: vprintf, _vprintf_l, vwprintf, _vwprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- vprintf
- _vwprintf_l
- _vprintf_l
- vwprintf
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
apitype: DLLExport
f1_keywords:
- vwprintf
- _vtprintf
dev_langs:
- C++
helpviewer_keywords:
- vwprintf function
- _vwprintf_l function
- vwprintf_l function
- _vtprintf function
- vtprintf_l function
- vprintf function
- _vprintf_l function
- vprintf_l function
- vtprintf function
- _vtprintf_l function
- formatted text [C++]
ms.assetid: 44549505-00a0-4fa7-9a85-f2e666f55a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c809278279aff17adfdf77f658d7a2759a87ce1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414817"
---
# <a name="vprintf-vprintfl-vwprintf-vwprintfl"></a>vprintf, _vprintf_l, vwprintf, _vwprintf_l

Écrit la sortie mise en forme en utilisant un pointeur désignant une liste d’arguments. Il existe des versions plus sécurisées de ces fonctions. Consultez [vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int vprintf(
   const char *format,
   va_list argptr
);
int _vprintf_l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int vwprintf(
   const wchar_t *format,
   va_list argptr
);
int _vwprintf_l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Paramètres

*format*<br/>
Spécification de format.

*argptr*<br/>
Pointeur vers la liste d'arguments.

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d'informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur de retour

**vprintf** et **vwprintf** retourner le nombre de caractères écrits, non compris le caractère null de fin, ou une valeur négative si une erreur se produit. Si *format* est un pointeur null, ou si la chaîne de format contient des caractères de mise en forme non valides, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent -1 et la valeur **errno** à **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions prend un pointeur vers une liste d’arguments, met en forme et écrit les données spécifiées vers **stdout**.

**vwprintf** est la version à caractères larges de **vprintf**; les deux fonctions se comportent de façon identique si le flux est ouvert en mode ANSI. **vprintf** ne prend actuellement en charge la sortie dans un flux de données UNICODE.

Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](http://msdn.microsoft.com/library/windows/desktop/ms717795). Notez que les chaînes de format non valide sont détectées et génèrent une erreur.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtprintf**|**vprintf**|**vprintf**|**vwprintf**|
|**_vtprintf_l**|**_vprintf_l**|**_vprintf_l**|**_vwprintf_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**vprintf**, **_vprintf_l**|\<stdio.h> et \<stdarg.h>|\<varargs.h>*|
|**vwprintf**, **_vwprintf_l**|\<stdio.h> ou \<wchar.h> et \<stdarg.h>|\<varargs.h>*|

\** Nécessaire pour la compatibilité avec UNIX V.

La console n’est pas pris en charge dans les applications de plateforme Windows universelle (UWP). Les descripteurs de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions d’exécution C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
