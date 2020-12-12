---
description: 'En savoir plus sur : strtof, _strtof_l, wcstof, _wcstof_l'
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 4/2/2020
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
- _o__strtof_l
- _o__wcstof_l
- _o_strtof
- _o_wcstof
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: 7a73df80fefb8d86431027650be2ecd236135dfd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322418"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof, _strtof_l, wcstof, _wcstof_l

Convertit les chaînes en valeur à virgule flottante simple précision.

## <a name="syntax"></a>Syntaxe

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>Paramètres

*strSource*<br/>
Chaîne se terminant par un caractère Null à convertir.

*endptr*<br/>
Pointeur désignant le caractère qui arrête l’analyse.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**strtof** retourne la valeur du nombre à virgule flottante, sauf lorsque la représentation provoque un dépassement de capacité, auquel cas la fonction retourne +/-**HUGE_VALF**. Le signe de **HUGE_VALF** correspond au signe de la valeur qui ne peut pas être représentée. **strtof** retourne 0 si aucune conversion ne peut être effectuée ou si un dépassement de capacité négatif se produit.

**wcstof** retourne des valeurs de façon analogue à **strtof**. Pour les deux fonctions, **errno** a la valeur **ERANGE** si le dépassement de capacité positif ou négatif se produit et que le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chaque fonction convertit la chaîne d’entrée *strSource* en **`float`** . La fonction **strtof** convertit *strSource* en valeur à précision simple. **strtof** arrête de lire la chaîne *strSource* au premier caractère qu’elle ne peut pas reconnaître comme faisant partie d’un nombre. Il peut s’agir du caractère Null de fin. **wcstof** est une version à caractères larges de **strtof**; son argument *strSource* est une chaîne de caractères larges. Sinon, ces fonctions se comportent de façon identique.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

Le paramètre de catégorie **LC_NUMERIC** des paramètres régionaux actuels détermine la reconnaissance du caractère de base dans *strSource*; Pour plus d’informations, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les fonctions qui n’ont pas le suffixe **_L** utilisent les paramètres régionaux actuels ; celles qui ont le suffixe sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’a pas la **valeur null**, un pointeur vers le caractère qui a arrêté l’analyse est stocké à l’emplacement désigné par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stockée à l’emplacement désigné par *endptr*.

**strtof** attend que *strSource* pointe vers une chaîne au format suivant :

[*espace blanc*] [*signe*] [*chiffres*] [__.__ *chiffres*] [{**e** &#124; **e**} [*signe*] *chiffres*]

Un espace *blanc* peut se composer d’espaces et de caractères de tabulation, qui sont ignorés ; *Sign* est un signe plus ( **+** ) ou moins ( **-** ); et les *chiffres* correspondent à un ou plusieurs chiffres décimaux. Si aucun chiffre n’apparaît avant le caractère de base, il doit en figurer au moins un après le caractère de base. Les chiffres décimaux peuvent être suivis d’un exposant, qui se compose d’une lettre d’introduction (**e** ou **e**) et d’un entier signé éventuellement. S’il n’apparaît ni exposant ni caractère de base, il est supposé qu’un caractère de base suit le dernier chiffre dans la chaîne. Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse.

Les versions UCRT de ces fonctions ne prennent pas en charge la conversion des lettres d’exposant de style Fortran (**d** ou **d**). Cette extension non standard était prise en charge par les versions antérieures de la bibliothèque CRT et peut être une modification avec rupture pour votre code.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C : \<stdlib.h> C++ : &lt; cstdlib> ou \<stdlib.h>|
|**wcstof**, **_wcstof_l**|C : \<stdlib.h> ou \<wchar.h> C++ : &lt; cstdlib>, \<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Interprétation des séquences de Multibyte-Character](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Fonctions de chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
