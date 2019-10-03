---
title: _vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l
ms.date: 11/04/2016
api_name:
- _vcprintf_s
- _vcprintf_s_l
- _vcwprintf_s
- _vcwprintf_s_l
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
- vcprintf_s
- vcwprintf_s_l
- _vcwprintf_s
- _vcwprintf_s_l
- _vcprintf_s_l
- _vtcprintf_s
- vcwprintf_s
- vcprintf_s_l
- _vcprintf_s
helpviewer_keywords:
- _vtcprintf_s_l function
- _vcwprintf_s_l function
- _vtcprintf_s function
- vtcprintf_s_l function
- vcprintf_s_l function
- _vcprintf_s function
- _vcwprintf_s function
- vcwprintf_s_l function
- vcwprintf_s function
- vcprintf_s function
- _vcprintf_s_l function
- vtcprintf_s function
- formatted text [C++]
ms.assetid: 5a46d45a-30db-45df-9850-455cbdac5636
ms.openlocfilehash: a6a3e94167adcc614a5de45a314fca25bdc9e1f2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945662"
---
# <a name="_vcprintf_s-_vcprintf_s_l-_vcwprintf_s-_vcwprintf_s_l"></a>_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l

Écrit la sortie mise en forme dans la console en utilisant un pointeur désignant une liste d’arguments. Ces versions de [_vcprintf, _vcprintf_l, _vcwprintf, _vcwprintf_l](vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _vcprintf(
   const char* format,
   va_list argptr
);
int _vcprintf(
   const char* format,
   locale_t locale,
   va_list argptr
);
int _vcwprintf_s(
   const wchar_t* format,
   va_list argptr
);
int _vcwprintf_s_l(
   const wchar_t* format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Paramètres

*format*<br/>
Spécification de format.

*argptr*<br/>
Pointeur désignant la liste d’arguments.

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d’informations, consultez [Syntaxe de spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur de retour

Nombre de caractères écrits ou valeur négative si une erreur de sortie se produit.

Comme les versions moins sécurisées de ces fonctions, si *format* est un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). En outre, à la différence des versions moins sécurisées de ces fonctions, si *format* ne spécifie pas un format valide, une exception de paramètre non valide est générée. Si l’exécution est autorisée à se poursuivre, ces fonctions retournent un code d’erreur et attribuent à **errno** la valeur de ce code d’erreur. Le code d’erreur par défaut est **EINVAL** si une valeur plus spécifique ne s’applique pas.

## <a name="remarks"></a>Notes

Chacune de ces fonctions prend un pointeur désignant une liste d’arguments, puis met en forme et écrit les données fournies dans la console. **_vcwprintf_s** est la version à caractères larges de **_vcprintf_s**. Elle prend une chaîne de caractères larges comme argument.

Les versions de ces fonctions qui ont le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux actuels.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtcprintf_s**|**_vcprintf_s**|**_vcprintf_s**|**_vcwprintf_s**|
|**_vtcprintf_s_l**|**_vcprintf_s_l**|**_vcprintf_s_l**|**_vcwprintf_s_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_vcprintf_s**, **_vcprintf_s_l**|\<conio.h> et \<stdarg.h>|\<varargs.h>*|
|**_vcwprintf_s**, **_vcwprintf_s_l**|\<conio.h> ou \<wchar.h> et \<stdarg.h>|\<varargs.h>*|

\* Nécessaire pour la compatibilité avec UNIX V.

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```cpp
// crt_vcprintf_s.cpp
#include <conio.h>
#include <stdarg.h>

// An error formatting function used to print to the console.
int eprintf_s(const char* format, ...)
{
    va_list args;
    va_start(args, format);
    int result = _vcprintf_s(format, args);
    va_end(args);
    return result;
}

int main()
{
    eprintf_s("(%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,
              "<some error text>");
    eprintf_s("    (Related to symbol '%s' defined on line %d).\n",
              "<symbol>", 5 );
}
```

```Output
(10,23): Error C2111 : <some error text>
    (Related to symbol '<symbol>' defined on line 5).
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
