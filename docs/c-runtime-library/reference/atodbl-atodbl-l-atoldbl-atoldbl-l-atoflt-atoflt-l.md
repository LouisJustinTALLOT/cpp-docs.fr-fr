---
description: 'En savoir plus sur : _atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l'
title: _atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l
ms.date: 4/2/2020
api_name:
- _atoldbl
- _atoldbl_l
- _atodbl
- _atoflt
- _atoflt_l
- _atodbl_l
- _o__atodbl
- _o__atodbl_l
- _o__atoflt
- _o__atoflt_l
- _o__atoldbl
- _o__atoldbl_l
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _atoflt
- _atoflt_l
- atodbl_l
- atoflt_l
- _atoldbl
- _atoldbl_l
- atodbl
- _atodbl_l
- atoldbl
- atoflt
- atoldbl_l
- _atodbl
helpviewer_keywords:
- _atodbl function
- _atoldbl_l function
- atoflt function
- atoflt_l function
- atoldbl function
- _atoldbl function
- atodbl_l function
- _atoflt_l function
- atoldbl_l function
- atodbl function
- string conversion, to floating point values
- _atoflt function
- _atodbl_l function
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
ms.openlocfilehash: 28db01c76da7789b5887d5209d133a63dede8d4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117521"
---
# <a name="_atodbl-_atodbl_l-_atoldbl-_atoldbl_l-_atoflt-_atoflt_l"></a>_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l

Convertit une chaîne en valeur double (**_atodbl**), long double (**_atoldbl**) ou float (**_atoflt**).

## <a name="syntax"></a>Syntaxe

```C
int _atodbl( _CRT_DOUBLE * value, char * str );
int _atodbl_l ( _CRT_DOUBLE * value, char * str, locale_t locale );
int _atoldbl( _LDOUBLE * value, char * str );
int _atoldbl_l ( _LDOUBLE * value, char * str, locale_t locale );
int _atoflt( _CRT_FLOAT * value, const char * str );
int _atoflt_l( _CRT_FLOAT * value, const char * str, locale_t locale );
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Valeur de type double, long double ou float produite par la conversion de la chaîne en une valeur à virgule flottante. Ces valeurs sont encapsulées dans une structure.

*str*<br/>
Chaîne à analyser en vue de sa conversion en une valeur à virgule flottante.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Retourne 0 en cas de réussite. Les codes d’erreur possibles sont **_UNDERFLOW** ou **_OVERFLOW**, qui sont définis dans le fichier d’en-tête \<math.h> .

## <a name="remarks"></a>Notes

Ces fonctions convertissent une chaîne en une valeur à virgule flottante. La différence entre ces fonctions et la famille de fonctions **atof** est que ces fonctions ne génèrent pas de code à virgule flottante et n’entraînent pas d’exceptions matérielles. Au lieu de cela, les conditions d’erreur sont signalées en tant que codes d’erreur.

Si une chaîne n’a pas d’interprétation valide comme valeur à virgule flottante, la *valeur* est définie à zéro et la valeur de retour est zéro.

Les versions de ces fonctions qui ont le suffixe **_L** sont identiques aux versions qui n’ont pas le suffixe, à ceci près qu’elles utilisent les paramètres *régionaux* qui sont passés au lieu des paramètres régionaux du thread actuel.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routines|En-tête requis|
|--------------|---------------------|
|**_atodbl**, **_atoldbl** **_atoflt**<br /><br /> **_atodbl_l**, **_atoldbl_l** **_atoflt_l**|\<stdlib.h>|

## <a name="example"></a>Exemple

```C
// crt_atodbl.c
// Uses _atodbl to convert a string to a double precision
// floating point value.

#include <stdlib.h>
#include <stdio.h>

int main()
{
   char str1[256] = "3.141592654";
   char abc[256] = "abc";
   char oflow[256] = "1.0E+5000";
   _CRT_DOUBLE dblval;
   _CRT_FLOAT fltval;
   int retval;

   retval = _atodbl(&dblval, str1);

   printf("Double value: %lf\n", dblval.x);
   printf("Return value: %d\n\n", retval);

   retval = _atoflt(&fltval, str1);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // A non-floating point value: returns 0.
   retval = _atoflt(&fltval, abc);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // Overflow.
   retval = _atoflt(&fltval, oflow);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   return 0;
}
```

```Output
Double value: 3.141593
Return value: 0

Float value: 3.141593
Return value: 0

Float value: 0.000000
Return value: 0

Float value: inf
Return value: 3
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
