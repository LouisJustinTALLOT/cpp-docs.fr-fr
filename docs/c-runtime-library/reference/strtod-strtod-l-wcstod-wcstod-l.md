---
title: strtod, _strtod_l, wcstod, _wcstod_l | Microsoft Docs
ms.custom: ''
ms.date: 10/20/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
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
dev_langs:
- C++
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b1e9971b4e4287b9a7578cf1295ed3c6f5cca1e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod, _strtod_l, wcstod, _wcstod_l

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

## <a name="return-value"></a>Valeur de retour

**strtod** retourne la valeur du nombre à virgule flottante, sauf lorsque la représentation sous forme de provoquerait un dépassement de capacité, dans ce cas, la fonction renvoie + et-**HUGE_VAL**. Le signe de **HUGE_VAL** correspond à la connexion de la valeur ne peut pas être représentée. **strtod** retourne 0 si aucune conversion n’est possible ou un dépassement de capacité négatif se produit.

**wcstod** renvoie les valeurs comme **strtod**. Pour les deux fonctions, **errno** a la valeur **ERANGE** si dépassement de capacité positif ou négatif se produit et le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Pour plus d’informations sur ce code de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chaque fonction convertit la chaîne d’entrée *strSource* à un **double**. Le **strtod** fonction convertit *strSource* en valeur double précision. **strtod** arrête la lecture de la chaîne *strSource* au premier caractère qu’il ne peut pas identifier en tant que partie d’un nombre. Il peut s’agir du caractère Null de fin. **wcstod** est une version à caractères larges de **strtod**; sa *strSource* argument est une chaîne à caractères larges. Ces fonctions se comportent sinon de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

Le **LC_NUMERIC** paramètre de catégorie de paramètres régionaux actuels détermine la reconnaissance du caractère point radix dans *strSource*. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les fonctions sans le **_l** suffixe utilisent les paramètres régionaux ; **_strtod_l** est identique à **_strtod_l** , sauf qu’elles utilisent le *paramètres régionaux* passés à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’est pas **NULL**, un pointeur vers le caractère qui l’a arrêté l’analyse est stocké à l’emplacement vers lequel pointé *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stocké à l’emplacement vers lequel pointé *endptr*.

**strtod** attend *strSource* pour pointer vers une chaîne de l’une des formes suivantes :

[*espace blanc*] [*signe*] {*chiffres* [*radix* *chiffres*] &#124;  *radix* *chiffres*} [{**e** &#124; **E**} [*signe*] *chiffres*] [*espace blanc*] [*signe*] {**0 x** &#124; **0 X**} {*hexdigits* [ *radix* *hexdigits*] &#124; *radix* *hexdigits*} [{**p** &#124; **P**} [*signe*] *hexdigits*] [*espace blanc*] [*signe*] {} **INF** &#124; **infini**} [*espace blanc*] [*signe*]  **NAN** [*séquence*]

L’interligne facultatif *espace blanc* peut contenir les caractères espace et la tabulation, qui sont ignorés ; *connexion* est plus (+) ou moins (-) ; *chiffres* sont un ou plusieurs chiffres décimaux ; *hexdigits* sont un ou plusieurs chiffres hexadécimaux ; *radix* est le caractère de point de base, un point (.) dans le paramètres régionaux « C » par défaut, ou les paramètres régionaux spécifiques valeur si les paramètres régionaux actuels sont différent ou lorsque *paramètres régionaux* est spécifié ; une *séquence* est une séquence d’alphanumériques ou traits de soulignement. Dans les formulaires nombres décimales et hexadécimales, si aucun chiffre ne s’affiche avant le caractère de point de base, au moins un doit apparaître après le caractère de point de base. Sous la forme décimale, les chiffres décimaux peuvent être suivies d’un exposant, qui se compose d’une lettre d’introduction (**e** ou **E**) et d’un entier signé si vous le souhaitez. Dans le format hexadécimal, les chiffres hexadécimaux peuvent être suivies d’un exposant, qui se compose d’une lettre d’introduction (**p** ou **P**) et éventuellement hexadécimal entier signé qui représente le exposant en tant qu’une puissance de 2. Sous une forme, si une partie exposant, ni un caractère de point de base s’affiche, un caractère de point de base est censé pour suivre le dernier chiffre dans la chaîne. La casse est ignorée dans les deux le **INF** et **NAN** forms. Le premier caractère qui ne tient pas un de ces formulaires s’arrête l’analyse.

Les versions UCRT de ces fonctions ne prennent pas en charge la conversion de type Fortran (**d** ou **D**) lettres exposant. Cette extension non standard était prise en charge par les versions antérieures de la bibliothèque CRT et peut être une modification avec rupture pour votre code. Les versions de la bibliothèque UCRT prend en charge les chaînes hexadécimales et aller-retour de valeurs INF et NAN, qui n’étaient pas pris en charge dans les versions antérieures. Cela peut également entraîner des modifications avec rupture dans votre code. Par exemple, la chaîne « 0x1a » est interprétée par **strtod** comme 0.0 dans les versions précédentes, mais comme 26.0 dans la version de l’UCRT.

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
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
