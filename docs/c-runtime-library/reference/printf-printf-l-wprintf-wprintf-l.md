---
title: printf, _printf_l, wprintf, _wprintf_l
ms.date: 11/04/2016
api_name:
- _printf_l
- wprintf
- _wprintf_l
- printf
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
- printf
- _tprintf
- wprintf
helpviewer_keywords:
- printf function
- printf_l function
- tprintf_l function
- tprintf function
- _printf_l function
- wprintf function
- writing to console
- wprintf_l function
- _tprintf_l function
- _wprintf_l function
- _tprintf function
- printf function, format specification fields
- printf function, using
- formatted text [C++]
ms.assetid: 77a854ae-5b48-4865-89f4-f2dc5cf80f52
ms.openlocfilehash: 431c27a26fb549705abde28b08654ce47498e239
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421323"
---
# <a name="printf-_printf_l-wprintf-_wprintf_l"></a>printf, _printf_l, wprintf, _wprintf_l

Imprime une sortie mise en forme dans le flux de sortie standard. Il existe des versions plus sécurisées de ces fonctions. Consultez [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int printf(
   const char *format [,
   argument]...
);
int _printf_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wprintf(
   const wchar_t *format [,
   argument]...
);
int _wprintf_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Paramètres

*format*<br/>
Contrôle de format.

*argument*<br/>
Arguments facultatifs.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de caractères imprimés ou une valeur négative si une erreur se produit. Si *format* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne-1 et définit **errno** sur **EINVAL**. Si **EOF** (0xFFFF) est rencontré dans un *argument*, la fonction retourne-1.

Pour plus d’informations sur les codes d’erreur et **errno** , consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **printf** met en forme et imprime une série de caractères et de valeurs dans le flux de sortie standard, **stdout**. Si les arguments suivent la chaîne de *format* , la chaîne de *format* doit contenir des spécifications qui déterminent le format de sortie des arguments. **printf** et [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md) se comportent de la même manière, sauf que **printf** écrit la sortie dans **stdout** plutôt que sur une destination de type **file**.

**wprintf** est une version à caractères larges de **printf**; le *format* est une chaîne de caractères larges. **wprintf** et **printf** se comportent de la même manière si le flux est ouvert en mode ANSI. **printf** ne prend pas actuellement en charge la sortie dans un flux Unicode.

Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_unicode défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf**|**printf**|**printf**|**wprintf**|

L’argument de *format* se compose de caractères ordinaires, de séquences d’échappement et de spécifications de format (si les arguments suivent le *format*). Les caractères ordinaires et les séquences d’échappement sont copiés dans **stdout** dans l’ordre de leur apparence. Par exemple, la ligne suivante :

```C
printf("Line one\n\t\tLine two\n");
```

génère cette sortie :

```Output
Line one
        Line two
```

Les [spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) commencent toujours par un signe de pourcentage ( **%** ) et sont lues de gauche à droite. Lorsque **printf** rencontre la première spécification de format (le cas échéant), il convertit la valeur du premier argument après le *format* et la génère en conséquence. La deuxième spécification de format entraîne la conversion et la sortie du deuxième argument, et ainsi de suite. S’il y a plus d’arguments que de spécifications de format, les arguments en trop sont ignorés. Les résultats sont indéfinis s’il n’y a pas assez d’arguments pour toutes les spécifications de format.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tprintf**|**printf**|**printf**|**wprintf**|
|**_tprintf_l**|**_printf_l**|**_printf_l**|**_wprintf_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**printf**, **_printf_l**|\<stdio.h>|
|**wprintf**, **_wprintf_l**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console, **stdin**, **stdout**et **stderr**, doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

> [!IMPORTANT]
> À compter de Windows 10 version 2004 (Build 19041), la `printf` famille de fonctions imprime exactement des nombres à virgule flottante représentables en fonction des règles IEEE 754 pour l’arrondi. Dans les versions précédentes de Windows, les nombres à virgule flottante représentables exactement se terminant par « 5 » s’arrondissent toujours. IEEE 754 déclare qu’il doit arrondir au chiffre pair le plus proche (également appelé « arrondissement de Banker »). Par exemple, 1,5 et 2,5 doivent arrondir à 2. Auparavant, 1,5 passerait à 2 et 2,5 à 3. Cette modification affecte uniquement les nombres exactement représentables. Par exemple, 2,35 (qui, lorsqu’il est représenté en mémoire, est plus proche de 2.35000000000000008) continue à s’arrondir à 2,4. L’arrondi effectué par ces fonctions respecte désormais également le mode d’arrondi de virgule flottante défini par [fesetenv](fesetenv1.md). Auparavant, l’arrondi a toujours choisi FE_TONEAREST comportement. Cette modification affecte uniquement les programmes créés à l’aide de Visual Studio 2019 version 16,2 et versions ultérieures. Pour utiliser le comportement d’arrondi de virgule flottante hérité, liez avec [legacy_stdio_float_rounding. obj](../link-options.md).

## <a name="example"></a>Exemple

```C
// crt_printf.c
// This program uses the printf and wprintf functions
// to produce formatted output.

#include <stdio.h>

int main( void )
{
   char     ch = 'h',
            *string = "computer";
   wchar_t  wch = L'w',
            *wstring = L"Unicode";
   int      count = -9234;
   double   fp = 251.7366;

   // Display integers
   printf( "Integer formats:\n"
           "   Decimal: %d  Justified: %.6d  "
           "Unsigned: %u\n",
           count, count, count, count );

   // Display decimals
   printf( "Decimal %d as:\n   Hex: %Xh  "
           "C hex: 0x%x  Octal: %o\n",
            count, count, count, count );

   // Display in different radixes
   printf( "Digits 10 equal:\n   Hex: %i  "
           "Octal: %i  Decimal: %i\n",
            0x10, 010, 10 );

   // Display characters
   printf("Characters in field (1):\n"
          "%10c%5hc%5C%5lc\n",
          ch, ch, wch, wch);
   wprintf(L"Characters in field (2):\n"
           L"%10C%5hc%5c%5lc\n",
           ch, ch, wch, wch);

   // Display strings
   printf("Strings in field (1):\n%25s\n"
          "%25.4hs\n   %S%25.3ls\n",
          string, string, wstring, wstring);
   wprintf(L"Strings in field (2):\n%25S\n"
           L"%25.4hs\n   %s%25.3ls\n",
           string, string, wstring, wstring);

   // Display real numbers
   printf("Real numbers:\n   %f %.2f %e %E\n",
          fp, fp, fp, fp );

   // Display pointer
   printf( "\nAddress as:   %p\n", &count);
}
```

### <a name="sample-output"></a>Exemple de sortie

```Output
Integer formats:
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062
Decimal -9234 as:
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756
Digits 10 equal:
   Hex: 16  Octal: 8  Decimal: 10
Characters in field (1):
         h    h    w    w
Characters in field (2):
         h    h    w    w
Strings in field (1):
                 computer
                     comp
   Unicode                      Uni
Strings in field (2):
                 computer
                     comp
   Unicode                      Uni
Real numbers:
   251.736600 251.74 2.517366e+002 2.517366E+002

Address as:   0012FF3C
```

## <a name="see-also"></a>Voir aussi

[Syntaxe de spécification de format : fonctions printf et wprintf](../format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
[_set_output_format](../../c-runtime-library/set-output-format.md)<br/>
