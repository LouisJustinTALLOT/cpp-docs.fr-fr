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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 03bd90d2848922ee4153b79432bb76245f749ed6
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813575"
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

*strSource*<br/>
Chaîne se terminant par un caractère Null à convertir.

*endptr*<br/>
Pointeur désignant le caractère qui arrête l’analyse.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**strtod** retourne la valeur du nombre à virgule flottante, sauf lorsque la représentation provoque un dépassement de capacité, auquel cas la fonction retourne +/-**HUGE_VAL**. Le signe de **HUGE_VAL** correspond au signe de la valeur qui ne peut pas être représentée. **strtod** retourne `0` si aucune conversion ne peut être effectuée ou si un dépassement de capacité négatif se produit.

**wcstod** retourne des valeurs analogues à **strtod**:

- Pour les deux fonctions, **errno** a la valeur **ERANGE** si le dépassement de capacité positif ou négatif se produit.
- S’il existe des paramètres non valides, **errno** a la valeur **EINVAL** et le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur ce code de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Remarques

Chaque fonction convertit la chaîne d’entrée *strSource* en valeur **double**. La fonction **strtod** convertit *strSource* en valeur double précision. **strtod** arrête de lire la chaîne *strSource* au premier caractère qu’elle ne peut pas reconnaître comme faisant partie d’un nombre. Ce caractère peut être le caractère null de fin. **wcstod** est une version à caractères larges de **strtod**; son argument *strSource* est une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

Le paramètre de catégorie **LC_NUMERIC** des paramètres régionaux actuels détermine la reconnaissance du caractère de point de base dans *strSource*. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les fonctions sans suffixe **_L** utilisent les paramètres régionaux actuels ; **_strtod_l** est identique à **_strtod_l** sauf qu’ils utilisent à la place les *paramètres régionaux* transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’est pas **null**, un pointeur vers le caractère qui a arrêté l’analyse est stocké à l’emplacement désigné par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stockée à l’emplacement désigné par *endptr*.

**strtod** s’attend à ce que *strSource* pointe vers une chaîne de l’une des formes suivantes :

[*espace blanc*] [*signe*] {*digits* digits [ *chiffres*de*base* ] &#124; les *chiffres*de *base* } [{**e** &#124; **e**} [*signe*] *chiffres*] [*espace*] [*signe*] {**0x** &#124; **0x**} {*hexdigits* [*radix* *hexdigits*] &#124; *base* *hexdigits*} [{**p** &#124; **p**} [*Sign*] *hexdigits*] [*Whitespace*] [*Sign*] {**INF** &#124; **infini**} [*blanc*] [*Sign*] **Nan** [*Sequence*]

L’espace *blanc* de début facultatif peut être constitué d’espaces et de caractères de tabulation, qui sont ignorés ; le *signe* est plus (+) ou moins (-); les *chiffres* correspondent à un ou plusieurs chiffres décimaux ; *hexdigits* sont un ou plusieurs chiffres hexadécimaux ; la *base* est le caractère de point de base, soit un point (.) dans les paramètres régionaux « C » par défaut, soit une valeur spécifique aux paramètres régionaux si les paramètres régionaux actuels sont différents ou lorsque les *paramètres régionaux* sont spécifiés ; une *séquence* est une séquence de caractères alphanumériques ou de traits de soulignement. Dans les formes numériques décimales et hexadécimales, si aucun chiffre n’apparaît avant le caractère de point de base, au moins un doit apparaître après le caractère de point de base. Dans la forme décimale, les chiffres décimaux peuvent être suivis d’un exposant, qui se compose d’une lettre d’introduction (**e** ou **e**) et d’un entier signé éventuellement. Au format hexadécimal, les chiffres hexadécimaux peuvent être suivis d’un exposant, qui se compose d’une lettre d’introduction (**p** ou **p**) et d’un entier hexadécimal éventuellement signé qui représente l’exposant comme une puissance de 2. Dans l’un ou l’autre formulaire, s’il n’existe pas de partie exposant ou de point de base, un caractère point de base est supposé suivre le dernier chiffre dans la chaîne. La casse est ignorée dans les formulaires **INF** et **Nan** . Le premier caractère qui ne correspond pas à l’une de ces formes arrête l’analyse.

Les versions UCRT de ces fonctions ne prennent pas en charge la conversion des lettres d’exposant de style Fortran (**d** ou **d**). Cette extension non standard était prise en charge par les versions antérieures de la bibliothèque CRT et peut être une modification avec rupture pour votre code. Les versions UCRT prennent en charge les chaînes hexadécimales et les allers-retours des valeurs INF et NAN, qui n’étaient pas prises en charge dans les versions antérieures. Cela peut également entraîner des modifications avec rupture dans votre code. Par exemple, la chaîne « 0x1A » est interprétée par **strtod** comme 0,0 dans les versions précédentes, mais comme 26,0 dans la version de UCRT.

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
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Interprétation des séquences de caractères multioctets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Fonctions de chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
