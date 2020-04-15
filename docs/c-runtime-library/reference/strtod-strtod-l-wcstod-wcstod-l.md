---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 4/2/2020
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
- _o__strtod_l
- _o__wcstod_l
- _o_strtod
- _o_wcstod
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: a688846d5db4d508327745728f8933c91bfd54e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337665"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod, _strtod_l, wcstod, _wcstod_l

Convertissent les chaînes en valeur double précision.

## <a name="syntax"></a>Syntaxe

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*strSource (en)*<br/>
Chaîne se terminant par un caractère Null à convertir.

*endptr*<br/>
Pointeur désignant le caractère qui arrête l’analyse.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strtod** retourne la valeur du numéro de point flottant, sauf lorsque la représentation provoquerait un débordement, auquel cas la fonction retourne -/-**HUGE_VAL**. Le signe de **HUGE_VAL** correspond au signe de la valeur qui ne peut pas être représentée. **strtod** renvoie 0 si aucune conversion ne peut être effectuée ou un underflow se produit.

**wcstod** retourne des valeurs de façon analogue à **strtod**. Pour les deux fonctions, **errno** est réglé sur **ERANGE** en cas de débordement ou de sous-flux et si le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [La validation des paramètres](../../c-runtime-library/parameter-validation.md). Pour plus d’informations sur ce code de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chaque fonction convertit la chaîne d’entrée *strSource* en un **double**. La fonction **strtod** convertit *strSource* en une valeur de double précision. **strtod** cesse de lire la chaîne *strSource* au premier caractère qu’il ne peut pas reconnaître comme faisant partie d’un certain nombre. Il peut s’agir du caractère Null de fin. **wcstod** est une version à caractère large de **strtod;** son argument *strSource* est une chaîne de caractère large. Ces fonctions se comportent sinon de façon identique.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

Le **LC_NUMERIC** cadre de catégorie de la localisation actuelle détermine la reconnaissance du caractère de point radix dans *strSource*. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les fonctions sans le **suffixe _l** utilisent le lieu actuel; **_strtod_l** est identique à **_strtod_l** sauf qu’ils utilisent le *lieu* passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr n’est* pas **NULL**, un pointeur sur le personnage qui a arrêté l’analyse est stocké à l’emplacement indiqué par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base invalide a été spécifiée), la valeur de *strSource* est stockée à l’endroit indiqué par *endptr*.

**strtod** s’attend à ce que *strSource* pointe vers une série de l’une des formes suivantes :

[*espace blanc*] [*signe*] chiffres*digits* *[chiffres radix* *digits*] &#124; *les chiffres*de *radix* [e**e** &#124; *hexdigits* **E**'*sequence*[*signe*] *chiffres*] [ **NAN** **INFINITY***radix* *hexdigits**whitespace* *radix* *hexdigits**sign**whitespace* **0X***sign* **P***whitespace*] [*signe*] '**' ' ' ' ' '** &#124; ' ' ' ' ' ' ' ' ' ' '*sign*' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '**&#124;** **&#124;** &#124; ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '*'* ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '

*L’espace blanc* de premier plan optionnel peut se composer de caractères d’espace et d’onglet, qui sont ignorés ; *signe* est soit plus () ou moins (-); *les chiffres* sont un ou plusieurs chiffres décimaux; *hexdigits* sont un ou plusieurs chiffres hexadecimal; *le radix* est le caractère de point radix, soit une période (.) dans le lieu par défaut " C », soit la valeur locale spécifique si le lieu actuel est différent ou quand *le lieu* est spécifié ; une *séquence* est une séquence de caractères alphanumériques ou de souligner. Dans les formes décimales et hexadecimal de nombre, si aucun chiffre n’apparaît avant le caractère de point de radix, au moins un doit apparaître après le caractère de point de radix. Sous la forme décimale, les chiffres décimaux peuvent être suivis d’un exposant, qui se compose d’une lettre d’introduction (**e** ou **E**) et d’un intégrer signé en option. Sous la forme hexadecimal, les chiffres hexadecimal peuvent être suivis par un exposant, qui se compose d’une lettre d’introduction (**p** ou **P**) et d’un intégrger hexadecimal signé optionnellement qui représente l’exposant comme un pouvoir de 2. Dans l’une ou l’autre forme, si ni une partie exposante ni un caractère de point radix n’apparaissent, un caractère de point radix est supposé suivre le dernier chiffre de la chaîne. Le cas est ignoré dans les deux formes **INF** et **NAN.** Le premier personnage qui ne correspond pas à l’une de ces formes arrête l’analyse.

Les versions UCRT de ces fonctions ne prennent pas en charge la conversion de lettres exposantes de style Fortran (**d** ou **D).** Cette extension non standard était prise en charge par les versions antérieures de la bibliothèque CRT et peut être une modification avec rupture pour votre code. Les versions DE l’UCRT prennent en charge les chaînes hexadecimales et les aller-retours des valeurs INF et NAN, qui n’ont pas été prises en charge dans des versions antérieures. Cela peut également entraîner des modifications de rupture dans votre code. Par exemple, la chaîne "0x1a" serait interprétée par **strtod** comme 0.0 dans les versions précédentes, mais comme 26.0 dans la version UCRT.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtod**, **_strtod_l**|C : &lt;stdlib.h> C++ : &lt;cstdlib> ou &lt;stdlib.h> |
|**wcstod**, **_wcstod_l**|C : &lt;stdlib.h> ou &lt;wchar.h> C++ : &lt;cstdlib>, &lt;stdlib.h> ou &lt;wchar.h> |

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
