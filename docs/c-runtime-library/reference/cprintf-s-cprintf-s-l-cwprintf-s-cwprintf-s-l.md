---
description: 'En savoir plus sur les éléments suivants : _cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l'
title: _cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l
ms.date: 11/04/2016
api_name:
- _cwprintf_s_l
- _cprintf_s_l
- _cprintf_s
- _cwprintf_s
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
- _cwprintf_s_l
- _cprintf_s
- cwprintf_s
- _cprintf_s_l
- cwprintf_s_l
- cprintf_s_l
- _tcprintf_s
- cprintf_s
- _cwprintf_s
- tcprintf_s
helpviewer_keywords:
- tcprintf_s_l function
- _cprintf_s_l function
- _cwprintf_s_l function
- tcprintf_s function
- _tcprintf_s_l function
- _cwprintf_s function
- cwprintf_s function
- _cprintf_s function
- cprintf_s function
- _tcprintf_s function
- cprintf_s_l function
- cwprintf_s_l function
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
ms.openlocfilehash: 0a6529a6a2861829028f11dd25e2b044faa498a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155954"
---
# <a name="_cprintf_s-_cprintf_s_l-_cwprintf_s-_cwprintf_s_l"></a>_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l

Met en forme et affiche les informations dans la console. Ces versions de [_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _cprintf_s(
   const char * format [,
   argument] ...
);
int _cprintf_s_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_s(
   const wchar * format [,
   argument] ...
);
int _cwprintf_s_l(
   const wchar * format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Paramètres

*format*<br/>
Chaîne de contrôle de format.

*argument*<br/>
Paramètres facultatifs.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Nombre de caractères affichés.

## <a name="remarks"></a>Notes

Ces fonctions mettent en forme et impriment une série de caractères et de valeurs directement dans la console, à l’aide de la fonction **_putch** (**_putwch** pour **_cwprintf_s**) à des caractères de sortie. Chaque *argument* (le cas échéant) est converti et sorti selon la spécification de format correspondante au *format*. Le format a la même forme et la même fonction que le paramètre *format* pour la fonction [printf_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) . Contrairement aux fonctions **fprintf_s**, **printf_s** et **sprintf_s** , ni **_cprintf_s** ni **_cwprintf_s** ne convertit les caractères de saut de ligne en combinaisons retour chariot-saut de ligne (CR-LF) lors de la sortie.

Une distinction importante est que **_cwprintf_s** affiche des caractères Unicode lorsqu’ils sont utilisés dans Windows NT. Contrairement à **_cprintf_s**, **_cwprintf_s** utilise les paramètres régionaux de la console actuelle

Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux actuels.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur.

Comme les versions non sécurisées (voir [_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)), ces fonctions valident leurs paramètres et appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md), si le *format* est un pointeur null. Ces fonctions diffèrent des versions non sécurisées en ce sens que la chaîne de format elle-même est également validée. S’il existe des spécificateurs de mise en forme inconnus ou incorrects, ces fonctions appellent le gestionnaire de paramètres non valides. Dans tous les cas, si l’exécution est autorisée à se poursuivre, les fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_s**|**_cprintf_s**|**_cprintf_s**|**_cwprintf_s**|
|**_tcprintf_s_l**|**_cprintf_s_l**|**_cprintf_s_l**|**_cwprintf_s_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_cprintf_s**, **_cprintf_s_l**|\<conio.h>|
|**_cwprintf_s**, **_cwprintf_s_l**|\<conio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_cprintf_s.c
// compile with: /c
// This program displays some variables to the console.

#include <conio.h>

int main( void )
{
   int      i = -16, h = 29;
   unsigned u = 62511;
   char     c = 'A';
   char     s[] = "Test";

   /* Note that console output does not translate \n as
    * standard output does. Use \r\n instead.
    */
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>Voir aussi

[E/s de console et de port](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)<br/>
[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)<br/>
[Syntaxe de spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
